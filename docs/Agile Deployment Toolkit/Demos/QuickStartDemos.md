## QUICK-START DEMOS  

**NOTE:** These quick start demos are only intended for use on the Linode platform using the supplied [StackScript](https://cloud.linode.com/stackscripts/635271) to demonstrate example usage cases for the Agile Deployment Toolkit as quickly and easily as possible.  The demos themselves are very quickly put together simply there for illustrative purposes they are not there to provide any truly useful function. If anyone would like to spend time crafting demos useful for real function that could be listed here that would be valued. 

The purpose of these quick start demos is to show you that with just some parameters you can achieve a lot using the Agile Deployment Toolkit with the possibility of going much deeper into it if you choose to.

For more information about parameter configuration please see the [spec](https://github.com/wintersys-projects/adt-build-machine-scripts/blob/main/templatedconfigurations/specification.md) and [quickspec](https://github.com/wintersys-projects/adt-build-machine-scripts/blob/main/templatedconfigurations/quick_specification.dat)

<br/>

**NOTE:** The onus of these demos is on the word "Quick" and what I mean by that is that throughout these demos I suggest using security keys and tokens which have "full access rights" for all function of your account and therefore can be generated once and reused across all function rather than "limited access keys" which can only be used for particular function according to their scoping. Obviously this is not the most secure approach and if you were doing processes similar to this for real you would want to follow the "principle of least privileges" meaning that you would generate key sets for specific function within your account and with limited access rights.  Is that clear, I set this up so that you only have to generate one set of keys with full access rights rather than several different keys each with specific and limited access scopes.  

**NOTE2:** The first time you deploy these demos to a specific domain name an SSL certificate will be generated for that domain which can take some time. If you make subsequent deployments if you use the same domain name the same certificates will be reused and the time take for the deployment to be made will be sped up. 

------------------------------

## MANDATORY INITIAL CONFIGURATION STEPS 
THIS WILL INSTALL THE DEFAULT DEMO

1. If you are a beginner, follow [here](./QuickStartDemosPrepBeginnerLevel.md)  
2. If you are an expert, follow [here](./QuickStartDemosPrepExpertLevel.md)

<br/>

-------------------------------

<span style="color:red">DO NOT PASS HERE IF YOU HAVEN'T SUCCESSFULLY COMPLETED EITHER STEP 1 (beginner) **OR** STEP2 (expert) ACCORDING TO YOUR EXPERIENCE</span>

Once you clicked "**Create Linode**" at the end of process 1 or 2 above, the default demo (an application built with Joomla and Community Builder) will deploy which will take some minutes. 

NOTE: The very first deployment you make to any URL which you haven't used yet with the current provider will take a bit longer (maybe as much as 5 minutes longer) because the DNS Propagation needed to generate an SSL certificate using Let's Encrypt takes some minutes (if anyone knows how to speed this up that would be cool). On subsequent deployments (using the exact same domain name that you have already deployed to and with the same provider, in this case Linode), the originally generated certificate (as long as it is still valid) will be re-used and so does not need to be regenerated and DNS validation satisfied and this will speed up the deployment. You can also set INPARALLEL to 1 and this will parallelise the current build making the build process orders of magnitude faster. 

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

## DEPLOYING THESE DEMOS USING CLOUD-INIT 

With the slight modification of following the step that says "Quick Demo" or "if you are making Quick Demo deployment" you can achieve the same thing as you have achieved using a StackScript but with a "UserData" script instead. UserData scripts have the disadvantage of being more complex to look at but the advantage of being platform independent. 

[DigitalOcean](https://www.wintersys-projects.uk/Agile%20Deployment%20Toolkit/Tutorials/digitalocean/buildmachine/)  
[Exoscale](https://www.wintersys-projects.uk/Agile%20Deployment%20Toolkit/Tutorials/exoscale/buildmachine/)  
[Linode](https://www.wintersys-projects.uk/Agile%20Deployment%20Toolkit/Tutorials/linode/build-machine/)  
[Vultr](https://www.wintersys-projects.uk/Agile%20Deployment%20Toolkit/Tutorials/vultr/buildmachine/)  






