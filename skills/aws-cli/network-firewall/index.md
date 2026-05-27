# AWS CLI v2 -- Network Firewall Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/network-firewall/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-firewall` | Firewall | Create a new firewall |
| `delete-firewall` | Firewall | Delete a firewall |
| `describe-firewall` | Firewall | Get detailed firewall information |
| `describe-firewall-metadata` | Firewall | Get firewall metadata |
| `list-firewalls` | Firewall | List all firewalls |
| `update-firewall-description` | Firewall | Update firewall description |
| `update-firewall-delete-protection` | Firewall | Enable/disable delete protection |
| `update-firewall-policy-change-protection` | Firewall | Enable/disable policy change protection |
| `update-firewall-encryption-configuration` | Firewall | Update encryption settings |
| `update-firewall-analysis-settings` | Firewall | Update analysis settings |
| `update-availability-zone-change-protection` | Firewall | Enable/disable AZ change protection |
| `associate-firewall-policy` | Firewall | Attach a policy to a firewall |
| `create-firewall-policy` | Policy | Create a firewall policy |
| `delete-firewall-policy` | Policy | Delete a firewall policy |
| `describe-firewall-policy` | Policy | Get firewall policy details |
| `list-firewall-policies` | Policy | List all firewall policies |
| `update-firewall-policy` | Policy | Update a firewall policy |
| `create-rule-group` | Rule Group | Create a rule group |
| `delete-rule-group` | Rule Group | Delete a rule group |
| `describe-rule-group` | Rule Group | Get rule group details |
| `describe-rule-group-metadata` | Rule Group | Get rule group metadata |
| `list-rule-groups` | Rule Group | List all rule groups |
| `update-rule-group` | Rule Group | Update a rule group |
| `create-tls-inspection-configuration` | TLS | Create TLS inspection configuration |
| `delete-tls-inspection-configuration` | TLS | Delete TLS inspection configuration |
| `describe-tls-inspection-configuration` | TLS | Get TLS inspection details |
| `list-tls-inspection-configurations` | TLS | List TLS inspection configurations |
| `update-tls-inspection-configuration` | TLS | Update TLS inspection configuration |
| `associate-subnets` | Subnet | Associate subnets with a firewall |
| `disassociate-subnets` | Subnet | Remove subnet associations |
| `associate-availability-zones` | Zone | Associate AZs with a firewall |
| `disassociate-availability-zones` | Zone | Remove AZ associations |
| `update-subnet-change-protection` | Subnet | Enable/disable subnet change protection |
| `create-vpc-endpoint-association` | VPC Endpoint | Create VPC endpoint association |
| `delete-vpc-endpoint-association` | VPC Endpoint | Delete VPC endpoint association |
| `describe-vpc-endpoint-association` | VPC Endpoint | Get VPC endpoint association details |
| `list-vpc-endpoint-associations` | VPC Endpoint | List VPC endpoint associations |
| `accept-network-firewall-transit-gateway-attachment` | Transit GW | Accept transit gateway attachment |
| `delete-network-firewall-transit-gateway-attachment` | Transit GW | Delete transit gateway attachment |
| `reject-network-firewall-transit-gateway-attachment` | Transit GW | Reject transit gateway attachment |
| `create-proxy` | Proxy | Create a forward proxy |
| `delete-proxy` | Proxy | Delete a proxy |
| `describe-proxy` | Proxy | Get proxy details |
| `list-proxies` | Proxy | List all proxies |
| `update-proxy` | Proxy | Update a proxy |
| `create-proxy-configuration` | Proxy | Create proxy configuration |
| `delete-proxy-configuration` | Proxy | Delete proxy configuration |
| `describe-proxy-configuration` | Proxy | Get proxy configuration details |
| `list-proxy-configurations` | Proxy | List proxy configurations |
| `update-proxy-configuration` | Proxy | Update proxy configuration |
| `describe-logging-configuration` | Logging | Get logging configuration |
| `update-logging-configuration` | Logging | Update logging configuration |
| `start-analysis-report` | Analysis | Start an analysis report |
| `list-analysis-reports` | Analysis | List analysis reports |
| `get-analysis-report-results` | Analysis | Get analysis report results |
| `describe-flow-operation` | Flow | Get flow operation details |
| `list-flow-operations` | Flow | List flow operations |
| `list-flow-operation-results` | Flow | List flow operation results |
| `start-flow-capture` | Flow | Start flow capture |
| `start-flow-flush` | Flow | Start flow flush |
| `describe-resource-policy` | Resource Policy | Get resource policy |
| `put-resource-policy` | Resource Policy | Create/update resource policy |
| `delete-resource-policy` | Resource Policy | Delete resource policy |
| `tag-resource` | Tag | Add tags to a resource |
| `untag-resource` | Tag | Remove tags from a resource |
| `list-tags-for-resource` | Tag | List tags for a resource |

---

## Global Options

These options are available on ALL `aws network-firewall` commands.

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

### Firewall Statuses
| Status | Description |
|--------|-------------|
| `PROVISIONING` | Firewall is being created |
| `DELETING` | Firewall is being deleted |
| `READY` | Firewall is active and ready |

### Configuration Sync States
| State | Description |
|-------|-------------|
| `PENDING` | Configuration change is pending |
| `IN_SYNC` | All endpoints have the latest configuration |
| `CAPACITY_CONSTRAINED` | Capacity limits reached |

### Firewall Policy Statuses
| Status | Description |
|--------|-------------|
| `ACTIVE` | Policy is active |
| `DELETING` | Policy is being deleted |
| `ERROR` | Policy has an error |

### Rule Group Types
| Type | Description |
|------|-------------|
| `STATELESS` | Rules evaluated independently per packet |
| `STATEFUL` | Rules maintain connection state |

### Stateful Rule Order
| Order | Description |
|-------|-------------|
| `DEFAULT_ACTION_ORDER` | Rules evaluated in default order |
| `STRICT_ORDER` | Rules evaluated by priority number |

### Log Types
| Type | Description |
|------|-------------|
| `ALERT` | Alert logs from stateful rule matches |
| `FLOW` | Network flow logs |
| `TLS` | TLS inspection logs |

### Log Destination Types
| Type | Description |
|------|-------------|
| `S3` | Amazon S3 bucket |
| `CloudWatchLogs` | CloudWatch Logs group |
| `KinesisDataFirehose` | Kinesis Data Firehose delivery stream |

### Stateless Default Actions
| Action | Description |
|--------|-------------|
| `aws:pass` | Pass the packet through |
| `aws:drop` | Drop the packet |
| `aws:forward_to_sfe` | Forward to stateful rule engine |

### Encryption Types
| Type | Description |
|------|-------------|
| `CUSTOMER_KMS` | Customer-managed KMS key |
| `AWS_OWNED_KMS_KEY` | AWS-owned KMS key (default) |
