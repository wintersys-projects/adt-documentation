#### DEVELOPING THE BUILD MACHINE SCRIPTS  

On your build machine installation you will find a clone of your live **&#0036;BUILD_HOME** directory in the **/home/development** directory.
This is where you can make changes to the scripts of the build machine and when you are ready push them to your github repository branch or sync them to your live **&#0036;BUILD_HOME** area.  

The workflow is  

1. Edit and or add scripts to **/home/development**
3. When you are happy with your script alterations, you have two options

- sync the changes you have made to your live **&#0036;BUILD_HOME** area
- push the changes you have made to your github branch

There are three scripts which help you do this easily they are called  

- /usr/sbin/sync - this script will sync your development scripts with your live scripts located at **&#0036;BUILD_HOME**    

- /usr/sbin/push - this script will push the modifications you have made to your github branch you call this with a commit message - **/usr/sbin/push "commit message 1"**    

- /usr/sbin/push-and-sync - this script will perform the push to git and the sync to the live directories in **&#0036;BUILD_HOME** - **/usr/sbin/push-and-sync "commit message 1"**   

This then is suggested workflow if you want to enhance and alter the build machine scripts
