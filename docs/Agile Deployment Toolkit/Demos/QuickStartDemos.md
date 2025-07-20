## QUICK-START DEMOS  

**NOTE:** These quick start demos are only intended for use on the Linode platform using the supplied [StackScript](https://cloud.linode.com/stackscripts/635271) to demonstrate example usage cases for the Agile Deployment Toolkit as quickly and easily as possible.  The demos themselves are very quickly put together simply there for illustrative purposes they are not there to provide any truly useful function. If anyone would like to spend time crafting demos useful for real function that could be listed here that would be valued. 

The purpose of these quick start demos is to show you that with just some parameters you can achieve a lot using the Agile Deployment Toolkit with the possibility of going much deeper into it if you choose to.

For more information about parameter configuration please see the [spec](https://github.com/wintersys-projects/adt-build-machine-scripts/blob/main/templatedconfigurations/specification.md) and [quickspec](https://github.com/wintersys-projects/adt-build-machine-scripts/blob/main/templatedconfigurations/quick_specification.dat)

**These initial steps are only required the first time you make a deployment. The result of these first steps can be used repeatedly for subsequent demo deployments.** 

--------------------------
<span style="color:red">**YOUR ONE TIME MANDATORY PREPARATORY STEPS**</span>

--------------------------

There are mandatory steps to follow in full before any of the demos can be deployed.

1. If you are a beginner, follow [here](./QuickStartDemosPrepBeginnerLevel.md)  
2. If you are an expert, follow [here](./QuickStartDemosPrepExpertLevel.md)

<span style="color:red">DO NOT PASS HERE IF YOU HAVEN'T SUCCESSFULLY COMPLETED EITHER STEP 1 (beginner) **OR** STEP2 (expert) ACCORDING TO YOUR EXPERIENCE</span>

Once you clicked "**Create Linode**" according to the mandatory steps above the default demo application built with joomla and community builder will deploy which will take some minutes. 

Once the build is completed (or earlier if you like, once the build machine is up and pingable) you can get the IP address of your build machine through the Linode GUI system (in my case: 172.237.116.127)

![](images/lin1.png "Linode Tutorial Image 1")

You can ssh onto your build machine with

>      ssh -p <build-machine-port> <username>@<build-machine-ip>
>      for example in my case this is: ssh -p 1035 agile-deployer@172.237.116.127

then do a

>      sudo su
>      <password> (as per the value you entered for 'The password for your build machine user (required)' into the StackScript and stored in your ~/adt-credentials.txt file)
>      cd adt-build-machine-scripts
>      ./Logs.sh

After you have performed all the pre-requisite steps above, you can choose which demo you want to follow from those listed below**</span>

### Demo 1 (Sample Joomla and Community Builder application)
DEFAULT DEMO REQUIRES NO ADDITION CONFIGURATION

[Community Builder](https://www.joomlapolis.com)

Once the application is installed, the username is "webmaster" and the password is "mnbcxz098321QQZZ". There are also test users and their usernames and passwords are: "testuser1" and "mnbcxz098321QQZZ" and "testuser2" "mnbcxz098321QQZZ"


Additional Demo Applications (each will require some extra configuration steps)

#### VITGIN CMS INSTALLS

If you are interested in installing Joomla based systems, click [here](./VirginCMSDemos.md)

#### SAMPLE JOOMLA APPLICATIONS

If you are interested in installing Joomla based systems, click [here](./JoomlaDemos.md)

#### SAMPLE WORDPRESS APPLICATIONS

If you are interested in installing Wordpress based systems, click [here](./WordpressDemos.md)

#### SAMPLE DRUPAL APPLICATIONS

If you are interested in installing Drupal based systems, click [here](./DrupalDemos.md)



 

---------------------------



---------------------------



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
