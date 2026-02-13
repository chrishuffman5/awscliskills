# AWS CLI v2 -- Control Tower (controltower) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/controltower/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-landing-zone` | Landing Zone | Create a landing zone |
| `get-landing-zone` | Landing Zone | Get landing zone details |
| `list-landing-zones` | Landing Zone | List all landing zones |
| `update-landing-zone` | Landing Zone | Update a landing zone |
| `delete-landing-zone` | Landing Zone | Delete a landing zone |
| `reset-landing-zone` | Landing Zone | Reset a landing zone |
| `get-landing-zone-operation` | Landing Zone | Get landing zone operation details |
| `list-landing-zone-operations` | Landing Zone | List landing zone operations |
| `enable-control` | Control | Enable a control on an OU |
| `disable-control` | Control | Disable a control on an OU |
| `get-enabled-control` | Control | Get enabled control details |
| `list-enabled-controls` | Control | List enabled controls |
| `reset-enabled-control` | Control | Reset an enabled control |
| `get-control-operation` | Control | Get control operation details |
| `list-control-operations` | Control | List control operations |
| `enable-baseline` | Baseline | Enable a baseline on an OU |
| `disable-baseline` | Baseline | Disable a baseline |
| `get-baseline` | Baseline | Get baseline details |
| `get-enabled-baseline` | Baseline | Get enabled baseline details |
| `list-baselines` | Baseline | List available baselines |
| `list-enabled-baselines` | Baseline | List enabled baselines |
| `update-enabled-baseline` | Baseline | Update an enabled baseline |
| `reset-enabled-baseline` | Baseline | Reset an enabled baseline |
| `get-baseline-operation` | Baseline | Get baseline operation details |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws controltower` commands.

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

### Landing Zone Statuses
| Status | Description |
|--------|-------------|
| `ACTIVE` | Landing zone is deployed and operational |
| `PROCESSING` | Landing zone operation is in progress |
| `FAILED` | Landing zone deployment failed |

### Landing Zone Drift Statuses
| Status | Description |
|--------|-------------|
| `DRIFTED` | Landing zone has drifted from desired configuration |
| `IN_SYNC` | Landing zone matches desired configuration |

### Control Operation Types
| Type | Description |
|------|-------------|
| `ENABLE_CONTROL` | Enabling a control on an OU |
| `DISABLE_CONTROL` | Disabling a control on an OU |
| `UPDATE_ENABLED_CONTROL` | Updating an enabled control |
| `RESET_ENABLED_CONTROL` | Resetting an enabled control |

### Operation Statuses
| Status | Description |
|--------|-------------|
| `SUCCEEDED` | Operation completed successfully |
| `FAILED` | Operation failed |
| `IN_PROGRESS` | Operation is currently running |

### Enabled Control Statuses
| Status | Description |
|--------|-------------|
| `SUCCEEDED` | Control is successfully deployed |
| `FAILED` | Control deployment failed |
| `UNDER_CHANGE` | Control is being modified |

### Drift Statuses
| Status | Description |
|--------|-------------|
| `DRIFTED` | Resource has drifted from expected state |
| `IN_SYNC` | Resource matches expected state |
| `NOT_CHECKING` | Drift detection not active |
| `UNKNOWN` | Drift status is unknown |

### Asynchronous Operations
All mutating operations (create, enable, disable, update, reset, delete) are asynchronous. They return an `operationIdentifier` (UUID) that can be tracked using `get-control-operation`, `get-landing-zone-operation`, or `get-baseline-operation`. Operation identifiers are valid for 90 days.
