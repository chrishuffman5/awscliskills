# AWS CLI v2 -- Systems Manager (SSM) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/ssm/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `put-parameter` | Parameter Store | Create or update a parameter |
| `get-parameter` | Parameter Store | Get a single parameter value |
| `get-parameters` | Parameter Store | Get multiple parameter values |
| `get-parameters-by-path` | Parameter Store | Get parameters under a path hierarchy |
| `delete-parameter` | Parameter Store | Delete a single parameter |
| `delete-parameters` | Parameter Store | Delete multiple parameters |
| `describe-parameters` | Parameter Store | List parameter metadata with filtering |
| `get-parameter-history` | Parameter Store | Get version history of a parameter |
| `label-parameter-version` | Parameter Store | Attach a label to a parameter version |
| `unlabel-parameter-version` | Parameter Store | Remove a label from a parameter version |
| `create-document` | Document | Create an SSM document |
| `delete-document` | Document | Delete an SSM document |
| `describe-document` | Document | Describe an SSM document |
| `get-document` | Document | Get the content of an SSM document |
| `list-documents` | Document | List SSM documents |
| `update-document` | Document | Update an SSM document |
| `update-document-default-version` | Document | Set the default version of a document |
| `list-document-versions` | Document | List versions of a document |
| `send-command` | Run Command | Send a command to target instances |
| `list-commands` | Run Command | List commands that were sent |
| `list-command-invocations` | Run Command | List command invocations |
| `get-command-invocation` | Run Command | Get details of a command invocation |
| `cancel-command` | Run Command | Cancel a running command |
| `start-session` | Session Manager | Start an interactive session |
| `terminate-session` | Session Manager | Terminate a session |
| `describe-sessions` | Session Manager | List sessions |
| `resume-session` | Session Manager | Resume a disconnected session |
| `create-maintenance-window` | Maintenance Window | Create a maintenance window |
| `delete-maintenance-window` | Maintenance Window | Delete a maintenance window |
| `describe-maintenance-windows` | Maintenance Window | List maintenance windows |
| `get-maintenance-window` | Maintenance Window | Get maintenance window details |
| `update-maintenance-window` | Maintenance Window | Update a maintenance window |
| `register-target-with-maintenance-window` | Maintenance Window | Register targets with a window |
| `deregister-target-from-maintenance-window` | Maintenance Window | Remove targets from a window |
| `describe-maintenance-window-targets` | Maintenance Window | List targets for a window |
| `register-task-with-maintenance-window` | Maintenance Window | Register a task with a window |
| `deregister-task-from-maintenance-window` | Maintenance Window | Remove a task from a window |
| `describe-maintenance-window-tasks` | Maintenance Window | List tasks for a window |
| `describe-maintenance-window-executions` | Maintenance Window | List window executions |
| `get-maintenance-window-execution` | Maintenance Window | Get execution details |
| `get-maintenance-window-execution-task` | Maintenance Window | Get execution task details |
| `create-patch-baseline` | Patch Baseline | Create a patch baseline |
| `delete-patch-baseline` | Patch Baseline | Delete a patch baseline |
| `describe-patch-baselines` | Patch Baseline | List patch baselines |
| `get-patch-baseline` | Patch Baseline | Get patch baseline details |
| `update-patch-baseline` | Patch Baseline | Update a patch baseline |
| `register-patch-baseline-for-patch-group` | Patch Baseline | Register a baseline for a patch group |
| `deregister-patch-baseline-for-patch-group` | Patch Baseline | Remove a baseline from a patch group |
| `describe-patch-groups` | Patch Baseline | List patch groups |
| `describe-patch-group-state` | Patch Baseline | Get patch compliance summary for a group |
| `describe-instance-patch-states` | Patch Baseline | Get patch states for instances |
| `describe-instance-patches` | Patch Baseline | List patches for an instance |
| `create-association` | State Manager | Create a State Manager association |
| `delete-association` | State Manager | Delete an association |
| `describe-association` | State Manager | Describe an association |
| `list-associations` | State Manager | List associations |
| `update-association` | State Manager | Update an association |
| `describe-association-executions` | State Manager | List association executions |
| `describe-association-execution-targets` | State Manager | List execution targets |
| `put-inventory` | Inventory | Submit inventory data for an instance |
| `get-inventory` | Inventory | Query inventory data |
| `get-inventory-schema` | Inventory | Get inventory type schema |
| `list-inventory-entries` | Inventory | List inventory entries for an instance |
| `delete-inventory` | Inventory | Delete custom inventory data |
| `create-ops-item` | OpsItem | Create an OpsItem |
| `delete-ops-item` | OpsItem | Delete an OpsItem |
| `get-ops-item` | OpsItem | Get an OpsItem |
| `update-ops-item` | OpsItem | Update an OpsItem |
| `describe-ops-items` | OpsItem | List OpsItems with filters |
| `list-ops-item-events` | OpsItem | List OpsItem events |
| `create-ops-metadata` | OpsItem | Create OpsMetadata |
| `delete-ops-metadata` | OpsItem | Delete OpsMetadata |
| `get-ops-metadata` | OpsItem | Get OpsMetadata |
| `list-ops-metadata` | OpsItem | List OpsMetadata |
| `update-ops-metadata` | OpsItem | Update OpsMetadata |
| `add-tags-to-resource` | Tags | Add tags to a resource |
| `remove-tags-from-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws ssm` commands.

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
| `--cli-binary-format` | string | `base64` | Format for binary blob input: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from a JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from a YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton: `input`, `yaml-input`, `output` |

---

## Common Patterns

### Parameter Types
| Type | Description |
|------|-------------|
| `String` | Plain text parameter |
| `StringList` | Comma-separated list of strings |
| `SecureString` | Encrypted parameter (uses KMS) |

### Parameter Tiers
| Tier | Max Size | Max Parameters | Description |
|------|----------|----------------|-------------|
| `Standard` | 4 KB | 10,000 | Free tier |
| `Advanced` | 8 KB | 100,000 | Charges apply |
| `Intelligent-Tiering` | 8 KB | 100,000 | Auto-selects tier |

### Document Types
| Type | Description |
|------|-------------|
| `Command` | Run Command document |
| `Automation` | Automation runbook |
| `Policy` | State Manager policy |
| `Session` | Session Manager document |
| `Package` | Distributor package |
| `DeploymentStrategy` | AppConfig deployment strategy |

### Command Status Values
| Status | Description |
|--------|-------------|
| `Pending` | Command is waiting to be sent |
| `InProgress` | Command is running |
| `Success` | Command completed successfully |
| `Cancelled` | Command was cancelled |
| `Failed` | Command failed |
| `TimedOut` | Command timed out |
| `Cancelling` | Command is being cancelled |

### Session Status Values
| Status | Description |
|--------|-------------|
| `Connected` | Session is active |
| `Connecting` | Session is being established |
| `Disconnected` | Session was disconnected |
| `Terminated` | Session was terminated |
| `Terminating` | Session is being terminated |
| `Failed` | Session failed to start |

### Resource Types for Tagging
| Type | Description |
|------|-------------|
| `Document` | SSM document |
| `ManagedInstance` | Managed instance |
| `MaintenanceWindow` | Maintenance window |
| `Parameter` | Parameter Store parameter |
| `PatchBaseline` | Patch baseline |
| `OpsItem` | OpsItem |
| `OpsMetadata` | OpsMetadata |
| `Automation` | Automation execution |
| `Association` | State Manager association |
