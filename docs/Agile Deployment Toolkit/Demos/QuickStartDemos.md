## QUICK-START DEMOS  

**NOTE:** These quick start demos are only intended for use on the Linode platform using the supplied [StackScript](https://cloud.linode.com/stackscripts/635271) to demonstrate example usage cases for the Agile Deployment Toolkit as quickly and easily as possible.  The demos themselves are very quickly put together simply there for illustrative purposes they are not there to provide any truly useful function. If anyone would like to spend time crafting demos useful for real function that could be listed here that would be valued. 

The purpose of these quick start demos is to show you that with just some parameters you can achieve a lot using the Agile Deployment Toolkit with the possibility of going much deeper into it if you choose to.

For more information about parameter configuration please see the [spec](https://github.com/wintersys-projects/adt-build-machine-scripts/blob/main/templatedconfigurations/specification.md) and [quickspec](https://github.com/wintersys-projects/adt-build-machine-scripts/blob/main/templatedconfigurations/quick_specification.dat)

<br/>

------------------------------

## MANDATORY INITIAL CONFIGURATION STEPS 
THIS WILL INSTALL THE DEFAULT DEMO

1. If you are a beginner, follow [here](./QuickStartDemosPrepBeginnerLevel.md)  
2. If you are an expert, follow [here](./QuickStartDemosPrepExpertLevel.md)

<br/>

-------------------------------

<span style="color:red">DO NOT PASS HERE IF YOU HAVEN'T SUCCESSFULLY COMPLETED EITHER STEP 1 (beginner) **OR** STEP2 (expert) ACCORDING TO YOUR EXPERIENCE</span>

Once you clicked "**Create Linode**" at the end of process 1 or 2 above, the default demo (an application built with Joomla and Community Builder) will deploy which will take some minutes. 

Once the build is completed (or earlier if you like, once the build machine is pingable) you can get the IP address of your build machine through the Linode GUI system (in my case: 172.237.116.127)

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

## FURTHER QUICK DEMOS

If you want to try further demos other than just our default one click [here](./CustomisedDemos.md). You might want to reference [Understanding StackScript overrides](./ExampleStackScriptOverride.md)

## USING LINODE CLOUD-INIT TO DEPLOY THESE DEMOS

If you follow [this](https://www.wintersys-projects.uk/Agile%20Deployment%20Toolkit/Tutorials/linode/build-machine) it will show you how to deploy these demos using user-data scripts rather than a Stackscript (which is platform dependent). You can then follow [here](./CustomisedDemos.md) applying the mods to your "cloud-init/user data" script and end up with the same result as if you use a Stackscript.

## DEPLOYING THESE DEMOS USING CLOUD-INIT ON OTHER PROVIDERS

[DigitalOcean](https://www.wintersys-projects.uk/Agile%20Deployment%20Toolkit/Tutorials/digitalocean/buildmachine/)  
[Exoscale](https://www.wintersys-projects.uk/Agile%20Deployment%20Toolkit/Tutorials/exoscale/build-machine/)  
[Vultr](https://www.wintersys-projects.uk/Agile%20Deployment%20Toolkit/Tutorials/vultr/build-machine/)  






