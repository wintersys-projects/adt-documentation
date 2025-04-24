**EXPEDITED BASELINE DEPLOYMENT METHOD**

YOU MUST HAVE THE MACHINES STILL RUNNING FROM THE PREVIOUS [TUTORIAL](./expedited-baseline-joomla.md) TO COMPLETE THIS TUTORIAL SUCCESSFULLY

On your build machine, you need to now make hourly periodicity [temporal backups](../../Deployment/Backups.md) of your application sourcecode and your application database.

To generate your temporal backups, you have to run two commands on your build machine. At the command prompt of your build machine cd into the **helperscripts** directory of your agile deployment toolkit installation. In my case it is like this:

>     cd /home/wintersys-projects/adt-build-machine-scripts/helperscripts

Then perform a temporal database backup
  
>     /bin/sh PerformDatabaseBackup.sh
 
Answering all of the questions and picking a periodicity, for example, HOURLY in your template. Check in your datastore for a database temporal backup which should look similar to this picture with an appropriate timestamp for you.

![](images/expedited/exo38.png "Exoscale Tutorial Image 38")

  
Then perform a temporal website sourcecode backup
  
>     /bin/sh PerformWebsiteBackup.sh
  
Making sure you pick the same periodicity as for the temporal database backup, for example, "HOURLY"

![](images/expedited/exo39.png "Exoscale Tutorial Image 39")

  
What we are then interested in is template 3 which is at:
  
>     /home/wintersys-projects/adt-build-machine-scripts/templatedconfigurations/templates/exoscale/exoscale3.tmpl
  
I can extract the values for the following variables from template 1 or template 2 which I used in the previous tutorials in the series and set them in template 3, replace these with your own live values:

>     export S3_ACCESS_KEY="EXO0a940f1387e31e370e91dc44" #MANDATORY
>     export S3_SECRET_KEY="a3GFn-40ZqEpvEp3bibjOOXchM-IX2lw0JcokCFW7KM" #MANDATORY
>     export ACCESS_KEY="EXO0a940f1387e31e370e91dc44" #MANDATORY
>     export SECRET_KEY="a3GFn-40ZqEpvEp3bibjOOXchM-IX2lw0JcokCFW7KM" #MANDATORY
>     export DNS_USERNAME="peterexoscale@yahoo.com"  #MANDATORY
>     export DNS_SECURITY_KEY="EXO0a940f1387e31e370e91dc44:a3GFn-40ZqEpvEp3bibjOOXchM-IX2lw0JcokCFW7KM"   #MANDATORY - This is your access key and your secret key, written: DNS_SECURITY_KEY="${ACCESS_KEY}:${SECRET_KEY}"
>     export CLOUDHOST_ACCOUNT_ID="peterexoscale@yahoo.com" #MANDATORY
>     export WEBSITE_DISPLAY_NAME="Test Social Network" #MANDATORY
>     export WEBSITE_NAME="drpatient" #MANDATORY - This is the exact value of the core of your WEBSITE_URL, for example, www.nuocial.org.uk would be nuocial
>     export WEBSITE_URL="social.drpatient.com"  #MANDATORY
>     export APPLICATION_REPOSITORY_OWNER="adt-apps" #MANDATORY
>     export APPLICATION_REPOSITORY_USERNAME="adt-apps" #MANDATORY
>     export APPLICATION_REPOSITORY_PASSWORD="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k4" #MANDATORY
>     export APPLICATION_REPOSITORY_TOKEN="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k4" #MANDATORY

  
What I then do is adjust  

**/home/wintersys-projects/adt-build-machine-scripts/templatedconfigurations/templates/exoscale/exoscale3.tmpl**  
  
to contain these values instead of its defaults.
  
I then need to set the template to use the temporal backups that I have generated and I do that by setting these values in template3:
  
>     export APPLICATION="joomla" #MANDATORY (joomla or wordpress or drupal or moodle)
>     export BUILD_CHOICE="2" #MANDATORY 2=hourly, 3=daily, 4=weekly, 5=monthly, 6=bimonthly
>     export BUILD_ARCHIVE_CHOICE="hourly" #MANDATORY hourly, daily, weekly, monthly, bimonthly
>     export PERSIST_ASSETS_TO_CLOUD="1" #MANDATORY This should only be 0 if your application has a very small number of assets
>     export DIRECTORIES_TO_MOUNT="images" #MANDATORY - this will define which directories in your webroot will be mounted from S3, if PERSIST_ASSETS_TO_CLOUD=1
  
Shutdown any webservers that you have running from tutorial 2 and you are then ready to perform a temporal build, as shown below:
  
If your template is configured correctly you can now run the build process selecting the appropriate template and cloudhost (exoscale and template 3 in other words). On your build machine, do as follows:

>     cd ${BUILD_HOME}
>     ./ExpeditedAgileDeploymentToolkit.sh

and answer any questions and select template 3 and have a bit of patience whilst the build runs. 
  

  
