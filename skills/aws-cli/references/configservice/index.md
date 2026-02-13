# AWS CLI v2 -- Config (AWS Config) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/configservice/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `put-config-rule` | Config Rules | Create or update a Config rule |
| `delete-config-rule` | Config Rules | Delete a Config rule |
| `describe-config-rules` | Config Rules | Describe Config rules |
| `describe-compliance-by-config-rule` | Config Rules | Get compliance status by rule |
| `describe-compliance-by-resource` | Config Rules | Get compliance status by resource |
| `get-compliance-details-by-config-rule` | Config Rules | Get compliance details for a rule |
| `get-compliance-details-by-resource` | Config Rules | Get compliance details for a resource |
| `get-compliance-summary-by-config-rule` | Config Rules | Get compliance summary across rules |
| `get-compliance-summary-by-resource-type` | Config Rules | Get compliance summary by resource type |
| `describe-config-rule-evaluation-status` | Config Rules | Get evaluation status for Config rules |
| `start-config-rules-evaluation` | Config Rules | Start on-demand evaluation for Config rules |
| `delete-evaluation-results` | Config Rules | Delete evaluation results for a Config rule |
| `get-custom-rule-policy` | Config Rules | Get Guard policy for a custom policy rule |
| `put-conformance-pack` | Conformance Packs | Create or update a conformance pack |
| `delete-conformance-pack` | Conformance Packs | Delete a conformance pack |
| `describe-conformance-packs` | Conformance Packs | Describe conformance packs |
| `describe-conformance-pack-status` | Conformance Packs | Get conformance pack deployment status |
| `get-conformance-pack-compliance-summary` | Conformance Packs | Get compliance summary for conformance packs |
| `describe-conformance-pack-compliance` | Conformance Packs | Get rule-level compliance in a pack |
| `get-conformance-pack-compliance-details` | Conformance Packs | Get resource-level compliance details in a pack |
| `list-conformance-pack-compliance-scores` | Conformance Packs | List compliance scores for conformance packs |
| `put-configuration-recorder` | Recorders | Create or update a configuration recorder |
| `delete-configuration-recorder` | Recorders | Delete a configuration recorder |
| `describe-configuration-recorders` | Recorders | Describe configuration recorders |
| `describe-configuration-recorder-status` | Recorders | Get configuration recorder status |
| `start-configuration-recorder` | Recorders | Start recording configurations |
| `stop-configuration-recorder` | Recorders | Stop recording configurations |
| `put-delivery-channel` | Delivery Channels | Create or update a delivery channel |
| `delete-delivery-channel` | Delivery Channels | Delete a delivery channel |
| `describe-delivery-channels` | Delivery Channels | Describe delivery channels |
| `describe-delivery-channel-status` | Delivery Channels | Get delivery channel status |
| `deliver-config-snapshot` | Delivery Channels | Deliver a configuration snapshot to S3 |
| `put-remediation-configurations` | Remediation | Create or update remediation configurations |
| `delete-remediation-configuration` | Remediation | Delete a remediation configuration |
| `describe-remediation-configurations` | Remediation | Describe remediation configurations |
| `put-remediation-exceptions` | Remediation | Create remediation exceptions |
| `delete-remediation-exceptions` | Remediation | Delete remediation exceptions |
| `describe-remediation-exceptions` | Remediation | Describe remediation exceptions |
| `describe-remediation-execution-status` | Remediation | Get remediation execution status |
| `start-remediation-execution` | Remediation | Start remediation for noncompliant resources |
| `put-configuration-aggregator` | Aggregators | Create or update a configuration aggregator |
| `delete-configuration-aggregator` | Aggregators | Delete a configuration aggregator |
| `describe-configuration-aggregators` | Aggregators | Describe configuration aggregators |
| `describe-configuration-aggregator-sources-status` | Aggregators | Get aggregator source status |
| `get-aggregate-compliance-details-by-config-rule` | Aggregators | Get aggregate compliance details by rule |
| `get-aggregate-config-rule-compliance-summary` | Aggregators | Get aggregate rule compliance summary |
| `get-aggregate-conformance-pack-compliance-summary` | Aggregators | Get aggregate conformance pack compliance |
| `get-aggregate-discovered-resource-counts` | Aggregators | Get aggregate resource counts |
| `get-aggregate-resource-config` | Aggregators | Get configuration of an aggregate resource |
| `list-aggregate-discovered-resources` | Aggregators | List resources in an aggregator |
| `batch-get-aggregate-resource-config` | Aggregators | Batch get aggregate resource configs |
| `select-aggregate-resource-config` | Aggregators | Run SQL query on aggregate resources |
| `put-aggregation-authorization` | Aggregators | Authorize aggregator account to collect data |
| `delete-aggregation-authorization` | Aggregators | Delete aggregation authorization |
| `describe-aggregation-authorizations` | Aggregators | List aggregation authorizations |
| `describe-pending-aggregation-requests` | Aggregators | List pending aggregation requests |
| `delete-pending-aggregation-request` | Aggregators | Delete a pending aggregation request |
| `list-discovered-resources` | Resources | List discovered resources |
| `get-discovered-resource-counts` | Resources | Get discovered resource counts |
| `get-resource-config-history` | Resources | Get configuration history for a resource |
| `batch-get-resource-config` | Resources | Batch get resource configurations |
| `select-resource-config` | Resources | Run SQL query on discovered resources |
| `put-evaluations` | Resource Evaluation | Submit evaluation results (custom rules) |
| `start-resource-evaluation` | Resource Evaluation | Start evaluating a resource |
| `get-resource-evaluation-summary` | Resource Evaluation | Get resource evaluation summary |
| `list-resource-evaluations` | Resource Evaluation | List resource evaluations |
| `put-external-evaluation` | Resource Evaluation | Publish external evaluation results |
| `put-organization-config-rule` | Organization Config | Create organization Config rule |
| `delete-organization-config-rule` | Organization Config | Delete organization Config rule |
| `describe-organization-config-rules` | Organization Config | Describe organization Config rules |
| `describe-organization-config-rule-statuses` | Organization Config | Get organization rule statuses |
| `get-organization-config-rule-detailed-status` | Organization Config | Get detailed member account status |
| `put-organization-conformance-pack` | Organization Config | Create organization conformance pack |
| `delete-organization-conformance-pack` | Organization Config | Delete organization conformance pack |
| `describe-organization-conformance-packs` | Organization Config | Describe organization conformance packs |
| `describe-organization-conformance-pack-statuses` | Organization Config | Get organization conformance pack statuses |
| `get-organization-conformance-pack-detailed-status` | Organization Config | Get detailed member account status |
| `get-organization-custom-rule-policy` | Organization Config | Get Guard policy for org custom rule |
| `put-retention-configuration` | Retention & Queries | Set retention period for config history |
| `delete-retention-configuration` | Retention & Queries | Delete retention configuration |
| `describe-retention-configurations` | Retention & Queries | Describe retention configurations |
| `put-stored-query` | Retention & Queries | Create or update a stored query |
| `delete-stored-query` | Retention & Queries | Delete a stored query |
| `get-stored-query` | Retention & Queries | Get a stored query |
| `list-stored-queries` | Retention & Queries | List stored queries |
| `tag-resource` | Tags | Add tags to a Config resource |
| `untag-resource` | Tags | Remove tags from a Config resource |
| `list-tags-for-resource` | Tags | List tags for a Config resource |

---

## Global Options

These options are available on ALL `aws configservice` commands.

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

### Compliance Types

| Value | Description |
|-------|-------------|
| `COMPLIANT` | Resource complies with the rule |
| `NON_COMPLIANT` | Resource does not comply |
| `NOT_APPLICABLE` | Rule does not apply to the resource |
| `INSUFFICIENT_DATA` | Not enough data to evaluate |

### Config Rule Source Owners

| Owner | Description |
|-------|-------------|
| `AWS` | AWS managed rule (use `SourceIdentifier` for rule name) |
| `CUSTOM_LAMBDA` | Custom rule backed by a Lambda function |
| `CUSTOM_POLICY` | Custom rule with inline Guard policy |

### Resource Types

AWS Config supports 200+ resource types. Common ones include:
- `AWS::EC2::Instance`, `AWS::EC2::SecurityGroup`, `AWS::EC2::VPC`
- `AWS::S3::Bucket`, `AWS::IAM::Role`, `AWS::IAM::Policy`
- `AWS::RDS::DBInstance`, `AWS::Lambda::Function`
- `AWS::ECS::Cluster`, `AWS::ECS::Service`

### Configuration Recorder Status

| Value | Description |
|-------|-------------|
| `true` (recording) | Recorder is actively recording |
| `false` (not recording) | Recorder is stopped |

### Conformance Pack States

| Status | Description |
|--------|-------------|
| `CREATE_IN_PROGRESS` | Pack is being created |
| `CREATE_COMPLETE` | Pack creation complete |
| `CREATE_FAILED` | Pack creation failed |
| `DELETE_IN_PROGRESS` | Pack is being deleted |
| `DELETE_FAILED` | Pack deletion failed |
