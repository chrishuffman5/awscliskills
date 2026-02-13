# AWS CLI v2 -- Detective Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/detective/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-graph` | Graph | Create a new behavior graph |
| `delete-graph` | Graph | Delete a behavior graph |
| `list-graphs` | Graph | List behavior graphs |
| `create-members` | Member | Add member accounts to a behavior graph |
| `delete-members` | Member | Remove member accounts from a behavior graph |
| `get-members` | Member | Get member account details |
| `list-members` | Member | List member accounts in a behavior graph |
| `accept-invitation` | Member | Accept invitation to contribute to a graph |
| `reject-invitation` | Member | Reject invitation to a graph |
| `disassociate-membership` | Member | Remove your account from a behavior graph |
| `list-invitations` | Member | List invitations to behavior graphs |
| `start-monitoring-member` | Member | Enable monitoring for a member account |
| `start-investigation` | Investigation | Start a new investigation |
| `get-investigation` | Investigation | Get investigation details |
| `list-investigations` | Investigation | List all investigations |
| `update-investigation-state` | Investigation | Update investigation status |
| `list-indicators` | Investigation | List investigation indicators |
| `list-datasource-packages` | Data Source | List data source packages |
| `update-datasource-packages` | Data Source | Update data source package configuration |
| `batch-get-graph-member-datasources` | Data Source | Get data source info for graph members |
| `batch-get-membership-datasources` | Data Source | Get data source info for memberships |
| `enable-organization-admin-account` | Organization | Enable organization admin account |
| `disable-organization-admin-account` | Organization | Disable organization admin account |
| `list-organization-admin-accounts` | Organization | List organization admin accounts |
| `describe-organization-configuration` | Organization | Describe organization configuration |
| `update-organization-configuration` | Organization | Update organization configuration |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws detective` commands.

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

### Behavior Graph
- A behavior graph is the core resource in Detective
- Each account can be the administrator of one behavior graph per Region
- Member accounts contribute their data to the administrator's behavior graph

### Investigation States
| State | Description |
|-------|-------------|
| `ACTIVE` | Investigation is currently active |
| `ARCHIVED` | Investigation has been archived |

### Investigation Severity
| Severity | Description |
|----------|-------------|
| `INFORMATIONAL` | No issue detected |
| `LOW` | Low severity finding |
| `MEDIUM` | Medium severity finding |
| `HIGH` | High severity finding |
| `CRITICAL` | Critical severity finding |

### Data Source Packages
| Package | Description |
|---------|-------------|
| `DETECTIVE_CORE` | Core Detective data (VPC Flow Logs, CloudTrail, GuardDuty) |
| `EKS_AUDIT` | EKS audit log data |
| `ASFF_SECURITYHUB_FINDING` | Security Hub findings |

### Member Account Statuses
| Status | Description |
|--------|-------------|
| `INVITED` | Account has been invited |
| `VERIFICATION_IN_PROGRESS` | Email verification in progress |
| `VERIFICATION_FAILED` | Email verification failed |
| `ENABLED` | Account is actively contributing data |
| `ACCEPTED_BUT_DISABLED` | Accepted but not enabled |
