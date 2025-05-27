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
>     domainspecifier="`/bin/echo ${website_url} | /usr/bin/awk -F'.' '{ for(i = 1; i <= NF; i++) { print $i; } }' | /usr/bin/cut -c1-3 | /usr/bin/tr '\n' '-' | /bin/sed 's/-//g'`"
>     
>     /usr/bin/find ${working_directory} -type f -exec sed -i -e "s/${domainspecifier}/ApplicationDomainSpec/g" -e "s/${website_url}/applicationdomainwww.tld/g" -e "s/${root_domain}/applicationrootdomain.tld/g" {} \;

3. Run the script RemoveApplicationBranding.sh passing the website url of your original website and the working directory where you extracted your webroot to as parameters, for example:

>     /bin/sh ./RemoveApplicationBranding.sh www.nuocial.uk /home/bob/scratch

3. Create dba.dat files and remove any configuration files for example /home/bob/scratchconfiguration.php /home/bob/scratchwp-config.php

4. Create a private repository with your git provider <identity>-webroot-sourcecode-baseline and push the entire contents of your working directory to the repository

DATABASE

1. download a copy of a database dump of your website to your laptop and call it (mandatory naming don't call it anything else) applicationDB.sql/.psql

2. copy the following shell script to your laptop

>     #!/bin/sh
>     
>     website_url="${1}"
>     
>     root_domain="`/bin/echo ${website_url} | /usr/bin/awk -F'.' '{$1=""}1' | /bin/sed 's/^ //g' | /bin/sed 's/ /./g'`"
>    
>     
>     domainspecifier="`/bin/echo ${website_url} | /usr/bin/awk -F'.' '{ for(i = 1; i <= NF; i++) { print $i; } }' | /usr/bin/cut -c1-3 | /usr/bin/tr '\n' '-' | /bin/sed 's/-//g'`"
>          
>     /bin/sed -i "s/${domainspecifier}/ApplicationDomainSpec/g" ./applicationDB.sql/.psql
>     /bin/sed -i "s/${website_url}/www.applicationdomain.tld/g" ./applicationDB.sql/.psql
>     /bin/sed -i "s/@${}/@applicationdomain.tld/g" ./applicationDB.sql/.psql
>     /bin/sed -i "s/${ROOT_DOMAIN}/applicationdomain.tld/g" ./applicationDB.sql/.psql

3. Create a private repository called <identifier>-db-baseline with your git provider

4. Push the file applicationDB.sql to this repository

You can now deploy your website as you would any other baselined website
