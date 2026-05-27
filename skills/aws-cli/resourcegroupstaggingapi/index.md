# AWS CLI v2 -- Resource Groups Tagging API Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/resourcegroupstaggingapi/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `get-resources` | Tagging | Get resources matching tag filters and resource type filters |
| `get-tag-keys` | Tagging | List all tag keys in the account/region |
| `get-tag-values` | Tagging | List all values for a specific tag key |
| `tag-resources` | Tagging | Add tags to one or more resources |
| `untag-resources` | Tagging | Remove tags from one or more resources |
| `get-compliance-summary` | Compliance | Get summary of tag compliance for resources |
| `start-report-creation` | Compliance | Generate a tag compliance report to S3 |
| `describe-report-creation` | Compliance | Check status of a tag compliance report |

---

## Global Options

These options are available on ALL `aws resourcegroupstaggingapi` commands.

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

### Tag Filter Structure

Tag filters narrow `get-resources` results to resources with specific tags:

```json
{
    "Key": "string",
    "Values": ["string"]
}
```

- If `Values` is empty, matches any resource with the given key regardless of value
- Multiple tag filters use AND logic (resource must match all filters)
- Multiple values within a filter use OR logic (resource must have at least one of the values)

### Resource Type Filters

Resource type strings follow the format `service:resourcetype`:

| Example | Description |
|---------|-------------|
| `ec2:instance` | EC2 instances |
| `ec2:volume` | EBS volumes |
| `s3` | S3 buckets |
| `rds:db` | RDS DB instances |
| `lambda:function` | Lambda functions |
| `ecs:cluster` | ECS clusters |

Specifying just the service name (e.g., `s3`) returns all resource types for that service.

### Compliance Status Values

| Status | Description |
|--------|-------------|
| `COMPLIANT` | Resource has all required tags |
| `NON_COMPLIANT` | Resource is missing one or more required tags |

### Pagination

All list/get operations that return multiple items support pagination:
- `--starting-token`: Token from previous response to continue pagination
- `--page-size`: Number of items per API call
- `--max-items`: Maximum total items to return
