# EventBridge Pipes — Quick Reference

## All Commands

| Command | Description |
|---------|-------------|
| `create-pipe` | Create a new EventBridge Pipe |
| `describe-pipe` | Retrieve pipe details including source/target parameters |
| `list-pipes` | List all pipes with optional filters |
| `update-pipe` | Modify an existing pipe |
| `delete-pipe` | Delete a pipe |
| `start-pipe` | Start a stopped pipe |
| `stop-pipe` | Stop a running pipe |
| `tag-resource` | Add tags to a pipe |
| `untag-resource` | Remove tags from a pipe |
| `list-tags-for-resource` | List tags for a pipe |

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

### List all running pipes
```bash
aws pipes list-pipes \
    --current-state RUNNING \
    --query 'Pipes[].{Name:Name,Source:Source,Target:Target}'
```

### Check pipe status
```bash
aws pipes describe-pipe --name my-pipe \
    --query '{State:CurrentState,Desired:DesiredState,Reason:StateReason}'
```

### List pipes filtering by source
```bash
aws pipes list-pipes \
    --source-prefix arn:aws:sqs:us-east-1:123456789012 \
    --query 'Pipes[].{Name:Name,Source:Source}'
```
