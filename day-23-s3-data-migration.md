# Day 23 – S3 Data Migration

## What I did
- Created a new private S3 bucket `nautilus-sync-21643`
- Migrated all data from `nautilus-s3-1464` using AWS CLI
- Verified that both buckets contain the same data

## What I learned
- AWS CLI can be used to manage and migrate S3 data
- `aws s3 sync` ensures complete and consistent data transfer
- Data verification is important after migration
- S3 sync allows reliable bucket-to-bucket data migration.

# Command Notes

1. `aws s3 mb s3://nautilus-sync-21643 --region us-east-1`  
  → Creates a new private S3 bucket in the specified region.
    - `mb`  make bucket
      → Stands for *make bucket* and is used to create a new S3 bucket.
  

2. `aws s3 sync s3://nautilus-s3-1464 s3://nautilus-sync-21643`  
  → Copies all objects from the source bucket to the destination bucket while keeping data consistent.
    - `sync`  data synchronization
      → Copies and updates files between two locations so that both contain the same data.


3. `aws s3 ls s3://nautilus-s3-1464 --recursive`  
  → Lists all objects in the source bucket to verify its contents.

4. `aws s3 ls s3://nautilus-sync-21643 --recursive`  
  → Lists all objects in the destination bucket to confirm successful data migration.
    - `ls`  list
      → Lists buckets or objects stored in an S3 bucket.
    - `--recursive`  
      → Includes all files and folders inside the bucket, not just the top level.
