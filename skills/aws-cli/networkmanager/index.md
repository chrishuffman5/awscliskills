# AWS CLI v2 -- Network Manager Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/networkmanager/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-global-network` | Global Network | Create a global network |
| `delete-global-network` | Global Network | Delete a global network |
| `describe-global-networks` | Global Network | Describe one or more global networks |
| `update-global-network` | Global Network | Update a global network |
| `create-core-network` | Core Network | Create a core network |
| `delete-core-network` | Core Network | Delete a core network |
| `get-core-network` | Core Network | Get core network details |
| `list-core-networks` | Core Network | List core networks |
| `update-core-network` | Core Network | Update core network description |
| `put-core-network-policy` | Core Network | Create or update core network policy |
| `get-core-network-policy` | Core Network | Get core network policy document |
| `get-core-network-change-set` | Core Network | Get pending policy change set |
| `get-core-network-change-events` | Core Network | Get core network change events |
| `execute-core-network-change-set` | Core Network | Execute a pending change set |
| `list-core-network-policy-versions` | Core Network | List policy versions |
| `delete-core-network-policy-version` | Core Network | Delete a policy version |
| `restore-core-network-policy-version` | Core Network | Restore a previous policy version |
| `create-core-network-prefix-list-association` | Prefix List | Associate prefix list with core network |
| `delete-core-network-prefix-list-association` | Prefix List | Remove prefix list association |
| `list-core-network-prefix-list-associations` | Prefix List | List prefix list associations |
| `list-core-network-routing-information` | Prefix List | List core network routing information |
| `create-site` | Site | Create a site |
| `delete-site` | Site | Delete a site |
| `get-sites` | Site | Get site details |
| `update-site` | Site | Update a site |
| `create-device` | Device | Create a device |
| `delete-device` | Device | Delete a device |
| `get-devices` | Device | Get device details |
| `update-device` | Device | Update a device |
| `create-link` | Link | Create a link |
| `delete-link` | Link | Delete a link |
| `get-links` | Link | Get link details |
| `update-link` | Link | Update a link |
| `associate-link` | Link | Associate a link with a device |
| `disassociate-link` | Link | Disassociate a link from a device |
| `get-link-associations` | Link | Get link-device associations |
| `create-connection` | Connection | Create a connection between devices |
| `delete-connection` | Connection | Delete a connection |
| `get-connections` | Connection | Get connection details |
| `update-connection` | Connection | Update a connection |
| `register-transit-gateway` | Transit Gateway | Register a Transit Gateway |
| `deregister-transit-gateway` | Transit Gateway | Deregister a Transit Gateway |
| `get-transit-gateway-registrations` | Transit Gateway | Get TGW registrations |
| `associate-transit-gateway-connect-peer` | Transit Gateway | Associate TGW Connect peer |
| `disassociate-transit-gateway-connect-peer` | Transit Gateway | Disassociate TGW Connect peer |
| `get-transit-gateway-connect-peer-associations` | Transit Gateway | Get TGW Connect peer associations |
| `create-transit-gateway-peering` | Transit Gateway | Create TGW peering |
| `get-transit-gateway-peering` | Transit Gateway | Get TGW peering details |
| `create-transit-gateway-route-table-attachment` | Transit Gateway | Create TGW route table attachment |
| `get-transit-gateway-route-table-attachment` | Transit Gateway | Get TGW route table attachment |
| `create-vpc-attachment` | Attachment | Create a VPC attachment |
| `update-vpc-attachment` | Attachment | Update a VPC attachment |
| `get-vpc-attachment` | Attachment | Get VPC attachment details |
| `create-connect-attachment` | Attachment | Create a Connect attachment |
| `get-connect-attachment` | Attachment | Get Connect attachment details |
| `create-site-to-site-vpn-attachment` | Attachment | Create site-to-site VPN attachment |
| `get-site-to-site-vpn-attachment` | Attachment | Get VPN attachment details |
| `create-direct-connect-gateway-attachment` | Attachment | Create DX gateway attachment |
| `get-direct-connect-gateway-attachment` | Attachment | Get DX gateway attachment details |
| `update-direct-connect-gateway-attachment` | Attachment | Update DX gateway attachment |
| `accept-attachment` | Attachment | Accept an attachment request |
| `reject-attachment` | Attachment | Reject an attachment request |
| `delete-attachment` | Attachment | Delete an attachment |
| `list-attachments` | Attachment | List attachments |
| `create-connect-peer` | Connect Peer | Create a Connect peer |
| `delete-connect-peer` | Connect Peer | Delete a Connect peer |
| `get-connect-peer` | Connect Peer | Get Connect peer details |
| `list-connect-peers` | Connect Peer | List Connect peers |
| `associate-connect-peer` | Connect Peer | Associate Connect peer with device |
| `disassociate-connect-peer` | Connect Peer | Disassociate Connect peer from device |
| `get-connect-peer-associations` | Connect Peer | Get Connect peer associations |
| `associate-customer-gateway` | Customer Gateway | Associate customer gateway with device |
| `disassociate-customer-gateway` | Customer Gateway | Disassociate customer gateway |
| `get-customer-gateway-associations` | Customer Gateway | Get customer gateway associations |
| `start-route-analysis` | Route Analysis | Start a route analysis |
| `get-route-analysis` | Route Analysis | Get route analysis results |
| `get-network-routes` | Network Resources | Get network routes |
| `get-network-resources` | Network Resources | Get network resources |
| `get-network-resource-counts` | Network Resources | Get resource counts |
| `get-network-resource-relationships` | Network Resources | Get resource relationships |
| `get-network-telemetry` | Network Resources | Get network telemetry |
| `update-network-resource-metadata` | Network Resources | Update resource metadata |
| `list-attachment-routing-policy-associations` | Routing Policy | List routing policy associations |
| `put-attachment-routing-policy-label` | Routing Policy | Set routing policy label |
| `remove-attachment-routing-policy-label` | Routing Policy | Remove routing policy label |
| `list-organization-service-access-status` | Organization | List org service access status |
| `start-organization-service-access-update` | Organization | Start org service access update |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |
| `get-resource-policy` | Resource Policy | Get resource policy |
| `put-resource-policy` | Resource Policy | Create or update resource policy |
| `delete-resource-policy` | Resource Policy | Delete resource policy |

---

## Global Options

These options are available on ALL `aws networkmanager` commands.

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
| `--cli-binary-format` | string | `base64` | Format for binary blob input |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from a JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from a YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton |

---

## Common Patterns

### Region Requirement

Network Manager is a global service. Most commands should use `--region us-west-2` as the API endpoint.

### Resource States

| State | Description |
|-------|-------------|
| `PENDING` | Resource is being created |
| `AVAILABLE` | Resource is ready for use |
| `UPDATING` | Resource is being updated |
| `DELETING` | Resource is being deleted |

### Attachment States

| State | Description |
|-------|-------------|
| `REJECTED` | Attachment was rejected |
| `PENDING_ATTACHMENT_ACCEPTANCE` | Waiting for acceptance |
| `CREATING` | Attachment is being created |
| `FAILED` | Attachment creation failed |
| `AVAILABLE` | Attachment is ready |
| `UPDATING` | Attachment is being updated |
| `PENDING_NETWORK_UPDATE` | Waiting for network update |
| `PENDING_TAG_ACCEPTANCE` | Waiting for tag acceptance |
| `DELETING` | Attachment is being deleted |

### Core Network States

| State | Description |
|-------|-------------|
| `CREATING` | Core network is being created |
| `UPDATING` | Core network is being updated |
| `AVAILABLE` | Core network is ready for use |
| `DELETING` | Core network is being deleted |

### Attachment Types

| Type | Description |
|------|-------------|
| `VPC` | VPC attachment |
| `CONNECT` | Connect attachment |
| `SITE_TO_SITE_VPN` | Site-to-site VPN attachment |
| `DIRECT_CONNECT_GATEWAY` | Direct Connect gateway attachment |
| `TRANSIT_GATEWAY_ROUTE_TABLE` | Transit Gateway route table attachment |
