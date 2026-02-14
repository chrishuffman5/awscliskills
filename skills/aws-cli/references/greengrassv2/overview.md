# AWS CLI v2 — IoT Greengrass v2

## Overview

Complete reference for all `aws greengrassv2` subcommands in AWS CLI v2. Covers component management, core device operations, deployment lifecycle, connectivity configuration, client device association, and account service roles. AWS IoT Greengrass v2 extends AWS to edge devices so they can act on locally generated data while using the cloud for management, analytics, and storage.

## Quick Reference — Common Workflows

### Create and deploy a component
```bash
aws greengrassv2 create-component-version \
    --inline-recipe fileb://com.example.HelloWorld-1.0.0.json

aws greengrassv2 create-deployment \
    --target-arn arn:aws:iot:us-east-1:123456789012:thing/MyGreengrassCore \
    --deployment-name "Deploy HelloWorld" \
    --components '{"com.example.HelloWorld":{"componentVersion":"1.0.0"}}'
```

### Check core device health and installed components
```bash
aws greengrassv2 get-core-device \
    --core-device-thing-name MyGreengrassCore

aws greengrassv2 list-installed-components \
    --core-device-thing-name MyGreengrassCore
```

### Deploy to a thing group with rollout configuration
```bash
aws greengrassv2 create-deployment \
    --target-arn arn:aws:iot:us-east-1:123456789012:thinggroup/MyDeviceGroup \
    --deployment-name "Fleet deployment" \
    --components '{"com.example.HelloWorld":{"componentVersion":"1.0.0","configurationUpdate":{"merge":"{\"Message\":\"Hello from fleet\"}"}}}' \
    --iot-job-configuration '{"jobExecutionsRolloutConfig":{"maximumPerMinute":10},"abortConfig":{"criteriaList":[{"failureType":"ALL","action":"CANCEL","thresholdPercentage":30.0,"minNumberOfExecutedThings":5}]}}' \
    --deployment-policies '{"failureHandlingPolicy":"ROLLBACK","componentUpdatePolicy":{"timeoutInSeconds":60,"action":"NOTIFY_COMPONENTS"}}'
```

### Associate client devices with a core device
```bash
aws greengrassv2 batch-associate-client-device-with-core-device \
    --core-device-thing-name MyGreengrassCore \
    --entries thingName=ClientDevice1 thingName=ClientDevice2
```

### Update connectivity information
```bash
aws greengrassv2 update-connectivity-info \
    --thing-name MyGreengrassCore \
    --connectivity-info '[{"id":"localIP","hostAddress":"192.168.1.10","portNumber":8883}]'
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Components | [components.md](components.md) | `create-component-version`, `describe-component`, `get-component`, `get-component-version-artifact`, `list-components`, `list-component-versions`, `delete-component`, `resolve-component-candidates` |
| Core Devices | [core-devices.md](core-devices.md) | `get-core-device`, `list-core-devices`, `delete-core-device`, `get-connectivity-info`, `update-connectivity-info`, `batch-associate-client-device-with-core-device`, `batch-disassociate-client-device-from-core-device`, `list-client-devices-associated-with-core-device`, `list-installed-components` |
| Deployments | [deployments.md](deployments.md) | `create-deployment`, `get-deployment`, `list-deployments`, `cancel-deployment`, `delete-deployment`, `list-effective-deployments` |
| Account & Service Role | [account.md](account.md) | `associate-service-role-to-account`, `disassociate-service-role-from-account`, `get-service-role-for-account` |
| Tags | [tags.md](tags.md) | `tag-resource`, `untag-resource`, `list-tags-for-resource` |
