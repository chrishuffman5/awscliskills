# AWS CLI v2 — Athena Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/athena/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `start-query-execution` | Query | Start a SQL query execution |
| `stop-query-execution` | Query | Stop (cancel) a running query |
| `get-query-execution` | Query | Get details about a query execution |
| `get-query-results` | Query | Get results from a completed query |
| `batch-get-query-execution` | Query | Get details about multiple query executions |
| `list-query-executions` | Query | List query execution IDs |
| `get-query-runtime-statistics` | Query | Get runtime statistics for a query |
| `create-named-query` | Named Query | Create a saved (named) query |
| `delete-named-query` | Named Query | Delete a named query |
| `get-named-query` | Named Query | Get a named query definition |
| `batch-get-named-query` | Named Query | Get multiple named queries |
| `list-named-queries` | Named Query | List named query IDs |
| `create-prepared-statement` | Prepared Statement | Create a prepared statement |
| `delete-prepared-statement` | Prepared Statement | Delete a prepared statement |
| `get-prepared-statement` | Prepared Statement | Get a prepared statement |
| `update-prepared-statement` | Prepared Statement | Update a prepared statement |
| `list-prepared-statements` | Prepared Statement | List prepared statements in a workgroup |
| `create-work-group` | Workgroup | Create a workgroup |
| `delete-work-group` | Workgroup | Delete a workgroup |
| `get-work-group` | Workgroup | Get workgroup details |
| `update-work-group` | Workgroup | Update a workgroup |
| `list-work-groups` | Workgroup | List workgroups |
| `create-data-catalog` | Data Catalog | Register a data catalog |
| `delete-data-catalog` | Data Catalog | Delete a data catalog |
| `get-data-catalog` | Data Catalog | Get data catalog details |
| `update-data-catalog` | Data Catalog | Update a data catalog |
| `list-data-catalogs` | Data Catalog | List data catalogs |
| `get-database` | Data Catalog | Get database details |
| `list-databases` | Data Catalog | List databases in a catalog |
| `get-table-metadata` | Data Catalog | Get table metadata |
| `list-table-metadata` | Data Catalog | List tables in a database |
| `create-notebook` | Notebook | Create a notebook |
| `delete-notebook` | Notebook | Delete a notebook |
| `get-notebook-metadata` | Notebook | Get notebook metadata |
| `update-notebook` | Notebook | Update notebook content |
| `update-notebook-metadata` | Notebook | Update notebook name/metadata |
| `list-notebook-metadata` | Notebook | List notebooks |
| `import-notebook` | Notebook | Import a notebook |
| `export-notebook` | Notebook | Export a notebook |
| `start-session` | Session | Start an interactive session |
| `terminate-session` | Session | Terminate a session |
| `get-session` | Session | Get session details |
| `get-session-status` | Session | Get session status |
| `list-sessions` | Session | List sessions |
| `start-calculation-execution` | Calculation | Start a calculation in a session |
| `stop-calculation-execution` | Calculation | Stop a running calculation |
| `get-calculation-execution` | Calculation | Get calculation details |
| `get-calculation-execution-status` | Calculation | Get calculation status |
| `list-calculation-executions` | Calculation | List calculations in a session |
| `create-capacity-reservation` | Capacity | Create a capacity reservation |
| `cancel-capacity-reservation` | Capacity | Cancel a capacity reservation |
| `get-capacity-reservation` | Capacity | Get reservation details |
| `get-capacity-assignment-configuration` | Capacity | Get assignment configuration |
| `put-capacity-assignment-configuration` | Capacity | Set assignment configuration |
| `list-capacity-reservations` | Capacity | List capacity reservations |
| `list-engine-versions` | Engine | List available engine versions |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags on a resource |

---

## Global Options

These options are available on ALL `aws athena` commands.

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
| `--cli-input-json` | string | -- | Read arguments from a JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from a YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton |

---

## Common Patterns

### Query Execution State Values
| State | Description |
|-------|-------------|
| `QUEUED` | Query is queued |
| `RUNNING` | Query is running |
| `SUCCEEDED` | Query completed successfully |
| `FAILED` | Query failed |
| `CANCELLED` | Query was cancelled |

### Workgroup State Values
| State | Description |
|-------|-------------|
| `ENABLED` | Workgroup is enabled |
| `DISABLED` | Workgroup is disabled |

### Data Catalog Types
| Type | Description |
|------|-------------|
| `LAMBDA` | Federated query connector (Lambda function) |
| `GLUE` | AWS Glue Data Catalog |
| `HIVE` | Apache Hive metastore |

### Session State Values
| State | Description |
|-------|-------------|
| `CREATING` | Session is being created |
| `CREATED` | Session is ready |
| `IDLE` | Session is idle |
| `BUSY` | Session is running a calculation |
| `TERMINATING` | Session is being terminated |
| `TERMINATED` | Session has terminated |
| `DEGRADED` | Session is degraded |
| `FAILED` | Session failed |
