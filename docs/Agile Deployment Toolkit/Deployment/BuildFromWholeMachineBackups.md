If you want to build machines with modsecurity active then that means that there has to be compilation of the webserver and modsecurity itself from source which can take up to 15 minutes per machine. This isn't really an acceptable level of time to wait for a machine to spin up so I provide a way of "cloning" machines so that they can then be built from those clones rather than from scratch which gets the provisioning time down to a couple of minutes. If you want to have faster provisioning times (particularly if you are compiling your webservers from source) then you might want performm one build run and then redeploy by building from whole machine backups which I describe how to do here. 

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

In the template that I want to use to perform the build from. What will happen then is that machines will build as usual but with a trimmed down "cloud-init" process and what will happen is that instead of installing software and so on the build process will upload the appropriate backup from the build machine and extract it onto the target machine. This will contain the appropriate software and so on. This might interest you if you are interested in efficient usage of resources because building out software from repositories for each deployment is a less efficient way of building your machines than simply extracting an archive that you hold on a machine on the same subnet as your target machine(s). 
