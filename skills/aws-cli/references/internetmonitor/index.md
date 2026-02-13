# AWS CLI v2 -- Internet Monitor Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/internetmonitor/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-monitor` | Monitor | Create a new Internet Monitor |
| `get-monitor` | Monitor | Get information about a monitor |
| `update-monitor` | Monitor | Update an existing monitor |
| `delete-monitor` | Monitor | Delete an Internet Monitor |
| `list-monitors` | Monitor | List all monitors |
| `list-health-events` | Event | List health events for a monitor |
| `get-health-event` | Event | Get details of a specific health event |
| `list-internet-events` | Event | List global internet events |
| `get-internet-event` | Event | Get details of a specific internet event |
| `start-query` | Query | Start a query on Internet Monitor data |
| `get-query-results` | Query | Retrieve results from a query |
| `get-query-status` | Query | Check the status of a query |
| `stop-query` | Query | Stop a running query |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws internetmonitor` commands.

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

### Monitor Status Values
| Status | Description |
|--------|-------------|
| `PENDING` | Monitor is being created |
| `ACTIVE` | Monitor is active and collecting data |
| `INACTIVE` | Monitor is paused |
| `ERROR` | Monitor encountered an error |

### Health Event Impact Types
| Type | Description |
|------|-------------|
| `AVAILABILITY` | Availability impact on total traffic |
| `PERFORMANCE` | Performance impact on total traffic |
| `LOCAL_AVAILABILITY` | Availability impact on local traffic |
| `LOCAL_PERFORMANCE` | Performance impact on local traffic |

### Health Event Status Values
| Status | Description |
|--------|-------------|
| `ACTIVE` | Event is currently ongoing |
| `RESOLVED` | Event has been resolved |

### Query Types
| Type | Description |
|------|-------------|
| `MEASUREMENTS` | Availability, performance, traffic, RTT at 5-min intervals |
| `TOP_LOCATIONS` | Top location/ASN combinations by traffic |
| `TOP_LOCATION_DETAILS` | TTFB for CloudFront and EC2 at 1-hour intervals |
| `OVERALL_TRAFFIC_SUGGESTIONS` | TTFB using 30-day weighted average |
| `OVERALL_TRAFFIC_SUGGESTIONS_DETAILS` | TTFB for top locations in proposed AWS location |
| `ROUTING_SUGGESTIONS` | Predicted RTT from IP prefix to AWS location |
