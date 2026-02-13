# AWS CLI v2 -- S3 (Simple Storage Service) Command Reference Index

> Based on AWS CLI v2.33.19 documentation. Sources: https://docs.aws.amazon.com/cli/latest/reference/s3/ and https://docs.aws.amazon.com/cli/latest/reference/s3api/

---

## Table of Contents

1. [High-Level Commands (`aws s3`)](#1-high-level-commands-aws-s3)
2. [Bucket Management (`aws s3api`)](#2-bucket-management-aws-s3api)
3. [Bucket Configuration](#3-bucket-configuration)
4. [Object Operations](#4-object-operations)
5. [Multipart Uploads](#5-multipart-uploads)
6. [Global Options Reference](#6-global-options-reference)

---


---

## All S3 Subcommands (Quick Reference)

### High-Level Commands (`aws s3`)

| Command | Description |
|---------|-------------|
| `cp` | Copy files/objects to and from S3 |
| `ls` | List S3 buckets or objects |
| `mb` | Make (create) a bucket |
| `mv` | Move files/objects to and from S3 |
| `presign` | Generate a presigned URL for an S3 object |
| `rb` | Remove (delete) a bucket |
| `rm` | Delete S3 objects |
| `sync` | Sync directories and S3 prefixes |
| `website` | Configure S3 website hosting |

### Low-Level Commands (`aws s3api`)

| Command | Category | Description |
|---------|----------|-------------|
| `abort-multipart-upload` | Multipart | Abort a multipart upload |
| `complete-multipart-upload` | Multipart | Complete a multipart upload |
| `copy-object` | Object | Copy an object |
| `create-bucket` | Bucket | Create a bucket |
| `create-multipart-upload` | Multipart | Initiate a multipart upload |
| `delete-bucket` | Bucket | Delete a bucket |
| `delete-bucket-cors` | Config | Remove CORS configuration |
| `delete-bucket-encryption` | Config | Remove default encryption |
| `delete-bucket-lifecycle` | Config | Remove lifecycle configuration |
| `delete-bucket-policy` | Config | Remove bucket policy |
| `delete-bucket-replication` | Config | Remove replication configuration |
| `delete-bucket-tagging` | Config | Remove bucket tags |
| `delete-bucket-website` | Config | Remove website configuration |
| `delete-object` | Object | Delete an object |
| `delete-objects` | Object | Delete multiple objects |
| `delete-object-tagging` | Object | Remove object tags |
| `delete-public-access-block` | Config | Remove public access block |
| `get-bucket-acl` | Config | Get bucket ACL |
| `get-bucket-cors` | Config | Get CORS configuration |
| `get-bucket-encryption` | Config | Get default encryption |
| `get-bucket-lifecycle-configuration` | Config | Get lifecycle rules |
| `get-bucket-location` | Bucket | Get bucket region |
| `get-bucket-logging` | Config | Get logging configuration |
| `get-bucket-notification-configuration` | Config | Get event notifications |
| `get-bucket-policy` | Config | Get bucket policy |
| `get-bucket-policy-status` | Config | Get policy public status |
| `get-bucket-replication` | Config | Get replication configuration |
| `get-bucket-tagging` | Config | Get bucket tags |
| `get-bucket-versioning` | Config | Get versioning state |
| `get-bucket-website` | Config | Get website configuration |
| `get-object` | Object | Download an object |
| `get-object-acl` | Object | Get object ACL |
| `get-object-attributes` | Object | Get object attributes |
| `get-object-tagging` | Object | Get object tags |
| `get-public-access-block` | Config | Get public access block |
| `head-bucket` | Bucket | Check bucket existence |
| `head-object` | Object | Get object metadata |
| `list-buckets` | Bucket | List all buckets |
| `list-multipart-uploads` | Multipart | List in-progress multipart uploads |
| `list-objects-v2` | Object | List objects in a bucket |
| `list-object-versions` | Object | List object versions |
| `list-parts` | Multipart | List parts of a multipart upload |
| `put-bucket-acl` | Config | Set bucket ACL |
| `put-bucket-cors` | Config | Set CORS configuration |
| `put-bucket-encryption` | Config | Set default encryption |
| `put-bucket-lifecycle-configuration` | Config | Set lifecycle rules |
| `put-bucket-logging` | Config | Set logging configuration |
| `put-bucket-notification-configuration` | Config | Set event notifications |
| `put-bucket-policy` | Config | Set bucket policy |
| `put-bucket-replication` | Config | Set replication configuration |
| `put-bucket-tagging` | Config | Set bucket tags |
| `put-bucket-versioning` | Config | Set versioning state |
| `put-bucket-website` | Config | Set website configuration |
| `put-object` | Object | Upload an object |
| `put-object-acl` | Object | Set object ACL |
| `put-object-tagging` | Object | Set object tags |
| `put-public-access-block` | Config | Set public access block |
| `restore-object` | Object | Restore archived object |
| `upload-part` | Multipart | Upload a part |
| `upload-part-copy` | Multipart | Copy a part from another object |

---


---

## 6. Global Options Reference

These options are available on ALL `aws s3` and `aws s3api` commands.

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `--debug` | boolean | false | Enable debug logging to stderr |
| `--endpoint-url` | string | -- | Override the default service endpoint URL |
| `--no-verify-ssl` | boolean | false | Disable SSL certificate verification |
| `--no-paginate` | boolean | false | Disable automatic pagination |
| `--output` | string | `json` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | -- | JMESPath query to filter output |
| `--profile` | string | `default` | Named AWS credential profile |
| `--region` | string | from config | AWS region to send requests to |
| `--version` | string | -- | Display the CLI version |
| `--color` | string | `auto` | Toggle color output: `on`, `off`, `auto` |
| `--no-sign-request` | boolean | false | Do not sign requests (for anonymous access) |
| `--ca-bundle` | string | -- | Path to custom CA certificate bundle for SSL |
| `--cli-read-timeout` | integer | 60 | Socket read timeout in seconds |
| `--cli-connect-timeout` | integer | 60 | Socket connect timeout in seconds |
| `--cli-binary-format` | string | `base64` | Format for binary blob input: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from a JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from a YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton: `input`, `yaml-input`, `output` |

---


---

## Common Patterns

### Storage Class Values

| Class | Description |
|-------|-------------|
| `STANDARD` | Default, high availability |
| `STANDARD_IA` | Infrequent access, lower cost per GB |
| `ONEZONE_IA` | Single AZ, lower cost than STANDARD_IA |
| `INTELLIGENT_TIERING` | Auto-tiering based on access patterns |
| `GLACIER` | Archive, minutes to hours retrieval |
| `GLACIER_IR` | Archive with instant retrieval |
| `DEEP_ARCHIVE` | Lowest cost, 12-48 hour retrieval |
| `REDUCED_REDUNDANCY` | Legacy, not recommended |
| `EXPRESS_ONEZONE` | S3 Express One Zone (directory buckets) |

### ACL Values

| Value | Description |
|-------|-------------|
| `private` | Owner gets FULL_CONTROL. No one else has access |
| `public-read` | Owner FULL_CONTROL. AllUsers get READ |
| `public-read-write` | Owner FULL_CONTROL. AllUsers get READ and WRITE |
| `authenticated-read` | Owner FULL_CONTROL. AuthenticatedUsers get READ |
| `aws-exec-read` | Owner FULL_CONTROL. EC2 gets READ |
| `bucket-owner-read` | Object owner FULL_CONTROL. Bucket owner gets READ |
| `bucket-owner-full-control` | Both object and bucket owner get FULL_CONTROL |

### S3 Event Types (for notifications)

| Event | Description |
|-------|-------------|
| `s3:ObjectCreated:*` | All object creation events |
| `s3:ObjectCreated:Put` | PUT object |
| `s3:ObjectCreated:Post` | POST object |
| `s3:ObjectCreated:Copy` | COPY object |
| `s3:ObjectCreated:CompleteMultipartUpload` | Complete multipart |
| `s3:ObjectRemoved:*` | All deletion events |
| `s3:ObjectRemoved:Delete` | DELETE object |
| `s3:ObjectRemoved:DeleteMarkerCreated` | Delete marker created |
| `s3:ObjectRestore:Post` | Restore initiated |
| `s3:ObjectRestore:Completed` | Restore completed |
| `s3:LifecycleExpiration:*` | Lifecycle expiration events |
| `s3:Replication:*` | Replication events |

### Filter Pattern Syntax (`--include` / `--exclude` for `aws s3` commands)

| Pattern | Description |
|---------|-------------|
| `*` | Matches everything |
| `?` | Matches any single character |
| `[sequence]` | Matches any character in sequence |
| `[!sequence]` | Matches any character not in sequence |

Filters are evaluated in order. Later rules override earlier ones.

```bash
# Upload only .jpg files
aws s3 cp ./dir s3://bucket/ --recursive --exclude "*" --include "*.jpg"

# Exclude logs directory
aws s3 sync ./dir s3://bucket/ --exclude "logs/*"
```
