
# AWS CLI v2 — CloudWatch (Monitoring & Logs)

## Overview

Complete reference for `aws cloudwatch` (metrics, alarms, dashboards) and `aws logs` (CloudWatch Logs) subcommands in AWS CLI v2. Covers metric publishing and retrieval, alarm configuration, composite alarms, dashboard management, log group/stream operations, metric filters, Logs Insights queries, and subscription filters.

## Quick Reference — Common Workflows

### Create an alarm on ECS service CPU
```bash
aws cloudwatch put-metric-alarm --alarm-name ecs-high-cpu \
  --metric-name CPUUtilization --namespace AWS/ECS \
  --dimensions Name=ClusterName,Value=my-cluster Name=ServiceName,Value=my-service \
  --statistic Average --period 300 --threshold 80 \
  --comparison-operator GreaterThanThreshold --evaluation-periods 2 \
  --alarm-actions arn:aws:sns:us-east-1:123456789012:my-topic
```

### Query logs with Insights
```bash
aws logs start-query --log-group-name /ecs/my-service \
  --start-time $(date -d '1 hour ago' +%s) --end-time $(date +%s) \
  --query-string 'fields @timestamp, @message | filter @message like /ERROR/ | sort @timestamp desc | limit 20'
aws logs get-query-results --query-id <query-id>
```

### Create a log group with retention
```bash
aws logs create-log-group --log-group-name /ecs/my-service
aws logs put-retention-policy --log-group-name /ecs/my-service --retention-in-days 30
```

### Get metric statistics
```bash
aws cloudwatch get-metric-statistics --namespace AWS/ECS \
  --metric-name MemoryUtilization --dimensions Name=ClusterName,Value=my-cluster \
  --start-time 2026-02-11T00:00:00Z --end-time 2026-02-11T12:00:00Z \
  --period 3600 --statistics Average Maximum
```

### Tail logs in real time
```bash
aws logs tail /ecs/my-service --follow --since 10m
```

## Covered Command Groups

| Group | Commands | CLI Service |
|-------|----------|-------------|
| Metrics | put-metric-data, get-metric-data, get-metric-statistics, list-metrics | `aws cloudwatch` |
| Alarms | put-metric-alarm, put-composite-alarm, describe-alarms, delete-alarms, set-alarm-state, enable/disable-alarm-actions | `aws cloudwatch` |
| Dashboards | put-dashboard, get-dashboard, list-dashboards, delete-dashboards | `aws cloudwatch` |
| Anomaly Detection | put-anomaly-detector, describe-anomaly-detectors, delete-anomaly-detector | `aws cloudwatch` |
| Metric Streams | put-metric-stream, get-metric-stream, list-metric-streams, delete-metric-stream, start/stop-metric-streams | `aws cloudwatch` |
| Insight Rules | put-insight-rule, describe-insight-rules, delete-insight-rules, enable/disable-insight-rules, get-insight-rule-report | `aws cloudwatch` |
| Log Groups | create, delete, describe, put-retention-policy, tag/untag | `aws logs` |
| Log Streams | create, delete, describe | `aws logs` |
| Log Events | put, get, filter, tail | `aws logs` |
| Metric Filters | put, describe, delete | `aws logs` |
| Subscription Filters | put, describe, delete | `aws logs` |
| Logs Insights | start-query, stop-query, get-query-results, describe-queries | `aws logs` |

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Metrics | [`metrics.md`](metrics.md) | put-metric-data, get-metric-data, get-metric-statistics, list-metrics, get-metric-widget-image |
| Alarms | [`alarms.md`](alarms.md) | put-metric-alarm, put-composite-alarm, describe-alarms, describe-alarms-for-metric, describe-alarm-history, delete-alarms, set-alarm-state, enable-alarm-actions, disable-alarm-actions, describe-alarm-contributors |
| Dashboards | [`dashboards.md`](dashboards.md) | put-dashboard, get-dashboard, list-dashboards, delete-dashboards |
| Anomaly Detection | [`anomaly-detection.md`](anomaly-detection.md) | put-anomaly-detector, describe-anomaly-detectors, delete-anomaly-detector |
| Insight Rules | [`insight-rules.md`](insight-rules.md) | put-insight-rule, describe-insight-rules, get-insight-rule-report, delete-insight-rules, enable-insight-rules, disable-insight-rules |
| Metric Streams | [`metric-streams.md`](metric-streams.md) | put-metric-stream, get-metric-stream, list-metric-streams, delete-metric-stream, start-metric-streams, stop-metric-streams |
| Tags (cloudwatch) | [`tags-cloudwatch.md`](tags-cloudwatch.md) | tag-resource, untag-resource, list-tags-for-resource |
| Log Groups | [`log-groups.md`](log-groups.md) | create-log-group, delete-log-group, describe-log-groups, put-retention-policy, delete-retention-policy, associate-kms-key, disassociate-kms-key |
| Log Streams | [`log-streams.md`](log-streams.md) | create-log-stream, delete-log-stream, describe-log-streams |
| Log Events | [`log-events.md`](log-events.md) | put-log-events, get-log-events, filter-log-events, tail, get-log-record, start-live-tail |
| Metric Filters | [`metric-filters.md`](metric-filters.md) | put-metric-filter, describe-metric-filters, delete-metric-filter, test-metric-filter |
| Subscription Filters | [`subscription-filters.md`](subscription-filters.md) | put-subscription-filter, describe-subscription-filters, delete-subscription-filter |
| Destinations | [`destinations.md`](destinations.md) | put-destination, put-destination-policy, describe-destinations, delete-destination |
| Logs Insights | [`logs-insights.md`](logs-insights.md) | start-query, get-query-results, stop-query, describe-queries |
| Export Tasks | [`export-tasks.md`](export-tasks.md) | create-export-task, describe-export-tasks, cancel-export-task |
| Resource Policies | [`resource-policies.md`](resource-policies.md) | put-resource-policy, describe-resource-policies, delete-resource-policy |
| Log Data Protection | [`log-data-protection.md`](log-data-protection.md) | put-data-protection-policy, get-data-protection-policy, delete-data-protection-policy |
| Query Definitions | [`query-definitions.md`](query-definitions.md) | put-query-definition, describe-query-definitions, delete-query-definition |
| Log Anomaly Detection | [`log-anomaly-detection.md`](log-anomaly-detection.md) | create-log-anomaly-detector, get-log-anomaly-detector, list-log-anomaly-detectors, update-log-anomaly-detector, delete-log-anomaly-detector, list-anomalies, update-anomaly |
| Tags (logs) | [`tags-logs.md`](tags-logs.md) | tag-resource, untag-resource, list-tags-for-resource |
