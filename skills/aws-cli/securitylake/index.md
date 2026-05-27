# AWS CLI v2 -- Security Lake Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/securitylake/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-data-lake` | Data Lake | Create a Security Lake data lake in specified regions |
| `delete-data-lake` | Data Lake | Delete the Security Lake data lake |
| `update-data-lake` | Data Lake | Update data lake configuration (encryption, lifecycle, replication) |
| `list-data-lakes` | Data Lake | List data lakes for specified regions |
| `create-data-lake-exception-subscription` | Data Lake | Create exception notification subscription |
| `delete-data-lake-exception-subscription` | Data Lake | Delete exception notification subscription |
| `get-data-lake-exception-subscription` | Data Lake | Get exception notification subscription details |
| `update-data-lake-exception-subscription` | Data Lake | Update exception notification subscription |
| `list-data-lake-exceptions` | Data Lake | List data lake exceptions (errors) |
| `get-data-lake-sources` | Data Lake | Get a snapshot of current data lake sources |
| `create-data-lake-organization-configuration` | Data Lake | Auto-enable Security Lake for new organization accounts |
| `delete-data-lake-organization-configuration` | Data Lake | Remove auto-enable organization configuration |
| `get-data-lake-organization-configuration` | Data Lake | Get organization auto-enable configuration |
| `register-data-lake-delegated-administrator` | Data Lake | Register delegated administrator for Security Lake |
| `deregister-data-lake-delegated-administrator` | Data Lake | Remove delegated administrator |
| `create-aws-log-source` | Log Sources | Enable natively-supported AWS log sources |
| `delete-aws-log-source` | Log Sources | Disable AWS log sources |
| `create-custom-log-source` | Log Sources | Add a custom log source |
| `delete-custom-log-source` | Log Sources | Remove a custom log source |
| `list-log-sources` | Log Sources | List enabled log sources |
| `create-subscriber` | Subscribers | Create a subscriber for data access |
| `delete-subscriber` | Subscribers | Delete a subscriber |
| `get-subscriber` | Subscribers | Get subscriber details |
| `update-subscriber` | Subscribers | Update subscriber configuration |
| `list-subscribers` | Subscribers | List all subscribers |
| `create-subscriber-notification` | Subscribers | Set up subscriber notification |
| `delete-subscriber-notification` | Subscribers | Remove subscriber notification |
| `update-subscriber-notification` | Subscribers | Update subscriber notification |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws securitylake` commands.

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
| `--cli-binary-format` | string | `base64` | Format for binary blob input: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from a JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from a YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton: `input`, `yaml-input`, `output` |

---

## Common Patterns

### AWS Log Source Names
| Source Name | Description |
|-------------|-------------|
| `ROUTE53` | Route 53 resolver query logs |
| `VPC_FLOW` | VPC Flow Logs |
| `SH_FINDINGS` | Security Hub findings |
| `CLOUD_TRAIL_MGMT` | CloudTrail management events |
| `LAMBDA_EXECUTION` | Lambda execution logs |
| `S3_DATA` | S3 data events |
| `EKS_AUDIT` | EKS audit logs |
| `WAF` | WAF logs |

### Data Lake Create Statuses
| Status | Description |
|--------|-------------|
| `INITIALIZED` | Data lake creation has been initialized |
| `PENDING` | Data lake creation is pending |
| `COMPLETED` | Data lake creation completed successfully |
| `FAILED` | Data lake creation failed |

### Subscriber Statuses
| Status | Description |
|--------|-------------|
| `ACTIVE` | Subscriber is active and receiving data |
| `DEACTIVATED` | Subscriber has been deactivated |
| `PENDING` | Subscriber creation is pending |
| `READY` | Subscriber is ready to receive data |

### Subscriber Access Types
| Type | Description |
|------|-------------|
| `S3` | Direct S3 bucket access to data lake |
| `LAKEFORMATION` | Access through AWS Lake Formation |
