# Directions

To start up the different containers individually.

spark 3.3 with jupyter notebook

```
docker-compose up notebook
```

minio (s3-compatible storage layer)

```
docker-compose up minio
```

nessie (transactional catalog for Apache Iceberg)

```
docker-compose up nessie
```

Dremio (data lakehouse platform (query engine, access layer, more))

```
docker-compose up dremio
```

There are three folders in this repo mapped specifically to the spark/notebook container which are:

- `datasets` use this for any sample datasets
- `notebooks` for storing notebooks
- `warehouse` to be used as a warehouse for written data

[Find Guides and Tutorials Here](https://github.com/developer-advocacy-dremio/quick-guides-from-dremio)

[Data Engineering: Create a Apache Iceberg based Data Lakehouse on your Laptop](https://dev.to/alexmercedcoder/data-engineering-create-a-apache-iceberg-based-data-lakehouse-on-your-laptop-41a8)

{
 "Version": "2012-10-17",
 "Statement": [
  {
   "Effect": "Allow",
   "Action": [
    "s3:ListBucket"
   ],
   "Resource": [
    "arn:aws:s3:::warehouse"
   ]
  },
  {
   "Effect": "Allow",
   "Action": [
    "s3:AbortMultipartUpload",
    "s3:DeleteObject",
    "s3:GetObject",
    "s3:ListMultipartUploadParts",
    "s3:PutObject"
   ],
   "Resource": [
    "arn:aws:s3:::warehouse/*"
   ]
  }
 ]
}

https://min.io/docs/minio/linux/administration/identity-access-management/policy-based-access-control.html#supported-s3-policy-actions
https://blog.min.io/migrating-hdfs-to-object-storage/
https://docs.starburst.io/latest/connector/hive-s3.html
https://github.com/starburstdata/dbt-trino/blob/master/docker-compose-starburst.yml
chmod 777 /tmp/hive