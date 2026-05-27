# AWS CLI v2 -- CloudWatch Network Monitor Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/networkmonitor/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-monitor` | Monitor | Create a new CloudWatch Network Monitor |
| `get-monitor` | Monitor | Get details about a specific monitor |
| `update-monitor` | Monitor | Update an existing monitor |
| `delete-monitor` | Monitor | Delete a CloudWatch Network Monitor |
| `list-monitors` | Monitor | List all CloudWatch Network Monitors |
| `create-probe` | Probe | Create a probe within an existing monitor |
| `get-probe` | Probe | Get details about a specific probe |
| `update-probe` | Probe | Update an existing probe |
| `delete-probe` | Probe | Delete a probe from a monitor |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws networkmonitor` commands.

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

### Monitor State Values
| State | Description |
|-------|-------------|
| `PENDING` | Monitor is being created or updated |
| `ACTIVE` | Monitor is active and collecting data |
| `INACTIVE` | Monitor is paused |
| `ERROR` | Monitor encountered an error |
| `DELETING` | Monitor is being deleted |

### Probe State Values
| State | Description |
|-------|-------------|
| `PENDING` | Probe is being created (transitions to ACTIVE in minutes) |
| `ACTIVE` | Probe is actively monitoring |
| `INACTIVE` | Probe is paused |
| `ERROR` | Probe encountered an error |
| `DELETING` | Probe is being deleted |
| `DELETED` | Probe has been deleted |

### Protocol Values
| Protocol | Description |
|----------|-------------|
| `TCP` | TCP connectivity test (requires `destinationPort`) |
| `ICMP` | ICMP ping test (no port required) |

### Aggregation Period
| Value | Description |
|-------|-------------|
| `30` | Metrics aggregated every 30 seconds |
| `60` | Metrics aggregated every 60 seconds (default) |
