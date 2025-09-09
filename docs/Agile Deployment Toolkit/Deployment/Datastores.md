The following is the list of buckets that can be created in the datastore during the operation of the toolkit


##### Buckets that persist across multiple deployments

>     1. s3://<website-url>-assets-<asset-type>
>     2. s3://<website-url>-assets-<asset-type>-backup-$$
>     3. s3://authip-adt-allowed-<build-machine-ip>
>     4. s3://<website-url>-multi-region
>     5. s3://<website-url>-ssl
>     6. s3://<website-url>-<period>
>     7. s3://<website-url>-db-<period>
>     8. s3://<website-url>-snap
1. This stores user generated application assets. This could grow to a large size based on application usage
2. This is a backup of the assets. When there is a new deployment of an application domain a backup can be made of existing assets from previous deployments.
3. This bucket contains a list of laptop IPs which are granted access to the build machine through the firewall.
4. In a multi-region deployment anything which needs to be shared between regions is written here
5. ssl certificates can be stored and therefore reused across separate deployment runs for a specific domain
6. This is where backups of the webroot of the application is stored for a specific period (hourly, daily and so on)
7. This is where backups of the db of the application is stored for a specific period (hourly, daily and so on)
8. This is where snapshot metadata is stored.

##### Buckets that are unique to each deployment

>     1. s3://<website-url>-config-<unique-token>

1. This is the main configuration bucket where the configuration details of the application can be stored. This bucket is uniquely generated for each deployment run for a specific domain. 
