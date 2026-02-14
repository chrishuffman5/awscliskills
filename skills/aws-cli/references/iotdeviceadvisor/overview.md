# AWS CLI v2 — IoT Device Advisor

## Overview

Complete reference for all `aws iotdeviceadvisor` subcommands in AWS CLI v2. Covers test suite definition management, test suite run execution and monitoring, endpoint configuration, and resource tagging. AWS IoT Device Advisor is a cloud-based testing service that validates IoT devices for reliable connectivity with AWS IoT Core. It provides pre-built tests to verify MQTT communication, TLS security, and device behavior against best practices.

## Quick Reference — Common Workflows

### Create a test suite definition
```bash
aws iotdeviceadvisor create-suite-definition \
    --suite-definition-configuration '{
        "suiteDefinitionName": "mqtt-connect-test",
        "rootGroup": "{\"configuration\":{},\"tests\":[{\"name\":\"MQTT_Connect\",\"configuration\":{\"EXECUTION_TIMEOUT\":120},\"id\":\"MQTT_Connect\"}]}",
        "devicePermissionRoleArn": "arn:aws:iam::123456789012:role/DeviceAdvisorRole",
        "devices": [{"thingArn": "arn:aws:iot:us-east-1:123456789012:thing/MyDevice"}],
        "protocol": "MqttV3_1_1"
    }'
```

### Get the Device Advisor endpoint and run tests
```bash
aws iotdeviceadvisor get-endpoint \
    --thing-arn arn:aws:iot:us-east-1:123456789012:thing/MyDevice

aws iotdeviceadvisor start-suite-run \
    --suite-definition-id qqcsmtyyjabl \
    --suite-run-configuration '{
        "primaryDevice": {
            "thingArn": "arn:aws:iot:us-east-1:123456789012:thing/MyDevice",
            "certificateArn": "arn:aws:iot:us-east-1:123456789012:cert/abc123"
        }
    }'
```

### Monitor test run and get report
```bash
aws iotdeviceadvisor get-suite-run \
    --suite-definition-id qqcsmtyyjabl \
    --suite-run-id nzlfyhaa18oa

aws iotdeviceadvisor get-suite-run-report \
    --suite-definition-id qqcsmtyyjabl \
    --suite-run-id nzlfyhaa18oa
```

### List suite definitions and runs
```bash
aws iotdeviceadvisor list-suite-definitions

aws iotdeviceadvisor list-suite-runs \
    --suite-definition-id qqcsmtyyjabl
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Suite Definitions | [suite-definitions.md](suite-definitions.md) | `create-suite-definition`, `get-suite-definition`, `update-suite-definition`, `delete-suite-definition`, `list-suite-definitions`, `get-endpoint` |
| Suite Runs | [suite-runs.md](suite-runs.md) | `start-suite-run`, `get-suite-run`, `get-suite-run-report`, `stop-suite-run`, `list-suite-runs` |
| Tags | [tags.md](tags.md) | `tag-resource`, `untag-resource`, `list-tags-for-resource` |
