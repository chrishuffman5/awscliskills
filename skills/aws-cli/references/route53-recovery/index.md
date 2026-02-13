# AWS CLI v2 -- Route 53 Application Recovery Controller Command Reference Index

> Based on AWS CLI v2 documentation. Sources:
> - https://docs.aws.amazon.com/cli/latest/reference/route53-recovery-cluster/
> - https://docs.aws.amazon.com/cli/latest/reference/route53-recovery-control-config/
> - https://docs.aws.amazon.com/cli/latest/reference/route53-recovery-readiness/

---

## Quick Reference

### route53-recovery-cluster (Data Plane)

| Command | Description |
|---------|-------------|
| `get-routing-control-state` | Get the current state (On/Off) of a routing control |
| `list-routing-controls` | List routing controls in a cluster or control panel |
| `update-routing-control-state` | Update the state of a single routing control |
| `update-routing-control-states` | Update the state of multiple routing controls in a batch |

### route53-recovery-control-config (Control Plane)

| Command | Category | Description |
|---------|----------|-------------|
| `create-cluster` | Cluster | Create a new recovery cluster |
| `delete-cluster` | Cluster | Delete a recovery cluster |
| `describe-cluster` | Cluster | Get details about a cluster |
| `list-clusters` | Cluster | List all recovery clusters |
| `update-cluster` | Cluster | Update cluster configuration |
| `create-control-panel` | Control Panel | Create a control panel in a cluster |
| `delete-control-panel` | Control Panel | Delete a control panel |
| `describe-control-panel` | Control Panel | Get details about a control panel |
| `list-control-panels` | Control Panel | List control panels |
| `update-control-panel` | Control Panel | Update a control panel |
| `create-routing-control` | Routing Control | Create a routing control in a cluster |
| `delete-routing-control` | Routing Control | Delete a routing control |
| `describe-routing-control` | Routing Control | Get details about a routing control |
| `list-routing-controls` | Routing Control | List routing controls in a control panel |
| `update-routing-control` | Routing Control | Update a routing control |
| `create-safety-rule` | Safety Rule | Create an assertion or gating safety rule |
| `delete-safety-rule` | Safety Rule | Delete a safety rule |
| `describe-safety-rule` | Safety Rule | Get details about a safety rule |
| `list-safety-rules` | Safety Rule | List safety rules for a control panel |
| `update-safety-rule` | Safety Rule | Update a safety rule |
| `list-associated-route53-health-checks` | Routing Control | List Route 53 health checks for a routing control |
| `get-resource-policy` | Resource Policy | Get the resource policy for a cluster |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |
| `wait cluster-created` | Wait | Wait until a cluster is created |
| `wait cluster-deleted` | Wait | Wait until a cluster is deleted |
| `wait control-panel-created` | Wait | Wait until a control panel is created |
| `wait control-panel-deleted` | Wait | Wait until a control panel is deleted |
| `wait routing-control-created` | Wait | Wait until a routing control is created |
| `wait routing-control-deleted` | Wait | Wait until a routing control is deleted |

### route53-recovery-readiness

| Command | Category | Description |
|---------|----------|-------------|
| `create-cell` | Cell | Create a readiness cell |
| `get-cell` | Cell | Get cell details |
| `update-cell` | Cell | Update a cell |
| `delete-cell` | Cell | Delete a cell |
| `list-cells` | Cell | List all cells |
| `get-cell-readiness-summary` | Cell | Get readiness summary for a cell |
| `create-readiness-check` | Readiness Check | Create a readiness check |
| `get-readiness-check` | Readiness Check | Get readiness check details |
| `update-readiness-check` | Readiness Check | Update a readiness check |
| `delete-readiness-check` | Readiness Check | Delete a readiness check |
| `list-readiness-checks` | Readiness Check | List all readiness checks |
| `get-readiness-check-status` | Readiness Check | Get readiness check status |
| `get-readiness-check-resource-status` | Readiness Check | Get resource-specific readiness status |
| `create-recovery-group` | Recovery Group | Create a recovery group |
| `get-recovery-group` | Recovery Group | Get recovery group details |
| `update-recovery-group` | Recovery Group | Update a recovery group |
| `delete-recovery-group` | Recovery Group | Delete a recovery group |
| `list-recovery-groups` | Recovery Group | List all recovery groups |
| `get-recovery-group-readiness-summary` | Recovery Group | Get readiness summary for a recovery group |
| `get-architecture-recommendations` | Recovery Group | Get architecture improvement recommendations |
| `create-resource-set` | Resource Set | Create a resource set |
| `get-resource-set` | Resource Set | Get resource set details |
| `update-resource-set` | Resource Set | Update a resource set |
| `delete-resource-set` | Resource Set | Delete a resource set |
| `list-resource-sets` | Resource Set | List all resource sets |
| `list-rules` | Resource Set | List readiness rules |
| `create-cross-account-authorization` | Cross-Account | Create cross-account authorization |
| `delete-cross-account-authorization` | Cross-Account | Delete cross-account authorization |
| `list-cross-account-authorizations` | Cross-Account | List cross-account authorizations |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resources` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL Route 53 Recovery commands.

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

### Resource Status Values
| Status | Description |
|--------|-------------|
| `PENDING` | Resource is being created |
| `DEPLOYED` | Resource is active and deployed |
| `PENDING_DELETION` | Resource is being deleted |

### Routing Control States
| State | Description |
|-------|-------------|
| `On` | Traffic flows to the associated cell/endpoint |
| `Off` | Traffic does not flow to the associated cell/endpoint |

### Readiness Statuses
| Status | Description |
|--------|-------------|
| `READY` | Resource passes all readiness rules |
| `NOT_READY` | Resource fails one or more readiness rules |
| `UNKNOWN` | Readiness status cannot be determined |
| `NOT_AUTHORIZED` | Insufficient permissions to check readiness |

### Safety Rule Types
| Type | Description |
|------|-------------|
| `ATLEAST` | At least N routing controls must be in the specified state |
| `AND` | All routing controls must be in the specified state |
| `OR` | At least one routing control must be in the specified state |

### Regional Endpoint Requirement
Route 53 ARC data plane operations (`route53-recovery-cluster`) require specifying a Regional cluster endpoint. The cluster provides 5 redundant Regional endpoints for high availability.
