# AWS CLI v2 — Kinesis (Data Streams + Data Analytics) Command Reference Index

> Based on AWS CLI v2 documentation. Sources: https://docs.aws.amazon.com/cli/latest/reference/kinesis/ , https://docs.aws.amazon.com/cli/latest/reference/kinesisanalyticsv2/

---

## Quick Reference — `aws kinesis`

| Command | Category | Description |
|---------|----------|-------------|
| `create-stream` | Stream | Create a new Kinesis data stream |
| `delete-stream` | Stream | Delete a data stream |
| `describe-stream` | Stream | Describe a stream (includes shard list) |
| `describe-stream-summary` | Stream | Get stream summary without shard list |
| `list-streams` | Stream | List all data streams in the account |
| `update-stream-mode` | Stream | Switch between provisioned and on-demand mode |
| `increase-stream-retention-period` | Stream | Extend data retention period (up to 8760 hours) |
| `decrease-stream-retention-period` | Stream | Reduce data retention period (min 24 hours) |
| `update-stream-warm-throughput` | Stream | Update warm throughput for on-demand streams |
| `update-max-record-size` | Stream | Update maximum record size |
| `list-shards` | Shard | List shards in a stream |
| `split-shard` | Shard | Split a shard into two shards |
| `merge-shards` | Shard | Merge two adjacent shards |
| `update-shard-count` | Shard | Update the number of shards |
| `get-shard-iterator` | Record | Get a shard iterator for reading records |
| `get-records` | Record | Read data records from a shard |
| `put-record` | Record | Write a single data record to a stream |
| `put-records` | Record | Write multiple data records to a stream |
| `register-stream-consumer` | Consumer | Register an enhanced fan-out consumer |
| `deregister-stream-consumer` | Consumer | Deregister a stream consumer |
| `describe-stream-consumer` | Consumer | Describe a stream consumer |
| `list-stream-consumers` | Consumer | List consumers for a stream |
| `enable-enhanced-monitoring` | Monitoring | Enable shard-level metrics |
| `disable-enhanced-monitoring` | Monitoring | Disable shard-level metrics |
| `start-stream-encryption` | Encryption | Enable server-side encryption |
| `stop-stream-encryption` | Encryption | Disable server-side encryption |
| `add-tags-to-stream` | Tags | Add tags to a stream |
| `remove-tags-from-stream` | Tags | Remove tags from a stream |
| `list-tags-for-stream` | Tags | List tags for a stream |
| `tag-resource` | Tags | Add tags to a resource (ARN-based) |
| `untag-resource` | Tags | Remove tags from a resource (ARN-based) |
| `list-tags-for-resource` | Tags | List tags for a resource (ARN-based) |
| `put-resource-policy` | Policy | Attach a resource policy |
| `get-resource-policy` | Policy | Get a resource policy |
| `delete-resource-policy` | Policy | Delete a resource policy |
| `describe-limits` | Account | View stream count and shard limits |
| `describe-account-settings` | Account | View account-level settings |
| `update-account-settings` | Account | Update account-level settings |
| `wait stream-exists` | Wait | Wait until a stream exists |
| `wait stream-not-exists` | Wait | Wait until a stream no longer exists |

---

## Quick Reference — `aws kinesisanalyticsv2`

| Command | Category | Description |
|---------|----------|-------------|
| `create-application` | Application | Create a Flink/SQL analytics application |
| `delete-application` | Application | Delete an analytics application |
| `describe-application` | Application | Describe an analytics application |
| `list-applications` | Application | List analytics applications |
| `update-application` | Application | Update application configuration |
| `start-application` | Application | Start a stopped application |
| `stop-application` | Application | Stop a running application |
| `rollback-application` | Application | Rollback to a previous version |
| `describe-application-version` | Application | Describe a specific application version |
| `list-application-versions` | Application | List all application versions |
| `describe-application-operation` | Application | Describe an application operation |
| `list-application-operations` | Application | List application operations |
| `add-application-input` | I/O | Add a streaming input source |
| `add-application-output` | I/O | Add an output destination |
| `delete-application-output` | I/O | Remove an output configuration |
| `add-application-input-processing-configuration` | I/O | Add Lambda input preprocessing |
| `delete-application-input-processing-configuration` | I/O | Remove input preprocessing |
| `discover-input-schema` | I/O | Auto-discover input schema |
| `add-application-reference-data-source` | I/O | Add S3 reference data source |
| `delete-application-reference-data-source` | I/O | Remove reference data source |
| `add-application-vpc-configuration` | I/O | Add VPC configuration |
| `delete-application-vpc-configuration` | I/O | Remove VPC configuration |
| `add-application-cloud-watch-logging-option` | Config | Add CloudWatch logging |
| `delete-application-cloud-watch-logging-option` | Config | Remove CloudWatch logging |
| `create-application-snapshot` | Snapshot | Create an application snapshot |
| `delete-application-snapshot` | Snapshot | Delete an application snapshot |
| `describe-application-snapshot` | Snapshot | Describe a snapshot |
| `list-application-snapshots` | Snapshot | List application snapshots |
| `create-application-presigned-url` | Config | Generate a presigned URL |
| `update-application-maintenance-configuration` | Config | Configure maintenance window |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws kinesis` and `aws kinesisanalyticsv2` commands.

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

### Stream Status Values
| Status | Description |
|--------|-------------|
| `CREATING` | Stream is being created |
| `DELETING` | Stream is being deleted |
| `ACTIVE` | Stream is ready for read/write operations |
| `UPDATING` | Stream is being updated (shard count, encryption, etc.) |

### Stream Modes
| Mode | Description |
|------|-------------|
| `PROVISIONED` | Fixed shard count, manual scaling |
| `ON_DEMAND` | Auto-scaling, pay per throughput |

### Shard Iterator Types
| Type | Description |
|------|-------------|
| `AT_SEQUENCE_NUMBER` | Start reading at the specified sequence number |
| `AFTER_SEQUENCE_NUMBER` | Start reading after the specified sequence number |
| `AT_TIMESTAMP` | Start reading at the specified timestamp |
| `TRIM_HORIZON` | Start reading at the oldest record in the shard |
| `LATEST` | Start reading just after the most recent record |

### Shard-Level Metrics
| Metric | Description |
|--------|-------------|
| `IncomingBytes` | Bytes ingested per shard |
| `IncomingRecords` | Records ingested per shard |
| `OutgoingBytes` | Bytes read per shard |
| `OutgoingRecords` | Records read per shard |
| `WriteProvisionedThroughputExceeded` | Throttled write requests |
| `ReadProvisionedThroughputExceeded` | Throttled read requests |
| `IteratorAgeMilliseconds` | Age of the last record read |
| `ALL` | Enable all shard-level metrics |

### Consumer Status Values
| Status | Description |
|--------|-------------|
| `CREATING` | Consumer is being registered |
| `DELETING` | Consumer is being deregistered |
| `ACTIVE` | Consumer is ready for use |

### Analytics Application Status Values
| Status | Description |
|--------|-------------|
| `DELETING` | Application is being deleted |
| `STARTING` | Application is starting |
| `STOPPING` | Application is stopping |
| `READY` | Application is stopped and ready to start |
| `RUNNING` | Application is running |
| `UPDATING` | Application is being updated |
| `AUTOSCALING` | Application is auto-scaling |
| `FORCE_STOPPING` | Application is being force-stopped |
| `ROLLING_BACK` | Application is rolling back |
| `MAINTENANCE` | Application is in maintenance |
| `ROLLED_BACK` | Application has been rolled back |
