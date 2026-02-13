# AWS CLI v2 -- Pricing Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/pricing/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `describe-services` | Pricing | List available services and their attribute names |
| `get-attribute-values` | Pricing | Get available values for a service attribute |
| `get-products` | Pricing | Query product pricing with filters |
| `list-price-lists` | Pricing | List available price list files |
| `get-price-list-file-url` | Pricing | Get URL to download a price list file |

---

## Global Options

These options are available on ALL `aws pricing` commands.

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

### Region Requirement
The Pricing API is available in `us-east-1` and `ap-south-1`. You must specify one of these regions.

### Filter Types
| Type | Description |
|------|-------------|
| `TERM_MATCH` | Exact match on field and value |
| `EQUALS` | Field value exactly equals provided value |
| `CONTAINS` | Field value contains provided value as substring |
| `ANY_OF` | Field value matches any of comma-separated values |
| `NONE_OF` | Field value does not match any of comma-separated values |

### Common Service Codes
| Code | Service |
|------|---------|
| `AmazonEC2` | Amazon EC2 |
| `AmazonS3` | Amazon S3 |
| `AmazonRDS` | Amazon RDS |
| `AmazonElastiCache` | Amazon ElastiCache |
| `AWSLambda` | AWS Lambda |
| `AmazonDynamoDB` | Amazon DynamoDB |
