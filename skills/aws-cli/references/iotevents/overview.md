# AWS CLI v2 — IoT Events

## Overview

Complete reference for `aws iotevents` and `aws iotevents-data` subcommands in AWS CLI v2. This merged reference covers IoT Events detector models (state machines), inputs, alarm models, runtime operations for detectors and alarms, logging, and tagging. IoT Events monitors IoT sensor data and triggers actions when significant events are detected, using detector models (finite state machines) and alarm models (threshold-based monitoring).

## Quick Reference — Common Workflows

### Create an input and detector model
```bash
# Create an input to receive sensor data
aws iotevents create-input \
    --input-name PressureInput \
    --input-definition '{"attributes":[{"jsonPath":"sensorData.pressure"},{"jsonPath":"motorid"}]}'

# Create a detector model (state machine)
aws iotevents create-detector-model \
    --detector-model-name PressureDetector \
    --detector-model-definition file://detector-model.json \
    --role-arn arn:aws:iam::123456789012:role/IoTEventsRole \
    --key motorid \
    --evaluation-method BATCH
```

### Create an alarm model
```bash
aws iotevents create-alarm-model \
    --alarm-model-name HighPressureAlarm \
    --role-arn arn:aws:iam::123456789012:role/IoTEventsRole \
    --alarm-rule '{"simpleRule":{"inputProperty":"$input.PressureInput.sensorData.pressure","comparisonOperator":"GREATER","threshold":"70"}}' \
    --severity 3
```

### Send data to a detector
```bash
aws iotevents-data batch-put-message \
    --messages '[{"messageId":"msg001","inputName":"PressureInput","payload":"{\"motorid\":\"motor-01\",\"sensorData\":{\"pressure\":85}}"}]'
```

### Check detector and alarm state
```bash
# Check detector state
aws iotevents-data describe-detector \
    --detector-model-name PressureDetector \
    --key-value motor-01

# Check alarm state
aws iotevents-data describe-alarm \
    --alarm-model-name HighPressureAlarm \
    --key-value motor-01
```

### Acknowledge and manage alarms
```bash
aws iotevents-data batch-acknowledge-alarm \
    --acknowledge-action-requests '[{"alarmModelName":"HighPressureAlarm","keyValue":"motor-01","requestId":"ack001","note":"Investigating"}]'
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Detector Models | [detector-models.md](detector-models.md) | `create-detector-model`, `describe-detector-model`, `list-detector-models`, `update-detector-model`, `delete-detector-model`, `list-detector-model-versions`, `start-detector-model-analysis`, `describe-detector-model-analysis`, `get-detector-model-analysis-results` |
| Inputs | [inputs.md](inputs.md) | `create-input`, `describe-input`, `list-inputs`, `update-input`, `delete-input`, `list-input-routings` |
| Alarm Models | [alarm-models.md](alarm-models.md) | `create-alarm-model`, `describe-alarm-model`, `list-alarm-models`, `update-alarm-model`, `delete-alarm-model`, `list-alarm-model-versions` |
| Detectors Runtime | [detectors-runtime.md](detectors-runtime.md) | `describe-detector` (iotevents-data), `list-detectors` (iotevents-data), `batch-put-message` (iotevents-data), `batch-update-detector` (iotevents-data), `batch-delete-detector` (iotevents-data) |
| Alarms Runtime | [alarms-runtime.md](alarms-runtime.md) | `describe-alarm` (iotevents-data), `list-alarms` (iotevents-data), `batch-acknowledge-alarm` (iotevents-data), `batch-disable-alarm` (iotevents-data), `batch-enable-alarm` (iotevents-data), `batch-reset-alarm` (iotevents-data), `batch-snooze-alarm` (iotevents-data) |
| Logging | [logging.md](logging.md) | `describe-logging-options`, `put-logging-options` |
| Tags | [tags.md](tags.md) | `tag-resource`, `untag-resource`, `list-tags-for-resource` |
