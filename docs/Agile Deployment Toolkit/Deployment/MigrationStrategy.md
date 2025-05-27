WEBROOT

1. download a copy of your websites webroot to your linux laptop and extract it into a working  directory (${working_dir} for example /home/bob/scratch

2. copy this shellscript to your linux laptop and call it RemoveApplicationBranding.sh

>     #!/bin/sh
>     
>     website_url="${1}"
>     working_directory="${2}"
>     
>     root_domain="`/bin/echo ${website_url} | /usr/bin/awk -F'.' '{$1=""}1' | /bin/sed 's/^ //g' | /bin/sed 's/ /./g'`"
>     
>     /usr/bin/find ${working_directory} -type f -exec sed -i -e "s/${domainspecifier}/ApplicationDomainSpec/g" -e "s/${website_url}/applicationdomainwww.tld/g" -e "s/${root_domain}/applicationrootdomain.tld/g" {} \;

3. Run the script RemoveApplicationBranding.sh passing the website url of your original website and the working directory where you extracted your webroot to as parameters, for example:

>     /bin/sh ./RemoveApplicationBranding.sh www.nuocial.uk /home/bob/scratch

3. Create dba.dat files and remove any configuration files for example /home/bob/scratchconfiguration.php /home/bob/scratchwp-config.php

4. Create a private repository with your git provider

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

3. NOTE: if you are changing the domain name of your website and you are deploying a wordpress application you will need to run application.sql through a tool called "serfix" for it to work correctly. You can find serfix [here](https://github.com/astockwell/serfix)

3. Run the shellscript passing in the original website url. For example:

>     /bin/sh ./RemoveApplicationBranding.sh www.nuocial.uk

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
