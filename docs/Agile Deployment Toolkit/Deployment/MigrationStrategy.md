WEBROOT

1. download a copy of your website's webroot to your linux laptop and extract it into a working  directory (${working_dir} for example /home/bob/scratch. Depending on what application you are deploying files which might be outside the webroot (for example moodledata for moodle) or private (for drupal) you need to make sure that if there are such directories they are present at the top level of your webroot. You can look at what is expected during installation by reviewing files such as [this](https://github.com/wintersys-projects/adt-webserver-scripts/blob/main/providerscripts/application/customise/drupal/CustomiseApplication.sh)

**IF YOU WANT TO GIVE YOUR MIGRATED WEBSITE A DIFFERENT DOMAIN NAME, FOLLOW THIS STEP (you can search and replace in a gui instead if you want)
IF YOU ARE DEPLOYING TO THE SAME DOMAIN NAME AS YOU PREVIOUSLY WERE, YOU CAN SKIP THIS STEP**

2. copy this shellscript to your linux laptop and call it RemoveApplicationBranding.sh

>     #!/bin/sh
>     
>     website_url="${1}"
>     working_directory="${2}"
>     
>     root_domain="`/bin/echo ${website_url} | /usr/bin/awk -F'.' '{$1=""}1' | /bin/sed 's/^ //g' | /bin/sed 's/ /./g'`"
>     
>     /usr/bin/find ${working_directory} -type f -exec sed -i -e "s/${website_url}/applicationdomainwww.tld/g" -e "s/${root_domain}/applicationrootdomain.tld/g" {} \;
 
Run the script RemoveApplicationBranding.sh passing the website url of your original website and the working directory where you extracted your webroot to as parameters, for example:

>     /bin/sh ./RemoveApplicationBranding.sh www.nuocial.uk /home/bob/scratch

3. Make sure dba.dat dbe.dat and dbp.dat (and for moodle dbt.dat) files are present and correct and remove any configuration files for example /home/bob/scratch/configuration.php for joomla or /home/bob/scratch/wp-config.php for wordpress


5. Create a private repository with your git provider

>     <identifier>-webroot-sourcecode-baseline

and push the entire contents of your working directory to the repository in a similar way to this:

>     git init
>     git add .
>     git commit -m "first commit"
>     git branch -M main
>     git remote add origin https://github.com/adt-apps/<identifier>-webroot-sourcecode-baseline.git
>     git push -u origin main

DATABASE

1. download a copy of a database dump of your website to your laptop and call it (mandatory naming don't call it anything else) applicationDB.sql/.psql

**IF YOU WANT TO GIVE YOUR MIGRATED WEBSITE A DIFFERENT DOMAIN NAME, FOLLOW THIS STEP (you can search and replace in a gui instead if you want)
IF YOU ARE DEPLOYING TO THE SAME DOMAIN NAME AS YOU PREVIOUSLY WERE, YOU CAN SKIP THIS STEP**
2. copy the following shell script to your laptop and call it RemoveApplicationBranding.sh

>     #!/bin/sh
>     
>     website_url="${1}"
>     
>     root_domain="`/bin/echo ${website_url} | /usr/bin/awk -F'.' '{$1=""}1' | /bin/sed 's/^ //g' | /bin/sed 's/ /./g'`"
>    
>     /bin/sed -i "s/${website_url}/www.applicationdomain.tld/g" ./applicationDB.sql|.psql
>     /bin/sed -i "s/@${root_domain}/@applicationdomain.tld/g" ./applicationDB.sql|.psql
>     /bin/sed -i "s/${root_domain}/applicationdomain.tld/g" ./applicationDB.sql|.psql

Run the shellscript passing in the original website url. For example:

>     /bin/sh ./RemoveApplicationBranding.sh www.nuocial.uk

**NOTE:** If you are changing the domain name of your website and you are deploying a wordpress application you will need to run applicationDB.sql through a tool called "serfix" for it to work correctly. You can find serfix [here](https://github.com/astockwell/serfix)

3. Create a private repository called

>     <identifier>-db-baseline

with your git provider

5. Push the file applicationDB.sql to this repository similar to what follows:

>     git init
>     git add .
>     git commit -m "first commit"
>     git branch -M main
>     git remote add origin https://github.com/adt-apps/<identifier>-db-baseline.git
>     git push -u origin main

You can now deploy your website as you would any other baselined website
