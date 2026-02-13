# AWS CLI v2 — Firehose (Amazon Data Firehose) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/firehose/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-delivery-stream` | Delivery Stream | Create a new delivery stream |
| `delete-delivery-stream` | Delivery Stream | Delete a delivery stream |
| `describe-delivery-stream` | Delivery Stream | Describe a delivery stream |
| `list-delivery-streams` | Delivery Stream | List delivery streams in the account |
| `update-destination` | Delivery Stream | Update delivery stream destination configuration |
| `start-delivery-stream-encryption` | Delivery Stream | Enable server-side encryption |
| `stop-delivery-stream-encryption` | Delivery Stream | Disable server-side encryption |
| `put-record` | Data | Write a single record to a delivery stream |
| `put-record-batch` | Data | Write multiple records to a delivery stream |
| `tag-delivery-stream` | Tags | Add tags to a delivery stream |
| `untag-delivery-stream` | Tags | Remove tags from a delivery stream |
| `list-tags-for-delivery-stream` | Tags | List tags for a delivery stream |

---

## Global Options

These options are available on ALL `aws firehose` commands.

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

### Delivery Stream Status Values
| Status | Description |
|--------|-------------|
| `CREATING` | Stream is being created |
| `CREATING_FAILED` | Stream creation failed |
| `DELETING` | Stream is being deleted |
| `DELETING_FAILED` | Stream deletion failed |
| `ACTIVE` | Stream is ready for data delivery |

### Delivery Stream Types
| Type | Description |
|------|-------------|
| `DirectPut` | Data is sent directly via `put-record` / `put-record-batch` |
| `KinesisStreamAsSource` | Data is sourced from a Kinesis data stream |
| `MSKAsSource` | Data is sourced from an Amazon MSK topic |
| `DatabaseAsSource` | Data is sourced from a database (CDC) |

### Supported Destinations
| Destination | Parameter Suffix |
|-------------|-----------------|
| Amazon S3 (extended) | `extended-s3-destination-*` |
| Amazon Redshift | `redshift-destination-*` |
| Amazon OpenSearch Service | `amazonopensearchservice-destination-*` |
| OpenSearch Serverless | `amazon-open-search-serverless-destination-*` |
| Splunk | `splunk-destination-*` |
| HTTP Endpoint | `http-endpoint-destination-*` |
| Snowflake | `snowflake-destination-*` |
| Apache Iceberg | `iceberg-destination-*` |

### Compression Formats
| Format | Supported Destinations |
|--------|----------------------|
| `UNCOMPRESSED` | All |
| `GZIP` | All |
| `ZIP` | S3 only |
| `Snappy` | S3 only |
| `HADOOP_SNAPPY` | S3 only |

### Encryption Key Types
| Type | Description |
|------|-------------|
| `AWS_OWNED_CMK` | AWS-owned customer master key (no additional cost) |
| `CUSTOMER_MANAGED_CMK` | Customer-managed KMS key (requires `KeyARN`) |

### Buffering Hints Defaults
| Setting | Default | Range |
|---------|---------|-------|
| `SizeInMBs` | 5 | 1-128 (S3), 1-100 (OpenSearch) |
| `IntervalInSeconds` | 300 | 0-900 |
