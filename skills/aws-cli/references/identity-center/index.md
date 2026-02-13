# AWS CLI v2 -- IAM Identity Center Command Reference Index

> Based on AWS CLI v2 documentation.
> Sources: https://docs.aws.amazon.com/cli/latest/reference/sso-admin/ , https://docs.aws.amazon.com/cli/latest/reference/identitystore/

---

## Quick Reference — sso-admin

| Command | Category | Description |
|---------|----------|-------------|
| `create-instance` | Instance | Create an IAM Identity Center instance |
| `delete-instance` | Instance | Delete an IAM Identity Center instance |
| `describe-instance` | Instance | Describe an instance |
| `list-instances` | Instance | List all instances |
| `update-instance` | Instance | Update an instance |
| `create-instance-access-control-attribute-configuration` | Instance | Configure ABAC attributes |
| `delete-instance-access-control-attribute-configuration` | Instance | Delete ABAC configuration |
| `describe-instance-access-control-attribute-configuration` | Instance | Describe ABAC configuration |
| `update-instance-access-control-attribute-configuration` | Instance | Update ABAC configuration |
| `add-region` | Instance | Add a region |
| `remove-region` | Instance | Remove a region |
| `describe-region` | Instance | Describe a region |
| `list-regions` | Instance | List regions |
| `create-permission-set` | Permission Set | Create a permission set |
| `delete-permission-set` | Permission Set | Delete a permission set |
| `describe-permission-set` | Permission Set | Describe a permission set |
| `update-permission-set` | Permission Set | Update a permission set |
| `list-permission-sets` | Permission Set | List all permission sets |
| `list-permission-sets-provisioned-to-account` | Permission Set | List permission sets provisioned to an account |
| `list-accounts-for-provisioned-permission-set` | Permission Set | List accounts where a permission set is provisioned |
| `provision-permission-set` | Permission Set | Provision a permission set |
| `describe-permission-set-provisioning-status` | Permission Set | Describe provisioning status |
| `list-permission-set-provisioning-status` | Permission Set | List provisioning statuses |
| `attach-managed-policy-to-permission-set` | Policy | Attach an AWS managed policy |
| `detach-managed-policy-from-permission-set` | Policy | Detach an AWS managed policy |
| `list-managed-policies-in-permission-set` | Policy | List managed policies in a permission set |
| `attach-customer-managed-policy-reference-to-permission-set` | Policy | Attach a customer-managed policy |
| `detach-customer-managed-policy-reference-from-permission-set` | Policy | Detach a customer-managed policy |
| `list-customer-managed-policy-references-in-permission-set` | Policy | List customer-managed policies |
| `put-inline-policy-to-permission-set` | Policy | Add inline policy |
| `get-inline-policy-for-permission-set` | Policy | Get inline policy |
| `delete-inline-policy-from-permission-set` | Policy | Delete inline policy |
| `put-permissions-boundary-to-permission-set` | Policy | Set permissions boundary |
| `get-permissions-boundary-for-permission-set` | Policy | Get permissions boundary |
| `delete-permissions-boundary-from-permission-set` | Policy | Delete permissions boundary |
| `create-account-assignment` | Assignment | Assign user/group to an account |
| `delete-account-assignment` | Assignment | Delete an account assignment |
| `list-account-assignments` | Assignment | List account assignments |
| `list-account-assignments-for-principal` | Assignment | List assignments for a user/group |
| `describe-account-assignment-creation-status` | Assignment | Describe assignment creation status |
| `list-account-assignment-creation-status` | Assignment | List assignment creation statuses |
| `describe-account-assignment-deletion-status` | Assignment | Describe assignment deletion status |
| `list-account-assignment-deletion-status` | Assignment | List assignment deletion statuses |
| `create-application` | Application | Create an application |
| `delete-application` | Application | Delete an application |
| `describe-application` | Application | Describe an application |
| `update-application` | Application | Update an application |
| `list-applications` | Application | List applications |
| `list-application-providers` | Application | List application providers |
| `create-application-assignment` | Application | Assign user/group to an application |
| `delete-application-assignment` | Application | Delete an application assignment |
| `describe-application-assignment` | Application | Describe an application assignment |
| `list-application-assignments` | Application | List application assignments |
| `list-application-assignments-for-principal` | Application | List application assignments for a principal |
| `put-application-access-scope` | App Config | Set application access scope |
| `get-application-access-scope` | App Config | Get application access scope |
| `delete-application-access-scope` | App Config | Delete application access scope |
| `list-application-access-scopes` | App Config | List application access scopes |
| `put-application-assignment-configuration` | App Config | Set assignment configuration |
| `get-application-assignment-configuration` | App Config | Get assignment configuration |
| `put-application-authentication-method` | App Config | Set authentication method |
| `get-application-authentication-method` | App Config | Get authentication method |
| `delete-application-authentication-method` | App Config | Delete authentication method |
| `list-application-authentication-methods` | App Config | List authentication methods |
| `put-application-grant` | App Config | Set application grant |
| `get-application-grant` | App Config | Get application grant |
| `delete-application-grant` | App Config | Delete application grant |
| `list-application-grants` | App Config | List application grants |
| `put-application-session-configuration` | App Config | Set session configuration |
| `get-application-session-configuration` | App Config | Get session configuration |
| `describe-application-provider` | App Config | Describe application provider |
| `create-trusted-token-issuer` | Token Issuer | Create a trusted token issuer |
| `delete-trusted-token-issuer` | Token Issuer | Delete a trusted token issuer |
| `describe-trusted-token-issuer` | Token Issuer | Describe a trusted token issuer |
| `update-trusted-token-issuer` | Token Issuer | Update a trusted token issuer |
| `list-trusted-token-issuers` | Token Issuer | List trusted token issuers |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

## Quick Reference — identitystore

| Command | Category | Description |
|---------|----------|-------------|
| `create-user` | User | Create a new user |
| `delete-user` | User | Delete a user |
| `describe-user` | User | Get user details |
| `update-user` | User | Update user attributes |
| `get-user-id` | User | Look up user ID by alternate identifier |
| `list-users` | User | List all users |
| `create-group` | Group | Create a new group |
| `delete-group` | Group | Delete a group |
| `describe-group` | Group | Get group details |
| `update-group` | Group | Update group attributes |
| `get-group-id` | Group | Look up group ID by alternate identifier |
| `list-groups` | Group | List all groups |
| `create-group-membership` | Group | Add a member to a group |
| `delete-group-membership` | Group | Remove a member from a group |
| `describe-group-membership` | Group | Get membership details |
| `get-group-membership-id` | Group | Look up membership ID |
| `is-member-in-groups` | Group | Check if a member is in specified groups |
| `list-group-memberships` | Group | List members in a group |
| `list-group-memberships-for-member` | Group | List groups a member belongs to |

---

## Global Options

These options are available on ALL `aws sso-admin` and `aws identitystore` commands.

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

### Principal Types
| Type | Description |
|------|-------------|
| `USER` | An individual user in IAM Identity Center |
| `GROUP` | A group in IAM Identity Center |

### Account Assignment Statuses
| Status | Description |
|--------|-------------|
| `IN_PROGRESS` | Operation is in progress |
| `FAILED` | Operation failed |
| `SUCCEEDED` | Operation completed successfully |

### Permission Set Provisioning Statuses
| Status | Description |
|--------|-------------|
| `IN_PROGRESS` | Provisioning is in progress |
| `FAILED` | Provisioning failed |
| `SUCCEEDED` | Provisioning completed successfully |

### Application Statuses
| Status | Description |
|--------|-------------|
| `ENABLED` | Application is active |
| `DISABLED` | Application is disabled |

### Target Types
| Type | Description |
|------|-------------|
| `AWS_ACCOUNT` | An AWS account |
| `ALL_PROVISIONED_ACCOUNTS` | All accounts where the permission set is provisioned |
