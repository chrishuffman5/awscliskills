# AWS CLI v2 -- Timestream Command Reference Index

> Based on AWS CLI v2 documentation. Sources:
> - https://docs.aws.amazon.com/cli/latest/reference/timestream-write/
> - https://docs.aws.amazon.com/cli/latest/reference/timestream-query/

---

## Quick Reference — timestream-write

| Command | Category | Description |
|---------|----------|-------------|
| `create-database` | Database | Create a new Timestream database |
| `describe-database` | Database | Describe a database |
| `update-database` | Database | Update database KMS key |
| `delete-database` | Database | Delete a database |
| `list-databases` | Database | List all databases |
| `create-table` | Table | Create a new table in a database |
| `describe-table` | Table | Describe a table |
| `update-table` | Table | Update table retention and schema |
| `delete-table` | Table | Delete a table |
| `list-tables` | Table | List tables in a database |
| `write-records` | Ingestion | Write time-series records to a table |
| `create-batch-load-task` | Ingestion | Create a batch load task from S3 |
| `describe-batch-load-task` | Ingestion | Describe a batch load task |
| `list-batch-load-tasks` | Ingestion | List batch load tasks |
| `resume-batch-load-task` | Ingestion | Resume a paused batch load task |
| `describe-endpoints` | Endpoints | Describe service endpoints |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

## Quick Reference — timestream-query

| Command | Category | Description |
|---------|----------|-------------|
| `query` | Query | Execute a time-series query |
| `cancel-query` | Query | Cancel a running query |
| `prepare-query` | Query | Prepare and validate a query |
| `create-scheduled-query` | Scheduled Query | Create a scheduled query |
| `describe-scheduled-query` | Scheduled Query | Describe a scheduled query |
| `update-scheduled-query` | Scheduled Query | Enable or disable a scheduled query |
| `delete-scheduled-query` | Scheduled Query | Delete a scheduled query |
| `execute-scheduled-query` | Scheduled Query | Manually execute a scheduled query |
| `list-scheduled-queries` | Scheduled Query | List all scheduled queries |
| `describe-endpoints` | Endpoints | Describe query service endpoints |
| `describe-account-settings` | Account | Describe account query settings |
| `update-account-settings` | Account | Update account query settings |
| `tag-resource` | Tags | Add tags to a query resource |
| `untag-resource` | Tags | Remove tags from a query resource |
| `list-tags-for-resource` | Tags | List tags for a query resource |

---

## Global Options

These options are available on ALL `aws timestream-write` and `aws timestream-query` commands.

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

### Database/Table Name Constraints
- **Pattern:** `[a-zA-Z0-9_.-]+`
- Database and table names are case-sensitive

### Measure Value Types
| Type | Description |
|------|-------------|
| `DOUBLE` | 64-bit floating point |
| `BIGINT` | 64-bit integer |
| `VARCHAR` | String (up to 2048 chars) |
| `BOOLEAN` | True/false |
| `TIMESTAMP` | Timestamp value |
| `MULTI` | Multi-measure record (contains multiple measure values) |

### Time Units
| Unit | Description |
|------|-------------|
| `MILLISECONDS` | Milliseconds since epoch |
| `SECONDS` | Seconds since epoch |
| `MICROSECONDS` | Microseconds since epoch |
| `NANOSECONDS` | Nanoseconds since epoch |

### Table Status Values
| Status | Description |
|--------|-------------|
| `ACTIVE` | Table is ready for read/write |
| `DELETING` | Table is being deleted |
| `RESTORING` | Table is being restored |

### Batch Load Task Statuses
| Status | Description |
|--------|-------------|
| `CREATED` | Task has been created |
| `IN_PROGRESS` | Task is actively loading data |
| `FAILED` | Task failed |
| `SUCCEEDED` | Task completed successfully |
| `PROGRESS_STOPPED` | Task was stopped |
| `PENDING_RESUME` | Task is pending resume |

### Scheduled Query States
| State | Description |
|-------|-------------|
| `ENABLED` | Scheduled query is active |
| `DISABLED` | Scheduled query is paused |
