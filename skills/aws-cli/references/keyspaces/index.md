# AWS CLI v2 -- Amazon Keyspaces Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/keyspaces/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-keyspace` | Keyspace | Create a new keyspace |
| `delete-keyspace` | Keyspace | Delete a keyspace |
| `get-keyspace` | Keyspace | Get keyspace details |
| `list-keyspaces` | Keyspace | List all keyspaces |
| `update-keyspace` | Keyspace | Update keyspace configuration |
| `create-table` | Table | Create a new table |
| `delete-table` | Table | Delete a table |
| `get-table` | Table | Get table details |
| `list-tables` | Table | List tables in a keyspace |
| `update-table` | Table | Update table configuration |
| `restore-table` | Table | Restore a table from backup |
| `get-table-auto-scaling-settings` | Table | Get auto-scaling settings |
| `create-type` | Type | Create a custom user-defined type |
| `delete-type` | Type | Delete a custom type |
| `get-type` | Type | Get custom type details |
| `list-types` | Type | List custom types |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws keyspaces` commands.

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
| `--no-sign-request` | boolean | false | Do not sign requests |
| `--ca-bundle` | string | -- | Path to custom CA certificate bundle |
| `--cli-read-timeout` | integer | 60 | Socket read timeout in seconds |
| `--cli-connect-timeout` | integer | 60 | Socket connect timeout in seconds |
| `--cli-binary-format` | string | `base64` | Format for binary blob input |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from JSON string or `file://` |
| `--cli-input-yaml` | string | -- | Read arguments from YAML string or `file://` |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton |

---

## Common Patterns

### Table Statuses
| Status | Description |
|--------|-------------|
| `ACTIVE` | Table is ready for use |
| `CREATING` | Table is being created |
| `UPDATING` | Table is being updated |
| `DELETING` | Table is being deleted |
| `DELETED` | Table has been deleted |
| `RESTORING` | Table is being restored |
| `INACCESSIBLE_ENCRYPTION_CREDENTIALS` | Table encryption key is inaccessible |

### Capacity Modes
| Mode | Description |
|------|-------------|
| `PAY_PER_REQUEST` | On-demand capacity (default) |
| `PROVISIONED` | Provisioned read/write capacity units |

### Cassandra Data Types
Keyspaces supports standard Cassandra types: `ascii`, `bigint`, `blob`, `boolean`, `counter`, `date`, `decimal`, `double`, `float`, `frozen`, `inet`, `int`, `list`, `map`, `set`, `smallint`, `text`, `time`, `timestamp`, `timeuuid`, `tinyint`, `tuple`, `uuid`, `varchar`, `varint`.

### Keyspace Name Constraints
- **Length:** 1-48 characters
- **Pattern:** Start with letter or number, followed by letters, numbers, or underscores
- **Case:** Case-sensitive

### Replication Strategies
| Strategy | Description |
|----------|-------------|
| `SINGLE_REGION` | Data replicated within a single AWS Region (default) |
| `MULTI_REGION` | Data replicated across multiple AWS Regions |
