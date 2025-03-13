if **ACTIVE_FIREWALLS = 0** - No active firewalls  
if **ACTIVE_FIREWALLS = 1** - UFW or iptables firewall only active on all machines   
if **ACTIVE_FIREWALLS = 2** - Native firewall only active on all machines  
if **ACTIVE_FIREWALLS = 3** - UFW or iptables and Native Firewall active on all machines  

On each machine there are two core scripts related to the firewalling of the machine

>      ${HOME}/security/KnickersUp.sh
>      ${HOME}/security/SetupFirewall.sh

Knickers up allows all outgoing connections and denies all incoming connections and this is the base position for the firewall

The script SetupFirewall.sh will selectively allow certain IP addresses to connect to certain ports. For example, the build machine is allowed to connect to the machines through the SSH port and if the machine is a webserver then the depending on the configuration, client ip addresses are allowed to connect to the machine through the 443 port also, if you you are configured to use cloudflare, only cloudflare IP addresses are allowed to connect to port 443 giving you some extra protection and if you are using an authentication server all client ip addresses are firewalled from access to port 443 of the webserver until they have been authenticated as valid by the authentication server you are running. 

The SetupFirewall script is run from cron on a minute by minute basis

If the firewall were to be inactive for some reason there is a script

>      ${HOME}/security/MonitorFirewall.sh

Which runs every minute and if the firewall were to become inactive an email will be sent and attempts made to restore the firewall to an active condition or state

If you have other configurations of firewalling that you need for any additional applications you install, then, you can modify the "SetupFirewall" script on each machine type so that the firewalling that you have meets your needs. 

When **ACTIVE_FIREWALLS = 2** or **ACTIVE_FIREWALLS = 3** then the native firewall is configured on each build. This takes place in the script

>     ${BUILD_HOME}/providerscripts/security/firewall/SetupNativeFirewall.sh

on the build machine. This script will set up a native firewall for each machine type. 

>     adt-autoscaler
>     adt-webserver
>     adt-database

As well as adding machines of each requisite type to the necessary firewall. On the autoscaler when a new webserver is provisioned the newly created machine is added to the firewall as it is provisioned/created using the CLI

Each firewall type will allow connections from its local VPC for SSH and database connections as well as any necessary public connections if (for example) a build machine is deployed outside the VPC or if port 443 on a webserver needs to be accessed from ourside the VPC. This way, the firewall is kept as tight as possible. And so if ACTIVE_FIREWALLS="3" you have double firewall protection, UFW of iptables as well as the native firewalling system provided by your VPS provider. 

Note, the build-machine is not added to any native firewall. When you  first provision your build-machine if you want to have a native firewall as well, you need to add the build-machine manually to the native firewall that you have set up. All other machine types are automatically added to the native firewalling system when appropriate. 
