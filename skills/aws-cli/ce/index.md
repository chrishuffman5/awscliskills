# AWS CLI v2 -- Cost Explorer Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/ce/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `get-cost-and-usage` | Cost & Usage | Retrieve cost and usage metrics with filtering and grouping |
| `get-cost-and-usage-with-resources` | Cost & Usage | Retrieve cost and usage with resource-level detail (last 14 days) |
| `get-cost-and-usage-comparisons` | Cost & Usage | Compare cost and usage across time periods |
| `get-cost-comparison-drivers` | Cost & Usage | Identify drivers of cost differences between periods |
| `get-cost-forecast` | Cost & Usage | Forecast future costs based on historical data |
| `get-usage-forecast` | Cost & Usage | Forecast future usage based on historical data |
| `get-dimension-values` | Cost & Usage | Retrieve available filter dimension values |
| `get-tags` | Cost & Usage | Query available tag keys and values for cost filtering |
| `get-approximate-usage-records` | Cost & Usage | Get approximate count of usage records |
| `create-cost-category-definition` | Cost Categories | Create a cost category with rules |
| `delete-cost-category-definition` | Cost Categories | Delete a cost category |
| `describe-cost-category-definition` | Cost Categories | Describe a cost category definition |
| `update-cost-category-definition` | Cost Categories | Update a cost category definition |
| `get-cost-categories` | Cost Categories | Retrieve cost category names and values |
| `list-cost-category-definitions` | Cost Categories | List all cost category definitions |
| `list-cost-category-resource-associations` | Cost Categories | List resource associations for a cost category |
| `create-anomaly-monitor` | Anomalies | Create a cost anomaly detection monitor |
| `delete-anomaly-monitor` | Anomalies | Delete a cost anomaly monitor |
| `get-anomaly-monitors` | Anomalies | Retrieve anomaly monitors |
| `update-anomaly-monitor` | Anomalies | Update an anomaly monitor |
| `create-anomaly-subscription` | Anomalies | Create an anomaly notification subscription |
| `delete-anomaly-subscription` | Anomalies | Delete an anomaly subscription |
| `get-anomaly-subscriptions` | Anomalies | Retrieve anomaly subscriptions |
| `update-anomaly-subscription` | Anomalies | Update an anomaly subscription |
| `get-anomalies` | Anomalies | Retrieve cost anomalies with filtering |
| `provide-anomaly-feedback` | Anomalies | Provide feedback on an anomaly (YES/NO/PLANNED_ACTIVITY) |
| `get-reservation-coverage` | Reservations | Retrieve reservation coverage data |
| `get-reservation-purchase-recommendation` | Reservations | Get reservation purchase recommendations |
| `get-reservation-utilization` | Reservations | Retrieve reservation utilization data |
| `get-savings-plans-coverage` | Savings Plans | Retrieve Savings Plans coverage data |
| `get-savings-plans-purchase-recommendation` | Savings Plans | Get Savings Plans purchase recommendations |
| `get-savings-plans-utilization` | Savings Plans | Retrieve Savings Plans utilization data |
| `get-savings-plans-utilization-details` | Savings Plans | Retrieve detailed Savings Plans utilization |
| `get-savings-plan-purchase-recommendation-details` | Savings Plans | Get details of a specific recommendation |
| `list-savings-plans-purchase-recommendation-generation` | Savings Plans | List recommendation generation jobs |
| `start-savings-plans-purchase-recommendation-generation` | Savings Plans | Start a recommendation generation job |
| `get-rightsizing-recommendation` | Rightsizing | Get EC2 rightsizing recommendations |
| `start-commitment-purchase-analysis` | Commitment Analysis | Start a commitment purchase analysis |
| `get-commitment-purchase-analysis` | Commitment Analysis | Get results of a commitment analysis |
| `list-commitment-purchase-analyses` | Commitment Analysis | List commitment purchase analyses |
| `list-cost-allocation-tags` | Cost Allocation Tags | List cost allocation tags |
| `update-cost-allocation-tags-status` | Cost Allocation Tags | Activate or deactivate cost allocation tags |
| `list-cost-allocation-tag-backfill-history` | Cost Allocation Tags | List tag backfill history |
| `start-cost-allocation-tag-backfill` | Cost Allocation Tags | Start a tag backfill job |
| `tag-resource` | Tags | Add tags to a Cost Explorer resource |
| `untag-resource` | Tags | Remove tags from a Cost Explorer resource |
| `list-tags-for-resource` | Tags | List tags for a Cost Explorer resource |

---

## Global Options

These options are available on ALL `aws ce` commands.

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

### Time Period Structure
All time-based queries use a `TimePeriod` structure:
```json
{
    "Start": "YYYY-MM-DD",
    "End": "YYYY-MM-DD"
}
```
Shorthand: `Start=2025-01-01,End=2025-02-01`

- Start date is **inclusive**, end date is **exclusive**
- Dates use `YYYY-MM-DD` or `YYYY-MM-DDTHH:MM:SSZ` format

### Filter Expression Structure
Many commands accept a `--filter` parameter using the Expression structure:
```json
{
    "Dimensions": {
        "Key": "SERVICE",
        "Values": ["Amazon Elastic Compute Cloud - Compute"],
        "MatchOptions": ["EQUALS"]
    }
}
```

Supports logical operators: `And`, `Or`, `Not` for complex filtering.

### Granularity Values
| Value | Description |
|-------|-------------|
| `DAILY` | Daily granularity |
| `MONTHLY` | Monthly granularity |
| `HOURLY` | Hourly granularity (limited availability) |

### Cost Metrics
| Metric | Description |
|--------|-------------|
| `AmortizedCost` | Cost with upfront payments spread across usage period |
| `BlendedCost` | Average rate across consolidated billing family |
| `NetAmortizedCost` | Amortized cost after discounts |
| `NetUnblendedCost` | Unblended cost after discounts |
| `NormalizedUsageAmount` | Usage normalized to instance-hour equivalents |
| `UnblendedCost` | Actual charges incurred |
| `UsageQuantity` | Amount of usage |

### Dimension Keys
Common dimension keys for filtering and grouping:
`AZ`, `INSTANCE_TYPE`, `LINKED_ACCOUNT`, `OPERATION`, `PURCHASE_TYPE`, `REGION`, `SERVICE`, `SERVICE_CODE`, `USAGE_TYPE`, `USAGE_TYPE_GROUP`, `RECORD_TYPE`, `OPERATING_SYSTEM`, `TENANCY`, `PLATFORM`, `DATABASE_ENGINE`, `INSTANCE_TYPE_FAMILY`, `BILLING_ENTITY`, `RESERVATION_ID`, `RESOURCE_ID`, `SAVINGS_PLAN_ARN`
