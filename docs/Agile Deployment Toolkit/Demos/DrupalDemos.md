#### MANDATORY PRE-REQUISITE STEPS (NEEDED BY ALL DEMOS BELOW)  

Perform step 1 or 2 below according to your experience and apply the overrides to your StackScript as described below for your desired demo type before you click "Create Linode"

1. If you are a beginner, follow [here](./QuickStartDemosPrepBeginnerLevel.md)  
2. If you are an expert, follow [here](./QuickStartDemosPrepExpertLevel.md)

-------------------------

#### QUICK DEMO OVERRIDE EXAMPLES

Once you have performed the mandatory steps above you can action specific demos by overriding the mentioned settings in the StackScript before you deploy it. By overriding different settings as described below, you will deploy different application types using the same StackScript.  

### Demo 1 (StackScript overrides for a baselined Opensocial demo)

[Opensocial](https://getopensocial.com)

1. Once the application is installed, the username is "webmaster" and the password is "mnbcxz098321QQQZZZ"  
 
>     set "The Display name for your website e.g. My Demo Website" to "My Opensocial Demo"  
>     set "APPLICATION" to "drupal"  
>     set "BASELINE DB REPOSITORY" to "opensocial-db-baseline" (with sample data) or "opensocialvanilla-db-baseline" (without sample data)  
>     set "APPLICATION BASELINE SOURCECODE REPOSITORY" to "opensocial-webroot-sourcecode-baseline" (with sample data) or "opensocialvanilla-webroot-sourcecode-baseline" (without sample data)

If you are using the cloud-init method raher than StackScript these you should set

>     export WEBSITE_DISPLAY_NAME="My Opensocial Demo"
>     export APPLICATION="drupal"  
>     export BASELINE DB REPOSITORY="opensocial-db-baseline" 
>     export APPLICATION BASELINE SOURCECODE REPOSITORY="opensocial-webroot-sourcecode-baseline"

NOTE: If you get any error messages from the Drupal CMS once it is installed you need to "clear all caches" which in my case I can do by going to this URL in my browser:

>     https://www.nuocial.uk/admin/config/development/performance

------------------------------

