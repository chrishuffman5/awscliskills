# AWS CLI v2 -- Global Accelerator Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/globalaccelerator/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-accelerator` | Accelerator | Create a standard accelerator |
| `delete-accelerator` | Accelerator | Delete an accelerator (must be disabled first) |
| `describe-accelerator` | Accelerator | Get accelerator details |
| `list-accelerators` | Accelerator | List all standard accelerators |
| `update-accelerator` | Accelerator | Update accelerator settings |
| `describe-accelerator-attributes` | Accelerator | Get accelerator attributes (flow logs) |
| `update-accelerator-attributes` | Accelerator | Update accelerator attributes (flow logs) |
| `create-listener` | Listener | Create a listener for an accelerator |
| `delete-listener` | Listener | Delete a listener |
| `describe-listener` | Listener | Get listener details |
| `list-listeners` | Listener | List listeners for an accelerator |
| `update-listener` | Listener | Update listener settings |
| `create-endpoint-group` | Endpoint Group | Create an endpoint group for a listener |
| `delete-endpoint-group` | Endpoint Group | Delete an endpoint group |
| `describe-endpoint-group` | Endpoint Group | Get endpoint group details |
| `list-endpoint-groups` | Endpoint Group | List endpoint groups for a listener |
| `update-endpoint-group` | Endpoint Group | Update endpoint group settings |
| `add-endpoints` | Endpoint Group | Add endpoints to an endpoint group |
| `remove-endpoints` | Endpoint Group | Remove endpoints from an endpoint group |
| `create-custom-routing-accelerator` | Custom Routing | Create a custom routing accelerator |
| `delete-custom-routing-accelerator` | Custom Routing | Delete a custom routing accelerator |
| `describe-custom-routing-accelerator` | Custom Routing | Get custom routing accelerator details |
| `list-custom-routing-accelerators` | Custom Routing | List custom routing accelerators |
| `update-custom-routing-accelerator` | Custom Routing | Update custom routing accelerator |
| `describe-custom-routing-accelerator-attributes` | Custom Routing | Get custom routing accelerator attributes |
| `update-custom-routing-accelerator-attributes` | Custom Routing | Update custom routing accelerator attributes |
| `create-custom-routing-listener` | Custom Routing | Create a custom routing listener |
| `delete-custom-routing-listener` | Custom Routing | Delete a custom routing listener |
| `describe-custom-routing-listener` | Custom Routing | Get custom routing listener details |
| `list-custom-routing-listeners` | Custom Routing | List custom routing listeners |
| `update-custom-routing-listener` | Custom Routing | Update a custom routing listener |
| `create-custom-routing-endpoint-group` | Custom Routing | Create a custom routing endpoint group |
| `delete-custom-routing-endpoint-group` | Custom Routing | Delete a custom routing endpoint group |
| `describe-custom-routing-endpoint-group` | Custom Routing | Get custom routing endpoint group details |
| `list-custom-routing-endpoint-groups` | Custom Routing | List custom routing endpoint groups |
| `add-custom-routing-endpoints` | Custom Routing | Add VPC subnet endpoints |
| `remove-custom-routing-endpoints` | Custom Routing | Remove VPC subnet endpoints |
| `allow-custom-routing-traffic` | Custom Routing | Allow traffic to specific destinations |
| `deny-custom-routing-traffic` | Custom Routing | Deny traffic to specific destinations |
| `list-custom-routing-port-mappings` | Custom Routing | List port mappings for an accelerator |
| `list-custom-routing-port-mappings-by-destination` | Custom Routing | List port mappings by destination |
| `create-cross-account-attachment` | Cross-Account | Create cross-account resource attachment |
| `delete-cross-account-attachment` | Cross-Account | Delete cross-account attachment |
| `describe-cross-account-attachment` | Cross-Account | Get cross-account attachment details |
| `list-cross-account-attachments` | Cross-Account | List cross-account attachments |
| `update-cross-account-attachment` | Cross-Account | Update cross-account attachment |
| `list-cross-account-resource-accounts` | Cross-Account | List accounts with cross-account resources |
| `list-cross-account-resources` | Cross-Account | List cross-account resources |
| `provision-byoip-cidr` | BYOIP | Provision a BYOIP address range |
| `deprovision-byoip-cidr` | BYOIP | Deprovision a BYOIP address range |
| `advertise-byoip-cidr` | BYOIP | Start advertising a BYOIP address range |
| `withdraw-byoip-cidr` | BYOIP | Stop advertising a BYOIP address range |
| `list-byoip-cidrs` | BYOIP | List BYOIP address ranges |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws globalaccelerator` commands.

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `--debug` | boolean | false | Enable debug logging to stderr |
| `--endpoint-url` | string | -- | Override the default service endpoint URL |
| `--no-verify-ssl` | boolean | false | Disable SSL certificate verification |
| `--no-paginate` | boolean | false | Disable automatic pagination |
| `--output` | string | `json` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | -- | JMESPath query to filter output |
| `--profile` | string | `default` | Named AWS credential profile |
| `--region` | string | from config | AWS region (`us-west-2` required for accelerator operations) |
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

### Accelerator Status Values
| Status | Description |
|--------|-------------|
| `DEPLOYED` | Accelerator is fully deployed and operational |
| `IN_PROGRESS` | Accelerator is being created or updated |

### Endpoint Health States
| State | Description |
|-------|-------------|
| `INITIAL` | Endpoint health has not yet been determined |
| `HEALTHY` | Endpoint is healthy |
| `UNHEALTHY` | Endpoint is unhealthy |

### BYOIP CIDR States
| State | Description |
|-------|-------------|
| `PENDING_PROVISIONING` | CIDR is being provisioned |
| `READY` | CIDR is provisioned and ready to advertise |
| `PENDING_ADVERTISING` | CIDR is being advertised |
| `ADVERTISING` | CIDR is actively advertising |
| `PENDING_WITHDRAWING` | CIDR is being withdrawn |
| `PENDING_DEPROVISIONING` | CIDR is being deprovisioned |
| `DEPROVISIONED` | CIDR has been deprovisioned |
| `FAILED_PROVISION` | CIDR provisioning failed |
| `FAILED_ADVERTISING` | CIDR advertising failed |
| `FAILED_WITHDRAW` | CIDR withdrawal failed |
| `FAILED_DEPROVISION` | CIDR deprovisioning failed |

### Region Requirement
All Global Accelerator API calls must use `--region us-west-2`.
