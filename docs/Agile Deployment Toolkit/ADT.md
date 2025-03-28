# Welcome to the Agile Deployment Toolkit Documentation

The Agile Deployment Toolkit is intended to be a power tool for CMS deployments to VPS systems. Like any “power tool”, you have to get used to it, and invest a bit of time to see how it works, but, in the hands of a skilled person there can be considerable advantages. I am looking for developers who want to test the toolkit in earnest so that any issues can be fleshed out.

Is shared hosting not the ideal solution for your web hosting?

Do you want to have your own set of configured VPS servers but do not want to spend the time configuring and deploying software on them?

Do you want to have consistent security processes baked into your server deployments?

Would you like to be able to redeploy to a different (supported) VPS host easily - within 5 - 10 minutes if needed?

Does automated server configuration with the latest releases of software included for each deployment sound attractive?

Would you like a low barrier to entry solution using nothing but basic scripting techniques?

Then you might be interested in the Agile Deployment Toolkit which currently supports Joomla, Wordpress, Moodle and Drupal CMS applications.

------------

**DO NOT DEPLOY THIS ON YOUR DAY TO DAY LINUX LAPTOP AS IT WILL MAKE CHANGES TO THE MACHINE'S CONFIGURATION**

There are four repositories associated with this toolkit: 

**[Agile Infrastructure Build Machine Scripts](https://github.com/wintersys-projects/adt-build-machine-scripts)**   
**[Agile Infrastructure Autoscaler Scripts](https://github.com/wintersys-projects/adt-autoscaler-scripts)**   
**[Agile Infrastructure Webserver Scripts](https://github.com/wintersys-projects/adt-webserver-scripts)**  
**[Agile Infrastructure Database Scripts](https://github.com/wintersys-projects/adt-database-scripts)**  

NOTE: The scripts in these repositories will control the build process for the different classes of server machines (autoscaling/webserving/database). You could run this on a dedicated linux (ubuntu/debian) laptop or on any laptop that you boot off a portable linux flash drive (with persistent storage enabled). I generally describe how to use this toolkit from a VPS linux machine running on the cloudhost of your choice.

Here is some more details about the toolkit. You might want to begin by running through some of the Quick Start Demos which are the mosst direct way to get anything up and running.  

**[Deployment Tutorials](<Agile Deployment Toolkit/Tutorials/TutorialsMenu.md>)**  
**[The Specification](https://github.com/wintersys-projects/adt-build-machine-scripts/blob/main/templatedconfigurations/specification.md)**  
**[Quick Start Demos](<Agile Deployment Toolkit/Demos/QuickStartDemos.md>)**  

-----------------------------------

**Concise Summary**

Automatically install LEMP LAMP LLMP LEPP LAPP or LLPP using parameters only.

----------------------------------

**What is a DMS (Deployment Management System)**

A DMS, like this one, is a powertool for helping with deploying servers using well tested and secured processes. Its power is that it can be extended easily and is very similar to a CMS system but for deployment rather than content. The ultimate objective is to make it possible to have your own bespoke application libraries. For example, in Joomla, something like a JAD (Joomla Applications Directory), in Wordpress something like a WAD (Wordpress Applications Directory) and in Drupal something like a DAD (Drupal Applications Directory). Application directories are envisioned to be whole applications that have been built (by expert application developers) to meet a particular business need and then the **whole** application is installed  ready for use "off the shelf" by a customer using this toolkit. For example, if you bought a solution like Hivebrite it would be a complete application already and you wouldn't need to do anything to build the application and that is the idea here to have preconfigured applications of all different types that can be built on top of CMS systems and installed using this toolkit. VERY simple (built in minutes) examples of this are shown in the "Quick Start Demos" referenced above. Ultimately I realised that limitations of solutions like Hivebrite is that the application developer is the only one with control over its feature set meaning that if a customer wants some feature they have to appeal to the Hivebrite developers for their feature request to be included which they may or may not honour. With an objective like what is being attempted here, an application developer can still build the base feature set of the application but the customer can tweak the work that the base application developer has put in so that it meets the customers requirements as best as is reasonably possible to expect. So with this solution you are free to make use of reusable base applications but you are also free to customise the base applications as well and for me this is an important win over solutions where you have to appeal to their developers for any customisations that you want. A CMS component vendor, then, could provide configured applications using their software which (people like me who don't know their software intricately) can then use for their community solutions safe in the knowledge that it is optimised and confgured by the experts. 

A DMS like this one does require learning just like a CMS does but would you want to go back to coding in basic HTML once you have discovered CMS systems, probably not. If its money that you are interested in, application developers using this toolkit should be able to produce high quality COTS (Commerical Off The Shelf) web applications using their CMS of choice and have the applications they have deveoped reused pre-configured by many customers making strides in all round productivity in the process. Think about the current model. If I want to build a "Community Builder" social network using Joomla I have to start from scratch wondering "what does this do", "how does that work" and so on, if I can instead use a preconfigured application solution complete with online quality reviews from an applications directory or library and so on then to get my community going I just "install the application" and if it only meets 80% of my needs I can customise 20% of it rather than being a "non expert" trying to build 100% of it and that is where the productivity gain that I could see is and the core reason I thought about building this solution. 

------------------------

**The Core**

With the core of the Agile Deployment Toolkit, it will make use of a set of services and providers. I elected to use Digital Ocean, Exoscale, Linode and Vultr to deploy on, or, as deployment options, but, the toolkit is designed to be forked and extended to support other providers maybe AWS, rackspace, google cloud and so on. You should work from your own forks of the repositories because you will likely want to change the configurations of APACHE, NGINX, or LIGHTTPD or other products with configuration profiles with in the sourcefiles of your repository and you can't do that if you deploy off the main core repositories. 

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

A DMS system such as this one can certainly speed your server deployments. It does require skill, and therefore learning to use. I have to leave this up to divine providence either other developers will want to take this forward and extend it, or, its operational footprint will stay as it is. My hope of course, is that there's interest from other developers in extending what has been done so far. As I was developing this timewise I would say that 50% of the effort was on developing it and 50% of the effort was on testing its function in different configurations. That's why this toolkit will stand or fall on how earnestly it is used because with earnest use it can remain well maintained as issues are reported as they arise.  
