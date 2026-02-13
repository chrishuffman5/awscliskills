# AWS CLI v2 -- Firewall Manager (FMS) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/fms/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `associate-admin-account` | Admin | Set the default Firewall Manager administrator |
| `disassociate-admin-account` | Admin | Remove the default Firewall Manager administrator |
| `get-admin-account` | Admin | Get the default administrator account |
| `get-admin-scope` | Admin | Get the admin scope for an administrator |
| `put-admin-account` | Admin | Create or update an administrator account |
| `list-admin-accounts-for-organization` | Admin | List admin accounts for the organization |
| `list-admins-managing-account` | Admin | List admins managing a specific account |
| `put-policy` | Policies | Create or update a Firewall Manager policy |
| `get-policy` | Policies | Get details of a Firewall Manager policy |
| `delete-policy` | Policies | Delete a Firewall Manager policy |
| `list-policies` | Policies | List all Firewall Manager policies |
| `get-compliance-detail` | Policies | Get compliance details for a member account |
| `list-compliance-status` | Policies | List compliance status for all member accounts |
| `get-violation-details` | Policies | Get violation details for a resource |
| `get-protection-status` | Policies | Get attack event details for Shield Advanced |
| `list-member-accounts` | Policies | List member accounts in the organization |
| `list-discovered-resources` | Policies | List discovered resources for a policy |
| `put-apps-list` | Apps & Protocols | Create or update an apps list |
| `get-apps-list` | Apps & Protocols | Get an apps list |
| `delete-apps-list` | Apps & Protocols | Delete an apps list |
| `list-apps-lists` | Apps & Protocols | List all apps lists |
| `put-protocols-list` | Apps & Protocols | Create or update a protocols list |
| `get-protocols-list` | Apps & Protocols | Get a protocols list |
| `delete-protocols-list` | Apps & Protocols | Delete a protocols list |
| `list-protocols-lists` | Apps & Protocols | List all protocols lists |
| `put-resource-set` | Resource Sets | Create or update a resource set |
| `get-resource-set` | Resource Sets | Get a resource set |
| `delete-resource-set` | Resource Sets | Delete a resource set |
| `list-resource-sets` | Resource Sets | List all resource sets |
| `list-resource-set-resources` | Resource Sets | List resources in a resource set |
| `batch-associate-resource` | Resource Sets | Associate resources with a resource set |
| `batch-disassociate-resource` | Resource Sets | Disassociate resources from a resource set |
| `associate-third-party-firewall` | Third-Party | Associate a third-party firewall |
| `disassociate-third-party-firewall` | Third-Party | Disassociate a third-party firewall |
| `get-third-party-firewall-association-status` | Third-Party | Get third-party firewall association status |
| `list-third-party-firewall-firewall-policies` | Third-Party | List third-party firewall policies |
| `put-notification-channel` | Notifications & Tags | Set the SNS notification channel |
| `get-notification-channel` | Notifications & Tags | Get the SNS notification channel |
| `delete-notification-channel` | Notifications & Tags | Delete the SNS notification channel |
| `tag-resource` | Notifications & Tags | Add tags to a resource |
| `untag-resource` | Notifications & Tags | Remove tags from a resource |
| `list-tags-for-resource` | Notifications & Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws fms` commands.

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

### Policy Types
| Type | Description |
|------|-------------|
| `WAF` | AWS WAF Classic |
| `WAFV2` | AWS WAF v2 |
| `SHIELD_ADVANCED` | AWS Shield Advanced |
| `SECURITY_GROUPS_COMMON` | Common security group policy |
| `SECURITY_GROUPS_CONTENT_AUDIT` | Security group content audit |
| `SECURITY_GROUPS_USAGE_AUDIT` | Security group usage audit |
| `NETWORK_FIREWALL` | AWS Network Firewall |
| `DNS_FIREWALL` | Route 53 Resolver DNS Firewall |
| `THIRD_PARTY_FIREWALL` | Third-party firewall |
| `IMPORT_NETWORK_FIREWALL` | Import existing Network Firewall |
| `NETWORK_ACL_COMMON` | Network ACL common policy |

### Violation Reasons
| Reason | Description |
|--------|-------------|
| `WEB_ACL_MISSING_RULE_GROUP` | Web ACL missing required rule group |
| `RESOURCE_MISSING_WEB_ACL` | Resource missing required web ACL |
| `RESOURCE_MISSING_SHIELD_PROTECTION` | Resource missing Shield protection |
| `RESOURCE_MISSING_SECURITY_GROUP` | Resource missing security group |
| `SECURITY_GROUP_UNUSED` | Security group is unused |
| `MISSING_FIREWALL` | Missing firewall |
| `MISSING_EXPECTED_ROUTE_TABLE` | Missing expected route table |
| `FMS_CREATED_SECURITY_GROUP_EDITED` | FMS-created security group was edited |

### Policy Status Values
| Status | Description |
|--------|-------------|
| `ACTIVE` | Policy is active and enforced |
| `OUT_OF_ADMIN_SCOPE` | Policy is outside the admin scope |
