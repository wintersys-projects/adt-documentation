I provide a method for taking whole machine backups that can then be used to build from in short order. 
This might be useful if you were building a lot of things from source because it can take some minutes for certain pieces of software to compile. 
A faster way (over time) might be to make the effort to build the machines in full and then take backups of the machines and build off those in the future.
Here is the process that I would use to make that possible:

1. I would configure the machines as I want and perform a build and check that everything is online to my taste once the build completes.
2. I would then go into the helper scipts directory on the build machine and run the appropriate scripts from the following:

>     ${BUILD_HOME}/helperscripts/ObtainWholeMachineBackupFromAuthenticatorMachine.sh
>     ${BUILD_HOME}/helperscripts/ObtainWholeMachineBackupFromAutoscalerMachine.sh
>     ${BUILD_HOME}/helperscripts/ObtainWholeMachineBackupFromDatabaseMachine.sh
>     ${BUILD_HOME}/helperscripts/ObtainWholeMachineBackupFromReveseProxyMachine.sh
>     ${BUILD_HOME}/helperscripts/ObtainWholeMachineBackupFromWebserverMachine.sh

This will generate a set of backups in 

>     ${BUILD_HOME}/runtimedata/wholemachinebackups

under the appropriate domain name. 

What I can then do is that if I want to build with that particular configuration using a whole machine backup, I simply set

>    BUILD_FROM_BACKUP="1"

In the template that I want to use to perform the build from. What will happen then is that machines will build as usual but with a trimmed down "cloud-init" process and what will happen is that instead of installing software and so on the build process will upload the appropriate backup from the build machine and extract it onto the machine. This will contain the appropriate software and so on. This might interest you if you are interested in efficient usage of resources because building out software from repositories for each deployment is a less efficient way of building your machines than simply extracting an archive that you hold on a machine on the same subnet as your target machine(s). 
