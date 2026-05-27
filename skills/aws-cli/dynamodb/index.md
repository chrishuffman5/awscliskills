# AWS CLI v2 -- DynamoDB (NoSQL Database) Complete Command Reference

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/dynamodb/ and https://docs.aws.amazon.com/cli/latest/reference/dynamodbstreams/

---

## All DynamoDB Subcommands (Quick Reference)

| Command | Category | Description |
|---------|----------|-------------|
| `batch-execute-statement` | PartiQL | Execute multiple PartiQL statements in a batch |
| `batch-get-item` | Batch | Retrieve multiple items from one or more tables |
| `batch-write-item` | Batch | Put or delete multiple items across tables |
| `create-backup` | Backup | Create an on-demand backup of a table |
| `create-global-table` | Global Tables | Create a global table from existing tables |
| `create-table` | Table | Create a new DynamoDB table |
| `delete-backup` | Backup | Delete an existing backup |
| `delete-item` | Item | Delete a single item by primary key |
| `delete-resource-policy` | Resource Policy | Delete a resource-based policy from a table or stream |
| `delete-table` | Table | Delete a table and all its items |
| `describe-backup` | Backup | Describe an existing backup |
| `describe-continuous-backups` | PITR | Describe continuous backups and PITR status |
| `describe-contributor-insights` | Insights | Describe contributor insights for a table/index |
| `describe-endpoints` | Endpoints | Describe regional endpoints |
| `describe-export` | Export | Describe an export to S3 |
| `describe-global-table` | Global Tables | Describe a global table |
| `describe-global-table-settings` | Global Tables | Describe global table region settings |
| `describe-import` | Import | Describe an import from S3 |
| `describe-kinesis-streaming-destination` | Kinesis | Describe Kinesis streaming destination |
| `describe-limits` | Limits | Describe provisioned-throughput account limits |
| `describe-table` | Table | Describe table properties |
| `describe-table-replica-auto-scaling` | Table | Describe replica auto-scaling settings |
| `describe-time-to-live` | TTL | Describe TTL settings for a table |
| `disable-kinesis-streaming-destination` | Kinesis | Disable Kinesis streaming for a table |
| `enable-kinesis-streaming-destination` | Kinesis | Enable Kinesis streaming for a table |
| `execute-statement` | PartiQL | Execute a single PartiQL statement |
| `execute-transaction` | PartiQL | Execute a transactional PartiQL operation |
| `export-table-to-point-in-time` | Export | Export table data to S3 |
| `get-item` | Item | Retrieve a single item by primary key |
| `get-resource-policy` | Resource Policy | Get a resource-based policy for a table or stream |
| `import-table` | Import | Import data from S3 into a new table |
| `list-backups` | Backup | List existing backups |
| `list-contributor-insights` | Insights | List contributor insights summaries |
| `list-exports` | Export | List export jobs |
| `list-global-tables` | Global Tables | List global tables |
| `list-imports` | Import | List import jobs |
| `list-tables` | Table | List table names |
| `list-tags-of-resource` | Tags | List tags on a resource |
| `put-item` | Item | Create or replace an item |
| `put-resource-policy` | Resource Policy | Attach a resource-based policy to a table or stream |
| `query` | Query | Query items using key condition expressions |
| `restore-table-from-backup` | Backup | Restore a table from an on-demand backup |
| `restore-table-to-point-in-time` | PITR | Restore a table to a specific point in time |
| `scan` | Scan | Read every item in a table or index |
| `tag-resource` | Tags | Add tags to a resource |
| `transact-get-items` | Transaction | Transactional read of up to 100 items |
| `transact-write-items` | Transaction | Transactional write of up to 100 actions |
| `untag-resource` | Tags | Remove tags from a resource |
| `update-continuous-backups` | PITR | Enable or disable point-in-time recovery |
| `update-contributor-insights` | Insights | Enable or disable contributor insights |
| `update-global-table` | Global Tables | Add or remove replicas from a global table |
| `update-global-table-settings` | Global Tables | Update global table region-specific settings |
| `update-item` | Item | Edit an existing item's attributes |
| `update-kinesis-streaming-destination` | Kinesis | Update Kinesis streaming configuration |
| `update-table` | Table | Modify table settings, GSIs, streams, etc. |
| `update-table-replica-auto-scaling` | Table | Update replica auto-scaling settings |
| `update-time-to-live` | TTL | Enable or disable TTL on a table |
| `wait` | Wait | Wait for a table condition |

### DynamoDB Streams Subcommands (`aws dynamodbstreams`)

| Command | Description |
|---------|-------------|
| `describe-stream` | Describe stream properties and shard list |
| `get-records` | Retrieve stream records from a shard |
| `get-shard-iterator` | Get an iterator for reading stream records |
| `list-streams` | List all DynamoDB streams |

---

---

# Global Options Reference

These options are available on all `aws dynamodb` and `aws dynamodbstreams` commands:

| Option | Type | Description |
|--------|------|-------------|
| `--debug` | boolean | Enable debug logging |
| `--endpoint-url` | string | Override default service URL |
| `--no-verify-ssl` | boolean | Disable SSL certificate verification |
| `--no-paginate` | boolean | Disable automatic pagination |
| `--output` | string | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | JMESPath query to filter response |
| `--profile` | string | Named profile from config/credentials file |
| `--region` | string | AWS region |
| `--version` | boolean | Display CLI version |
| `--color` | string | Color output: `on`, `off`, `auto` |
| `--no-sign-request` | boolean | Do not sign requests (public resources only) |
| `--ca-bundle` | string | CA certificate bundle for SSL |
| `--cli-read-timeout` | integer | Socket read timeout in seconds (default: 60) |
| `--cli-connect-timeout` | integer | Socket connect timeout in seconds (default: 60) |
| `--cli-binary-format` | string | Binary blob format: `base64` (default), `raw-in-base64-out` |
| `--no-cli-pager` | boolean | Disable CLI pager |
| `--cli-auto-prompt` | boolean | Enable auto-prompt for parameters |
| `--no-cli-auto-prompt` | boolean | Disable auto-prompt |
| `--cli-input-json` | string | Read arguments from JSON string |
| `--cli-input-yaml` | string | Read arguments from YAML string |
| `--generate-cli-skeleton` | string | Print JSON/YAML skeleton: `input`, `yaml-input`, or `output` |
