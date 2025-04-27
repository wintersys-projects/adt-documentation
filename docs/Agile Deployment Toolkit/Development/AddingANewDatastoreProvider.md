To add a new datastore manipulation tool such as rclone or s5cmd in addition to the s3cmd that the core supports you will need to modify or add to the following files:

>     adt-autoscaler-scripts/installscripts/InstallDatastoreTools.sh
>     adt-autoscaler-scripts/providerscripts/datastore/InitialiseDatastoreConfig.sh

>     adt-build-machine-scripts/builddescriptors/buildstyles.dat
>     adt-build-machine-scripts/initscripts/InitialiseDatastoreConfig.sh
>     adt-build-machine-scripts/installscripts/InstallDatastoreTools.sh
>     adt-build-machine-scripts/providerscripts/datastore/*

>     adt-database-scripts/installscripts/InstallDatastoreTools.sh
>     adt-database-scripts/providerscripts/datastore/*

>     adt-webserver-scripts/installscripts/InstallDatastoreTools.sh
>     adt-webserver-scripts/providerscripts/datastore/*

