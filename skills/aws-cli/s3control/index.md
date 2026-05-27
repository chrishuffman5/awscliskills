# AWS CLI v2 -- S3 Control Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/s3control/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-access-point` | Access Point | Create an access point for an S3 bucket |
| `delete-access-point` | Access Point | Delete an access point |
| `get-access-point` | Access Point | Get access point metadata |
| `list-access-points` | Access Point | List access points for an account |
| `list-access-points-for-directory-buckets` | Access Point | List access points for directory buckets |
| `put-access-point-policy` | Access Point | Associate a policy with an access point |
| `get-access-point-policy` | Access Point | Get the policy for an access point |
| `delete-access-point-policy` | Access Point | Delete an access point policy |
| `get-access-point-policy-status` | Access Point | Get policy status (public or not) |
| `put-access-point-scope` | Access Point | Set access point scope for directory buckets |
| `get-access-point-scope` | Access Point | Get access point scope |
| `delete-access-point-scope` | Access Point | Delete access point scope |
| `create-access-point-for-object-lambda` | Object Lambda | Create an Object Lambda access point |
| `delete-access-point-for-object-lambda` | Object Lambda | Delete an Object Lambda access point |
| `get-access-point-for-object-lambda` | Object Lambda | Get Object Lambda access point metadata |
| `list-access-points-for-object-lambda` | Object Lambda | List Object Lambda access points |
| `put-access-point-configuration-for-object-lambda` | Object Lambda | Set Object Lambda configuration |
| `get-access-point-configuration-for-object-lambda` | Object Lambda | Get Object Lambda configuration |
| `put-access-point-policy-for-object-lambda` | Object Lambda | Set Object Lambda access point policy |
| `get-access-point-policy-for-object-lambda` | Object Lambda | Get Object Lambda access point policy |
| `delete-access-point-policy-for-object-lambda` | Object Lambda | Delete Object Lambda access point policy |
| `get-access-point-policy-status-for-object-lambda` | Object Lambda | Get Object Lambda policy status |
| `create-access-grants-instance` | Access Grants | Create an S3 Access Grants instance |
| `delete-access-grants-instance` | Access Grants | Delete an Access Grants instance |
| `get-access-grants-instance` | Access Grants | Get Access Grants instance details |
| `list-access-grants-instances` | Access Grants | List Access Grants instances |
| `get-access-grants-instance-for-prefix` | Access Grants | Get Access Grants instance for an S3 prefix |
| `get-access-grants-instance-resource-policy` | Access Grants | Get resource policy for Access Grants instance |
| `put-access-grants-instance-resource-policy` | Access Grants | Set resource policy for Access Grants instance |
| `delete-access-grants-instance-resource-policy` | Access Grants | Delete resource policy |
| `associate-access-grants-identity-center` | Access Grants | Associate with IAM Identity Center |
| `dissociate-access-grants-identity-center` | Access Grants | Dissociate from IAM Identity Center |
| `create-access-grants-location` | Access Grants | Register a location for access grants |
| `delete-access-grants-location` | Access Grants | Delete a registered location |
| `get-access-grants-location` | Access Grants | Get location details |
| `list-access-grants-locations` | Access Grants | List registered locations |
| `update-access-grants-location` | Access Grants | Update a registered location |
| `create-access-grant` | Access Grants | Create an access grant |
| `delete-access-grant` | Access Grants | Delete an access grant |
| `get-access-grant` | Access Grants | Get access grant details |
| `list-access-grants` | Access Grants | List access grants |
| `list-caller-access-grants` | Access Grants | List caller's access grants |
| `get-data-access` | Access Grants | Get temporary credentials via access grant |
| `create-multi-region-access-point` | Multi-Region AP | Create a Multi-Region Access Point |
| `delete-multi-region-access-point` | Multi-Region AP | Delete a Multi-Region Access Point |
| `get-multi-region-access-point` | Multi-Region AP | Get Multi-Region Access Point details |
| `list-multi-region-access-points` | Multi-Region AP | List Multi-Region Access Points |
| `get-multi-region-access-point-policy` | Multi-Region AP | Get MRAP policy |
| `put-multi-region-access-point-policy` | Multi-Region AP | Set MRAP policy |
| `get-multi-region-access-point-policy-status` | Multi-Region AP | Get MRAP policy status |
| `get-multi-region-access-point-routes` | Multi-Region AP | Get MRAP routing configuration |
| `submit-multi-region-access-point-routes` | Multi-Region AP | Submit MRAP route configuration |
| `describe-multi-region-access-point-operation` | Multi-Region AP | Describe async MRAP operation status |
| `create-job` | Batch Operations | Create an S3 Batch Operations job |
| `describe-job` | Batch Operations | Describe a Batch Operations job |
| `list-jobs` | Batch Operations | List Batch Operations jobs |
| `update-job-priority` | Batch Operations | Update job priority |
| `update-job-status` | Batch Operations | Update job status (cancel, confirm, etc.) |
| `get-job-tagging` | Batch Operations | Get tags for a job |
| `put-job-tagging` | Batch Operations | Set tags on a job |
| `delete-job-tagging` | Batch Operations | Remove tags from a job |
| `put-storage-lens-configuration` | Storage Lens | Create or update Storage Lens configuration |
| `get-storage-lens-configuration` | Storage Lens | Get Storage Lens configuration |
| `delete-storage-lens-configuration` | Storage Lens | Delete Storage Lens configuration |
| `list-storage-lens-configurations` | Storage Lens | List Storage Lens configurations |
| `put-storage-lens-configuration-tagging` | Storage Lens | Set tags on Storage Lens configuration |
| `get-storage-lens-configuration-tagging` | Storage Lens | Get Storage Lens configuration tags |
| `delete-storage-lens-configuration-tagging` | Storage Lens | Remove Storage Lens configuration tags |
| `create-storage-lens-group` | Storage Lens | Create a Storage Lens group |
| `get-storage-lens-group` | Storage Lens | Get a Storage Lens group |
| `list-storage-lens-groups` | Storage Lens | List Storage Lens groups |
| `update-storage-lens-group` | Storage Lens | Update a Storage Lens group |
| `delete-storage-lens-group` | Storage Lens | Delete a Storage Lens group |
| `create-bucket` | Outposts Bucket | Create an S3 on Outposts bucket |
| `delete-bucket` | Outposts Bucket | Delete an Outposts bucket |
| `get-bucket` | Outposts Bucket | Get Outposts bucket metadata |
| `list-regional-buckets` | Outposts Bucket | List regional and Outposts buckets |
| `get-bucket-policy` | Outposts Bucket | Get Outposts bucket policy |
| `put-bucket-policy` | Outposts Bucket | Set Outposts bucket policy |
| `delete-bucket-policy` | Outposts Bucket | Delete Outposts bucket policy |
| `get-bucket-tagging` | Outposts Bucket | Get Outposts bucket tags |
| `put-bucket-tagging` | Outposts Bucket | Set Outposts bucket tags |
| `delete-bucket-tagging` | Outposts Bucket | Delete Outposts bucket tags |
| `get-bucket-lifecycle-configuration` | Outposts Bucket | Get Outposts bucket lifecycle rules |
| `put-bucket-lifecycle-configuration` | Outposts Bucket | Set Outposts bucket lifecycle rules |
| `delete-bucket-lifecycle-configuration` | Outposts Bucket | Delete lifecycle configuration |
| `get-bucket-replication` | Outposts Bucket | Get Outposts bucket replication config |
| `put-bucket-replication` | Outposts Bucket | Set Outposts bucket replication config |
| `delete-bucket-replication` | Outposts Bucket | Delete Outposts replication config |
| `get-bucket-versioning` | Outposts Bucket | Get Outposts bucket versioning status |
| `put-bucket-versioning` | Outposts Bucket | Set Outposts bucket versioning |
| `put-public-access-block` | Public Access | Set account-level public access block |
| `get-public-access-block` | Public Access | Get account-level public access block |
| `delete-public-access-block` | Public Access | Remove account-level public access block |
| `tag-resource` | Tags | Add tags to an S3 Control resource |
| `untag-resource` | Tags | Remove tags from an S3 Control resource |
| `list-tags-for-resource` | Tags | List tags for an S3 Control resource |

---

## Global Options

These options are available on ALL `aws s3control` commands.

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

## Common Patterns

### Account ID Required

Most `aws s3control` commands require `--account-id` (12-digit AWS account ID). This is different from most other AWS CLI services where the account is implicit.

### Asynchronous Operations

Multi-Region Access Point create/delete operations are asynchronous. They return a `RequestTokenARN` that you use with `describe-multi-region-access-point-operation` to check status.

### S3 on Outposts ARN Format

For S3 on Outposts resources, use the full ARN format:
```
arn:aws:s3-outposts:<region>:<account-id>:outpost/<outpost-id>/bucket/<bucket-name>
arn:aws:s3-outposts:<region>:<account-id>:outpost/<outpost-id>/accesspoint/<name>
```

### Batch Operations Job Statuses

| Status | Description |
|--------|-------------|
| `New` | Job was just created |
| `Preparing` | S3 is processing the manifest |
| `Ready` | Job is ready to run (needs confirmation if required) |
| `Active` | Job is currently running |
| `Pausing` | Job is being paused |
| `Paused` | Job is paused |
| `Completing` | Job is finishing |
| `Complete` | Job finished |
| `Cancelling` | Job is being cancelled |
| `Cancelled` | Job was cancelled |
| `Failing` | Job is failing |
| `Failed` | Job failed |
| `Suspended` | Job is suspended |

### Multi-Region Access Point Statuses

| Status | Description |
|--------|-------------|
| `READY` | MRAP is available for use |
| `CREATING` | MRAP is being created |
| `PARTIALLY_CREATED` | Some regions created |
| `PARTIALLY_DELETED` | Some regions deleted |
| `DELETING` | MRAP is being deleted |
| `INCONSISTENT_ACROSS_REGIONS` | Inconsistent state |
