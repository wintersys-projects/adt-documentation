To support a new database engine type you will need to modify or add to the following files:

>     adt-autoscaler-scripts/autoscaler/InitialiseCloudInit.sh

>     adt-build-machine-scripts/builddescriptors/buildstyles.dat
>     adt-build-machine-scripts/initscripts/InitialiseCloudInit.sh
>     adt-build-machine-scripts/initscripts/InitialiseDatabaseService.sh
>     adt-build-machine-scripts/providerscripts/application/moodle/SetApplicationConfig.sh
>     adt-build-machine-scripts/providerscripts/security/firewall/TightenDBaaSFirewall.sh
>     adt-build-machine-scripts/templatedconfigurations/quick_specification.dat
>     adt-build-machine-scripts/templatedconfigurations/specification.md

>     adt-database-scripts/applicationdb/*
>     adt-database-scripts/installscripts/InstallDatabaseClient.sh
>     adt-database-scripts/installscripts/InstallDatabaseServer.sh
>     adt-database-scripts/installscripts/InstallMySQLClient.sh
>     adt-database-scripts/installscripts/InstallMySQLServer.sh
>     adt-database-scripts/providerscripts/database/*
>     adt-database-scripts/providerscripts/utilities/remote/AccessDB.sh
>     adt-database-scripts/providerscripts/utilities/remote/ConnectToMySQLDB.sh
>     adt-database-scripts/providerscripts/utilities/status/IsDatabaseUp.sh

>     adt-webserver-scripts/installscripts/InstallDatabaseClient.sh
>     adt-webserver-scripts/installscripts/InstallMySQLClient.sh
>     adt-webserver-scripts/providerscripts/application/configuration/drupal/InitialiseVirginInstall.sh
>     adt-webserver-scripts/providerscripts/application/configuration/joomla/InitialiseVirginInstall.sh
>     adt-webserver-scripts/providerscripts/application/configuration/moodle/InitialiseVirginInstall.sh
>     adt-webserver-scripts/providerscripts/application/configuration/wordpress/InitialiseVirginInstall.sh
>     adt-webserver-scripts/providerscripts/application/processing/drupal/CheckInstalled.sh
>     adt-webserver-scripts/providerscripts/application/processing/drupal/CheckUser.sh
>     adt-webserver-scripts/providerscripts/application/processing/drupal/TruncateCache.sh
>     adt-webserver-scripts/providerscripts/utilities/remote/ConnectToRemoteMySQL.sh
>     adt-webserver-scripts/providerscripts/utilities/status/CheckServerAlive.sh
>     adt-webserver-scripts/ws.sh
