# IoT Events — Quick Reference

## All Commands

| Command | Service | Description |
|---------|---------|-------------|
| `batch-acknowledge-alarm` | iotevents-data | Acknowledge one or more alarms |
| `batch-delete-detector` | iotevents-data | Delete one or more detector instances |
| `batch-disable-alarm` | iotevents-data | Disable one or more alarms |
| `batch-enable-alarm` | iotevents-data | Enable one or more alarms |
| `batch-put-message` | iotevents-data | Send messages (inputs) to detectors |
| `batch-reset-alarm` | iotevents-data | Reset one or more alarms |
| `batch-snooze-alarm` | iotevents-data | Snooze one or more alarms |
| `batch-update-detector` | iotevents-data | Update one or more detector instances |
| `create-alarm-model` | iotevents | Create an alarm model |
| `create-detector-model` | iotevents | Create a detector model (state machine) |
| `create-input` | iotevents | Create an input for detector/alarm data |
| `delete-alarm-model` | iotevents | Delete an alarm model |
| `delete-detector-model` | iotevents | Delete a detector model |
| `delete-input` | iotevents | Delete an input |
| `describe-alarm` | iotevents-data | Describe an alarm instance |
| `describe-alarm-model` | iotevents | Describe an alarm model |
| `describe-detector` | iotevents-data | Describe a detector instance |
| `describe-detector-model` | iotevents | Describe a detector model |
| `describe-detector-model-analysis` | iotevents | Describe a detector model analysis |
| `describe-input` | iotevents | Describe an input |
| `describe-logging-options` | iotevents | Describe logging options |
| `get-detector-model-analysis-results` | iotevents | Get detector model analysis results |
| `list-alarm-model-versions` | iotevents | List alarm model versions |
| `list-alarm-models` | iotevents | List alarm models |
| `list-alarms` | iotevents-data | List alarm instances |
| `list-detector-model-versions` | iotevents | List detector model versions |
| `list-detector-models` | iotevents | List detector models |
| `list-detectors` | iotevents-data | List detector instances |
| `list-input-routings` | iotevents | List input routings |
| `list-inputs` | iotevents | List inputs |
| `list-tags-for-resource` | iotevents | List tags for a resource |
| `put-logging-options` | iotevents | Set logging options |
| `start-detector-model-analysis` | iotevents | Start analyzing a detector model |
| `tag-resource` | iotevents | Add tags to a resource |
| `untag-resource` | iotevents | Remove tags from a resource |
| `update-alarm-model` | iotevents | Update an alarm model |
| `update-detector-model` | iotevents | Update a detector model |
| `update-input` | iotevents | Update an input |

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

### Check all detector instances for a model
```bash
aws iotevents-data list-detectors \
    --detector-model-name PressureDetector \
    --query 'detectorSummaries[].{Key:keyValue,State:state.stateName}'
```

### List active alarms
```bash
aws iotevents-data list-alarms \
    --alarm-model-name HighPressureAlarm \
    --query 'alarmSummaries[?stateName==`ACTIVE`]'
```

### Get detector model analysis errors
```bash
aws iotevents start-detector-model-analysis \
    --detector-model-definition file://model.json

aws iotevents get-detector-model-analysis-results \
    --analysis-id abc123
```
