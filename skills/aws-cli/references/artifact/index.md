# AWS CLI v2 -- Artifact (artifact) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/artifact/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `list-reports` | Report | List all available compliance reports |
| `get-report-metadata` | Report | Get metadata for a specific report |
| `get-report` | Report | Download a compliance report |
| `get-term-for-report` | Report | Get terms and token for a report |
| `list-report-versions` | Report | List all versions of a report |
| `list-customer-agreements` | Agreement | List customer agreements |
| `get-account-settings` | Settings | Get account settings |
| `put-account-settings` | Settings | Update account settings |

---

## Global Options

These options are available on ALL `aws artifact` commands.

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

### Report States
| State | Description |
|-------|-------------|
| `PUBLISHED` | Report is published and available |
| `UNPUBLISHED` | Report is not yet published |

### Report Upload States
| State | Description |
|-------|-------------|
| `PROCESSING` | Report is being processed |
| `COMPLETE` | Report upload is complete |
| `FAILED` | Report upload failed |
| `FAULT` | Report upload encountered a fault |

### Acceptance Types
| Type | Description |
|------|-------------|
| `PASSTHROUGH` | No explicit acceptance required |
| `EXPLICIT` | Explicit acceptance of terms required |

### Agreement States
| State | Description |
|-------|-------------|
| `ACTIVE` | Agreement is active |
| `CUSTOMER_TERMINATED` | Customer terminated the agreement |
| `AWS_TERMINATED` | AWS terminated the agreement |

### Agreement Types
| Type | Description |
|------|-------------|
| `CUSTOM` | Custom agreement |
| `DEFAULT` | Default agreement |
| `MODIFIED` | Modified agreement |

### Notification Subscription Statuses
| Status | Description |
|--------|-------------|
| `SUBSCRIBED` | Account is subscribed to notifications |
| `NOT_SUBSCRIBED` | Account is not subscribed to notifications |

### Report ID Format
Report IDs follow the pattern `report-[a-zA-Z0-9]{16}` (e.g., `report-abc123def456gh78`).

### Downloading Reports
To download a report, you must first call `get-term-for-report` to obtain a `termToken`, then use that token with `get-report`. The `get-report` response includes a presigned S3 URL to access the report document.
