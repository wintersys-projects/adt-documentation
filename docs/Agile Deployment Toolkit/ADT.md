# Welcome to the Agile Deployment Toolkit Documentation

The Agile Deployment Toolkit is a power tool for CMS deployments on VPS machines. In the hands of a skilled person there are advantages to this approach.advantages. In summary:

Is shared hosting not the ideal solution for your web hosting?

Do you want to have your own set of configured VPS servers but do not want to spend the time configuring and deploying software on them?

Do you want to have consistent security processes baked into your server deployments?

Would you like to be able to redeploy to a different (supported) VPS host easily - within 5 - 10 minutes if needed?

Does automated server configuration with the latest releases of software included for each deployment sound attractive?

Would you like a low barrier to entry solution using nothing but basic scripting techniques?

Then you might be interested in the Agile Deployment Toolkit which currently supports Joomla, Wordpress, Moodle and Drupal CMS applications.

------------

There are four repositories associated with this toolkit: 

**[Agile Infrastructure Build Machine Scripts](https://github.com/wintersys-projects/adt-build-machine-scripts)**   
**[Agile Infrastructure Autoscaler Scripts](https://github.com/wintersys-projects/adt-autoscaler-scripts)**   
**[Agile Infrastructure Webserver Scripts](https://github.com/wintersys-projects/adt-webserver-scripts)**  
**[Agile Infrastructure Database Scripts](https://github.com/wintersys-projects/adt-database-scripts)**  

NOTE: The scripts in these repositories will control the build process for the three different classes of server machines (autoscaler/webserver/database server). You could potentially run the build process on a dedicated linux (Ubuntu/Debian) laptop or on any laptop that you boot off a portable linux flash drive (with persistent storage enabled). I generally describe how to use this toolkit from a VPS linux machine and you SHOULD NOT use your day to day linux laptop as your build machine because the build process will install software that you might not want on your daily laptop and will also make some configuration changes to your system.

The Quick start demos below are specifically designed to give you a taste for this with the least effort possible and if you like what you see, you can do a deeper dive into what I have built here. 

**[Quick Start Demos](<Demos/QuickStartDemos.md>)**  
**[Deployment Tutorials](<Tutorials/TutorialsMenu.md>)**  
**[The Specification](https://github.com/wintersys-projects/adt-build-machine-scripts/blob/main/templatedconfigurations/specification.md)**  


----------------------------------

**What is a DMS (Deployment Management System)**

This is a DMS system, so, what is a DMS system? A DMS is for helping with deploying servers using well tested and secured processes. Its power is that it can be extended easily and is very similar in design character to a CMS system but for deployment rather than content. The ultimate objective is to make it possible to have your own bespoke application libraries. For example, in Joomla, something like a JAD (Joomla Applications Directory), in Wordpress something like a WAD (Wordpress Applications Directory) and in Drupal something like a DAD (Drupal Applications Directory). Application directories are envisioned to be whole applications that have been built (by expert application developers) to meet a particular business need and then the **whole** application is installed  ready for use "off the shelf" by a customer using this toolkit. For example, if you bought a solution like Hivebrite it would be a complete application already and you wouldn't need to do anything to build the application but the idea here to have preconfigured applications of all different types that can be built on top of CMS systems and installed using this toolkit. VERY simple example applications (built in minutes) are shown in the "Quick Start Demos" referenced above. Ultimately I realised that limitations of solutions like Hivebrite is that the application developer is the only one with control over its feature set meaning that if a customer wants some feature that is not supported they have to appeal to the developers for their feature request to be included which they may or may not honour. With an objective like I have with a DMS system, an application developer can still build the base feature set of the application which the customer can buy "off the shelf", but, the customer can tweak the work that the base application developer has put in so that it meets the customers precise requirements. So with this solution you are free to make use of reusable base applications but you are also free to customise the base applications as well and for me this is an important win over solutions where you have to appeal to their developers for any customisations that you want. A CMS component vendor, then, could provide complete and configured applications using their extensions and components which (people like me who don't know their software intricately) can then use as their community solutions safe in the knowledge that it is optimised and confgured by the experts. 

A DMS like this one does require learning just like a CMS does but would you want to go back to coding in basic HTML once you have discovered CMS systems, possibly not. If its money that you are interested in, application developers using this toolkit should be able to produce high quality COTS (Commerical Off The Shelf) web applications using their CMS of choice and have the applications they have deveoped reused by many customers making strides in all round productivity in the process. Think about the current model. If I want to build a "Community Builder" social network using Joomla I have to start from scratch wondering "what does this do", "how does that work" and so does the "other guy" doing something very similar to me. If I can instead use a preconfigured application solution complete with online quality reviews from an applications directory or library and the "other guy" can do the same and so on then that satisifies a basic software engineering requirement of "write once, use many times" and it's that "write once use many" principle which is at the heart of what I want to do here. 

------------------------

**The Core**

With the core of the Agile Deployment Toolkit, it will make use of a set of services and providers. I elected to use Digital Ocean, Exoscale, Linode and Vultr to deploy on, or, as deployment options, but, the toolkit is designed to be forked and extended to support other providers maybe AWS, Rackspace, Google Cloud and so on. You should work from your own forks of the repositories because you will likely want to change the configurations of APACHE, NGINX, or LIGHTTPD or other products with configuration profiles within the sourcefiles of your forked repository and you can't do that if you deploy off the this main core set "wintersys" provided repositories. 

The full set of services that are supported by the core of the toolkit and which you can extend in your forks is:

1. For VPS services, one of - Digital Ocean, Linode, Exoscale or Vultr
2. For Email services, one of - Amazon SES, Mailjet or Sendpulse
3. For Git based services, one of - Bitbucket, Github or Gitlab
4. For DNS services, one of - Cloudflare, Digital Ocean, Exoscale, Linode, Vultr 
5. For S3 compatible bject store services, one of - Digital Ocean Spaces, Exoscale Object Store, Linode Object Store, Vultr Object Store
6. I chose these VPS providers to deploy with because they have managed database offerings, if you wish to make a production ready deployment with this toolkit it is recommended that you make your deloyment using their managed database offerings. For development deployments, you can use the default "apt" database install to your own VPS system within your VPC that this toolkit provides. 

--------------------------------

**Build Methods Overview**

There are two types of build method you can employ to get a functioning application. These is the hardcore build (only use once you are more experienced with this tool), and the expedited build method. 

-------------------------------

**The Conclusion**

A DMS system such as this one can certainly speed your server deployments. It does require skill, and therefore learning to use but once you get a taste for it the result can be sweet.  
