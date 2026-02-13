# AWS CLI v2 -- Cost and Usage Report Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/cur/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `put-report-definition` | Reports | Create a new Cost and Usage Report definition |
| `delete-report-definition` | Reports | Delete a report definition |
| `describe-report-definitions` | Reports | List all report definitions in the account |
| `modify-report-definition` | Reports | Modify an existing report definition |
| `tag-resource` | Tags | Add tags to a CUR resource |
| `untag-resource` | Tags | Remove tags from a CUR resource |
| `list-tags-for-resource` | Tags | List tags for a CUR resource |

---

## Global Options

These options are available on ALL `aws cur` commands.

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

### Report Formats
| Format | Compression | Use Case |
|--------|-------------|----------|
| `textORcsv` | `ZIP` or `GZIP` | General CSV-based analysis |
| `Parquet` | `Parquet` | Athena, Redshift Spectrum, columnar analytics |

### Time Units
| Value | Description |
|-------|-------------|
| `HOURLY` | Hourly granularity |
| `DAILY` | Daily granularity |
| `MONTHLY` | Monthly granularity |

### Additional Artifacts
| Artifact | Description |
|----------|-------------|
| `REDSHIFT` | Manifest for Amazon Redshift COPY |
| `QUICKSIGHT` | Manifest for Amazon QuickSight |
| `ATHENA` | Manifest for Amazon Athena integration |

### Report Status Values
| Status | Description |
|--------|-------------|
| `SUCCESS` | Last delivery was successful |
| `ERROR_PERMISSIONS` | S3 bucket permission error |
| `ERROR_NO_BUCKET` | S3 bucket does not exist |

### Region Requirement
CUR API operations must be called from `us-east-1` region.
