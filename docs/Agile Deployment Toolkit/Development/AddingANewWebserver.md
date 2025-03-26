To add a new webserver type (for example, litespeed) you will need to add or modify the following files:

>     adt-autoscaler-scripts/autoscaler/InitialiseCloudInit.sh
>     adt-autoscaler-scripts/providerscripts/server/cloud-init/*

>     adt-build-machine-scripts/initscripts/InitialiseCloudInit.sh
>     adt-build-machine-scripts/providerscripts/server/cloud-init/*
>     adt-build-machine-scripts/templatedconfigurations/quick_specification.dat
>     adt-build-machine-scripts/templatedconfigurations/specification.md

>     adt-webserver-scripts/installscripts/InstallAuthenticator.sh
>     adt-webserver-scripts/installscripts/InstallNGINX.sh
>     adt-webserver-scripts/installscripts/InstallPHPBase.sh
>     adt-webserver-scripts/installscripts/InstallWebserver.sh
>     adt-webserver-scripts/installscripts/nginx/BuildNginxFromSource.sh
>     adt-webserver-scripts/providerscripts/dns/TrustRemoteProxy.sh
>     adt-webserver-scripts/providerscripts/webserver/*
