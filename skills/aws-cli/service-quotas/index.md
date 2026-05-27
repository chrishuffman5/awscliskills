# AWS CLI v2 -- Service Quotas Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/service-quotas/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `get-service-quota` | Quota | Get the applied value for a specific quota |
| `get-aws-default-service-quota` | Quota | Get the AWS default value for a quota |
| `list-services` | Quota | List AWS services with available quotas |
| `list-service-quotas` | Quota | List all quotas for a service |
| `list-aws-default-service-quotas` | Quota | List default quota values for a service |
| `request-service-quota-increase` | Request | Request a quota increase |
| `get-requested-service-quota-change` | Request | Get details of a quota increase request |
| `list-requested-service-quota-change-history` | Request | List all quota increase requests |
| `list-requested-service-quota-change-history-by-quota` | Request | List increase requests for a specific quota |
| `associate-service-quota-template` | Template | Associate the quota template with Organizations |
| `disassociate-service-quota-template` | Template | Disassociate the quota template from Organizations |
| `get-association-for-service-quota-template` | Template | Get the association status of the template |
| `put-service-quota-increase-request-into-template` | Template | Add a quota increase to the template |
| `get-service-quota-increase-request-from-template` | Template | Get a quota request from the template |
| `list-service-quota-increase-requests-in-template` | Template | List all quota requests in the template |
| `delete-service-quota-increase-request-from-template` | Template | Remove a quota request from the template |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws service-quotas` commands.

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

### Request Status Values
| Status | Description |
|--------|-------------|
| `PENDING` | Request is pending review |
| `CASE_OPENED` | Support case has been opened |
| `APPROVED` | Request was approved |
| `DENIED` | Request was denied |
| `CASE_CLOSED` | Support case has been closed |
| `NOT_APPROVED` | Request was not approved |
| `INVALID_REQUEST` | Request was invalid |

### Error Codes
| Code | Description |
|------|-------------|
| `DEPENDENCY_ACCESS_DENIED_ERROR` | Caller lacks permissions for a dependency |
| `DEPENDENCY_THROTTLING_ERROR` | Dependency service is throttling requests |
| `DEPENDENCY_SERVICE_ERROR` | Dependency service returned an error |
| `SERVICE_QUOTA_NOT_AVAILABLE_ERROR` | The quota is not available |

### Quota Code Format
Quota codes follow the pattern `L-XXXXXXXX` (e.g., `L-1216C47A` for EC2 Running On-Demand instances).

### Service Code Examples
| Service Code | Service |
|-------------|---------|
| `ec2` | Amazon EC2 |
| `elasticloadbalancing` | Elastic Load Balancing |
| `rds` | Amazon RDS |
| `s3` | Amazon S3 |
| `lambda` | AWS Lambda |
| `dynamodb` | Amazon DynamoDB |
| `ecs` | Amazon ECS |
| `vpc` | Amazon VPC |
| `iam` | AWS IAM |
| `cloudformation` | AWS CloudFormation |
