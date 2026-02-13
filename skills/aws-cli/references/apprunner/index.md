# AWS CLI v2 -- App Runner Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/apprunner/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-service` | Service | Create an App Runner service |
| `describe-service` | Service | Get service details |
| `list-services` | Service | List all services |
| `update-service` | Service | Update service configuration |
| `delete-service` | Service | Delete a service |
| `pause-service` | Service | Pause a running service |
| `resume-service` | Service | Resume a paused service |
| `start-deployment` | Service | Trigger a new deployment |
| `list-operations` | Service | List operations for a service |
| `create-connection` | Connection | Create a source code connection |
| `describe-connection` | Connection | Get connection details |
| `list-connections` | Connection | List all connections |
| `delete-connection` | Connection | Delete a connection |
| `create-auto-scaling-configuration` | Auto Scaling | Create an auto scaling configuration |
| `describe-auto-scaling-configuration` | Auto Scaling | Get auto scaling config details |
| `list-auto-scaling-configurations` | Auto Scaling | List auto scaling configurations |
| `delete-auto-scaling-configuration` | Auto Scaling | Delete an auto scaling configuration |
| `list-services-for-auto-scaling-configuration` | Auto Scaling | List services using an auto scaling config |
| `update-default-auto-scaling-configuration` | Auto Scaling | Update the default auto scaling config |
| `create-observability-configuration` | Observability | Create an observability configuration |
| `describe-observability-configuration` | Observability | Get observability config details |
| `list-observability-configurations` | Observability | List observability configurations |
| `delete-observability-configuration` | Observability | Delete an observability configuration |
| `create-vpc-connector` | VPC | Create a VPC connector |
| `describe-vpc-connector` | VPC | Get VPC connector details |
| `list-vpc-connectors` | VPC | List VPC connectors |
| `delete-vpc-connector` | VPC | Delete a VPC connector |
| `create-vpc-ingress-connection` | VPC | Create a VPC ingress connection |
| `describe-vpc-ingress-connection` | VPC | Get VPC ingress connection details |
| `list-vpc-ingress-connections` | VPC | List VPC ingress connections |
| `update-vpc-ingress-connection` | VPC | Update a VPC ingress connection |
| `delete-vpc-ingress-connection` | VPC | Delete a VPC ingress connection |
| `associate-custom-domain` | Custom Domain | Associate a custom domain |
| `disassociate-custom-domain` | Custom Domain | Disassociate a custom domain |
| `describe-custom-domains` | Custom Domain | Describe custom domains for a service |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws apprunner` commands.

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

### Service Statuses
| Status | Description |
|--------|-------------|
| `CREATE_FAILED` | Service creation failed |
| `RUNNING` | Service is running |
| `DELETED` | Service has been deleted |
| `DELETE_FAILED` | Service deletion failed |
| `PAUSED` | Service is paused |
| `OPERATION_IN_PROGRESS` | An operation is in progress |

### Connection Statuses
| Status | Description |
|--------|-------------|
| `PENDING_HANDSHAKE` | Connection requires GitHub OAuth handshake |
| `AVAILABLE` | Connection is ready to use |
| `ERROR` | Connection has an error |
| `DELETED` | Connection has been deleted |

### Supported Runtimes
| Runtime | Description |
|---------|-------------|
| `PYTHON_3` | Python 3 |
| `NODEJS_12` | Node.js 12 |
| `NODEJS_14` | Node.js 14 |
| `NODEJS_16` | Node.js 16 |
| `NODEJS_18` | Node.js 18 |
| `CORRETTO_8` | Amazon Corretto 8 (Java) |
| `CORRETTO_11` | Amazon Corretto 11 (Java) |
| `GO_1` | Go 1 |
| `DOTNET_6` | .NET 6 |
| `PHP_81` | PHP 8.1 |
| `RUBY_31` | Ruby 3.1 |

### Image Repository Types
| Type | Description |
|------|-------------|
| `ECR` | Amazon ECR (private) |
| `ECR_PUBLIC` | Amazon ECR Public |

### Custom Domain Statuses
| Status | Description |
|--------|-------------|
| `CREATING` | Domain association is being created |
| `CREATE_FAILED` | Domain association failed |
| `ACTIVE` | Domain is active |
| `DELETING` | Domain is being disassociated |
| `DELETE_FAILED` | Domain disassociation failed |
| `PENDING_CERTIFICATE_DNS_VALIDATION` | Waiting for DNS validation |
| `BINDING_CERTIFICATE` | SSL certificate is being bound |
