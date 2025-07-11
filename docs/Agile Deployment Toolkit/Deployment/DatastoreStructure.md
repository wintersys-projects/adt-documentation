Buckets that persist across multiple deployments
------------------------------------------------

>     1. s3://<website-url>-assets-<asset-type>
>     2. s3://<website-url>-assets-<asset-type>-backup-$$
>     3. s3://authip-adt-allowed-<build-machine-ip>
>     4. s3://<website-url>-multi-region
>     5. s3://<website-url>-ssl
>     6. s3://<website-url>-<period>
>     7. s3://<website-url>-db-<period>

buckets that are unique to each deployment
-----------------------------------------
>     1. s3://<website-url>-config-<unique-token>
