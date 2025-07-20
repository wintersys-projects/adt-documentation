## QUICK-START DEMOS  

**NOTE:** These quick start demos are only intended for use on the Linode platform using the supplied [StackScript](https://cloud.linode.com/stackscripts/635271) to demonstrate example usage cases for the Agile Deployment Toolkit as quickly and easily as possible.  The demos themselves are very quickly put together simply there for illustrative purposes they are not there to provide any truly useful function. If anyone would like to spend time crafting demos useful for real function that could be listed here that would be valued. 

The purpose of these quick start demos is to show you that with just some parameters you can achieve a lot using the Agile Deployment Toolkit with the possibility of going much deeper into it if you choose to.

For more information about parameter configuration please see the [spec](https://github.com/wintersys-projects/adt-build-machine-scripts/blob/main/templatedconfigurations/specification.md) and [quickspec](https://github.com/wintersys-projects/adt-build-machine-scripts/blob/main/templatedconfigurations/quick_specification.dat)

**These initial steps are only required the first time you make a deployment. The result of these first steps can be used repeatedly for subsequent demo deployments.** 

--------------------------
<span style="color:red">**YOUR ONE TIME MANDATORY PREPARATORY STEPS**</span>

--------------------------

There are mandatory steps to follow in full before any of the demos can be deployed.

If you are a beginner, follow [here](./QuickStartDemosPrepBeginnerLevel.md)  
If you are an expert, follow [here](./QuickStartDemosPrepExpertLevel.md)  

The last thing you should have done in completing these preparatory steps is "Create Linode" and then wait for the servers to deploy.

Once you click "**Create Linode**", the build will deploy which will take some minutes. 

Once the build is completed (or earlier if you like, once the build machine is up) you can get the IP address of your build machine through the Linode GUI system (in my case: 172.237.116.127)

![](images/lin1.png "Linode Tutorial Image 1")

You can ssh onto the build machine once it has started up with

>      ssh -p <build-machine-port> <username>@<build-machine-ip>

then do a

>      sudo su <password as per the value you entered for 'The password for your build machine user (required)' into the StackScript>
>      cd adt-build-machine-scripts
>      ./Logs.sh

**Note 1:**

Be aware that a new SSL certificate is issued each time you run this Stackscript which means that if you do multiple deployments you will run into "rate limiting" problems. If you need to perform multiple build cycles for a particular domain you are best off using the expedited method as described [here](<../Tutorials/linode/FOLLOW ME.md>). You can also set SSL_LIVE_CERT to 0 to use a staging certificate which doesn't have such restrictive rate limiting as a production certificate but it will likely give you a browser security warning when you access your website. 

**Note 2:**

Once the build has completed you might have to give the Linode DNS system a few minutes to refresh with the IP address that has been added for this build. 

**Note 3:** 

If you are using the Linode DNS system which you are by default then you might need to clear your broswer's DNS cache between deployments for the website to display. In Chrome you can do this by going to "**chrome://net-internals/#dns**"


--------------------------
<span style="color:red">**After you have performed all the pre-requisite steps above, you can choose which demo you want to follow from those listed below**</span>

--------------------------

### Demo 1 (Sample Community Builder Joomla application) 

[Community Builder](https://www.joomlapolis.com)

1. Follow the all the pre-requisite at the top of this page 
2. You can play with additional settings such as machine size and so on in any of these demos, but, this first demo application should install without needing any additional steps above and beyond what is outlined in the pre-requisite steps.   
3. Once the application is installed, the username is "webmaster" and the password is "mnbcxz098321QQZZ". There are also test users and their usernames and passwords are: "testuser1" and "mnbcxz098321QQZZ" and "testuser2" "mnbcxz098321QQZZ"

---------------------------

### Demo 2 (Sample Joomla Application)

This is just a sample joomla install with some sample data installed 

1. Assuming that you have your valid credentials in your credentials file on your laptop (if you don't know what this is, go to the beginning of this document and start there) follow the steps in "POPULATE YOUR STACKSCRIPT" above.
2. Once the steps in POPULATE YOUR STACKCRIPT have been followed fully, make the following additional changes to the advanced settings of your Stackscript.
3. Once the application is installed, the username is "webmaster" and the password is "mnbcxz098321QQQZZZ".
 
>      set "The Display name for your website e.g. My Demo Website" to "My Joomla Demo"  
>      set "BASELINE DB REPOSITORY" to "joomlademo-db-baseline" 
>      set "APPLICATION BASELINE SOURCECODE REPOSITORY" to "joomlademo-webroot-sourcecode-baseline"  

---------------------------

### Demo 3 (Sample Joomla Astroid Application) 

[Astroid Framework](https://astroidframe.work/)

This is just a sample joomla install with the astroid framework installed

1. Assuming that you have your valid credentials in your credentials file on your laptop (if you don't know what this is, go to the beginning of this document and start there) follow the steps in "POPULATE YOUR STACKSCRIPT" above.
2. Once the steps in POPULATE YOUR STACKCRIPT have been followed fully, make the following additional changes to the advanced settings of your Stackscript.  
 
>      set "The Display name for your website e.g. My Demo Website" to "My Astroid Demo"   
>      set "BASELINE DB REPOSITORY" to "astroid-db-baseline" 
>      set "APPLICATION BASELINE SOURCECODE REPOSITORY" to "astroid-webroot-sourcecode-baseline"   

Once the application is installed, the username is "admin" and the password is "mnbcxz098321QQZZ"

----------------------------
### Demo 4 (Sample Joomla Kunena Application) 

[Kunena](https://www.kunena.org)

This is just a sample joomla install with the kunena forum installed

1. Assuming that you have your valid credentials in your credentials file on your laptop (if you don't know what this is, go to the beginning of this document and start there) follow the steps in "POPULATE YOUR STACKSCRIPT" above.
2. Once the steps in POPULATE YOUR STACKCRIPT have been followed fully, make the following additional changes to the advanced settings of your Stackscript.
 
>     set "The Display name for your website e.g. My Demo Website" to "My Kunena Demo"   
>     set "BASELINE DB REPOSITORY" to "kunena-db-baseline" 
>     set "APPLICATION BASELINE SOURCECODE REPOSITORY" to "kunena-webroot-sourcecode-baseline"   

Once the application is installed, the username is "webmaster" and the password is "mnbcxz098321QQZZ"

----------------------------

### Demo 5 (Sample Joomlart Free Templates Example Applications) 

1. Assuming that you have your valid credentials in your credentials file on your laptop (if you don't know what this is, go to the beginning of this document and start there) follow the steps in "POPULATE YOUR STACKSCRIPT" above.
2. Once the steps in POPULATE YOUR STACKCRIPT have been followed fully, make the following additional changes to the advanced settings of your Stackscript.

#### Demo JA Template One  

[Joomlart Purity](https://www.joomlart.com/joomla/templates/ja-purity-iv)
This is just a sample joomla install with the purity template installed 

>     set "BASELINE DB REPOSITORY" to "purity-db-baseline" 
>     set "APPLICATION BASELINE SOURCECODE REPOSITORY" to "purity-webroot-sourcecode-baseline"   

OR  

#### Demo JA Template Two  
[Joomlart Stark](https://www.joomlart.com/joomla/templates/ja-stark)
This is just a sample joomla install with the stark template installed 

>     set "BASELINE DB REPOSITORY" to "stark-db-baseline" 
>     set "APPLICATION BASELINE SOURCECODE REPOSITORY" to "stark-webroot-sourcecode-baseline"  

OR 

#### Demo JA Template Three  
[Joomlart Campaign](https://www.joomlart.com/joomla/templates/ja-campaign)
This is just a sample joomla install with the stark template installed 

>     set "BASELINE DB REPOSITORY" to "campaign-db-baseline" 
>     set "APPLICATION BASELINE SOURCECODE REPOSITORY" to "campaign-webroot-sourcecode-baseline"    


Once the application is installed, the username is "webmaster" and the password is "mnbcxz098321QQZZ"

----------------------------

### Demo 6 (Sample Wordpress Application)

This is just a sample wordpress template with some sample data installed which will show you how you can get a pre-built site up and running with this toolkit

1. Assuming that you have your valid credentials in your credentials file on your laptop (if you don't know what this is, go to the beginning of this document and start there) follow the steps in "POPULATE YOUR STACKSCRIPT" above.
2. Once the steps in POPULATE YOUR STACKCRIPT have been followed fully, make the following additional changes to the advanced settings of your Stackscript.
 
>     set "The Display name for your website e.g. My Demo Website" to "My Wordpress Demo"  
>     set "APPLICATION" to "wordpress"  
>     set "APPLICATION IDENTIFIER" to "2"  
>     set "BASELINE DB REPOSITORY" to "wordpressdemo-db-baseline" 
>     set "APPLICATION BASELINE SOURCECODE REPOSITORY" to "wordpressdemo-webroot-sourcecode-baseline"  

---------------------------

### Demo 7 (Sample Drupal Based Opensocial Application)

[Opensocial](https://getopensocial.com)

1. Assuming that you have your valid credentials in your credentials file on your laptop (if you don't know what this is, go to the beginning of this document and start there) follow the steps in "POPULATE YOUR STACKSCRIPT" above.
2. Once the steps in POPULATE YOUR STACKCRIPT have been followed fully, make the following additional changes to the advanced settings of your Stackscript.
 
>     set "The Display name for your website e.g. My Demo Website" to "My Opensocial Demo"  
>     set "APPLICATION" to "drupal"  
>     set "APPLICATION IDENTIFIER" to "3"  
>     set "BASELINE DB REPOSITORY" to "opensocial-db-baseline" (with sample data) or "opensocialvanilla-db-baseline" (without sample data)  
>     set "APPLICATION BASELINE SOURCECODE REPOSITORY" to "opensocial-webroot-sourcecode-baseline" (with sample data) or "opensocialvanilla-webroot-sourcecode-baseline" (without sample data)  

Once the application is installed, the username is "webmaster" and the password is "mnbcxz098321QQQZZZ"  

---------------------------

### Demo 8 (Virgin Joomla install)  

1. Assuming that you have your valid credentials in your credentials file on your laptop (if you don't know what this is, go to the beginning of this document and start there) follow the steps in "POPULATE YOUR STACKSCRIPT" above.
2. Once the steps in POPULATE YOUR STACKCRIPT have been followed fully, make the following additional changes to the advanced settings of your Stackscript.

>     set "The number (1, 2 or 3) of the template you are using" to "1"  
>     set "The Display name for your website e.g. My Demo Website" to "My Joomla Demo"  
>     set "APPLICATION" to "joomla"  
>     set "APPLICATION IDENTIFIER" to "1"  
>     set "JOOMLA VERSION" and set it to the latest version of Joomla for example, "5.1.2"  
>     set "BUILD CHOICE" to "0"  
>     set "BUILD ARCHIVE CHOICE" to "virgin"  
>     set "BASELINE DB REPOSITORY" to "VIRGIN"  
>     set "APPLICATION BASELINE SOURCECODE REPOSITORY" to "JOOMLA:5.1.2"  


You can then deploy your Linode using your Stackscript and wait for your Joomla install will come online at the URL you specified in your stackscript

To find your database credentials log on to your build machine and do the following:

>     root@localhost:/home/agile-deployer/adt-build-machine-scripts# ./Log.sh
>     Which cloudhost do you want to view logs for DigitalOcean (do), Exoscale (exo), Linode (lin) or Vultr (vul)
>     Please type one of do, exo, lin, vul
>     lin
>     What is the build identifier you want to connect to?
>     You have these builds to choose from: 
>     testbuild
>     Please enter the name of the build of the server you wish to connect with
>     testbuild
>     tail (t) or cat (c) or vim (v)
>     c
>     Do you want out (1) or err (2) or stat (3)
>     1
>     ###############################################################################################################################
>     OK, I'll be kind and show you one time your joomla database credentials
>     Please make a note of them but remember to keep them safe and secret
>     You can enter them in the GUI system when you install the application
>     #########################################
>     Database name: nictmksgrn
>     Database username: u6jy8wvuru
>     Database password: pp7jem8cnp
>     #########################################
>     The database public IP address is: 172.236.3.58
>     The database private IP address is: 10.0.1.4 (try this one first from your application if it timesout, try the public one)
>     The database port is 2035
>     You can make up your own database prefix but make sure to include the '_' character at the end of your prefix (for example 'dbprefix_')
>     #########################################
>     You are not using the default port for your database
>     REMEMBER to tell joomla this by putting the database hostname as 10.0.1.4:2035 when you enter it in the GUI during the install process

You will need to wait for a minute before the _J security check file is removed which this system does automatically for you before you can proceed to completion of the installation

---------------------------

### Demo 9 (Virgin Wordpress install)  

1. Assuming that you have your valid credentials in your credentials file on your laptop (if you don't know what this is, go to the beginning of this document and start there) follow the steps in "POPULATE YOUR STACKSCRIPT" above.
2. Once the steps in POPULATE YOUR STACKCRIPT have been followed fully, make the following additional changes to the advanced settings of your Stackscript.


>     set "The number (1, 2 or 3) of the template you are using" to "1"  
>     set "The Display name for your website e.g. My Demo Website" to "My Wordpress Demo"  
>     set "APPLICATION" to "wordpress"  
>     set "APPLICATION IDENTIFIER" to "2"  
>     set "BUILD CHOICE" to "0"  
>     set "BUILD ARCHIVE CHOICE" to "virgin"  
>     set "BASELINE DB REPOSITORY" to "VIRGIN"  
>     set "APPLICATION BASELINE SOURCECODE REPOSITORY" to "WORDPRESS"    

You can then deploy your Linode using your Stackscript and wait for your Wordpress install will come online 

To find your database credentials log on to your build machine and do the following:

>     root@localhost:/home/agile-deployer/adt-build-machine-scripts# ./Log.sh
>     Which cloudhost do you want to view logs for DigitalOcean (do), Exoscale (exo), Linode (lin) or Vultr (vul)
>     Please type one of do, exo, lin, vul
>     lin
>     What is the build identifier you want to connect to?
>     You have these builds to choose from: 
>     testbuild
>     Please enter the name of the build of the server you wish to connect with
>     testbuild
>     tail (t) or cat (c) or vim (v)
>     c
>     Do you want out (1) or err (2) or stat (3)
>     1
>     OK, I'll be kind and show you one time your wordpress database credentials.
>     Please make a note of them but remember to keep them safe and secret
>     You can enter them in the GUI system when you install the application
>     #########################################
>     Database name: nmrwrhhgqn
>     Database username: u34krmarsu
>     Database password: pxkrdithvp
>     #########################################
>     The database public IP address is: 172.237.96.84
>     The database private IP address is: 10.0.1.5 (try this one first from your application if it timesout, try the public one)
>     The database port is 2035
>     You can make up your own database prefix but make sure to include the '_' character at the end of your prefix (for example 'dbprefix_')
>     #########################################
>     You are not using the default port for your database
>     REMEMBER to tell wordpress this by putting the database hostname as 10.0.1.5:2035 when you enter it in the GUI during the install process
>     ######################################
>     =========================================================================================================================================
>     If you have trouble accessing your new wordpress site, one thing that might be wrong is permalinks within wordpress
>     In this case, go to https://<dns-name>/wp-admin, login and rebuild permalinks under settings->permalinks
 
-----------------------

### Demo 10 (Virgin Drupal install)  

1. Assuming that you have your valid credentials in your credentials file on your laptop (if you don't know what this is, go to the beginning of this document and start there) follow the steps in "POPULATE YOUR STACKSCRIPT" above.
2. Once the steps in POPULATE YOUR STACKCRIPT have been followed fully, make the following additional changes to the advanced settings of your Stackscript. 

>     set "The number (1, 2 or 3) of the template you are using" to "1"  
>     set "The Display name for your website e.g. My Demo Website" to "My Drupal Demo" 
>     set "APPLICATION" to "drupal"   
>     set "APPLICATION IDENTIFIER" to "3"  
>     set "DRUPAL VERSION" set it to the latest version of drupal for example, "10.0.10" 
>     set "BUILD CHOICE" to "0"  
>     set "BUILD ARCHIVE CHOICE" to "virgin"   
>     set "BASELINE DB REPOSITORY" to "VIRGIN"  
>     set "APPLICATION BASELINE SOURCECODE REPOSITORY" to "DRUPAL:10.0.10"   

You can then deploy your Linode using your Stackscript and wait for your Drupal install will come online  

You can install "Opensocial" or "Drupal CMS" by making the following modifications to the 9 settings that you made in this demo.   

**OPENSOCIAL**  

To install [OPENSOCIAL](https://www.getopensocial.com/) make the following modification to the steps above:

At the time of writing, PHP8.1 is the highest supported version of PHP by opensocial so you need to set these values to install opensocial 
>     set "PHP VERSION" to "8.1"
>     set "The Display name for your website e.g. My Demo Website" to "My Opensocial Demo"  
>     set "APPLICATION BASELINE SOURCECODE REPOSITORY" to "DRUPAL:social"

**DRUPAL CMS**  

You can install [DRUPAL CMS](https://new.drupal.org/drupal-cms) by making the modification to the steps above:

>     set "The Display name for your website e.g. My Demo Website" to "My Druapl CMS Demo"  
>     set "APPLICATION BASELINE SOURCECODE REPOSITORY" to "DRUPAL:cms"

>     root@localhost:/home/agile-deployer/adt-build-machine-scripts# ./Log.sh
>     Which cloudhost do you want to view logs for DigitalOcean (do), Exoscale (exo), Linode (lin) or Vultr (vul)
>     Please type one of do, exo, lin, vul
>     lin
>     What is the build identifier you want to connect to?
>     You have these builds to choose from: 
>     testbuild
>     Please enter the name of the build of the server you wish to connect with
>     testbuild
>     tail (t) or cat (c) or vim (v)
>     c
>     Do you want out (1) or err (2) or stat (3)
>     1
>     OK, I'll be kind and show you one time your drupal database credentials.
>     Please make a note of them but remember to keep them safe and secret
>     You can enter them in the GUI system when you install the application
>     #########################################
>     Database name: n0i6qxap3n
>     Database username: uxzpsfznqu
>     Database password: pvhflpebvp
>     #########################################
>     The database public IP address is: 172.236.31.76
>     The database private IP address is: 10.0.1.4 (try this one first from your application if it timesout, try the public one)
>     The database port is 2035
>     You can make up your own database prefix but make sure to include the '_' character at the end of your prefix (for example 'dbprefix_')
>     #########################################
>     ####################################################################
>     Waiting for the application install to have been completed at: https://<dns-url>/core/install.php
>     Use the credentials listed above please

--------------------------

### Demo 11 (Virgin Moodle install)  

1. Assuming that you have your valid credentials in your credentials file on your laptop (if you don't know what this is, go to the beginning of this document and start there) follow the steps in "POPULATE YOUR STACKSCRIPT" above.
2. Once the steps in POPULATE YOUR STACKCRIPT have been followed fully, make the following additional changes to the advanced settings of your Stackscript.

>     set "The number (1, 2 or 3) of the template you are using" to "1"  
>     set "The Display name for your website e.g. My Demo Website" to "My Moodle Demo"  
>     set "APPLICATION" to "moodle"  
>     set "APPLICATION IDENTIFIER" to "4"  
>     set "BUILD CHOICE" to "0"  
>     set "BUILD ARCHIVE CHOICE" to "virgin"  
>     set "BASELINE DB REPOSITORY" to "VIRGIN"  
>     set "APPLICATION BASELINE SOURCECODE REPOSITORY" to "MOODLE"   

You can then deploy your Linode using your Stackscript and wait for your Moodle install will come online  
Once moodle is installed, I go to demo.nuocial.org.uk/index.php and you should do the same for your domain.

>     OK, I'll be kind and show you one time your moodle database credentials.
>     Please make a note of them but remember to keep them safe and secret
>     You can enter them in the GUI system when you install the application
>     #########################################
>     Database name: nhoz7thefn
>     Database username: ua2dtr1wbu
>     Database password: panh53iiap
>     #########################################
>     The database public IP address is: 172.236.8.173
>     The database private IP address is: 10.0.1.4 (try this one first from your application if it timesout, try the public one)
>     The database port is 2035
>     You can make up your own database prefix but make sure to include the '_' character at the end of your prefix (for example 'dbprefix_')
>     #########################################
>     ####################################################################
>     Moodle should be available at: https://<your-dns>
>     ####################################################################

----------------------------

### Demo 12 (Sample Virgin Joomla Install from a Baseline Repository)

This is just a sample joomla install there's no sample data or anything it just shows you how you could baseline a virgin joomla installation for maximum ease when making repeated virgin CMS deployments. The advantage to creating a baseline of a virgin installation of a CMS is that you don't have to enter any parameters into the application GUI because the system deals with it all for you and so you can make faster deployments once you have a baseline to build from. The disadvantage is that you have to update the installed CMS from the administrator backend to the latest version because the baseline you made some weeks/months ago will be several releases back from current.

1. Assuming that you have your valid credentials in your credentials file on your laptop (if you don't know what this is, go to the beginning of this document and start there) follow the steps in "POPULATE YOUR STACKSCRIPT" above.
2. Once the steps in POPULATE YOUR STACKCRIPT have been followed fully, make the following additional changes to the advanced settings of your Stackscript.
3. Once the application is installed, the username is "webmaster" and the password is "mnbcxz098321QQQZZZ"

>     set "The number (1, 2 or 3) of the template you are using" to "2"  
>     set "The Display name for your website e.g. My Demo Website" to "My Vanilla Joomla Installation"  
>     set "APPLICATION" to "joomla"  
>     set "APPLICATION IDENTIFIER" to "1"  
>     set "BASELINE DB REPOSITORY" to "joomla5.2.5-db-baseline" 
>     set "APPLICATION BASELINE SOURCECODE REPOSITORY" to "joomla5.2.5-webroot-sourcecode-baseline"

Wait for the application install to have been completed and available at:

>      https://<dns-url>

-----------------

### Demo 13 (Sample Virgin Wordpress Install from a Baseline Repository)  

This is a sample virgin wordpress installation from baselined repositories.  

1. Assuming that you have your valid credentials in your credentials file on your laptop (if you don't know what this is, go to the beginning of this document and start there) follow the steps in "POPULATE YOUR STACKSCRIPT" above.
2. Once the steps in POPULATE YOUR STACKCRIPT have been followed fully, make the following additional changes to the advanced settings of your Stackscript.
3. Once the application is installed, the username is "webmaster" and the password is "mnbcxz098321QQQZZZ"

>     set "The number (1, 2 or 3) of the template you are using" to "2"  
>     set "The Display name for your website e.g. My Demo Website" to "My Vanilla Wordpress Installation"  
>     set "APPLICATION" to "wordpress"  
>     set "APPLICATION IDENTIFIER" to "2"  
>     set "BASELINE DB REPOSITORY" to "wordpress6.8.1-db-baseline" 
>     set "APPLICATION BASELINE SOURCECODE REPOSITORY" to "wordpress6.8.1-webroot-sourcecode-baseline"

Wait for the application install to have been completed and available at:

>      https://<dns-url>


Once the application is installed, the username is "webmaster" and the password is "mnbcxz098321QQZZ".


-----------------

### Demo 14 (Sample Virgin Drupal Install from a Baseline Repository)  

This is a sample virgin drupal installation from baselined repositories.  

1. Assuming that you have your valid credentials in your credentials file on your laptop (if you don't know what this is, go to the beginning of this document and start there) follow the steps in "POPULATE YOUR STACKSCRIPT" above.
2. Once the steps in POPULATE YOUR STACKCRIPT have been followed fully, make the following additional changes to the advanced settings of your Stackscript.
3. Once the application is installed, the username is "webmaster" and the password is "mnbcxz098321QQQZZZ"


>     set "The number (1, 2 or 3) of the template you are using" to "2"  
>     set "The Display name for your website e.g. My Demo Website" to "My Vanilla Drupal Installation"  
>     set "APPLICATION" to "drupal"  
>     set "APPLICATION IDENTIFIER" to "3"  
>     set "BASELINE DB REPOSITORY" to "drupal11.1.7-db-baseline" 
>     set "APPLICATION BASELINE SOURCECODE REPOSITORY" to "drupal11.1.7-webroot-sourcecode-baseline"

Wait for the application install to have been completed and available at:

>      https://<dns-url>


Once the application is installed, the username is "webmaster" and the password is "mnbcxz098321QQZZ".

-----------------

### Demo 15 (Sample Virgin Moodle Install from a Baseline Repository)  

This is a sample virgin moodle installation from baselined repositories.  

1. Assuming that you have your valid credentials in your credentials file on your laptop (if you don't know what this is, go to the beginning of this document and start there) follow the steps in "POPULATE YOUR STACKSCRIPT" above.
2. Once the steps in POPULATE YOUR STACKCRIPT have been followed fully, make the following additional changes to the advanced settings of your Stackscript.
3. Once the application is installed, the username is "webmaster" and the password is "mnbcxz098321QQQZZZ$$"


>     set "The number (1, 2 or 3) of the template you are using" to "2"  
>     set "The Display name for your website e.g. My Demo Website" to "My Vanilla Moodle Installation"  
>     set "APPLICATION" to "moodle"  
>     set "APPLICATION IDENTIFIER" to "4"  
>     set "BASELINE DB REPOSITORY" to "moodle5.0-db-baseline" 
>     set "APPLICATION BASELINE SOURCECODE REPOSITORY" to "moodle5.0-webroot-sourcecode-baseline"

Wait for the application install to have been completed and available at:

>      https://<dns-url>


Once the application is installed, the username is "webmaster" and the password is "mnbcxz098321QQZZ$$".
