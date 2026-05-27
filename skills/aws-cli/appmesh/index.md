# AWS CLI v2 -- App Mesh Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/appmesh/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-mesh` | Mesh | Create a service mesh |
| `delete-mesh` | Mesh | Delete a service mesh |
| `describe-mesh` | Mesh | Describe a service mesh |
| `list-meshes` | Mesh | List all service meshes |
| `update-mesh` | Mesh | Update a service mesh |
| `create-virtual-node` | Virtual Node | Create a virtual node |
| `delete-virtual-node` | Virtual Node | Delete a virtual node |
| `describe-virtual-node` | Virtual Node | Describe a virtual node |
| `list-virtual-nodes` | Virtual Node | List virtual nodes in a mesh |
| `update-virtual-node` | Virtual Node | Update a virtual node |
| `create-virtual-service` | Virtual Service | Create a virtual service |
| `delete-virtual-service` | Virtual Service | Delete a virtual service |
| `describe-virtual-service` | Virtual Service | Describe a virtual service |
| `list-virtual-services` | Virtual Service | List virtual services in a mesh |
| `update-virtual-service` | Virtual Service | Update a virtual service |
| `create-virtual-router` | Virtual Router | Create a virtual router |
| `delete-virtual-router` | Virtual Router | Delete a virtual router |
| `describe-virtual-router` | Virtual Router | Describe a virtual router |
| `list-virtual-routers` | Virtual Router | List virtual routers in a mesh |
| `update-virtual-router` | Virtual Router | Update a virtual router |
| `create-route` | Route | Create a route for a virtual router |
| `delete-route` | Route | Delete a route |
| `describe-route` | Route | Describe a route |
| `list-routes` | Route | List routes for a virtual router |
| `update-route` | Route | Update a route |
| `create-virtual-gateway` | Virtual Gateway | Create a virtual gateway for ingress |
| `delete-virtual-gateway` | Virtual Gateway | Delete a virtual gateway |
| `describe-virtual-gateway` | Virtual Gateway | Describe a virtual gateway |
| `list-virtual-gateways` | Virtual Gateway | List virtual gateways in a mesh |
| `update-virtual-gateway` | Virtual Gateway | Update a virtual gateway |
| `create-gateway-route` | Gateway Route | Create a gateway route |
| `delete-gateway-route` | Gateway Route | Delete a gateway route |
| `describe-gateway-route` | Gateway Route | Describe a gateway route |
| `list-gateway-routes` | Gateway Route | List gateway routes for a virtual gateway |
| `update-gateway-route` | Gateway Route | Update a gateway route |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws appmesh` commands.

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
| `ACTIVE` | Resource is active and operational |
| `INACTIVE` | Resource is inactive |
| `DELETED` | Resource has been deleted |

### Supported Protocols
| Protocol | Used In |
|----------|---------|
| `http` | Virtual nodes, virtual routers, virtual gateways, routes |
| `http2` | Virtual nodes, virtual routers, virtual gateways, routes |
| `grpc` | Virtual nodes, virtual routers, virtual gateways, routes |
| `tcp` | Virtual nodes, virtual routers, routes |

### TLS Modes
| Mode | Description |
|------|-------------|
| `STRICT` | Only accept TLS connections |
| `PERMISSIVE` | Accept both TLS and plaintext connections |
| `DISABLED` | Do not enforce TLS |

### Metadata Structure
All App Mesh resources return a `metadata` object:
```json
{
    "arn": "string",
    "createdAt": "timestamp",
    "lastUpdatedAt": "timestamp",
    "meshOwner": "string",
    "resourceOwner": "string",
    "uid": "string",
    "version": "long"
}
```
