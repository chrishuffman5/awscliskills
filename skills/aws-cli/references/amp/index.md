# AWS CLI v2 -- Amazon Managed Service for Prometheus (AMP) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/amp/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-workspace` | Workspace | Create a new Prometheus workspace |
| `delete-workspace` | Workspace | Delete a workspace |
| `describe-workspace` | Workspace | Describe a workspace |
| `list-workspaces` | Workspace | List all workspaces |
| `update-workspace-alias` | Workspace | Update workspace alias |
| `create-alert-manager-definition` | Alert Manager | Create alert manager definition |
| `delete-alert-manager-definition` | Alert Manager | Delete alert manager definition |
| `describe-alert-manager-definition` | Alert Manager | Describe alert manager definition |
| `put-alert-manager-definition` | Alert Manager | Update alert manager definition |
| `create-rule-groups-namespace` | Rule Groups | Create a rule groups namespace |
| `delete-rule-groups-namespace` | Rule Groups | Delete a rule groups namespace |
| `describe-rule-groups-namespace` | Rule Groups | Describe a rule groups namespace |
| `list-rule-groups-namespaces` | Rule Groups | List rule groups namespaces |
| `put-rule-groups-namespace` | Rule Groups | Update a rule groups namespace |
| `create-scraper` | Scraper | Create a scraper |
| `delete-scraper` | Scraper | Delete a scraper |
| `describe-scraper` | Scraper | Describe a scraper |
| `list-scrapers` | Scraper | List scrapers |
| `update-scraper` | Scraper | Update a scraper |
| `get-default-scraper-configuration` | Scraper | Get default scraper configuration |
| `create-logging-configuration` | Logging | Create logging configuration |
| `delete-logging-configuration` | Logging | Delete logging configuration |
| `describe-logging-configuration` | Logging | Describe logging configuration |
| `update-logging-configuration` | Logging | Update logging configuration |
| `describe-resource-policy` | Resource Policy | Describe resource policy |
| `put-resource-policy` | Resource Policy | Create/update resource policy |
| `delete-resource-policy` | Resource Policy | Delete resource policy |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |
| `wait workspace-active` | Wait | Wait until workspace is active |
| `wait workspace-deleted` | Wait | Wait until workspace is deleted |
| `wait scraper-active` | Wait | Wait until scraper is active |
| `wait scraper-deleted` | Wait | Wait until scraper is deleted |

---

## Global Options

These options are available on ALL `aws amp` commands.

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

### Workspace Status Values
| Status | Description |
|--------|-------------|
| `CREATING` | Workspace is being created |
| `ACTIVE` | Workspace is ready for use |
| `UPDATING` | Workspace is being updated |
| `DELETING` | Workspace is being deleted |
| `CREATION_FAILED` | Workspace creation failed |

### Scraper Status Values
| Status | Description |
|--------|-------------|
| `CREATING` | Scraper is being created |
| `ACTIVE` | Scraper is active and running |
| `DELETING` | Scraper is being deleted |
| `CREATION_FAILED` | Scraper creation failed |
| `DELETION_FAILED` | Scraper deletion failed |

### Alert Manager Definition Status
| Status | Description |
|--------|-------------|
| `CREATING` | Definition is being created |
| `ACTIVE` | Definition is active |
| `UPDATING` | Definition is being updated |
| `CREATION_FAILED` | Creation failed |
| `UPDATE_FAILED` | Update failed |

### Rule Groups Namespace Status
| Status | Description |
|--------|-------------|
| `CREATING` | Namespace is being created |
| `ACTIVE` | Namespace is active |
| `UPDATING` | Namespace is being updated |
| `DELETING` | Namespace is being deleted |
| `CREATION_FAILED` | Creation failed |
| `UPDATE_FAILED` | Update failed |

### Wait Commands
The `aws amp wait` subcommand blocks until a resource reaches a specific state:

| Waiter | Description |
|--------|-------------|
| `workspace-active` | Wait until workspace status is ACTIVE |
| `workspace-deleted` | Wait until workspace is deleted |
| `scraper-active` | Wait until scraper status is ACTIVE |
| `scraper-deleted` | Wait until scraper is deleted |

```bash
aws amp wait workspace-active --workspace-id ws-12345
aws amp wait scraper-active --scraper-id s-12345
```
