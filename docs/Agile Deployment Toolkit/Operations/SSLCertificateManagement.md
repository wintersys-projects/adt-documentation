### SSL CERTIFICATE RENEWAL

Each webserver in your system requires a valid SSL cerificate. Currenly an SSL certificate can be generated by letsencrypt or it can be manually supplied.

When the build is being initiated on the build machine part of what happens is as follows:

1. The build machine checks if there is an SSL certificate available for the current domain, cloudhost and build identifier on the file system of the build machine. If there is (and it is valid) then that certificate is used
2. If there is no pre-existing SSL certificate on the file system of the build-machine that meets our needs then a new certificate is generated or supplied by the person making the deployment
3. One way or another we have to have an acceptable SSL certificate and the certificate we have is copied to the S3 datastore that is shared with the webservers. A check is made to ensure that the SSL certificate has been successfully copied to the S3 Datastore
4. When each webserver builds then it copies the certificate from the S3 Datastore to its own filesystem and configures the webserver  to use this certificate for its SSL needs. We can then forget about the SSL certificate for a while.
5. Every night a cronjob runs that checks the validity of the SSL certificate on each webserver. If the certificate is found to be short on validity or is about to expire, then one of the webservers will generate a new certificate and copy that cerificate to the S3 datastore, overwriting the original certificate. All the other webservers then copy this "new" SSL certificate to their own file systems and restart their webservers. 

This whole process is basically a hands off process and should only need manual intervention if something is off with the process for some reason so unless you are manually deploying an SSL certificate as a deployer you shouldn't need to to anything to have your web property SSL secured. 

-------------------------------

In a bit more detail, this process can be described as:

As part of the pre-build process on the build-machine a test is made to see if these files already exist from a previous build

>     ${BUILD_HOME}/runtimedata/${CLOUDHOST}/${BUILD_IDENTIFIER}/ssl/${WEBSITE_URL}/fullchain.pem 
>     ${BUILD_HOME}/runtimedata/${CLOUDHOST}/${BUILD_IDENTIFIER}/ssl/${WEBSITE_URL}/privkey.pem 

If they exist then a check is made to see if they are valid certificates. If the certificates are valid they are copied to the datastore. If they are not valid then new certificates are generated and stored in these same files and then copied to the S3 datastore. A check is made to see that the certificates have copied successfully to the datastore.

What 1. means is that at the end of the pre-build process SSL certificates will be available in the datastore which can be used by any webserver as its SSL certificate. When each webserver is built either the initial build process webserver or a webserver which has been built as part of an autoscaling event the certificate the certificates generated in 1. will be copied to the new webserver from the datastore and can then be used by that webserver as its SSL certificate. Each webserver stores its ssl certificates at

>     ${HOME}/ssl/live/${WEBSITE_URL}/*.pem

There is a daily cron job which runs once a day to check certificate validation. If there are n webservers running then the webserver that "gets there first" checks the validity of its SSL certificate (which will be either valid or invalid for all n webservers) and then if the existing certificate is found to be invalid, a new certificate is generated on the elected machine and is written to the S3 datastore. All the other webservers then copy the new certificate from the datastore to their own

>     ${HOME}/ssl/live/${WEBSITE_URL}/*.pem

If this system works correctly it should be a "hands off process" meaning that in normal operation you don't need to do anything to do with certificates because all of this manages it behind the scenes.

if SSL_GENERATION_METHOD is set to MANUAL then the pre-build process will ask you for a certificate to use for the current build which you will have to obtain from your prefered third party certificate provider. If you use the manual SSL certificate approach you will have to manually update the certificates on your servers. The manual option is only really meant for an emergency if you can't get your certificate in the usual way.
