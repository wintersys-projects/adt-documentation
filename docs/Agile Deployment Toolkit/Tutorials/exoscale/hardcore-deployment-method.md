
To get a "hardcore" userdata script that you can use for multiple deployments what you need will need a fully configured template that the user data script can be built from. To have a fully configured template, you can follow the appropriate tutorial below depending on whether you want your userdata script to deploy a virgin CMS, a baselined application or a deployment based on a temporal backup in your datastore.

[Virgin CMS Installation](./expedited-virgin-joomla.md)   
[Baseline CMS Installation](./expedited-baseline-joomla.md)  
[Temporal CMS Installation](./expedited-temporal-joomla.md)

Once you have made a deployment using one of these tutorials then you can be confident that the template associated with the deployment is valid and knowing that you have a valid template you can go ahead and create a hardcore build userdata script. 

Virgin class builds are associated with template1 (exoscale1.tmpl), baseline builds are associated with template 2 (exoscale2.tmpl) and temporal builds are associated with template 3 (exoscale3.tmpl)

In this example, we will use template 1 assuming that we have followed the Vigin CMS installation tutorial.  

>     /bin/mkdir ./adt-build-machine-scripts/overridescripts/
>     /bin/cp ./adt-build-machine-scripts/templatedconfigurations/templates/exoscale/exoscale1.tmpl ./adt-build-machine-scripts/overridescripts/exoscale1override.tmpl  

Then you need to run the script:

>     cd helperscripts

>     ./GenerateHardcoreUserDataScript.sh

This will leave you with a script:

>    ../userdatascripts/${userdatascript}   

where ${userdatascript} is the descriptive name you gave when prompted.  

Edit the userdata script (../userdatascripts/${userdatascript} )

It is mandatory to edit your userdata script and modify these values within it to your liking:

>     export BUILDMACHINE_USER="agile-user"
>     export BUILDMACHINE_PASSWORD="Hjdhfb34hd£" #Make sure any password you choose is strong enough to pass any strength enforcement rules of your OS
>     export BUILDMACHINE_SSH_PORT="1035"
>     export LAPTOP_IP="111.111.111.111"

>     export SSH=\"\" #paste your public key here
>     export SELECTED_TEMPLATE="1"


------------------------------------------

Now you have your userdata script take a copy of the entirity of it using copy and paste and then follow [these](./buildmachine-hardcore.md) instructions PASTING THE SCRIPT YOU HAVE JUST COPIED INTO THE USERDATA AREA OF YOUR EXOSCALE MACHINE INSTEAD OF THE MODIFIED TEMPLATE. The build machine will then install **AND**  run the agile deployment toolkit. This is just an alternative method to the expedited build process which you may or may not perfer.


At this point, your build machine should be up and running. 
