# AWS CLI v2 — S3 Control

## Overview

Complete reference for all `aws s3control` subcommands in AWS CLI v2. Covers access point management, Object Lambda access points, S3 Access Grants, Multi-Region Access Points, S3 Batch Operations, Storage Lens configurations, Outposts bucket management, and account-level public access block settings.

## Quick Reference — Common Workflows

### Block all public access at the account level
```bash
aws s3control put-public-access-block \
  --account-id 123456789012 \
  --public-access-block-configuration \
    BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=true,RestrictPublicBuckets=true
```

### Create an access point
```bash
aws s3control create-access-point \
  --account-id 123456789012 \
  --name finance-ap \
  --bucket my-bucket
```

### Create a VPC-restricted access point
```bash
aws s3control create-access-point \
  --account-id 123456789012 \
  --name vpc-ap \
  --bucket my-bucket \
  --vpc-configuration VpcId=vpc-1a2b3c4d
```

### Create a Multi-Region Access Point
```bash
aws s3control create-multi-region-access-point \
  --account-id 123456789012 \
  --details '{
    "Name": "my-mrap",
    "Regions": [
      {"Bucket": "bucket-us-east-1"},
      {"Bucket": "bucket-eu-west-1"}
    ]
  }' \
  --region us-west-2
```

### Create and run an S3 Batch Operations job
```bash
aws s3control create-job \
  --account-id 123456789012 \
  --operation '{"S3PutObjectTagging":{"TagSet":[{"Key":"env","Value":"prod"}]}}' \
  --manifest '{"Spec":{"Format":"S3BatchOperations_CSV_20180820","Fields":["Bucket","Key"]},"Location":{"ObjectArn":"arn:aws:s3:::manifest-bucket/manifest.csv","ETag":"abc123"}}' \
  --report '{"Bucket":"arn:aws:s3:::report-bucket","Prefix":"reports/","Format":"Report_CSV_20180820","Enabled":true,"ReportScope":"AllTasks"}' \
  --priority 10 \
  --role-arn arn:aws:iam::123456789012:role/BatchRole \
  --confirmation-required
```

### Set up S3 Access Grants
```bash
# Create an Access Grants instance
aws s3control create-access-grants-instance \
  --account-id 123456789012

# Register a location
aws s3control create-access-grants-location \
  --account-id 123456789012 \
  --location-scope s3://my-bucket/data/ \
  --iam-role-arn arn:aws:iam::123456789012:role/AccessGrantsRole

# Create an access grant
aws s3control create-access-grant \
  --account-id 123456789012 \
  --access-grants-location-id default \
  --grantee GranteeType=IAM,GranteeIdentifier=arn:aws:iam::123456789012:role/DataAnalyst \
  --permission READ
```

### Create a Storage Lens configuration
```bash
aws s3control put-storage-lens-configuration \
  --account-id 123456789012 \
  --config-id my-dashboard \
  --storage-lens-configuration '{
    "Id": "my-dashboard",
    "AccountLevel": {
      "BucketLevel": {}
    },
    "IsEnabled": true
  }'
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Access Points | [`access-points.md`](access-points.md) | create-access-point, delete-access-point, get-access-point, list-access-points, list-access-points-for-directory-buckets, put-access-point-policy, get-access-point-policy, delete-access-point-policy, get-access-point-policy-status, put-access-point-scope, get-access-point-scope, delete-access-point-scope |
| Object Lambda | [`object-lambda.md`](object-lambda.md) | create-access-point-for-object-lambda, delete-access-point-for-object-lambda, get-access-point-for-object-lambda, list-access-points-for-object-lambda, put-access-point-configuration-for-object-lambda, get-access-point-configuration-for-object-lambda, put-access-point-policy-for-object-lambda, get-access-point-policy-for-object-lambda, delete-access-point-policy-for-object-lambda, get-access-point-policy-status-for-object-lambda |
| Access Grants | [`access-grants.md`](access-grants.md) | create-access-grants-instance, delete-access-grants-instance, get-access-grants-instance, list-access-grants-instances, create-access-grants-location, delete-access-grants-location, get-access-grants-location, list-access-grants-locations, update-access-grants-location, create-access-grant, delete-access-grant, get-access-grant, list-access-grants, list-caller-access-grants, get-data-access, associate-access-grants-identity-center, dissociate-access-grants-identity-center, get-access-grants-instance-for-prefix, get-access-grants-instance-resource-policy, put-access-grants-instance-resource-policy, delete-access-grants-instance-resource-policy |
| Multi-Region Access Points | [`multi-region-access-points.md`](multi-region-access-points.md) | create-multi-region-access-point, delete-multi-region-access-point, get-multi-region-access-point, list-multi-region-access-points, get-multi-region-access-point-policy, put-multi-region-access-point-policy, get-multi-region-access-point-policy-status, get-multi-region-access-point-routes, submit-multi-region-access-point-routes, describe-multi-region-access-point-operation |
| Batch Operations | [`batch-operations.md`](batch-operations.md) | create-job, describe-job, list-jobs, update-job-priority, update-job-status, get-job-tagging, put-job-tagging, delete-job-tagging |
| Storage Lens | [`storage-lens.md`](storage-lens.md) | put-storage-lens-configuration, get-storage-lens-configuration, delete-storage-lens-configuration, list-storage-lens-configurations, put-storage-lens-configuration-tagging, get-storage-lens-configuration-tagging, delete-storage-lens-configuration-tagging, create-storage-lens-group, get-storage-lens-group, list-storage-lens-groups, update-storage-lens-group, delete-storage-lens-group |
| Outposts Buckets | [`outposts-buckets.md`](outposts-buckets.md) | create-bucket, delete-bucket, get-bucket, list-regional-buckets, get-bucket-policy, put-bucket-policy, delete-bucket-policy, get-bucket-tagging, put-bucket-tagging, delete-bucket-tagging, get-bucket-lifecycle-configuration, put-bucket-lifecycle-configuration, delete-bucket-lifecycle-configuration, get-bucket-replication, put-bucket-replication, delete-bucket-replication, get-bucket-versioning, put-bucket-versioning |
| Public Access & Tags | [`public-access-tags.md`](public-access-tags.md) | put-public-access-block, get-public-access-block, delete-public-access-block, tag-resource, untag-resource, list-tags-for-resource |
