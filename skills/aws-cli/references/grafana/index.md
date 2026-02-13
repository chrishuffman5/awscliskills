# AWS CLI v2 — Amazon Managed Grafana Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/grafana/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-workspace` | Workspace | Create a Grafana workspace |
| `delete-workspace` | Workspace | Delete a Grafana workspace |
| `describe-workspace` | Workspace | Get details about a workspace |
| `list-workspaces` | Workspace | List all workspaces |
| `update-workspace` | Workspace | Update workspace settings |
| `describe-workspace-configuration` | Workspace | Get workspace configuration |
| `update-workspace-configuration` | Workspace | Update workspace configuration |
| `list-versions` | Workspace | List available Grafana versions |
| `describe-workspace-authentication` | Authentication | Get authentication config for a workspace |
| `update-workspace-authentication` | Authentication | Update authentication config |
| `list-permissions` | Permissions | List permissions for a workspace |
| `update-permissions` | Permissions | Update user/group permissions |
| `create-workspace-service-account` | Service Account | Create a service account |
| `delete-workspace-service-account` | Service Account | Delete a service account |
| `list-workspace-service-accounts` | Service Account | List service accounts |
| `create-workspace-service-account-token` | Service Account | Create a service account token |
| `delete-workspace-service-account-token` | Service Account | Delete a service account token |
| `list-workspace-service-account-tokens` | Service Account | List service account tokens |
| `create-workspace-api-key` | API Key | Create a workspace API key |
| `delete-workspace-api-key` | API Key | Delete a workspace API key |
| `associate-license` | License | Associate a license with a workspace |
| `disassociate-license` | License | Disassociate a license from a workspace |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws grafana` commands.

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

### Workspace Statuses
| Status | Description |
|--------|-------------|
| `ACTIVE` | Workspace is running |
| `CREATING` | Workspace is being created |
| `DELETING` | Workspace is being deleted |
| `FAILED` | Workspace creation failed |
| `UPDATING` | Workspace is being updated |
| `UPGRADING` | Workspace is being upgraded |
| `DELETION_FAILED` | Workspace deletion failed |
| `CREATION_FAILED` | Workspace creation failed |
| `UPDATE_FAILED` | Workspace update failed |
| `UPGRADE_FAILED` | Workspace upgrade failed |
| `LICENSE_REMOVAL_FAILED` | License removal failed |
| `VERSION_UPDATING` | Grafana version is being updated |
| `VERSION_UPDATE_FAILED` | Grafana version update failed |

### Permission Types
| Type | Description |
|------|-------------|
| `SERVICE_MANAGED` | AWS manages permissions |
| `CUSTOMER_MANAGED` | Customer manages permissions |

### Authentication Providers
| Provider | Description |
|----------|-------------|
| `AWS_SSO` | AWS IAM Identity Center |
| `SAML` | SAML 2.0 identity provider |

### Grafana Roles
| Role | Description |
|------|-------------|
| `ADMIN` | Full access to all Grafana features |
| `EDITOR` | Can create and edit dashboards |
| `VIEWER` | Read-only access to dashboards |

### Data Sources
Common supported data sources: `AMAZON_OPENSEARCH_SERVICE`, `CLOUDWATCH`, `PROMETHEUS`, `XRAY`, `TIMESTREAM`, `SITEWISE`, `ATHENA`, `REDSHIFT`, `TWINMAKER`.
