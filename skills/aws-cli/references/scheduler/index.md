# EventBridge Scheduler — Quick Reference

## All Commands

| Command | Description |
|---------|-------------|
| `create-schedule` | Create a new schedule |
| `get-schedule` | Get details about a schedule |
| `list-schedules` | List schedules with optional filters |
| `update-schedule` | Update an existing schedule |
| `delete-schedule` | Delete a schedule |
| `create-schedule-group` | Create a schedule group |
| `get-schedule-group` | Get details about a schedule group |
| `list-schedule-groups` | List schedule groups |
| `delete-schedule-group` | Delete a schedule group and its schedules |
| `tag-resource` | Add tags to a schedule group |
| `untag-resource` | Remove tags from a schedule group |
| `list-tags-for-resource` | List tags for a schedule group |

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

## Schedule Expression Formats

| Format | Syntax | Example |
|--------|--------|---------|
| One-time | `at(yyyy-mm-ddThh:mm:ss)` | `at(2026-03-01T08:00:00)` |
| Rate | `rate(value unit)` | `rate(5 minutes)`, `rate(1 hour)` |
| Cron | `cron(min hr dom mon dow yr)` | `cron(0 9 * * ? *)` |

## Common Patterns

### List all enabled schedules
```bash
aws scheduler list-schedules \
    --state ENABLED \
    --query 'Schedules[].{Name:Name,Group:GroupName,Target:Target.Arn}'
```

### Disable a schedule temporarily
```bash
aws scheduler update-schedule \
    --name my-schedule \
    --state DISABLED \
    --schedule-expression "rate(1 hour)" \
    --flexible-time-window Mode=OFF \
    --target '{"Arn":"arn:aws:lambda:us-east-1:123456789012:function:MyFunc","RoleArn":"arn:aws:iam::123456789012:role/Role"}'
```

### List schedules in a group
```bash
aws scheduler list-schedules \
    --group-name production-jobs \
    --query 'Schedules[].{Name:Name,State:State}'
```
