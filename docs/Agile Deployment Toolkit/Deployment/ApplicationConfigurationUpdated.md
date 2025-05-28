**This toolkit does not allow updates to configuration files (such as wp-config.php or configuration.php) through the application's GUI system.**

Instead use the following process which will automatically update all of your webserver configurations in one go. What this means is that if you have 4 webservers running, if you follow this process on one of them, then the changes you make to the application configuration on that one server will be pushed to the other 3 webservers that are running. 

So, if you want to update your, for example, Joomla "configuration.php" file or your Wordpress "wp-config.php" files, then this is the way to go about it.  
Changing the application configuration on one webserver and having the change pushed out to all your webservers is powerful but also requires caution because a change made to a configuration file with errors in it could take your whole website offline.

**Updating your applications configuration in a multi-webserver configuration**

- Login to one of your webservers using the helperscript on your build machine
-  Run the script:

>     /usr/bin/changing_config 

- Go to

>     ${HOME}/runtime

and make your updates to the appropriate (depending on which application type you are using) configuration file, one of, 

>     joomla_configuration.php, wordpress_config.php, drupal_settings.php, moodle_config.php

- Once your updates are made to your configuration file run the script

>     /usr/bin/config

to push the changes you have made to your S3 config datastore bucket. So, the '/usr/bin/config' will push your changes to all your webservers. The script performs syntax checking which has to be passed before the changes you make are accepted by the system. 

- Run the script:

>     /usr/bin/changed_config

Configuration changes you make using the application's GUI system to an individual webserver will be overwritten by default. The reason for this is that when you have say 8 webservers running if you use the GUI system to make your configuration updates it will only update one of the webservers and the rest will remain as they were because this system doesn't use shared filesystems for the webserver webroot. You can't tell which webserver you have updated and which webserver you haven't. I chose to make needed update changes to the 

>     ${HOME}/runtime/<config-file>

and have that changed file accepted as the authoritative configuration file instead and push the changes out to other webservers from there there in a conscious and deliberate way. 

If you make a change to 

>     ${HOME}/runtime/<config-file>

and then run /usr/bin/config, here are the steps that the system goes through to push the changes you have made to all webservers.

- The script

>     ${HOME}/application/configuration/ApplicationConfigurationUpdate.sh

will be run and this will run a syntax check and copy the configuration file to the S3 datastore.

- Every minute, each webserver looks for an updated configuration file for the installed application type when the script:

>     ${HOME}/application/configuration/SetApplicationConfiguration.sh

is run. When this script is run and a new configuration file is discovered in the S3 datastore, the new configuration file is copied by the current webserver and each other webserver in turn to their

>     ${HOME}/runtime

directory where a second syntax check is made using PHP validation. If the syntax check is passed, then the new configuration file that the current webserver has retrived from the datastore is presumed to be valid and is copied to the current applications configuration file location under the directory

>     /var/www/html/


If all has gone well,then the applications configuration will have been updated
