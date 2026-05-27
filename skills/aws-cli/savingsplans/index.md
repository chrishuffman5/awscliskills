# AWS CLI v2 -- Savings Plans Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/savingsplans/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-savings-plan` | Savings Plans | Purchase a new Savings Plan |
| `delete-queued-savings-plan` | Savings Plans | Delete a queued (not yet active) Savings Plan |
| `describe-savings-plans` | Savings Plans | Describe your Savings Plans |
| `describe-savings-plan-rates` | Savings Plans | Describe the rates for a Savings Plan |
| `return-savings-plan` | Savings Plans | Return a Savings Plan (within return window) |
| `describe-savings-plans-offerings` | Offerings | Browse available Savings Plans offerings |
| `describe-savings-plans-offering-rates` | Offerings | Browse offering rates for a specific offering |
| `tag-resource` | Tags | Add tags to a Savings Plans resource |
| `untag-resource` | Tags | Remove tags from a Savings Plans resource |
| `list-tags-for-resource` | Tags | List tags for a Savings Plans resource |

---

## Global Options

These options are available on ALL `aws savingsplans` commands.

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

### Savings Plan Types
| Type | Description |
|------|-------------|
| `Compute` | Flexible across EC2, Fargate, and Lambda |
| `EC2Instance` | Specific to EC2 instance family and region |
| `SageMaker` | Specific to SageMaker usage |
| `Database` | Specific to RDS, DynamoDB, ElastiCache, and other database services |

### Payment Options
| Option | Description |
|--------|-------------|
| `All Upfront` | Full payment at purchase |
| `Partial Upfront` | Partial payment at purchase, rest billed hourly |
| `No Upfront` | No upfront payment, full hourly billing at discounted rate |

### Plan States
| State | Description |
|-------|-------------|
| `payment-pending` | Payment is being processed |
| `payment-failed` | Payment failed |
| `active` | Plan is active and providing discounts |
| `retired` | Plan has expired |
| `queued` | Plan is scheduled to start in the future |
| `queued-deleted` | Queued plan was deleted before activation |
| `pending-return` | Return has been requested |
| `returned` | Plan has been returned |

### Product Types
`EC2`, `Fargate`, `Lambda`, `SageMaker`, `RDS`, `DSQL`, `DynamoDB`, `ElastiCache`, `DocDB`, `Neptune`, `Timestream`, `Keyspaces`, `DMS`
