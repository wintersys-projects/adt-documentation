Depending on your application type you might want to place different requirements on your webservers in terms of how you configure your application webroot. Its quite possible in different scenarios down the line you might have applications with different needs, for example you might have an application with no dynamic assets being uploaded and a relatively small code base in which case one of the solutions I am about to describe will be the best fit solution and you might have another application with terrabytes of data to access at a reasonable price with speed not being such an important factor for you or you might have a lot of dynamic assets and speed is still an important factor and so on. So, you need to do an analysis of which of the provided solution is the best fit solution for your application before you make a deployment to use it. So, let me outline some various scenarios.

1. The native filesystem of your webserver without any services to embellish it. This would be how you could arrange things if your application doesn't produce dynamic assets through user uploads and so on and it has a relatively small code base. If you have more than one webserver you will likely want to switch on SYNC_WEBROOTS to synchronise the webroots of your different webservers when any changes are made

2. Offload your dynamic assets at an application level. CMS systems such as joomla provide solutions or plugins to offload dynamic assets to an S£ backed storage solution, for example: [amazon s3 for joomla](https://extensions.joomla.org/extension/amazon-s3-filesystem/). This is the prefered solution for offloading your dynamic assets from your webserver because it reduces the load on your webserver. In some situations (Community Builder) for example, offloading assets at an application level are not possible at the moment [community builder](https://www.joomlapolis.com/forum/professional-members-support/246825-cdns) and so I made the effort to build out a solution using tools such as rclone, s3fs, geesefs and goofys to mount S3 buckets to the webservers directly and I describe that next.

3. If you want to have a very large data capacity available to you you can mount various buckets which are automatically created according to a defined nomenclature when you set some parameters in your template as described [here](https://www.wintersys-projects.uk/Agile%20Deployment%20Toolkit/Operations/WebrootConfigurationWorkflow/) under operational workflows. So, you can set as many directories as you want here so your application might want one directory for images one directory for data and one directory for videos and each of those directories will have its own associated bucket with the huge amounts of data avaiable to it there. 

4. And so if even that is not enough you can have up to 9 buckets all available as a shared mount on one mount point. So you could have

/var/www/images1,/var/www/images2,/var/www/images3,/var/www/images4/var/www/images5,/var/www/images6 as a single shared mount to /var/www/html/images

This is easy to setup all you have to do is put the following into your template:

DIRECTORIES_TO_MOUNT="merge=images6"

And so what that will do is it will create 6 buckets if they don't exist mount them to your webservers file system as separate mount points /var/www/images1, for example, and then merge them into a single shared mount point /var/www/html/images

So, there's several layers to that and being backed by S3 it won't be as fast as using a native filesystem but the advantage you get here is extremely large shared capacity on your webservers. 

So, you might have your setup as following if you want a shared mount

PERSIST_ASSETS_TO_DATASTORE="1"
DIRECTORIES_TO_MOUNT="merge=images6:media/data"

And that will give you 7 buckets mounted to two mount points. 

The reason I offer this as a solution is two fold: cost (S3 storage is cheaper than block storage) and secondly (at the time of writing) networked filesystems have become available which I am going to support in due course (its 2025 right now and I intend to support add support for them in 2026) networked filesystems are more expensive however so if you are on a budget you might prefer to use S3 backed storage instead of the networked file systems that are being offered now. The networked filesystems I have seen at the moment are from [vultr](https://www.vultr.com/products/file-system) and [digital ocean](https://www.digitalocean.com/products/storage/network-file-storage) if you see documentation for these products I have implemented support for them (although it won't currently be available in that style for linode and exoscale) as they don't have comparable offerings at the moment. 
