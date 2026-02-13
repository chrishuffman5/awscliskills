# AWS CLI v2 -- Security Hub Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/securityhub/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `enable-security-hub` | Hub | Enable Security Hub in the account |
| `disable-security-hub` | Hub | Disable Security Hub |
| `describe-hub` | Hub | Describe Security Hub settings |
| `update-security-hub-configuration` | Hub | Update Security Hub configuration |
| `get-findings` | Finding | Get security findings with filters |
| `batch-import-findings` | Finding | Import findings from integrations |
| `batch-update-findings` | Finding | Batch update finding attributes |
| `update-findings` | Finding | Update finding note and verification state |
| `get-finding-history` | Finding | Get finding change history |
| `create-insight` | Insight | Create a custom insight |
| `delete-insight` | Insight | Delete a custom insight |
| `get-insights` | Insight | Get custom insight details |
| `get-insight-results` | Insight | Get insight aggregation results |
| `update-insight` | Insight | Update a custom insight |
| `describe-standards` | Standard | Describe available security standards |
| `batch-enable-standards` | Standard | Enable security standards |
| `batch-disable-standards` | Standard | Disable security standards |
| `get-enabled-standards` | Standard | Get enabled standards |
| `describe-standards-controls` | Standard | Describe standard controls |
| `update-standards-control` | Standard | Update a standards control |
| `batch-get-standards-control-associations` | Standard | Get standards control associations |
| `batch-update-standards-control-associations` | Standard | Update standards control associations |
| `list-standards-control-associations` | Standard | List standards control associations |
| `list-security-control-definitions` | Security Control | List security control definitions |
| `get-security-control-definition` | Security Control | Get a security control definition |
| `batch-get-security-controls` | Security Control | Batch get security controls |
| `update-security-control` | Security Control | Update a security control |
| `create-automation-rule` | Automation Rule | Create an automation rule |
| `list-automation-rules` | Automation Rule | List automation rules |
| `batch-get-automation-rules` | Automation Rule | Batch get automation rules |
| `batch-update-automation-rules` | Automation Rule | Batch update automation rules |
| `batch-delete-automation-rules` | Automation Rule | Batch delete automation rules |
| `create-configuration-policy` | Configuration Policy | Create a configuration policy |
| `delete-configuration-policy` | Configuration Policy | Delete a configuration policy |
| `get-configuration-policy` | Configuration Policy | Get a configuration policy |
| `list-configuration-policies` | Configuration Policy | List configuration policies |
| `update-configuration-policy` | Configuration Policy | Update a configuration policy |
| `get-configuration-policy-association` | Configuration Policy | Get a policy association |
| `list-configuration-policy-associations` | Configuration Policy | List policy associations |
| `batch-get-configuration-policy-associations` | Configuration Policy | Batch get policy associations |
| `start-configuration-policy-association` | Configuration Policy | Start policy association |
| `start-configuration-policy-disassociation` | Configuration Policy | Start policy disassociation |
| `create-finding-aggregator` | Finding Aggregator | Create cross-region aggregator |
| `delete-finding-aggregator` | Finding Aggregator | Delete a finding aggregator |
| `get-finding-aggregator` | Finding Aggregator | Get a finding aggregator |
| `list-finding-aggregators` | Finding Aggregator | List finding aggregators |
| `update-finding-aggregator` | Finding Aggregator | Update a finding aggregator |
| `create-aggregator-v2` | Aggregator v2 | Create a v2 aggregator |
| `delete-aggregator-v2` | Aggregator v2 | Delete a v2 aggregator |
| `get-aggregator-v2` | Aggregator v2 | Get a v2 aggregator |
| `list-aggregators-v2` | Aggregator v2 | List v2 aggregators |
| `update-aggregator-v2` | Aggregator v2 | Update a v2 aggregator |
| `create-connector-v2` | Connector v2 | Create a v2 connector |
| `delete-connector-v2` | Connector v2 | Delete a v2 connector |
| `get-connector-v2` | Connector v2 | Get a v2 connector |
| `list-connectors-v2` | Connector v2 | List v2 connectors |
| `update-connector-v2` | Connector v2 | Update a v2 connector |
| `register-connector-v2` | Connector v2 | Register a v2 connector |
| `create-action-target` | Action Target | Create a custom action target |
| `delete-action-target` | Action Target | Delete a custom action target |
| `describe-action-targets` | Action Target | Describe action targets |
| `update-action-target` | Action Target | Update an action target |
| `create-members` | Member | Create member accounts |
| `delete-members` | Member | Delete member accounts |
| `get-members` | Member | Get member account details |
| `invite-members` | Member | Invite member accounts |
| `list-members` | Member | List member accounts |
| `disassociate-members` | Member | Disassociate members |
| `accept-administrator-invitation` | Member | Accept administrator invitation |
| `disassociate-from-administrator-account` | Member | Disassociate from administrator |
| `get-administrator-account` | Member | Get administrator account |
| `get-invitations-count` | Member | Get invitation count |
| `list-invitations` | Member | List invitations |
| `decline-invitations` | Member | Decline invitations |
| `delete-invitations` | Member | Delete invitations |
| `enable-organization-admin-account` | Organization | Enable org admin account |
| `disable-organization-admin-account` | Organization | Disable org admin account |
| `list-organization-admin-accounts` | Organization | List org admin accounts |
| `describe-organization-configuration` | Organization | Describe org configuration |
| `update-organization-configuration` | Organization | Update org configuration |
| `describe-products` | Product | Describe available products |
| `enable-import-findings-for-product` | Product | Enable findings import |
| `disable-import-findings-for-product` | Product | Disable findings import |
| `list-enabled-products-for-import` | Product | List enabled products |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws securityhub` commands.

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

### Severity Labels
| Label | Description |
|-------|-------------|
| `INFORMATIONAL` | No issue found or informational finding |
| `LOW` | Issue that does not require immediate action |
| `MEDIUM` | Issue that should be addressed but is not urgent |
| `HIGH` | Issue that should be addressed as a priority |
| `CRITICAL` | Issue that must be remediated immediately |

### Workflow Statuses
| Status | Description |
|--------|-------------|
| `NEW` | Initial state of a finding |
| `NOTIFIED` | Finding has been shared with the resource owner |
| `RESOLVED` | Finding has been reviewed and remediated |
| `SUPPRESSED` | Finding is not actionable and should not surface |

### Record States
| State | Description |
|-------|-------------|
| `ACTIVE` | Finding is current and should be reviewed |
| `ARCHIVED` | Finding is no longer current |

### Compliance Statuses
| Status | Description |
|--------|-------------|
| `PASSED` | Resource is compliant with the control |
| `WARNING` | Information is missing or feature not supported |
| `FAILED` | Resource is not compliant with the control |
| `NOT_AVAILABLE` | Check could not be performed |

### ASFF (AWS Security Finding Format)
All findings in Security Hub use ASFF. Key required fields:
- `SchemaVersion` — ASFF version
- `Id` — Unique identifier for the finding
- `ProductArn` — ARN of the product that generated the finding
- `GeneratorId` — Identifier for the component that generated the finding
- `AwsAccountId` — AWS account where the finding was generated
- `CreatedAt` / `UpdatedAt` — Timestamps (ISO 8601)
- `Title` / `Description` — Human-readable finding information
- `Resources` — AWS resources related to the finding
- `Severity` — Finding severity
