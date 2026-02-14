# CloudWatch RUM — Quick Reference

## All Commands

| Command | Description |
|---------|-------------|
| `create-app-monitor` | Create an application monitor |
| `get-app-monitor` | Retrieve app monitor details |
| `list-app-monitors` | List all app monitors |
| `update-app-monitor` | Modify an app monitor |
| `delete-app-monitor` | Delete an app monitor |
| `get-app-monitor-data` | Retrieve monitoring data from an app monitor |
| `put-rum-events` | Send RUM telemetry events |
| `batch-create-rum-metric-definitions` | Create multiple metric definitions |
| `batch-delete-rum-metric-definitions` | Delete multiple metric definitions |
| `batch-get-rum-metric-definitions` | Retrieve multiple metric definitions |
| `update-rum-metric-definition` | Update a metric definition |
| `put-rum-metrics-destination` | Create or update a metrics destination |
| `list-rum-metrics-destinations` | List metrics destinations for an app monitor |
| `delete-rum-metrics-destination` | Delete a metrics destination |
| `put-resource-policy` | Create or update a resource policy |
| `get-resource-policy` | Retrieve a resource policy |
| `delete-resource-policy` | Delete a resource policy |
| `tag-resource` | Add tags to a resource |
| `untag-resource` | Remove tags from a resource |
| `list-tags-for-resource` | List tags for a resource |

## Global Options

All commands accept these options:

| Option | Description |
|--------|-------------|
| `--output` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | JMESPath query to filter output |
| `--region` | AWS region |
| `--profile` | Named credential profile |
| `--no-cli-pager` | Disable pager for output |
| `--cli-input-json` | Read parameters from JSON string |
| `--cli-input-yaml` | Read parameters from YAML string |
| `--generate-cli-skeleton` | Print JSON/YAML input skeleton |

## Common Patterns

### List all active app monitors
```bash
aws rum list-app-monitors \
    --query 'AppMonitorSummaries[?State==`ACTIVE`].{Name:Name,Id:Id,Platform:Platform}'
```

### Get JavaScript error events from last 24 hours
```bash
aws rum get-app-monitor-data \
    --name my-web-app \
    --time-range After=$(date -d '24 hours ago' +%s) \
    --filters Name=EventType,Values=com.amazon.rum.js_error_event
```

### Check metric definitions for an app monitor
```bash
aws rum batch-get-rum-metric-definitions \
    --app-monitor-name my-web-app \
    --destination CloudWatch \
    --query 'MetricDefinitions[].{Name:Name,Id:MetricDefinitionId}'
```
