# AWS CLI v2 -- Cloud Map (Service Discovery) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/servicediscovery/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-http-namespace` | Namespace | Create an HTTP namespace for API-based discovery |
| `create-private-dns-namespace` | Namespace | Create a private DNS namespace backed by Route 53 |
| `create-public-dns-namespace` | Namespace | Create a public DNS namespace backed by Route 53 |
| `delete-namespace` | Namespace | Delete a namespace |
| `get-namespace` | Namespace | Get details of a namespace |
| `list-namespaces` | Namespace | List all namespaces |
| `update-http-namespace` | Namespace | Update an HTTP namespace |
| `update-private-dns-namespace` | Namespace | Update a private DNS namespace |
| `update-public-dns-namespace` | Namespace | Update a public DNS namespace |
| `create-service` | Service | Create a service within a namespace |
| `delete-service` | Service | Delete a service |
| `get-service` | Service | Get details of a service |
| `list-services` | Service | List all services |
| `update-service` | Service | Update a service configuration |
| `get-service-attributes` | Service | Get custom attributes for a service |
| `update-service-attributes` | Service | Update custom attributes for a service |
| `delete-service-attributes` | Service | Delete custom attributes from a service |
| `register-instance` | Instance | Register an instance with a service |
| `deregister-instance` | Instance | Deregister an instance from a service |
| `get-instance` | Instance | Get details of an instance |
| `list-instances` | Instance | List instances for a service |
| `get-instances-health-status` | Instance | Get health status of instances |
| `update-instance-custom-health-status` | Instance | Update custom health status of an instance |
| `discover-instances` | Instance | Discover registered instances by namespace and service |
| `discover-instances-revision` | Instance | Get the revision number for discovered instances |
| `get-operation` | Operation | Get the status of an asynchronous operation |
| `list-operations` | Operation | List asynchronous operations |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws servicediscovery` commands.

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

### Namespace Types
| Type | Description |
|------|-------------|
| `DNS_PUBLIC` | Public DNS namespace with Route 53 public hosted zone |
| `DNS_PRIVATE` | Private DNS namespace with Route 53 private hosted zone (requires VPC) |
| `HTTP` | HTTP-only namespace for API-based discovery (no DNS records) |

### Service Types
| Type | Description |
|------|-------------|
| `HTTP` | Created with `--type HTTP`; API-only discovery, no DNS records |
| `DNS_HTTP` | DNS namespace with health checking; supports both DNS and API discovery |
| `DNS` | DNS namespace with Route 53 health checking only |

### Instance Health Status
| Status | Description |
|--------|-------------|
| `HEALTHY` | Instance is healthy |
| `UNHEALTHY` | Instance is unhealthy |
| `UNKNOWN` | Health status has not been evaluated |

### Operation Status
| Status | Description |
|--------|-------------|
| `SUBMITTED` | Operation has been submitted |
| `PENDING` | Operation is being processed |
| `SUCCESS` | Operation completed successfully |
| `FAIL` | Operation failed |

### Common Instance Attributes
| Attribute | Description |
|-----------|-------------|
| `AWS_INSTANCE_IPV4` | IPv4 address (for A records) |
| `AWS_INSTANCE_IPV6` | IPv6 address (for AAAA records) |
| `AWS_INSTANCE_PORT` | Port number (for SRV records) |
| `AWS_INSTANCE_CNAME` | CNAME target (for CNAME records) |
| `AWS_EC2_INSTANCE_ID` | EC2 instance ID |
| `AWS_ALIAS_DNS_NAME` | Route 53 alias target |
| `AWS_INIT_HEALTH_STATUS` | Initial health status: `HEALTHY` or `UNHEALTHY` |
