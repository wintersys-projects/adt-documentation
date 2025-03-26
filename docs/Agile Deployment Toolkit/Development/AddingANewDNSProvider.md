To add a new DNS provider you will need to review and add to the following files for your new DNS provider. It would be cool to have other providers supported that provide services similar to cloudflare to provide deployers with other options

>     adt-autoscaler-scripts/autoscaler/AddIPToDNS.sh
>     adt-autoscaler-scripts/autoscaler/GetDNSIPs.sh
>     adt-autoscaler-scripts/autoscaler/RemoveIPFromDNS.sh
>     adt-autoscaler-scripts/providerscripts/security/firewall/GetProxyDNSIPs.sh

>     adt-build-machine-scripts/buildscripts/FinaliseBuildProcessing.sh
>     adt-build-machine-scripts/initscripts/InitialiseDNSRecord.sh
>     adt-build-machine-scripts/providerscripts/dns/*
>     adt-build-machine-scripts/providerscripts/security/firewall/GetProxyDNSIPs.sh
>     adt-build-machine-scripts/providerscripts/server/ObtainSSLCertificate.sh
>     adt-build-machine-scripts/templatedconfigurations/ValidateTemplate.sh
>     adt-build-machine-scripts/templatedconfigurations/quick_specification.dat
>     adt-build-machine-scripts/templatedconfigurations/specification.md

>     adt-webserver-scripts/providerscripts/webserver/configuration/InstallNginxConfigurationForAuthenticator.sh
>     adt-webserver-scripts/providerscripts/webserver/configuration/InstallNginxConfigurationFromRepo.sh
>     adt-webserver-scripts/providerscripts/webserver/configuration/InstallNginxConfigurationFromSource.sh
>     adt-webserver-scripts/security/ObtainSSLCertificate.sh
>     adt-webserver-scripts/security/SetupFirewall.sh
