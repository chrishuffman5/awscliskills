# AWS CLI v2 -- ELB (Elastic Load Balancing Classic) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/elb/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-load-balancer` | Load Balancer | Create a Classic Load Balancer |
| `delete-load-balancer` | Load Balancer | Delete a Classic Load Balancer |
| `describe-load-balancers` | Load Balancer | Describe one or more load balancers |
| `describe-load-balancer-attributes` | Load Balancer | Describe load balancer attributes |
| `modify-load-balancer-attributes` | Load Balancer | Modify load balancer attributes |
| `describe-account-limits` | Load Balancer | Describe account limits for ELB |
| `create-load-balancer-listeners` | Listener | Add one or more listeners to a load balancer |
| `delete-load-balancer-listeners` | Listener | Remove one or more listeners from a load balancer |
| `set-load-balancer-listener-ssl-certificate` | Listener | Set the SSL certificate for a listener |
| `register-instances-with-load-balancer` | Instance | Register instances with a load balancer |
| `deregister-instances-from-load-balancer` | Instance | Deregister instances from a load balancer |
| `describe-instance-health` | Instance | Describe the health of registered instances |
| `configure-health-check` | Instance | Configure the health check for a load balancer |
| `create-load-balancer-policy` | Policy | Create a load balancer policy |
| `delete-load-balancer-policy` | Policy | Delete a load balancer policy |
| `describe-load-balancer-policies` | Policy | Describe load balancer policies |
| `describe-load-balancer-policy-types` | Policy | Describe available policy types |
| `create-app-cookie-stickiness-policy` | Policy | Create an app cookie stickiness policy |
| `create-lb-cookie-stickiness-policy` | Policy | Create an LB cookie stickiness policy |
| `set-load-balancer-policies-of-listener` | Policy | Set policies on a listener |
| `set-load-balancer-policies-for-backend-server` | Policy | Set policies for a backend server |
| `apply-security-groups-to-load-balancer` | Networking | Associate security groups with a VPC load balancer |
| `attach-load-balancer-to-subnets` | Networking | Add subnets to a load balancer |
| `detach-load-balancer-from-subnets` | Networking | Remove subnets from a load balancer |
| `enable-availability-zones-for-load-balancer` | Networking | Enable Availability Zones for a load balancer |
| `disable-availability-zones-for-load-balancer` | Networking | Disable Availability Zones for a load balancer |
| `add-tags` | Tags | Add tags to load balancers |
| `remove-tags` | Tags | Remove tags from load balancers |
| `describe-tags` | Tags | Describe tags for load balancers |
| `wait any-instance-in-service` | Wait | Wait until any instance is in service |
| `wait instance-deregistered` | Wait | Wait until an instance is deregistered |
| `wait instance-in-service` | Wait | Wait until an instance is in service |

---

## Global Options

These options are available on ALL `aws elb` commands.

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

### Load Balancer Name Constraints
- **Length:** 1 to 32 characters
- **Pattern:** Letters, numbers, and hyphens; must not begin or end with a hyphen

### Health Check Target Format
`Protocol:Port` or `Protocol:Port/PathToPing`

Examples:
- `TCP:80` — TCP check on port 80
- `HTTP:80/health` — HTTP GET on port 80 at `/health`
- `HTTPS:443/status` — HTTPS GET on port 443 at `/status`

### Instance State Values
| State | Description |
|-------|-------------|
| `InService` | Instance is healthy and registered |
| `OutOfService` | Instance has failed health check or is deregistered |

### Listener Protocol Values
| Protocol | Description |
|----------|-------------|
| `HTTP` | HTTP protocol |
| `HTTPS` | HTTPS protocol (requires SSL certificate) |
| `TCP` | TCP protocol |
| `SSL` | SSL protocol (requires SSL certificate) |

### Wait Commands
The `aws elb wait` subcommand blocks until a resource reaches a specific state:

| Waiter | Description |
|--------|-------------|
| `any-instance-in-service` | Wait until at least one instance is InService |
| `instance-deregistered` | Wait until a specific instance is deregistered |
| `instance-in-service` | Wait until a specific instance is InService |

```bash
aws elb wait any-instance-in-service --load-balancer-name my-clb
aws elb wait instance-in-service --load-balancer-name my-clb --instances i-0123456789abcdef0
```
