# AWS CLI v2 — S3 (Simple Storage Service)

## Overview

Complete reference for `aws s3` (high-level) and `aws s3api` (low-level) subcommands in AWS CLI v2. Covers bucket management, object operations, storage classes, lifecycle rules, versioning, access policies, encryption, website hosting, and transfer acceleration.

## Quick Reference — Common Workflows

### Create bucket and upload
```bash
aws s3 mb s3://my-bucket --region us-east-1
aws s3 cp local-file.txt s3://my-bucket/path/
aws s3 sync ./local-dir s3://my-bucket/prefix/ --delete
```

### Download and list objects
```bash
aws s3 ls s3://my-bucket/prefix/ --recursive
aws s3 cp s3://my-bucket/path/file.txt ./local-file.txt
aws s3 sync s3://my-bucket/prefix/ ./local-dir
```

### Generate presigned URL
```bash
aws s3 presign s3://my-bucket/path/file.txt --expires-in 3600
```

### Set bucket policy
```bash
aws s3api put-bucket-policy --bucket my-bucket --policy file://policy.json
```

### Enable versioning
```bash
aws s3api put-bucket-versioning --bucket my-bucket --versioning-configuration Status=Enabled
```

### Configure lifecycle rule
```bash
aws s3api put-bucket-lifecycle-configuration --bucket my-bucket --lifecycle-configuration file://lifecycle.json
```

## Covered Command Groups

| Group | Commands | CLI Service |
|-------|----------|-------------|
| High-Level | cp, mv, rm, sync, ls, mb, rb, presign, website | `aws s3` |
| Buckets | create, delete, head, list, get/put policy, versioning, lifecycle, encryption, logging, cors, website, acl, replication, accelerate, tagging | `aws s3api` |
| Objects | get, put, delete, copy, head, list-objects-v2, restore, select, presign, multipart uploads | `aws s3api` |
| Access Points | create, delete, get, list access points and policies | `aws s3control` |

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| High-Level Commands (`aws s3`) | [`high-level-commands.md`](high-level-commands.md) | cp, mv, rm, sync, ls, mb, rb, presign, website |
| Bucket Management (`aws s3api`) | [`bucket-management.md`](bucket-management.md) | create-bucket, delete-bucket, head-bucket, list-buckets, get-bucket-location |
| Bucket Configuration | [`bucket-configuration.md`](bucket-configuration.md) | put-bucket-policy, get-bucket-policy, delete-bucket-policy, get-bucket-policy-status, put-bucket-versioning, get-bucket-versioning, put-bucket-lifecycle-configuration, get-bucket-lifecycle-configuration, delete-bucket-lifecycle, put-bucket-encryption, get-bucket-encryption, delete-bucket-encryption, put-bucket-logging, get-bucket-logging, put-bucket-cors, get-bucket-cors, delete-bucket-cors, put-bucket-website, get-bucket-website, delete-bucket-website, put-bucket-acl, get-bucket-acl, put-bucket-replication, get-bucket-replication, delete-bucket-replication, put-bucket-tagging, get-bucket-tagging, delete-bucket-tagging, put-bucket-notification-configuration, get-bucket-notification-configuration, put-public-access-block, get-public-access-block, delete-public-access-block, put-bucket-accelerate-configuration, get-bucket-accelerate-configuration |
| Object Operations | [`object-operations.md`](object-operations.md) | put-object, get-object, delete-object, delete-objects, copy-object, head-object, list-objects-v2, list-object-versions, restore-object, get-object-acl, put-object-acl, get-object-tagging, put-object-tagging, delete-object-tagging, get-object-attributes |
| Multipart Uploads | [`multipart-uploads.md`](multipart-uploads.md) | create-multipart-upload, upload-part, upload-part-copy, complete-multipart-upload, abort-multipart-upload, list-multipart-uploads, list-parts |
