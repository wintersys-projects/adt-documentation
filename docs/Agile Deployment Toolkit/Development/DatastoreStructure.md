Buckets that persist across multiple deployments
------------------------------------------------
s3://<website-url>-assets-<asset-type>
s3://<website-url>-assets-<asset-type>-backup-$$
s3://authip-adt-allowed-<build-machine-ip>
s3://<website-url>-multi-region
s3://<website-url>-ssl
s3://<website-url>-<period>
s3://<website-url>-db-<period>

buckets that are unique to each deployment
-----------------------------------------
s3://<website-url>-config-<unique-token>
