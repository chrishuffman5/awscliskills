# AWS CLI v2 -- Outposts Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/outposts/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-outpost` | Outpost | Create a new Outpost |
| `get-outpost` | Outpost | Get information about an Outpost |
| `list-outposts` | Outpost | List all Outposts in an account |
| `update-outpost` | Outpost | Update Outpost properties |
| `delete-outpost` | Outpost | Delete an Outpost |
| `get-outpost-instance-types` | Outpost | List instance types for an Outpost |
| `get-outpost-supported-instance-types` | Outpost | List supported instance types for an Outpost order |
| `create-site` | Site | Create a new site |
| `get-site` | Site | Get information about a site |
| `list-sites` | Site | List all sites in an account |
| `update-site` | Site | Update site properties |
| `delete-site` | Site | Delete a site |
| `get-site-address` | Site | Get the site address |
| `update-site-address` | Site | Update the site address |
| `update-site-rack-physical-properties` | Site | Update rack physical properties |
| `create-order` | Order | Create an order for an Outpost |
| `get-order` | Order | Get order details |
| `list-orders` | Order | List all orders |
| `start-capacity-task` | Capacity | Start a capacity task on an Outpost |
| `get-capacity-task` | Capacity | Get capacity task details |
| `list-capacity-tasks` | Capacity | List capacity tasks |
| `cancel-capacity-task` | Capacity | Cancel a capacity task |
| `list-assets` | Asset | List assets on an Outpost |
| `start-connection` | Connection | Start a connection to an Outpost |
| `get-connection` | Connection | Get connection details |
| `list-catalog-items` | Catalog | List available catalog items |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws outposts` commands.

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

### Outpost Lifecycle Statuses
| Status | Description |
|--------|-------------|
| `ACTIVE` | Outpost is operational |
| `INSTALLING` | Outpost hardware is being installed |
| `PENDING` | Outpost order is being processed |
| `DECOMMISSIONING` | Outpost is being decommissioned |
| `ISOLATED` | Outpost has lost connection to the parent Region |

### Payment Options
| Option | Description |
|--------|-------------|
| `ALL_UPFRONT` | Pay the entire amount upfront |
| `NO_UPFRONT` | No upfront payment, pay monthly |
| `PARTIAL_UPFRONT` | Partial upfront payment with monthly payments |

### Payment Terms
| Term | Description |
|------|-------------|
| `THREE_YEARS` | Three-year term commitment |
| `ONE_YEAR` | One-year term commitment |

### Capacity Task Statuses
| Status | Description |
|--------|-------------|
| `REQUESTED` | Task has been requested |
| `IN_PROGRESS` | Task is being executed |
| `COMPLETED` | Task completed successfully |
| `FAILED` | Task failed |
| `CANCELLED` | Task was cancelled |
| `WAITING_FOR_EVACUATION` | Waiting for instances to evacuate |

### Asset Types
| Type | Description |
|------|-------------|
| `COMPUTE` | Compute asset (server) |

### Address Type Values
| Type | Description |
|------|-------------|
| `SHIPPING_ADDRESS` | Shipping address for delivery |
| `OPERATING_ADDRESS` | Operating address of the site |
