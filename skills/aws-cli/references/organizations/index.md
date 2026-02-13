# AWS CLI v2 -- Organizations Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/organizations/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-organization` | Organization | Create a new AWS Organization |
| `delete-organization` | Organization | Delete the organization |
| `describe-organization` | Organization | Describe the organization |
| `list-roots` | Organization | List root organizational units |
| `enable-all-features` | Organization | Enable all features in the organization |
| `leave-organization` | Organization | Leave the organization (member account only) |
| `create-account` | Accounts | Create a new member account |
| `create-gov-cloud-account` | Accounts | Create a GovCloud account pair |
| `close-account` | Accounts | Close a member account |
| `describe-account` | Accounts | Describe a member account |
| `describe-create-account-status` | Accounts | Get status of account creation |
| `list-accounts` | Accounts | List all accounts |
| `list-accounts-for-parent` | Accounts | List accounts under a parent |
| `list-create-account-status` | Accounts | List account creation statuses |
| `move-account` | Accounts | Move an account to a different OU |
| `remove-account-from-organization` | Accounts | Remove a member account |
| `invite-account-to-organization` | Accounts | Invite an existing account |
| `create-organizational-unit` | Organizational Units | Create an OU |
| `delete-organizational-unit` | Organizational Units | Delete an OU |
| `describe-organizational-unit` | Organizational Units | Describe an OU |
| `list-organizational-units-for-parent` | Organizational Units | List OUs under a parent |
| `list-children` | Organizational Units | List children of a parent |
| `list-parents` | Organizational Units | List parents of a child |
| `update-organizational-unit` | Organizational Units | Update an OU name |
| `create-policy` | Policies | Create a policy |
| `delete-policy` | Policies | Delete a policy |
| `describe-policy` | Policies | Describe a policy |
| `update-policy` | Policies | Update a policy |
| `list-policies` | Policies | List policies by type |
| `list-policies-for-target` | Policies | List policies attached to a target |
| `list-targets-for-policy` | Policies | List targets for a policy |
| `attach-policy` | Policies | Attach a policy to a target |
| `detach-policy` | Policies | Detach a policy from a target |
| `describe-effective-policy` | Policies | Get effective policy for an account |
| `enable-policy-type` | Policies | Enable a policy type on a root |
| `disable-policy-type` | Policies | Disable a policy type on a root |
| `accept-handshake` | Handshakes | Accept a handshake |
| `cancel-handshake` | Handshakes | Cancel a handshake |
| `decline-handshake` | Handshakes | Decline a handshake |
| `describe-handshake` | Handshakes | Describe a handshake |
| `list-handshakes-for-account` | Handshakes | List handshakes for an account |
| `list-handshakes-for-organization` | Handshakes | List handshakes for the organization |
| `register-delegated-administrator` | Delegated Admin | Register a delegated administrator |
| `deregister-delegated-administrator` | Delegated Admin | Deregister a delegated administrator |
| `list-delegated-administrators` | Delegated Admin | List delegated administrators |
| `list-delegated-services-for-account` | Delegated Admin | List delegated services for an account |
| `enable-aws-service-access` | Service Access | Enable a service for org integration |
| `disable-aws-service-access` | Service Access | Disable a service for org integration |
| `list-aws-service-access-for-organization` | Service Access | List enabled services |
| `put-resource-policy` | Resource Policy | Create or update a resource policy |
| `delete-resource-policy` | Resource Policy | Delete the resource policy |
| `describe-resource-policy` | Resource Policy | Describe the resource policy |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws organizations` commands.

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

### Organization Feature Sets

| Feature Set | Description |
|-------------|-------------|
| `ALL` | Full organization features including SCPs and all policy types |
| `CONSOLIDATED_BILLING` | Billing features only (no SCPs) |

### Policy Types

| Type | Description |
|------|-------------|
| `SERVICE_CONTROL_POLICY` | SCPs that control permissions in member accounts |
| `TAG_POLICY` | Tag standardization policies |
| `BACKUP_POLICY` | AWS Backup policies for organization |
| `AISERVICES_OPT_OUT_POLICY` | AI services opt-out policies |

### Account Status

| Status | Description |
|--------|-------------|
| `ACTIVE` | Account is active |
| `SUSPENDED` | Account is suspended |
| `PENDING_CLOSURE` | Account closure is in progress |

### Create Account Status

| State | Description |
|-------|-------------|
| `IN_PROGRESS` | Account creation is in progress |
| `SUCCEEDED` | Account was created successfully |
| `FAILED` | Account creation failed |

### Handshake States

| State | Description |
|-------|-------------|
| `REQUESTED` | Handshake has been sent |
| `OPEN` | Handshake is awaiting response |
| `CANCELED` | Handshake was canceled |
| `ACCEPTED` | Handshake was accepted |
| `DECLINED` | Handshake was declined |
| `EXPIRED` | Handshake expired (15 days) |

### ID Prefixes

| Prefix | Entity |
|--------|--------|
| `r-` | Root |
| `ou-` | Organizational Unit |
| `o-` | Organization |
| `p-` | Policy |
| `h-` | Handshake |

### Region Note

AWS Organizations is a global service. All API calls go to `us-east-1` regardless of the configured region.
