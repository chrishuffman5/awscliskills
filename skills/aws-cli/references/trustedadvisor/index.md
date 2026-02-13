# AWS CLI v2 -- Trusted Advisor (trustedadvisor + support) Command Reference Index

> Based on AWS CLI v2 documentation. Sources: https://docs.aws.amazon.com/cli/latest/reference/trustedadvisor/ , https://docs.aws.amazon.com/cli/latest/reference/support/

---

## Quick Reference

| Command | Namespace | Category | Description |
|---------|-----------|----------|-------------|
| `list-recommendations` | trustedadvisor | Recommendation | List all recommendations |
| `get-recommendation` | trustedadvisor | Recommendation | Get details of a specific recommendation |
| `list-recommendation-resources` | trustedadvisor | Recommendation | List resources for a recommendation |
| `update-recommendation-lifecycle` | trustedadvisor | Recommendation | Update lifecycle stage of a recommendation |
| `batch-update-recommendation-resource-exclusion` | trustedadvisor | Recommendation | Batch update resource exclusions |
| `list-checks` | trustedadvisor | Recommendation | List all available Trusted Advisor checks |
| `list-organization-recommendations` | trustedadvisor | Organization | List organization-level recommendations |
| `get-organization-recommendation` | trustedadvisor | Organization | Get details of an organization recommendation |
| `list-organization-recommendation-accounts` | trustedadvisor | Organization | List accounts for an organization recommendation |
| `list-organization-recommendation-resources` | trustedadvisor | Organization | List resources for an organization recommendation |
| `update-organization-recommendation-lifecycle` | trustedadvisor | Organization | Update lifecycle of an organization recommendation |
| `create-case` | support | Support Case | Create a new support case |
| `describe-cases` | support | Support Case | Describe support cases |
| `add-communication-to-case` | support | Support Case | Add communication to a support case |
| `describe-communications` | support | Support Case | Describe communications for a case |
| `resolve-case` | support | Support Case | Resolve a support case |
| `describe-services` | support | Support Case | List AWS service codes and categories |
| `describe-severity-levels` | support | Support Case | List severity levels |
| `describe-create-case-options` | support | Support Case | Get options for creating a case |
| `describe-supported-languages` | support | Support Case | Get supported languages for cases |
| `add-attachments-to-set` | support | Support Case | Add attachments to an attachment set |
| `describe-attachment` | support | Support Case | Describe a case attachment |
| `describe-trusted-advisor-checks` | support | Trusted Advisor | List all classic Trusted Advisor checks |
| `describe-trusted-advisor-check-result` | support | Trusted Advisor | Get results of a Trusted Advisor check |
| `describe-trusted-advisor-check-summaries` | support | Trusted Advisor | Get summaries of Trusted Advisor checks |
| `describe-trusted-advisor-check-refresh-statuses` | support | Trusted Advisor | Get refresh statuses of checks |
| `refresh-trusted-advisor-check` | support | Trusted Advisor | Request a refresh of a check |

---

## Global Options

These options are available on ALL `aws trustedadvisor` and `aws support` commands.

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

### Recommendation Pillars
| Pillar | Description |
|--------|-------------|
| `cost_optimizing` | Cost optimization recommendations |
| `performance` | Performance improvement recommendations |
| `security` | Security best practice recommendations |
| `service_limits` | Service limit/quota recommendations |
| `fault_tolerance` | Fault tolerance and resilience recommendations |
| `operational_excellence` | Operational excellence recommendations |

### Recommendation Statuses
| Status | Description |
|--------|-------------|
| `ok` | No issues found |
| `warning` | Potential issues detected |
| `error` | Action required |

### Lifecycle Stages
| Stage | Description |
|-------|-------------|
| `in_progress` | Recommendation is being addressed |
| `pending_response` | Awaiting response |
| `dismissed` | Recommendation has been dismissed |
| `resolved` | Recommendation has been resolved |

### Update Reason Codes
| Code | Description |
|------|-------------|
| `non_critical_account` | Non-critical account |
| `temporary_account` | Temporary account |
| `valid_business_case` | Valid business case |
| `other_methods_available` | Other methods available |
| `low_priority` | Low priority |
| `not_applicable` | Not applicable |
| `other` | Other reason |

### Recommendation Sources
| Source | Description |
|--------|-------------|
| `aws_config` | AWS Config |
| `compute_optimizer` | Compute Optimizer |
| `cost_explorer` | Cost Explorer |
| `lse` | License recommendations |
| `manual` | Manual check |
| `pse` | Proactive Support Engineering |
| `rds` | RDS recommendations |
| `resilience` | Resilience recommendations |
| `resilience_hub` | Resilience Hub |
| `security_hub` | Security Hub |
| `stir` | Service Team Internal Review |
| `ta_check` | Trusted Advisor check |
| `well_architected` | Well-Architected review |

### Support Case Statuses
| Status | Description |
|--------|-------------|
| `all-open` | All open cases |
| `customer-action-completed` | Customer action completed |
| `opened` | Case opened |
| `pending-customer-action` | Pending customer action |
| `reopened` | Case reopened |
| `resolved` | Case resolved |
| `unassigned` | Case unassigned |
| `work-in-progress` | Work in progress |

### Important Notes
- The `aws support` Trusted Advisor commands must use the **US East (N. Virginia)** region (`us-east-1`).
- Both APIs require a **Business, Enterprise On-Ramp, or Enterprise Support plan**.
- The `aws trustedadvisor` API is the newer interface; `aws support describe-trusted-advisor-*` commands provide the classic interface.
