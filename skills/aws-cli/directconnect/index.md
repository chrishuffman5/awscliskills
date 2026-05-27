# AWS CLI v2 -- Direct Connect Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/directconnect/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `accept-direct-connect-gateway-association-proposal` | Gateway | Accept a gateway association proposal from another account |
| `allocate-hosted-connection` | Connection | Allocate a hosted connection on an interconnect or LAG |
| `allocate-private-virtual-interface` | Virtual Interface | Provision a private virtual interface for another account |
| `allocate-public-virtual-interface` | Virtual Interface | Provision a public virtual interface for another account |
| `allocate-transit-virtual-interface` | Virtual Interface | Provision a transit virtual interface for another account |
| `associate-connection-with-lag` | Connection | Associate an existing connection with a LAG |
| `associate-hosted-connection` | Connection | Associate a hosted connection with a LAG |
| `associate-mac-sec-key` | MACsec | Associate a MACsec key with a connection or LAG |
| `associate-virtual-interface` | Virtual Interface | Associate a virtual interface with an owner account |
| `confirm-connection` | Connection | Confirm a hosted connection creation |
| `confirm-customer-agreement` | Connection | Confirm the customer agreement |
| `confirm-private-virtual-interface` | Virtual Interface | Accept ownership of a private virtual interface |
| `confirm-public-virtual-interface` | Virtual Interface | Accept ownership of a public virtual interface |
| `confirm-transit-virtual-interface` | Virtual Interface | Accept ownership of a transit virtual interface |
| `create-bgp-peer` | BGP | Create a BGP peer on a virtual interface |
| `create-connection` | Connection | Create a dedicated connection |
| `create-direct-connect-gateway` | Gateway | Create a Direct Connect gateway |
| `create-direct-connect-gateway-association` | Gateway | Associate a gateway with a VGW or TGW |
| `create-direct-connect-gateway-association-proposal` | Gateway | Create a cross-account gateway association proposal |
| `create-interconnect` | Interconnect | Create an interconnect (partner only) |
| `create-lag` | LAG | Create a link aggregation group |
| `create-private-virtual-interface` | Virtual Interface | Create a private virtual interface |
| `create-public-virtual-interface` | Virtual Interface | Create a public virtual interface |
| `create-transit-virtual-interface` | Virtual Interface | Create a transit virtual interface |
| `delete-bgp-peer` | BGP | Delete a BGP peer from a virtual interface |
| `delete-connection` | Connection | Delete a dedicated connection |
| `delete-direct-connect-gateway` | Gateway | Delete a Direct Connect gateway |
| `delete-direct-connect-gateway-association` | Gateway | Delete a gateway association |
| `delete-direct-connect-gateway-association-proposal` | Gateway | Delete a gateway association proposal |
| `delete-interconnect` | Interconnect | Delete an interconnect (partner only) |
| `delete-lag` | LAG | Delete a link aggregation group |
| `delete-virtual-interface` | Virtual Interface | Delete a virtual interface |
| `describe-connections` | Connection | Describe one or all connections |
| `describe-customer-metadata` | Connection | Describe customer metadata |
| `describe-direct-connect-gateway-association-proposals` | Gateway | Describe gateway association proposals |
| `describe-direct-connect-gateway-associations` | Gateway | Describe gateway associations |
| `describe-direct-connect-gateway-attachments` | Gateway | Describe gateway attachments |
| `describe-direct-connect-gateways` | Gateway | Describe Direct Connect gateways |
| `describe-hosted-connections` | Connection | Describe hosted connections on an interconnect or LAG |
| `describe-interconnects` | Interconnect | Describe one or all interconnects |
| `describe-lags` | LAG | Describe one or all LAGs |
| `describe-loa` | Connection | Describe the Letter of Authorization for a connection |
| `describe-locations` | Connection | List Direct Connect locations |
| `describe-router-configuration` | Virtual Interface | Get router configuration for a virtual interface |
| `describe-tags` | Tags | Describe tags for Direct Connect resources |
| `describe-virtual-gateways` | Gateway | Describe virtual private gateways |
| `describe-virtual-interfaces` | Virtual Interface | Describe one or all virtual interfaces |
| `disassociate-connection-from-lag` | Connection | Remove a connection from a LAG |
| `disassociate-mac-sec-key` | MACsec | Remove a MACsec key from a connection or LAG |
| `list-virtual-interface-test-history` | BGP | List BGP failover test history |
| `start-bgp-failover-test` | BGP | Start a BGP failover test |
| `stop-bgp-failover-test` | BGP | Stop a BGP failover test |
| `tag-resource` | Tags | Add tags to a Direct Connect resource |
| `untag-resource` | Tags | Remove tags from a Direct Connect resource |
| `update-connection` | Connection | Update connection name or encryption mode |
| `update-direct-connect-gateway` | Gateway | Update a Direct Connect gateway name |
| `update-direct-connect-gateway-association` | Gateway | Update allowed prefixes for a gateway association |
| `update-lag` | LAG | Update LAG name, minimum links, or encryption mode |
| `update-virtual-interface-attributes` | Virtual Interface | Update virtual interface MTU |

---

## Global Options

These options are available on ALL `aws directconnect` commands.

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

### Connection States
| State | Description |
|-------|-------------|
| `ordering` | Initial state of a hosted connection provisioned on an interconnect |
| `requested` | Initial state of a standard connection; LOA-CFA pending |
| `pending` | Connection approved and being initialized |
| `available` | Network link is up and connection is ready for use |
| `down` | Network link is down |
| `deleting` | Connection is being deleted |
| `deleted` | Connection has been deleted |
| `rejected` | Hosted connection was rejected by the owner |
| `unknown` | Connection state is not available |

### Virtual Interface States
| State | Description |
|-------|-------------|
| `confirming` | Creation pending owner confirmation |
| `verifying` | Public virtual interface validation pending |
| `pending` | Created but not yet ready for traffic |
| `available` | Ready to forward traffic |
| `down` | BGP session is down |
| `testing` | BGP failover test in progress |
| `deleting` | Being deleted |
| `deleted` | Deleted and cannot forward traffic |
| `rejected` | Owner declined creation |
| `unknown` | State not available |

### Gateway States
| State | Description |
|-------|-------------|
| `pending` | Initial state after creation |
| `available` | Ready for use |
| `deleting` | Being deleted |
| `deleted` | Has been deleted |

### Association States
| State | Description |
|-------|-------------|
| `associating` | Association is being created |
| `associated` | Association is active |
| `disassociating` | Association is being removed |
| `disassociated` | Association has been removed |
| `updating` | Allowed prefixes are being updated |

### LAG States
| State | Description |
|-------|-------------|
| `requested` | Initial state after creation |
| `pending` | Being provisioned |
| `available` | Ready for use |
| `down` | All member connections are down |
| `deleting` | Being deleted |
| `deleted` | Has been deleted |
| `unknown` | State not available |
