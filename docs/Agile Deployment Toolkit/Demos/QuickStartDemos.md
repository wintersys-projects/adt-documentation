 ## QUICK-START DEMOS  

**NOTE:** These quick start demos are only intended for use on the Linode platform using the supplied [StackScript](https://cloud.linode.com/stackscripts/635271) to demonstrate example usage cases for the Agile Deployment Toolkit as quickly and easily as possible.  The demos themselves are very quickly put together simply there for illustrative purposes they are not there to provide any truly useful function. If anyone would like to spend time crafting demos useful for real function that could be listed here that would be valued. 

The purpose of these quick start demos is to show you that with just some parameters you can achieve a lot using the Agile Deployment Toolkit with the possibility of going much deeper into it if you choose to.

For more information about parameter configuration please see the [spec](https://github.com/wintersys-projects/adt-build-machine-scripts/blob/main/templatedconfigurations/specification.md) and [quickspec](https://github.com/wintersys-projects/adt-build-machine-scripts/blob/main/templatedconfigurations/quick_specification.dat)

<br/>

------------------------------

## Default Demo Application (no additional configuration required)

This demo makes use of [Community Builder](https://www.joomlapolis.com)

Once the application is installed, the username is "webmaster" and the password is "mnbcxz098321QQZZ". 
There are also test users and their usernames and passwords are: "testuser1" and "mnbcxz098321QQZZ" and "testuser2" "mnbcxz098321QQZZ"

<span style="color:red">**YOUR ONE TIME MANDATORY PREPARATORY STEPS**</span>
<br/>

**These initial steps are only required to get your data items the first time you make a deployment. The result of these first steps can be used repeatedly for subsequent demo deployments as long as the data items used, access keys and so on haven't expired, been deleted or rotated** 

<br/>

1. If you are a beginner, follow [here](./QuickStartDemosPrepBeginnerLevel.md)  
2. If you are an expert, follow [here](./QuickStartDemosPrepExpertLevel.md)

<br/>

<span style="color:red">DO NOT PASS HERE IF YOU HAVEN'T SUCCESSFULLY COMPLETED EITHER STEP 1 (beginner) **OR** STEP2 (expert) ACCORDING TO YOUR EXPERIENCE</span>

Once you clicked "**Create Linode**" according to the mandatory steps above the default demo application built with Joomla and Community Builder will deploy which will take some minutes. 

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

<br/><br/> 

-----------------

## Additional Demo Applications 

To install one of these additional applications follow the exact same steps as for the default application but with the additional tweeks 
outline below for the specific application type you are deploying. 

#### VIRGIN CMS INSTALLS

If you are interested in Virgin CMS installs, apply the appropriate tweeks to your Stackscipt [here](./VirginCMSDemos.md)

#### SAMPLE JOOMLA APPLICATIONS

If you are interested in installing Joomla based demos, apply the appropriate tweeks to your Stackscipt [here](./JoomlaDemos.md)

#### SAMPLE WORDPRESS APPLICATIONS

If you are interested in installing Wordpress based demos, apply the appropriate tweeks to your Stackscipt [here](./WordpressDemos.md)

#### SAMPLE DRUPAL APPLICATIONS

If you are interested in installing Drupal based demos, apply the appropriate tweeks to your Stackscipt [here](./DrupalDemos.md)

#### SAMPLE MOODLE APPLICATIONS

If you are interested in installing Moodle based demos, apply the appropriate tweeks to your Stackscipt [here](./MoodleDemos.md)

----------------------




