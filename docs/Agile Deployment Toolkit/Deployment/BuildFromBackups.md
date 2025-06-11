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
