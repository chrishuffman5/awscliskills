# AWS CLI v2 -- Application Discovery Service Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/discovery/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `describe-agents` | Agent | List/describe discovery agents |
| `start-data-collection-by-agent-ids` | Agent | Start agent data collection |
| `stop-data-collection-by-agent-ids` | Agent | Stop agent data collection |
| `batch-delete-agents` | Agent | Delete agents in batch |
| `describe-configurations` | Configuration | Get configuration details by ID |
| `list-configurations` | Configuration | List configurations by type |
| `list-server-neighbors` | Configuration | List server network dependencies |
| `get-discovery-summary` | Configuration | Get discovery summary statistics |
| `start-batch-delete-configuration-task` | Configuration | Start batch configuration deletion |
| `describe-batch-delete-configuration-task` | Configuration | Describe batch delete task status |
| `create-application` | Application | Create an application grouping |
| `update-application` | Application | Update application details |
| `delete-applications` | Application | Delete applications |
| `associate-configuration-items-to-application` | Application | Associate servers to application |
| `disassociate-configuration-items-from-application` | Application | Remove servers from application |
| `start-export-task` | Export/Import | Start a data export |
| `describe-export-tasks` | Export/Import | Describe export task status |
| `start-continuous-export` | Export/Import | Start continuous export to S3 |
| `stop-continuous-export` | Export/Import | Stop continuous export |
| `describe-continuous-exports` | Export/Import | Describe continuous exports |
| `start-import-task` | Export/Import | Import data from CSV |
| `describe-import-tasks` | Export/Import | Describe import task status |
| `batch-delete-import-data` | Export/Import | Delete imported data |
| `create-tags` | Tags | Add tags to resources |
| `delete-tags` | Tags | Remove tags from resources |
| `describe-tags` | Tags | List tags for resources |

---

## Global Options

These options are available on ALL `aws discovery` commands.

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

### Configuration Types
| Type | Description |
|------|-------------|
| `SERVER` | Discovered servers |
| `PROCESS` | Discovered processes |
| `CONNECTION` | Network connections |
| `APPLICATION` | Application groupings |

### Agent Health Values
| Status | Description |
|--------|-------------|
| `HEALTHY` | Agent is functioning normally |
| `UNHEALTHY` | Agent has issues |
| `RUNNING` | Agent is actively running |
| `UNKNOWN` | Agent status unknown |
| `BLACKLISTED` | Agent is blacklisted |
| `SHUTDOWN` | Agent has been shut down |

### Export Status Values
| Status | Description |
|--------|-------------|
| `IN_PROGRESS` | Export is running |
| `SUCCEEDED` | Export completed successfully |
| `FAILED` | Export failed |

### Import Status Values
| Status | Description |
|--------|-------------|
| `IMPORT_IN_PROGRESS` | Import is running |
| `IMPORT_COMPLETE` | Import completed successfully |
| `IMPORT_COMPLETE_WITH_ERRORS` | Import completed with some errors |
| `IMPORT_FAILED` | Import failed |
| `DELETE_IN_PROGRESS` | Import data deletion in progress |
| `DELETE_COMPLETE` | Import data deleted |

### Filter Conditions
| Condition | Description |
|-----------|-------------|
| `EQUALS` | Exact match |
| `NOT_EQUALS` | Does not match |
| `CONTAINS` | Contains substring |
| `NOT_CONTAINS` | Does not contain substring |
