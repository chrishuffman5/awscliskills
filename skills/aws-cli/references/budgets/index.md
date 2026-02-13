# AWS CLI v2 -- Budgets Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/budgets/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-budget` | Budgets | Create a new budget with optional notifications |
| `delete-budget` | Budgets | Delete a budget and its notifications/subscribers |
| `describe-budget` | Budgets | Describe a single budget |
| `describe-budgets` | Budgets | List all budgets for an account |
| `update-budget` | Budgets | Update an existing budget |
| `describe-budget-performance-history` | Budgets | Get budget performance history over time |
| `create-budget-action` | Budget Actions | Create an auto-remediation action for a budget |
| `delete-budget-action` | Budget Actions | Delete a budget action |
| `describe-budget-action` | Budget Actions | Describe a specific budget action |
| `update-budget-action` | Budget Actions | Update a budget action |
| `execute-budget-action` | Budget Actions | Manually execute a budget action |
| `describe-budget-action-histories` | Budget Actions | Describe action execution history |
| `describe-budget-actions-for-account` | Budget Actions | List all budget actions for an account |
| `describe-budget-actions-for-budget` | Budget Actions | List all actions for a specific budget |
| `create-notification` | Notifications | Add a notification to a budget |
| `delete-notification` | Notifications | Remove a notification from a budget |
| `update-notification` | Notifications | Update a budget notification |
| `describe-notifications-for-budget` | Notifications | List notifications for a budget |
| `describe-budget-notifications-for-account` | Notifications | List all budget notifications for an account |
| `create-subscriber` | Subscribers | Add a subscriber to a notification |
| `delete-subscriber` | Subscribers | Remove a subscriber from a notification |
| `update-subscriber` | Subscribers | Replace a subscriber on a notification |
| `describe-subscribers-for-notification` | Subscribers | List subscribers for a notification |
| `tag-resource` | Tags | Add tags to a budget resource |
| `untag-resource` | Tags | Remove tags from a budget resource |
| `list-tags-for-resource` | Tags | List tags for a budget resource |

---

## Global Options

These options are available on ALL `aws budgets` commands.

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

### Budget Types
| Type | Description |
|------|-------------|
| `COST` | Track spending against a dollar amount |
| `USAGE` | Track usage quantity |
| `RI_UTILIZATION` | Track Reserved Instance utilization percentage |
| `RI_COVERAGE` | Track Reserved Instance coverage percentage |
| `SAVINGS_PLANS_UTILIZATION` | Track Savings Plans utilization percentage |
| `SAVINGS_PLANS_COVERAGE` | Track Savings Plans coverage percentage |

### Time Units
| Value | Description |
|-------|-------------|
| `DAILY` | Budget resets daily |
| `MONTHLY` | Budget resets monthly |
| `QUARTERLY` | Budget resets quarterly |
| `ANNUALLY` | Budget resets annually |
| `CUSTOM` | Custom time period (no auto-reset) |

### Action Types
| Type | Description |
|------|-------------|
| `APPLY_IAM_POLICY` | Attach an IAM policy to users, roles, or groups |
| `APPLY_SCP_POLICY` | Apply a Service Control Policy to OUs or accounts |
| `RUN_SSM_DOCUMENTS` | Run SSM documents to stop EC2 or RDS instances |

### Account ID
All `aws budgets` commands require `--account-id` (12-digit AWS account ID).
