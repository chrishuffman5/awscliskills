# AWS CLI v2 — CloudWatch Command Reference Index

> Based on AWS CLI v2 documentation. Sources: https://docs.aws.amazon.com/cli/latest/reference/cloudwatch/ and https://docs.aws.amazon.com/cli/latest/reference/logs/

---


## All CloudWatch Subcommands (Quick Reference)

### `aws cloudwatch` Commands

| Command | Category | Description |
|---------|----------|-------------|
| `delete-alarms` | Alarms | Delete one or more alarms |
| `delete-anomaly-detector` | Anomaly | Delete an anomaly detection model |
| `delete-dashboards` | Dashboards | Delete one or more dashboards |
| `delete-insight-rules` | Insight Rules | Delete one or more Contributor Insight rules |
| `delete-metric-stream` | Metric Streams | Delete a metric stream |
| `describe-alarm-contributors` | Alarms | Retrieve top contributors for alarm |
| `describe-alarm-history` | Alarms | Retrieve history for an alarm |
| `describe-alarms` | Alarms | Retrieve information about alarms |
| `describe-alarms-for-metric` | Alarms | Retrieve alarms for a metric |
| `describe-anomaly-detectors` | Anomaly | List anomaly detection models |
| `describe-insight-rules` | Insight Rules | List Contributor Insight rules |
| `disable-alarm-actions` | Alarms | Disable actions for alarms |
| `disable-insight-rules` | Insight Rules | Disable Contributor Insight rules |
| `enable-alarm-actions` | Alarms | Enable actions for alarms |
| `enable-insight-rules` | Insight Rules | Enable Contributor Insight rules |
| `get-dashboard` | Dashboards | Retrieve dashboard details |
| `get-insight-rule-report` | Insight Rules | Get Contributor Insight rule report |
| `get-metric-data` | Metrics | Retrieve metric values using queries |
| `get-metric-statistics` | Metrics | Retrieve statistics for a metric |
| `get-metric-stream` | Metric Streams | Get metric stream details |
| `get-metric-widget-image` | Metrics | Retrieve a snapshot graph as PNG |
| `list-dashboards` | Dashboards | List dashboards |
| `list-managed-insight-rules` | Insight Rules | List managed Contributor Insight rules |
| `list-metric-streams` | Metric Streams | List metric streams |
| `list-metrics` | Metrics | List available metrics |
| `list-tags-for-resource` | Tags | List tags for a resource |
| `put-anomaly-detector` | Anomaly | Create/update anomaly detection model |
| `put-composite-alarm` | Alarms | Create/update a composite alarm |
| `put-dashboard` | Dashboards | Create/update a dashboard |
| `put-insight-rule` | Insight Rules | Create/update Contributor Insight rule |
| `put-managed-insight-rules` | Insight Rules | Create managed Contributor Insight rules |
| `put-metric-alarm` | Alarms | Create/update a metric alarm |
| `put-metric-data` | Metrics | Publish metric data points |
| `put-metric-stream` | Metric Streams | Create/update a metric stream |
| `set-alarm-state` | Alarms | Temporarily set alarm state |
| `start-metric-streams` | Metric Streams | Start streaming for metric streams |
| `stop-metric-streams` | Metric Streams | Stop streaming for metric streams |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |

### `aws logs` Commands

| Command | Category | Description |
|---------|----------|-------------|
| `associate-kms-key` | Log Groups | Associate KMS key with log group |
| `cancel-export-task` | Export | Cancel an export task |
| `create-export-task` | Export | Export log data to S3 |
| `create-log-anomaly-detector` | Anomaly | Create log anomaly detector |
| `create-log-group` | Log Groups | Create a log group |
| `create-log-stream` | Log Streams | Create a log stream |
| `delete-data-protection-policy` | Data Protection | Delete data protection policy |
| `delete-destination` | Destinations | Delete a log destination |
| `delete-log-anomaly-detector` | Anomaly | Delete log anomaly detector |
| `delete-log-group` | Log Groups | Delete a log group |
| `delete-log-stream` | Log Streams | Delete a log stream |
| `delete-metric-filter` | Metric Filters | Delete a metric filter |
| `delete-query-definition` | Query Definitions | Delete a saved query |
| `delete-resource-policy` | Resource Policies | Delete a resource policy |
| `delete-retention-policy` | Log Groups | Remove retention policy (never expire) |
| `delete-subscription-filter` | Subscription Filters | Delete a subscription filter |
| `describe-destinations` | Destinations | List log destinations |
| `describe-export-tasks` | Export | List export tasks |
| `describe-log-groups` | Log Groups | List/describe log groups |
| `describe-log-streams` | Log Streams | List/describe log streams |
| `describe-metric-filters` | Metric Filters | List metric filters |
| `describe-queries` | Logs Insights | List Logs Insights queries |
| `describe-query-definitions` | Query Definitions | List saved query definitions |
| `describe-resource-policies` | Resource Policies | List resource policies |
| `describe-subscription-filters` | Subscription Filters | List subscription filters |
| `disassociate-kms-key` | Log Groups | Remove KMS key from log group |
| `filter-log-events` | Log Events | Filter log events by pattern |
| `get-data-protection-policy` | Data Protection | Get data protection policy |
| `get-log-events` | Log Events | Get log events from a stream |
| `get-log-record` | Log Events | Get a single log record |
| `get-query-results` | Logs Insights | Get query results |
| `list-tags-for-resource` | Tags | List tags for a resource |
| `put-data-protection-policy` | Data Protection | Set data protection policy |
| `put-destination` | Destinations | Create/update a destination |
| `put-destination-policy` | Destinations | Set access policy for a destination |
| `put-log-events` | Log Events | Upload log events to a stream |
| `put-metric-filter` | Metric Filters | Create/update a metric filter |
| `put-query-definition` | Query Definitions | Create/update a saved query |
| `put-resource-policy` | Resource Policies | Create/update a resource policy |
| `put-retention-policy` | Log Groups | Set retention policy on a log group |
| `put-subscription-filter` | Subscription Filters | Create/update a subscription filter |
| `start-live-tail` | Log Events | Start live tail session |
| `start-query` | Logs Insights | Start a Logs Insights query |
| `stop-query` | Logs Insights | Stop a running query |
| `tag-resource` | Tags | Add tags to a resource |
| `tail` | Log Events | Tail log group output |
| `test-metric-filter` | Metric Filters | Test a filter pattern |
| `untag-resource` | Tags | Remove tags from a resource |
| `update-log-anomaly-detector` | Anomaly | Update log anomaly detector |

---

# Part A — `aws cloudwatch`

---


## Global Options Reference

These options are available for all `aws cloudwatch` and `aws logs` commands:

| Option | Type | Description |
|--------|------|-------------|
| `--debug` | boolean | Enable debug logging |
| `--endpoint-url` | string | Override default service endpoint URL |
| `--no-verify-ssl` | boolean | Skip SSL certificate verification |
| `--no-paginate` | boolean | Disable automatic pagination |
| `--output` | string | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | JMESPath query to filter response |
| `--profile` | string | Named AWS CLI profile to use |
| `--region` | string | AWS Region to use |
| `--version` | string | Display CLI version |
| `--color` | string | Color output: `on`, `off`, `auto` |
| `--no-sign-request` | boolean | Do not sign requests (anonymous access) |
| `--ca-bundle` | string | CA certificate bundle for SSL verification |
| `--cli-read-timeout` | integer | Socket read timeout in seconds (default: 60) |
| `--cli-connect-timeout` | integer | Socket connect timeout in seconds (default: 60) |
| `--cli-binary-format` | string | Binary format: `base64` (default in v2) or `raw-in-base64-out` |
| `--no-cli-pager` | boolean | Disable CLI pager |
| `--cli-auto-prompt` | boolean | Auto-prompt for parameters |
| `--no-cli-auto-prompt` | boolean | Disable auto-prompt |
| `--cli-input-json` | string | Read arguments from JSON string |
| `--cli-input-yaml` | string | Read arguments from YAML string |
| `--generate-cli-skeleton` | string | Print skeleton input: `input`, `yaml-input`, `output` |
