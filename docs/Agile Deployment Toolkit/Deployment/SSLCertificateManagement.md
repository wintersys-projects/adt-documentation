SSL Certificate Generation Process

When you make a deployment (expedited or hardcore) that includes a webserver then that webserver will require an SSL certificate. 

The certificate will be generated and installed as part of the build process. Two different certificate generation services are supported, letsencrypt and zerossl. You set one or the other by setting the following values

For Letsencrypt you need to set

SSLCERTCLIENT:lego in the configuration file ${BUILD_HOME}/builddescriptors/buildstyles.dat on the build machine

and you need to set

export SSL_GENERATION_SERVICE="LETSENCRYPT" in your template

(be aware that for production standard certificates there are issuance limits and if your build stalls waiting for a certificate to be issued its quite possible that its because you have hit an issuance limit)

For Zerossl you need to set

SSLCERTCLIENT:acme in the configuration file ${BUILD_HOME}/builddescriptors/buildstyles.dat on the build machine

and you need to set

export SSL_GENERATION_SERVICE="ZEROSSL" in your template

If you set these values correctly the system will try and deploy a certificate that your server can use. If a cerfificate is successfully generated a copy of it will be stored on the filesystem of your buildmachine at:

>      ${BUILD_HOME}/runtimedata/${CLOUDHOST}/${BUILD_IDENTIFIER}/ssl/${DNS_CHOICE}/lets/${WEBSITE_URL}

or 

>      ${BUILD_HOME}/runtimedata/${CLOUDHOST}/${BUILD_IDENTIFIER}/ssl/${DNS_CHOICE}/zero/${WEBSITE_URL}

A copy will also be written to the datastore which is at:

>      s3://<website-url>-<dns-choice>-<ssl-client>-ssl

The webservers themselves will pick up and install the SSL certificate from the copy that is in the datastore

On subsequent deployments for the same webserver url, the deployment process will make use of the copy of the certificate that is in the datastore which is checked for validity and then installed

SSL Certificate Generation Process

The SSL certificates that are now installed on your webservers have a finite lifespan and so at some point if your servers are running longterm the certificates will need to be renewed/replaced. I use the build machine to coordinate certificate renewal and I do this by using a cronjob running on the build machine to check the age of the certificates that are on the build machine firewall and if they are close to expiring new certificates are issued. This cron job is installed on the build machine as part of the build process but by default it is commented out and so there is an action that you are prompted to do or expected to know about as part of the build process which is that if you want your certificates to be renewed which is to uncomment the appropriate cron task. If your build machine isn't online 24/7, for example, your build machine is run from a portable usb running debian/ubuntu then you will need to take the crontask (which runs nightly) and run it yourself as a command from the command line when at a time when your build machine is online. Each webserver checks on a daily basis for updated SSL certificates in the datastore and if it finds updated certs they are installed on the webserver and the webserver restarted. 
