**EXPEDITED VIRGIN DEPLOYMENT METHOD**

PREBUILD NECESSITIES

If you don't already have a build machine running in the Exoscale cloud, follow these steps to get ready for the main build)

1. Begin by following this: [Build Machine Setup](./buildmachine.md)

Following the steps in 1. will give you a build machine with access through the firewall for one machine (the laptop IP address that you provided).

-----------------------------

EXPEDITED BUILD PROCESS

This will deploy the latest version of Joomla using template 1 which you can read about here: [template 1](https://github.com/wintersys-projects/adt-build-machine-scripts/blob/main/templatedconfigurations/templates/digitalocean/digitalocean1.description) and the expedited method.

If you have followed these steps your build machine is online and secured and you have an SSH session open to it from your laptop through which to initiate your build processes.

We need several pieces of information from our cloud host and 3rd party services for a successful build to be possible:

I am going to use the example of joomla to build from and so this example will build a virgin installation of the latest version of joomla

---------------------------------------

To find the latest version of Joomla, I go to this URL in my browser:

[Joomla Latest](https://downloads.joomla.org/)

And I note the latest version in a separate text file:

>     joomla_version="5.3.0"  

You can of course use a legacy version of joomla also by choosing a different version numnber. 

-------------------------------------

In production use you should use the principle of least privileges to generate 2 different access tokens, one token for compute and one token for DNS scope, but, to make this tutorial simple we can just generate one token with permissions for both scope sets. 

Create a personal access token as follows:

![](images/expedited/do-25.png "Digital Ocean Tutorial Image 25")
![](images/expedited/do-26.png "Digital Ocean Tutorial Image 26")
![](images/expedited/do-27.png "Digital Ocean Tutorial Image 27")


Now record your token in your separate text file on your laptop

>     digitalocean_access_token="dop_v1_51ac....."  

-----------------------------------

Now you need to generate an access key and a secret key for Digital Ocean Spaces which is the S3 compatible object storage offering from Digital Ocean
How to generate your access key and your secret key is shown in the following images:

![](images/expedited/do-28.png "Digital Ocean Tutorial Image 28")
![](images/expedited/do-29.png "Digital Ocean Tutorial Image 29")

Now record your spaces secret key and your spaces access key in the text file on your laptop

>     digitaloceanspaces_access_key="DO00Y....."
>     digitaloceanspaces_secret_key="eAlmw....."


--------------------------

You now need to make a note of the email address that you login to your digitalocean account with:

>     digitalocean_email="peterdigitalocean@yahoo.com"

-----------------------------------

You then need the url that you want to use for your website. If you don't have a DNS URL for your website, you need to purchase one and set the nameservers to digitalocean as described [here](../../Deployment/Nameservers.md)

>     digitalocean_dns_name="www.drpatient.uk"

--------------------------------

You then need to get an access key for your personal github account (you are advised to have a new separate github account for use with this toolkit)

[Setting up a github account](https://docs.github.com/en/get-started/onboarding/getting-started-with-your-github-account)  

[Setting up personal access tokens for github](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)  

(your personal access token must have enough privileges to create repositories which means the "administrator" and "contents" options need to be set to read/write. Only setting these two values follows the principle of least privileges) 

![](images/expedited/do-30.png "Digital Ocean Tutorial Image 30")
![](images/expedited/do-31.png "Digital Ocean Tutorial Image 31")
![](images/expedited/do-32.png "Digital Ocean Tutorial Image 32")
![](images/expedited/do-33.png "Digital Ocean Tutorial Image 33")


>     digitalocean_github_username="adt-apps" #MANDATORY
>     digitalocean_github_key="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k4" #MANDATORY

So, that should be all the core credentials that I need to make a deployment. I can save my text file now (and keep it secure) because I might want to use these credentials again for other deployments or redeployments.  

--------------------------------------------

So, at the command line of my build machine that we spun up earlier:

My chosen username is "wintersys-projects"

So, to begin an expedited build process, I need to:

>     cd /home/wintersys-projects/adt-build-machine-scripts/templatedconfigurations/templates/digitalocean

Then we can open up the 

>     vi digitalocean1.tmpl

I then update all fields marked "MANDATORY" (marked in red) referring to the values that I have stored in the text file in my laptop in the correct template and when I am finished it looks like:

\###############################################################################################  
\# Refer to: ${BUILD_HOME}/templatedconfigurations/specification.md  
\###############################################################################################  
\#This template is configured for virgin style builds  
  
\#####MANDATORY - Bare minimum set of values that you must provide for a build to have any chance of succeeding  
\#####NOT REQUIRED - isn't used by the Exoscale  
 
\#####Application Settings#########  
<span style="color:red">export APPLICATION="joomla" #MANDATORY </span>  
<span style="color:red">export JOOMLA_VERSION="5.3.0" #MANDATORY (depending on the above settings - a joomla deployment) </span>  
export DRUPAL_VERSION="" #MANDATORY (depending on the above settings - a drupal deployment)  
<span style="color:red">export APPLICATION_BASELINE_SOURCECODE_REPOSITORY="JOOMLA:5.3.0" #MANDATORY </span>  
export BASELINE_DB_REPOSITORY="VIRGIN"  
export APPLICATION_LANGUAGE="PHP"  
export PHP_VERSION="8.4"  
export BUILD_ARCHIVE_CHOICE="virgin"  
export APPLICATION_NAME="Demo Application"  
    
\#####S3 Datastore Settings#######    
<span style="color:red">export S3_ACCESS_KEY="DO00YVU7YHGD1HHDJK"  #MANDATORY</span>     
<span style="color:red">export S3_SECRET_KEY="eAlmwh3y7eJovZSN/TxSz7RZrsbdvjvburfr7whs"  #MANDATORY</span>    
export S3_HOST_BASE="ams3.digitaloceanspaces.com"  
export S3_LOCATION="US" #For digitalocean, this always needs to be set to "US"  
export DATASTORE_CHOICE="digitalocean"  
export DIRECTORIES_TO_MOUNT="" #This should always be unset for a virgin and baseline deployments  
export PERSIST_ASSETS_TO_DATASTORE="0" #This should always be set to 0 for a virgin and baseline deployment  
     
\#####OS Settings#########  
export BUILDOS="debian" # One of ubuntu|debian  
export BUILDOS_VERSION="12" #  24.04 (or later for BUILDOS="ubuntu") | 12 (or later for BUILDOS="debian")
 
\######Cloudhost Provider Settings#######  
<span style="color:red">export TOKEN="dop_v1_51ac97f187fadb12ac70022521dbafh3f56259608fad0dadafbb594e2417ab78dba2" #MANDATORY</span>  
export S3_ACCESS_KEY=""  #NOT REQUIRED   
export S3_SECRET_KEY=""  #NOT REQUIRED   
export CLOUDHOST_ACCOUNT_ID=""  #NOT REQUIRED  
     
\######DNS Settings##########  
<span style="color:red">export DNS_USERNAME="peterdigitalocean@yahoo.com"  #MANDATORY</span>    
<span style="color:red">export DNS_SECURITY_KEY="dop_v1_51ac97f187fadb12ac70022521dbafh3f56259608fad0dadafbb594e2417ab78dba2"  #MANDATORY</span>    
export DNS_CHOICE="digitalocean" #you will need to set your DNS nameservers according to this choice

\#####Webserver Settings########  
<span style="color:red">export WEBSITE_DISPLAY_NAME="Joomla Tutorial" #MANDATORY</span>    
<span style="color:red">export WEBSITE_NAME="drpatient" #MANDATORY</span>    
<span style="color:red">export WEBSITE_URL="www.drpatient.uk"  #MANDATORY</span>    
export WEBSERVER_CHOICE="NGINX"  
export NUMBER_WS="1"  
export MAX_WEBSERVERS="10"
   
\#####Git settings#####  
export GIT_USER="Templated User"   
export GIT_EMAIL_ADDRESS="templateduser@dummyemailZ123.com"   
   
\#####Infrastructure Repository Settings#######  
export INFRASTRUCTURE_REPOSITORY_PROVIDER="github"  
export INFRASTRUCTURE_REPOSITORY_OWNER="wintersys-projects"  
export INFRASTRUCTURE_REPOSITORY_USERNAME="wintersys-projects"  
export INFRASTRUCTURE_REPOSITORY_PASSWORD="none"  
    
\###### Application Repository Settings########  
export APPLICATION_REPOSITORY_PROVIDER="github"   
<span style="color:red">export APPLICATION_REPOSITORY_OWNER="adt-apps" #MANDATORY</span>    
<span style="color:red">export APPLICATION_REPOSITORY_USERNAME="adt-apps" #MANDATORY</span>    
<span style="color:red">export APPLICATION_REPOSITORY_PASSWORD="ghp_d51wi3xkDez6Mi53hypNm" #MANDATORY</span>    
<span style="color:red">export APPLICATION_REPOSITORY_TOKEN="ghp_d51wi3xkDez6Mi53hypNm" #MANDATORY</span>    
    
\##### System Email Settings#########  
export SYSTEM_EMAIL_PROVIDER=""  
export SYSTEM_TOEMAIL_ADDRESS=""  
export SYSTEM_FROMEMAIL_ADDRESS=""  
export SYSTEM_EMAIL_USERNAME=""   
export SYSTEM_EMAIL_PASSWORD=""   
export EMAIL_NOTIFICATION_LEVEL="ERROR"  

\##### Database Settings######  
export DB_PORT="2035"  
export DATABASE_INSTALLATION_TYPE="Maria"  
export DATABASE_DBaaS_INSTALLATION_TYPE=""  
export BYPASS_DB_LAYER="0"  
    
\#####Server Settings #######  
export REGION="lon1"  
export DB_SERVER_TYPE="s-1vcpu-1gb"  
export WS_SERVER_TYPE="s-1vcpu-1gb"  
export AS_SERVER_TYPE="s-1vcpu-1gb"  
export AUTH_SERVER_TYPE="s-1vcpu-1gb"  
export CLOUDHOST="digitalocean"  
export MACHINE_TYPE="DROPLET"  
export SSH_PORT="1035"  
export SERVER_TIMEZONE_CONTINENT="Europe"  
export SERVER_TIMEZONE_CITY="London"  
export USER="root"  
export SYNC_WEBROOTS="0"  
export AUTHENTICATION_SERVER="0"  
export USER_EMAIL_DOMAIN=""  

\#####Build Settings######  
export PRODUCTION="0"  
export DEVELOPMENT="1"  
<span style="color:red">export BUILD_IDENTIFIER="tutorial" #MANDATORY </span>     
export NO_AUTOSCALERS="0"  

\#####Security Settings#####  
export ACTIVE_FIREWALLS="3"  
export PUBLIC_KEY_NAME="AGILE_TOOLKIT_PUBLIC_KEY"  
export SSL_GENERATION_METHOD="AUTOMATIC"  
export SSL_GENERATION_SERVICE="LETSENCRYPT"  
export SSL_LIVE_CERT="1"  
export ALGORITHM="rsa"  
export BUILD_MACHINE_VPC="1"  
<span style="color:red">export VPC_IP_RANGE="10.106.16.0/20" </span>  
export VPC_NAME="adt-vpc"  
     
\#####Build Style#######  
export INPARALLEL="0"  

IMPORTANT: Remember to set VPC_IP_RAMGE approptiately. You can get the VPC_IP_RANGE as shown in this image:

![](images/expedited/do-34.png "Digital Ocean Tutorial Image 34")



If your template looks similar to the one I have provided here with all the fields marked in red having your custom values then you should be ready for deployment

>     ${BUILD_HOME}/ExpeditedAgileDeploymentToolkit.sh

Note: because I haven't asked you to set up system emailing (to keep this tutorial as simple as possible) you will see these below messages during the deployment but you can safely ignore them it just means that there won't be any system emails sent for this deployment iteration.

IGNORE THESE IF YOU SEE THEM
>     Your value for the variable SYSTEM_EMAIL_PROVIDER () doesn't appear to be valid please review
>     It looks to me like the email address for the variable SYSTEM_TOEMAIL_ADDRESS () doesn't appear to be valid please review
>     It looks to me like the email address for the variable SYSTEM_FROMEMAIL_ADDRESS () doesn't appear to be valid please review

You will then need to answer the questions that you are asked and in a few minutes you should be able to install joomla using the GUI system of your browser. Please note, the credentials,port,database IP that you need to enter into the joomla GUI will be shown at the end of the build process.

When I ran the build process when writing this tutorial it looked as follows:

![](images/expedited/do-35.png "Digital Ocean Tutorial Image 35")
![](images/expedited/do-36.png "Digital Ocean Tutorial Image 36")
![](images/expedited/do-37.png "Digital Ocean Tutorial Image 37")
![](images/expedited/do-38.png "Digital Ocean Tutorial Image 38")
![](images/expedited/do-39.png "Digital Ocean Tutorial Image 39")

<span style="color:red">NOTE: In this image or this part of the output you will find the credentials you must set for your joomla application</span>   

![](images/expedited/do-40.png "Digital Ocean Tutorial Image 40")
![](images/expedited/do-41.png "Digital Ocean Tutorial Image 41")

<span style="color:red">NOTE: To display the joomla application you must go to your website URL in your browser such as https://www.drpatient.uk/installation/index.php</span>   

![](images/expedited/do-42.png "Digital Ocean Tutorial Image 42")

Assuming that you have your Joomla application online that's this tutorial through.   

What I would do if I wanted to build a Wordpress, Moodle or Drupal installation would be to follow the same procedure with the same template, but, minimally change the template as follows:

**For Wordpress:**

>     export APPLICATION="wordpress"
>     export APPLICATION_BASELINE_SOURCECODE_REPOSITORY="WORDPRESS" #MANDATORY 

**For Drupal:**

>     export APPLICATION="drupal"
>     export DRUPAL_VERSION="11.0.1" 
>     export APPLICATION_BASELINE_SOURCECODE_REPOSITORY="DRUPAL:11.0.1" #MANDATORY 

**For Moodle:**

>     export APPLICATION="moodle"
>     export APPLICATION_BASELINE_SOURCECODE_REPOSITORY="MOODLE" #MANDATORY 

So, you have a template now that you can use over and over again for deploying different installations of these CMS systems. You can study the spec and learn how to modify the template in order to change machine sizes, regions, PHP settings and so on. 
