# AWS CLI v2 -- Macie (macie2) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/macie2/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `enable-macie` | Session | Enable Amazon Macie |
| `disable-macie` | Session | Disable Amazon Macie |
| `get-macie-session` | Session | Get Macie session information |
| `update-macie-session` | Session | Update Macie session settings |
| `create-classification-job` | Classification Job | Create a data classification job |
| `describe-classification-job` | Classification Job | Get classification job details |
| `list-classification-jobs` | Classification Job | List classification jobs |
| `update-classification-job` | Classification Job | Update a classification job |
| `get-findings` | Finding | Retrieve findings |
| `list-findings` | Finding | List finding IDs |
| `get-finding-statistics` | Finding | Get finding statistics |
| `create-sample-findings` | Finding | Generate sample findings |
| `create-findings-filter` | Findings Filter | Create a findings filter |
| `delete-findings-filter` | Findings Filter | Delete a findings filter |
| `get-findings-filter` | Findings Filter | Get findings filter details |
| `list-findings-filters` | Findings Filter | List findings filters |
| `update-findings-filter` | Findings Filter | Update a findings filter |
| `get-findings-publication-configuration` | Findings Filter | Get publication configuration |
| `put-findings-publication-configuration` | Findings Filter | Set publication configuration |
| `create-allow-list` | Allow List | Create an allow list |
| `delete-allow-list` | Allow List | Delete an allow list |
| `get-allow-list` | Allow List | Get allow list details |
| `list-allow-lists` | Allow List | List all allow lists |
| `update-allow-list` | Allow List | Update an allow list |
| `create-custom-data-identifier` | Data Identifier | Create a custom data identifier |
| `delete-custom-data-identifier` | Data Identifier | Delete a custom data identifier |
| `get-custom-data-identifier` | Data Identifier | Get custom data identifier details |
| `list-custom-data-identifiers` | Data Identifier | List custom data identifiers |
| `batch-get-custom-data-identifiers` | Data Identifier | Batch get custom data identifiers |
| `list-managed-data-identifiers` | Data Identifier | List managed data identifiers |
| `test-custom-data-identifier` | Data Identifier | Test a custom data identifier |
| `describe-buckets` | Bucket | Describe S3 buckets analyzed by Macie |
| `get-bucket-statistics` | Bucket | Get S3 bucket statistics |
| `search-resources` | Bucket | Search Macie resources |
| `get-classification-export-configuration` | Bucket | Get classification export settings |
| `put-classification-export-configuration` | Bucket | Set classification export settings |
| `get-classification-scope` | Bucket | Get classification scope |
| `list-classification-scopes` | Bucket | List classification scopes |
| `update-classification-scope` | Bucket | Update classification scope |
| `get-automated-discovery-configuration` | Automated Discovery | Get automated discovery config |
| `update-automated-discovery-configuration` | Automated Discovery | Update automated discovery config |
| `list-automated-discovery-accounts` | Automated Discovery | List automated discovery accounts |
| `batch-update-automated-discovery-accounts` | Automated Discovery | Batch update discovery accounts |
| `get-resource-profile` | Resource Profile | Get resource profile information |
| `list-resource-profile-artifacts` | Resource Profile | List resource profile artifacts |
| `list-resource-profile-detections` | Resource Profile | List resource profile detections |
| `update-resource-profile` | Resource Profile | Update resource profile |
| `update-resource-profile-detections` | Resource Profile | Update resource profile detections |
| `get-reveal-configuration` | Sensitivity | Get reveal configuration |
| `update-reveal-configuration` | Sensitivity | Update reveal configuration |
| `get-sensitive-data-occurrences` | Sensitivity | Get sensitive data occurrences |
| `get-sensitive-data-occurrences-availability` | Sensitivity | Check data availability |
| `get-sensitivity-inspection-template` | Sensitivity | Get sensitivity inspection template |
| `list-sensitivity-inspection-templates` | Sensitivity | List sensitivity templates |
| `update-sensitivity-inspection-template` | Sensitivity | Update sensitivity template |
| `create-member` | Member | Create a member account |
| `delete-member` | Member | Delete a member account |
| `get-member` | Member | Get member account details |
| `list-members` | Member | List member accounts |
| `disassociate-member` | Member | Disassociate a member |
| `create-invitations` | Member | Send membership invitations |
| `accept-invitation` | Member | Accept membership invitation |
| `decline-invitations` | Member | Decline invitations |
| `delete-invitations` | Member | Delete invitations |
| `list-invitations` | Member | List invitations |
| `get-invitations-count` | Member | Get invitation count |
| `disassociate-from-administrator-account` | Member | Disassociate from administrator |
| `get-administrator-account` | Member | Get administrator account |
| `update-member-session` | Member | Update member session |
| `enable-organization-admin-account` | Organization | Enable org admin account |
| `disable-organization-admin-account` | Organization | Disable org admin account |
| `list-organization-admin-accounts` | Organization | List org admin accounts |
| `describe-organization-configuration` | Organization | Describe org configuration |
| `update-organization-configuration` | Organization | Update org configuration |
| `get-usage-statistics` | Usage | Get usage statistics |
| `get-usage-totals` | Usage | Get usage totals |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |
| `wait` | Wait | Wait for resource state changes |

---

## Global Options

These options are available on ALL `aws macie2` commands.

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

### Classification Job Types
| Type | Description |
|------|-------------|
| `ONE_TIME` | Analyzes specified objects once |
| `SCHEDULED` | Analyzes objects on a recurring schedule |

### Classification Job Statuses
| Status | Description |
|--------|-------------|
| `RUNNING` | Job is currently running |
| `PAUSED` | Job is paused |
| `CANCELLED` | Job has been cancelled |
| `COMPLETE` | Job has completed |
| `IDLE` | Scheduled job waiting for next run |
| `USER_PAUSED` | Job was paused by user |

### Finding Severity
| Severity | Score | Description |
|----------|-------|-------------|
| `Low` | 1 | Low severity finding |
| `Medium` | 2 | Medium severity finding |
| `High` | 3 | High severity finding |

### Finding Categories
| Category | Description |
|----------|-------------|
| `CLASSIFICATION` | Sensitive data was detected |
| `POLICY` | Policy violation was detected |

### Managed Data Identifier Categories
Common categories: `CREDENTIALS`, `FINANCIAL_INFORMATION`, `PERSONAL_INFORMATION`, `PERSONAL_HEALTH_INFORMATION`
