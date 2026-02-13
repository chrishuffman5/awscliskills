# AWS CLI v2 -- RAM (Resource Access Manager) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/ram/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-resource-share` | Resource Share | Create a new resource share |
| `update-resource-share` | Resource Share | Update a resource share |
| `delete-resource-share` | Resource Share | Delete a resource share |
| `get-resource-shares` | Resource Share | Get details of resource shares |
| `associate-resource-share` | Resource Share | Associate resources or principals with a share |
| `disassociate-resource-share` | Resource Share | Disassociate resources or principals from a share |
| `get-resource-share-associations` | Resource Share | Get associations for resource shares |
| `list-resources` | Resource Share | List shared resources |
| `list-principals` | Resource Share | List principals with shared resources |
| `list-resource-types` | Resource Share | List supported shareable resource types |
| `get-resource-policies` | Resource Share | Get resource-based policies for shared resources |
| `promote-resource-share-created-from-policy` | Resource Share | Promote a policy-created share to standard |
| `enable-sharing-with-aws-organization` | Resource Share | Enable sharing within AWS Organizations |
| `accept-resource-share-invitation` | Invitation | Accept a resource share invitation |
| `reject-resource-share-invitation` | Invitation | Reject a resource share invitation |
| `get-resource-share-invitations` | Invitation | Get resource share invitations |
| `list-pending-invitation-resources` | Invitation | List resources in pending invitations |
| `create-permission` | Permission | Create a customer-managed permission |
| `create-permission-version` | Permission | Create a new version of a permission |
| `delete-permission` | Permission | Delete a customer-managed permission |
| `delete-permission-version` | Permission | Delete a version of a permission |
| `get-permission` | Permission | Get details of a permission |
| `list-permissions` | Permission | List all permissions |
| `list-permission-versions` | Permission | List versions of a permission |
| `list-permission-associations` | Permission | List permission associations |
| `list-resource-share-permissions` | Permission | List permissions for a resource share |
| `associate-resource-share-permission` | Permission | Associate a permission with a share |
| `disassociate-resource-share-permission` | Permission | Disassociate a permission from a share |
| `replace-permission-associations` | Permission | Replace permission associations |
| `list-replace-permission-associations-work` | Permission | List replacement work status |
| `set-default-permission-version` | Permission | Set default version of a permission |
| `promote-permission-created-from-policy` | Permission | Promote a policy-created permission |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-source-associations` | Organization | List source associations |

---

## Global Options

These options are available on ALL `aws ram` commands.

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

### Resource Share Statuses
| Status | Description |
|--------|-------------|
| `PENDING` | Share is being created |
| `ACTIVE` | Share is active and usable |
| `FAILED` | Share creation failed |
| `DELETING` | Share is being deleted |
| `DELETED` | Share has been deleted |

### Association Types
| Type | Description |
|------|-------------|
| `PRINCIPAL` | Association with a principal (account, OU, organization) |
| `RESOURCE` | Association with a resource |
| `SOURCE` | Association with a source |

### Association Statuses
| Status | Description |
|--------|-------------|
| `ASSOCIATING` | Association is being created |
| `ASSOCIATED` | Association is active |
| `FAILED` | Association failed |
| `DISASSOCIATING` | Association is being removed |
| `DISASSOCIATED` | Association has been removed |
| `SUSPENDED` | Association is suspended |
| `SUSPENDING` | Association is being suspended |
| `RESTORING` | Association is being restored |

### Invitation Statuses
| Status | Description |
|--------|-------------|
| `PENDING` | Invitation is pending acceptance |
| `ACCEPTED` | Invitation has been accepted |
| `REJECTED` | Invitation has been rejected |
| `EXPIRED` | Invitation has expired |

### Resource Owner Values
| Value | Description |
|-------|-------------|
| `SELF` | Resources owned by the calling account |
| `OTHER-ACCOUNTS` | Resources shared with the calling account |
