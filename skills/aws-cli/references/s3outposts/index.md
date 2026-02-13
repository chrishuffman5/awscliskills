# AWS CLI v2 -- S3 Outposts Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/s3outposts/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-endpoint` | Endpoint | Create an S3 on Outposts endpoint |
| `delete-endpoint` | Endpoint | Delete an S3 on Outposts endpoint |
| `list-endpoints` | Endpoint | List S3 on Outposts endpoints |
| `list-outposts-with-s3` | Endpoint | List Outposts that have S3 provisioned |
| `list-shared-endpoints` | Endpoint | List shared S3 on Outposts endpoints |

---

## Global Options

These options are available on ALL `aws s3outposts` commands.

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
| `--cli-binary-format` | string | `base64` | Format for binary blob input: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from a JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from a YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton: `input`, `yaml-input`, `output` |

---

## Common Patterns

### Endpoint Status Values
| Status | Description |
|--------|-------------|
| `Pending` | Endpoint is being created |
| `Available` | Endpoint is ready for use |
| `Deleting` | Endpoint is being deleted |
| `Create_Failed` | Endpoint creation failed |
| `Delete_Failed` | Endpoint deletion failed |

### Access Types
| Type | Description |
|------|-------------|
| `Private` | VPC connectivity (default) |
| `CustomerOwnedIp` | On-premises network access using customer-owned IP pool |
