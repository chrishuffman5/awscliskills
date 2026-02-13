# Lookout for Equipment — Quick Reference

## All Commands

| Command | Description |
|---------|-------------|
| `create-dataset` | Create a dataset for sensor data |
| `describe-dataset` | Describe a dataset |
| `list-datasets` | List datasets |
| `delete-dataset` | Delete a dataset |
| `import-dataset` | Import a dataset from another account/region |
| `start-data-ingestion-job` | Start ingesting data from S3 into a dataset |
| `describe-data-ingestion-job` | Describe a data ingestion job |
| `list-data-ingestion-jobs` | List data ingestion jobs |
| `create-model` | Train a new ML model |
| `describe-model` | Describe a model |
| `list-models` | List models |
| `update-model` | Update model configuration |
| `delete-model` | Delete a model |
| `describe-model-version` | Describe a specific model version |
| `list-model-versions` | List model versions |
| `update-active-model-version` | Set the active model version |
| `import-model-version` | Import a model version from another account/region |
| `create-inference-scheduler` | Create an inference scheduler |
| `describe-inference-scheduler` | Describe an inference scheduler |
| `list-inference-schedulers` | List inference schedulers |
| `update-inference-scheduler` | Update an inference scheduler |
| `delete-inference-scheduler` | Delete an inference scheduler |
| `start-inference-scheduler` | Start an inference scheduler |
| `stop-inference-scheduler` | Stop an inference scheduler |
| `list-inference-executions` | List inference executions |
| `list-inference-events` | List detected anomaly events |
| `create-label-group` | Create a label group |
| `describe-label-group` | Describe a label group |
| `list-label-groups` | List label groups |
| `update-label-group` | Update a label group |
| `delete-label-group` | Delete a label group |
| `create-label` | Create a label (anomaly annotation) |
| `describe-label` | Describe a label |
| `list-labels` | List labels |
| `delete-label` | Delete a label |
| `create-retraining-scheduler` | Create a retraining scheduler |
| `describe-retraining-scheduler` | Describe a retraining scheduler |
| `list-retraining-schedulers` | List retraining schedulers |
| `update-retraining-scheduler` | Update a retraining scheduler |
| `delete-retraining-scheduler` | Delete a retraining scheduler |
| `start-retraining-scheduler` | Start a retraining scheduler |
| `stop-retraining-scheduler` | Stop a retraining scheduler |
| `list-sensor-statistics` | List sensor data quality statistics |
| `put-resource-policy` | Create/update a resource policy |
| `describe-resource-policy` | Describe a resource policy |
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

### Check model training status
```bash
aws lookoutequipment describe-model --model-name my-model \
    --query '{Status:Status,Metrics:ModelMetrics}'
```

### List all anomaly events in a time range
```bash
aws lookoutequipment list-inference-events \
    --inference-scheduler-name my-scheduler \
    --interval-start-time 2024-01-01T00:00:00Z \
    --interval-end-time 2024-01-31T23:59:59Z \
    --query 'InferenceEventSummaries[].{Start:EventStartTime,End:EventEndTime,Duration:EventDurationInSeconds}'
```

### Get sensor data quality summary
```bash
aws lookoutequipment list-sensor-statistics \
    --dataset-name my-dataset \
    --query 'SensorStatisticsSummaries[?MissingValues.Percentage>`5`].{Sensor:SensorName,Missing:MissingValues.Percentage}'
```
