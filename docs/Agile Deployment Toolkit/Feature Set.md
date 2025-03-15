* Fully automated virgin server configuration and deployment with sensible default webserver and database configuration settings with best practice security guidelines baked in.

* Flexible deployment options - number of webservers to be used for a deployment when in production mode with a single webserver development mode, for when you are developing your application.

* In built resilient and scalable architecture including flexible time based scaling to accommodate increased or decreased capacity

* Option to use "self managed" databases or to use managed as a service databases from a 3rd party (DBaaS)

* Moderate learning curve for usage

* Support for deployment to multiple cloud hosts. Currently, Digital Ocean, Exoscale, Linode, Vultr and AWS. If you develop a problem or issue with the cloud host you have deployed to, simply perform a frictionless redeploy to another of the supported VPS cloud host providers

* Easily choose the machine sizes that you want to deploy to, depending on what capacity you need

* Deploy to Ubuntu or Debian with extensibility of the scripts to other flavours of Linux taken into consideration

* Automated "double" backups

* Easy inbuilt SMTP configuration for your application

* Several supported application types - Joomla, Wordpress, Drupal, Moodle and with a little work, further application types can be added

* Built with general extensibility in mind so that scripts are easy to extend

* Free to use, free to extend

* Choice to use Cloudflare as your DNS service provider for increased security

* Easy command line access to your servers (no faff)

* Choice of webservers to use, NGINX, APACHE, LIGHTTPD

* Current support for PHP based applications, but, with potential to be extended to support other languages

* Ability to store application assets in Object Storage which saves disk capacity (and cost) on your server machines

* Choice of self managed databases to use, currently, MariaDB, MySQL or Postgres

* Status messages deliverable by email during system operation

***

The Agile Deployment Toolkit is designed to have a core of functionality, which can be thoroughly tested and well maintained, but, it is also designed to be extensible outside of the core so that it is flexible enough to support an arbitrary set of solutions as are required by the users of the toolkit.

## BUILT FOR SERVER ENTHUSIASTS

This deployment system is best suited for server enthusiasts. If you don't want to have any control over your servers, you can use one of the many C-Panel solutions that are out there, but, if you love being a server mechanic and not treating your server systems as a black box, this might give your server fetish a boost. The freedom you get to tweak and customise your server setups using consistent practices is what is on offer here. You do gain freedoms using a system such as this and that is the 'value add' I am giving you here. Plenty of people start out with a vanilla Linux install and have to build out from there, this will give you linux installs with appropriate softwares (webserver, databases, system managements and architecture), preinstalled and configured for use at scale. It will also build your servers with consistent security practices built in and with an eye to scalability as well as helper scripts to ease operational management of your servers. Lets get back to not just driving the car, but, understanding how the car works as well. This is intended to be a powertool which to my mind means you have to learn how to use it safely but in skilled hands it has great power. This tool is going to require input from other people but its very much designed to be extended and enhanced and I will be interested to see how much uptake there is from others who want to contribute and to extend to the toolkit to other cloudhosts such as Google Cloud or Upcloud or to add an additional application such as NextCloud and so on. The main thing is to have an active userbase that can report back any break points if they arise over time as codebases such as CLI tools introduce deprecations and so on.

## BRIEF OVERVIEW:

The intention is to provide an automated solution to provisioning infrastructure such as autoscaling, webserver and database services in support of large scale CMS deployments (currently Joomla, Wordpress, Drupal and Moodle). The deployer of the CMS system has to alter parameters to suit in a configuration file [for example](https://github.com/wintersys-projects/adt-build-machine-scripts/blob/main/templatedconfigurations/templates/digitalocean/digitalocean1.tmpl) and start the build. Some minutes later the whole infrastructure will be online and can be taken offline and redeployed with another provider (currently supported are Digital Ocean, Linode, Exoscale, Vultr) in an agile way. Once applications are built out using the CMS you have chosen the updated codebase and database can be baselined and stored in git repos (currently Github, Gitlab or Bitbucket) for repeated deployments of the baselined application that has been created. To give you some idea of the extent of the parameters which can be configured, please review the [specification](https://github.com/wintersys-projects/adt-build-machine-scripts/blob/main/templatedconfigurations/specification.md) mentioned above. Once a build is complete, the deployer has full access to the servers that have been deployed and is confident that the servers are built with consistent security practices. 

## A NOTE ON WHAT I MEAN BY 'AGILE'

I use the term agile to mean that you can take your infrastructure offline and have it redeployed in minutes in an agile way. This is useful, if, for example, your VPS provider is having issues in a particular data centre which is affecting you and you want to take your project out of that datacentre or region and want to deploy it in another data centre or region which isn't having issues, you know how it is, sometimes datacentres have connectivity issues and so on and this agile approach makes you more resilient. If the VPS provider you are with is having major issues then you can shutdown with them and redeploy to one of the other supported VPS providers. This is what I mean by the term agile in the "Agile Deployment Toolkit" nomenclature.
