# Elastic Transcoder — Quick Reference

**Legacy Service:** For new workloads, use AWS Elemental MediaConvert instead.

## All Commands

| Command | Description |
|---------|-------------|
| `cancel-job` | Cancel a transcoding job |
| `create-job` | Create a transcoding job |
| `create-pipeline` | Create a transcoding pipeline |
| `create-preset` | Create a custom transcoding preset |
| `delete-pipeline` | Delete a pipeline |
| `delete-preset` | Delete a custom preset |
| `list-jobs-by-pipeline` | List jobs for a specific pipeline |
| `list-jobs-by-status` | List jobs by status |
| `list-pipelines` | List pipelines |
| `list-presets` | List presets (system and custom) |
| `read-job` | Get details for a job |
| `read-pipeline` | Get details for a pipeline |
| `read-preset` | Get details for a preset |
| `update-pipeline` | Update a pipeline |
| `update-pipeline-notifications` | Update pipeline notification settings |
| `update-pipeline-status` | Pause or activate a pipeline |
| `wait` | Wait for a resource to reach a specific state |

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

### Check job status
```bash
aws elastictranscoder read-job --id 1234567890123-abcdef \
    --query 'Job.{Id:Id,Status:Status,Output:Output.Status}'
```

### List completed jobs for a pipeline
```bash
aws elastictranscoder list-jobs-by-pipeline \
    --pipeline-id 1234567890123-abcdef \
    --query 'Jobs[?Status==`Complete`].{Id:Id,Key:Output.Key}'
```

### List system presets
```bash
aws elastictranscoder list-presets \
    --query 'Presets[?Type==`System`].{Id:Id,Name:Name,Container:Container}'
```

## Wait Conditions

| Waiter | Description |
|--------|-------------|
| `job-complete` | Wait until a job reaches Complete status |
