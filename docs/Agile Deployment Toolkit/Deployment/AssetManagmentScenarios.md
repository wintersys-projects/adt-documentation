There are various scenarios related to the dynamic assets such as images, text files and videos that your application generates. I will outline those scenarios here. First of all I will describe scenarios where elastic filesystems are not available for mount because the current provider either doesn't support them or you don't want to use them because they are more expensive than S3 solutions. 

1. You have multiple webservers but your application doesn't generate many or even any dynamic assets

You can just use the standard webroot /var/www/html synchronised with the webroots of the other machines using the heavy weight file sync mechanism

2. Your application generates a lot of dynamic assets:

You mount an S3 bucket for each of the various directories that you expect your application to produce assets into. This will involve setting up your template such as

>     PERSIST_ASSETS_TO_DATASTORE="1"
>     DIRECTORIES_TO_MOUNT="images:media/videos"

When you set these values in your template it will mount two separate buckets created in your datatstore as /var/www/images and /var/www/media/videos

When your application accesses these asset directories it will be accessing the media mounted from s3. The mount is made by using one of the following tools depending how you have configured "buildstyles.dat"

>     s3fs, goofys, geesefs, or rclone

You will then have a whole s3 bucket for each of these mount points and so you could have "n" buckets mounted into your webroot and have them all as their separate bucket giving you huge capacity. There is a performance penalty and it remains to be seen how ths functions under load but as a solution it exists right now although it is not commonly recommended to mount s3 buckets like this. Its possible you can fine tune the parameters of your choosen tool compared to what is in the default script to improve performance for your particular use case. 

Its not recommended but you might have an application usage scenario where you need enormous data capacity and performance is not so important and in that case you can use mhddfs in buildstyles.dat to merge multiple s3 buckets into a single mount point in your webroot.

When you switch on the heavyweight filesync mechanism for your webroot the webroots of your webservers will be synchronised but the directories where the assets are that are mounted from s3 will be excluded from the webroot synchronisation process.

3. You can repeat scenario 2 uploading assets to an s3 bucket using the datastore mount tool of your choice but at an application level you can connect your application to the s3 bucket using a CDN to access the assets in the s3 bucket thereby reducing the load on your webservers compared to scenario 2 where its your webservers responsibility to serve the assets when your application requests them and not a CDN

You can read about how to setup your webroot for heavyweight synchronisation here:

[heavyweight](https://www.wintersys-projects.uk/Agile%20Deployment%20Toolkit/Operations/FileSystemSyncing)

4. Offload assets at an application level whereby you don't need to use any of the datastore mount tools but you most likely still want to stop the application assets which can be gigabytes and more of data in a busy application from being stored as part of your backup and the way you can do this is by setting (for example in joomla)

>     DIRECTORIES_TO_MOUNT="images"

And that will bypass storing the assets in that directory to the backup when a backup is made. This is essential because backups are only really meant for the sourcecode of your application, not the assets because you don't want to be downloading gigabytes of asset data every time you install from an application backup. 
