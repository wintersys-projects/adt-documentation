From time to time new versions of the ubuntu and debian operating systems are released. To integrate a new version (for example ubuntu 26.04 or debian 13)  
the following files have to be updasted to support these new versions:

adt-autoscaler-scripts/providerscripts/cloudhost/GetOperatingSystemVersion.sh  
adt-autoscaler-scripts/providerscripts/server/CreateServer.sh 
adt-build-machine-scripts/providerscripts/cloudhost/GetOperatingSystemVersion.sh  
adt-build-machine-scripts/providerscripts/server/CreateServer.sh  
adt-webserver-scripts/installscripts/InstallPHPBase.sh  

You can look at the examples of other versions of each OS to see how the updates need to be made. 

I am not sure how possible this is but if you wanted to have a go at deploying to, for example, rocky linux you would need to change the following  files:

>     adt-autoscaler-scripts/installscripts/*
>     adt-autoscaler-scripts/providerscripts/cloudhost/*
>     adt-autoscaler-scripts/providerscripts/utilities/processing/RunServiceCommand.sh
>     adt-autoscaler-scripts/providerscripts/utilities/software/UpdateSoftware.sh

>     adt-build-machine-scripts/ExpeditedAgileDeploymentToolkit.sh
>     adt-build-machine-scripts/helperscripts/RunServiceCommand.sh
>     adt-build-machine-scripts/initscripts/InitialiseCompatibilityChecks.sh
>     adt-build-machine-scripts/initscripts/InitialiseCompatibilityChecks.sh
>     adt-build-machine-scripts/installscripts/*
>     adt-build-machine-scripts/providerscripts/cloudhost/*
>     adt-build-machine-scripts/templatedconfigurations/ValidateTemplate.sh
>     adt-build-machine-scripts/templatedconfigurations/quick_specification.dat
>     adt-build-machine-scripts/templatedconfigurations/specification.md
>     adt-build-machine-scripts/templatedconfigurations/templateoverrides/OverrideScript.sh

>     adt-database-scripts/installscripts/*
>     adt-database-scripts/providerscripts/utilities/processing/RunServiceCommand.sh
>     adt-database-scripts/providerscripts/utilities/software/UpdateSoftware.sh

>     adt-webserver-scripts/installscripts/*
>     adt-webserver-scripts/providerscripts/utilities/processing/RunServiceCommand.sh
>     adt-webserver-scripts/providerscripts/utilities/software/UpdateSoftware.sh
