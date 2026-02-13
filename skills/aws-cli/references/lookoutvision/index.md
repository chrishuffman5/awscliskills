# Lookout for Vision — Quick Reference

## All Commands

| Command | Description |
|---------|-------------|
| `create-project` | Create a new Lookout for Vision project |
| `delete-project` | Delete a project (datasets and models must be removed first) |
| `describe-project` | Describe a project including its datasets |
| `list-projects` | List projects in the current region |
| `create-model` | Train a new model version within a project |
| `delete-model` | Delete a model version (must be stopped first) |
| `describe-model` | Describe a model version including status and performance metrics |
| `list-models` | List model versions in a project |
| `start-model` | Start hosting a model version for inference |
| `stop-model` | Stop a running model version |
| `detect-anomalies` | Detect anomalies in an image using a hosted model |
| `create-dataset` | Create a training or test dataset in a project |
| `delete-dataset` | Delete a dataset from a project |
| `describe-dataset` | Describe a dataset including image statistics |
| `list-dataset-entries` | List JSON Line entries in a dataset |
| `update-dataset-entries` | Add or update JSON Line entries in a dataset |
| `describe-model-packaging-job` | Describe a model packaging job for edge deployment |
| `list-model-packaging-jobs` | List model packaging jobs in a project |
| `start-model-packaging-job` | Start a model packaging job (creates Greengrass component) |
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

### Check model training status
```bash
aws lookoutvision describe-model \
    --project-name my-project \
    --model-version 1 \
    --query '{Status:ModelDescription.Status,Performance:ModelDescription.Performance}'
```

### List all projects with creation dates
```bash
aws lookoutvision list-projects \
    --query 'Projects[].{Name:ProjectName,Created:CreationTimestamp}'
```

### Get dataset image statistics
```bash
aws lookoutvision describe-dataset \
    --project-name my-project \
    --dataset-type train \
    --query 'DatasetDescription.ImageStats'
```
