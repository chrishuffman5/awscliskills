# AWS CLI v2 — IoT Wireless

## Overview

Complete reference for all `aws iotwireless` subcommands in AWS CLI v2. Covers wireless device management (LoRaWAN and Sidewalk), wireless gateway operations, destinations, device and service profiles, FUOTA (firmware update over the air) tasks, multicast groups, device import, network analyzer, event configuration, logging, metrics, partner accounts, positioning, and resource tagging. AWS IoT Wireless connects and manages wireless devices using LoRaWAN and Sidewalk protocols.

## Quick Reference — Common Workflows

### Create a LoRaWAN device with OTAA
```bash
aws iotwireless create-device-profile \
    --name my-lorawan-profile \
    --lorawan '{"MacVersion":"1.0.3","RegParamsRevision":"RP002-1.0.1","RfRegion":"US915","SupportsJoin":true}'

aws iotwireless create-service-profile \
    --name my-service-profile

aws iotwireless create-destination \
    --name my-destination \
    --expression-type RuleName \
    --expression IoTWirelessRule \
    --role-arn arn:aws:iam::123456789012:role/IoTWirelessRole

aws iotwireless create-wireless-device \
    --type LoRaWAN \
    --destination-name my-destination \
    --name my-lorawan-device \
    --lorawan '{"DevEui":"ac12efc654d23fc2","DeviceProfileId":"PROFILE_ID","ServiceProfileId":"SERVICE_ID","OtaaV1_0_x":{"AppKey":"3f4ca100e2fc675ea123f4eb12c4a012","AppEui":"b4c231a359bc2e3d"}}'
```

### Register a LoRaWAN gateway
```bash
aws iotwireless create-wireless-gateway \
    --name my-lorawan-gateway \
    --lorawan '{"GatewayEui":"a1b2c3d4567890ab","RfRegion":"US915"}'
```

### Start a firmware update (FUOTA)
```bash
aws iotwireless create-fuota-task \
    --name firmware-v2 \
    --firmware-update-image s3://my-bucket/firmware/v2.bin \
    --firmware-update-role arn:aws:iam::123456789012:role/FuotaRole \
    --lorawan '{"RfRegion":"US915"}'

aws iotwireless associate-wireless-device-with-fuota-task \
    --id FUOTA_TASK_ID \
    --wireless-device-id DEVICE_ID

aws iotwireless start-fuota-task --id FUOTA_TASK_ID
```

### Send data to a device
```bash
aws iotwireless send-data-to-wireless-device \
    --id DEVICE_ID \
    --transmit-mode 1 \
    --payload-data "SGVsbG8gV29ybGQ=" \
    --wireless-metadata '{"LoRaWAN":{"FPort":1}}'
```

### Create a multicast group
```bash
aws iotwireless create-multicast-group \
    --name my-multicast \
    --lorawan '{"RfRegion":"US915","DlClass":"ClassC"}'

aws iotwireless associate-wireless-device-with-multicast-group \
    --id MULTICAST_GROUP_ID \
    --wireless-device-id DEVICE_ID
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Wireless Devices | [wireless-devices.md](wireless-devices.md) | `create-wireless-device`, `get-wireless-device`, `list-wireless-devices`, `update-wireless-device`, `delete-wireless-device`, `get-wireless-device-statistics`, `send-data-to-wireless-device`, `test-wireless-device`, `deregister-wireless-device`, `delete-queued-messages`, `list-queued-messages` |
| Wireless Gateways | [wireless-gateways.md](wireless-gateways.md) | `create-wireless-gateway`, `get-wireless-gateway`, `list-wireless-gateways`, `update-wireless-gateway`, `delete-wireless-gateway`, `get-wireless-gateway-statistics`, `get-wireless-gateway-certificate`, `get-wireless-gateway-firmware-information`, `associate-wireless-gateway-with-certificate`, `disassociate-wireless-gateway-from-certificate`, `associate-wireless-gateway-with-thing`, `disassociate-wireless-gateway-from-thing` |
| Gateway Tasks | [gateway-tasks.md](gateway-tasks.md) | `create-wireless-gateway-task`, `get-wireless-gateway-task`, `delete-wireless-gateway-task`, `create-wireless-gateway-task-definition`, `get-wireless-gateway-task-definition`, `delete-wireless-gateway-task-definition`, `list-wireless-gateway-task-definitions` |
| Destinations | [destinations.md](destinations.md) | `create-destination`, `get-destination`, `list-destinations`, `update-destination`, `delete-destination` |
| Profiles | [profiles.md](profiles.md) | `create-device-profile`, `get-device-profile`, `list-device-profiles`, `delete-device-profile`, `create-service-profile`, `get-service-profile`, `list-service-profiles`, `delete-service-profile` |
| FUOTA Tasks | [fuota.md](fuota.md) | `create-fuota-task`, `get-fuota-task`, `list-fuota-tasks`, `update-fuota-task`, `delete-fuota-task`, `start-fuota-task`, `associate-wireless-device-with-fuota-task`, `disassociate-wireless-device-from-fuota-task`, `associate-multicast-group-with-fuota-task`, `disassociate-multicast-group-from-fuota-task` |
| Multicast Groups | [multicast.md](multicast.md) | `create-multicast-group`, `get-multicast-group`, `list-multicast-groups`, `update-multicast-group`, `delete-multicast-group`, `get-multicast-group-session`, `start-multicast-group-session`, `cancel-multicast-group-session`, `send-data-to-multicast-group`, `associate-wireless-device-with-multicast-group`, `disassociate-wireless-device-from-multicast-group`, `start-bulk-associate-wireless-device-with-multicast-group`, `start-bulk-disassociate-wireless-device-from-multicast-group`, `list-multicast-groups-by-fuota-task` |
| Device Import | [device-import.md](device-import.md) | `start-single-wireless-device-import-task`, `start-wireless-device-import-task`, `get-wireless-device-import-task`, `list-wireless-device-import-tasks`, `delete-wireless-device-import-task`, `update-wireless-device-import-task`, `list-devices-for-wireless-device-import-task` |
| Network Analyzer | [network-analyzer.md](network-analyzer.md) | `create-network-analyzer-configuration`, `get-network-analyzer-configuration`, `list-network-analyzer-configurations`, `update-network-analyzer-configuration`, `delete-network-analyzer-configuration` |
| Events & Logging | [events-logging.md](events-logging.md) | `get-event-configuration-by-resource-types`, `update-event-configuration-by-resource-types`, `get-resource-event-configuration`, `update-resource-event-configuration`, `list-event-configurations`, `get-log-levels-by-resource-types`, `update-log-levels-by-resource-types`, `get-resource-log-level`, `put-resource-log-level`, `reset-resource-log-level`, `reset-all-resource-log-levels` |
| Metrics & Partner Accounts | [metrics-partners.md](metrics-partners.md) | `get-metrics`, `get-metric-configuration`, `update-metric-configuration`, `associate-aws-account-with-partner-account`, `disassociate-aws-account-from-partner-account`, `get-partner-account`, `list-partner-accounts`, `update-partner-account` |
| Position & Service | [position-service.md](position-service.md) | `get-position-estimate`, `get-resource-position`, `update-resource-position`, `get-service-endpoint`, `associate-wireless-device-with-thing`, `disassociate-wireless-device-from-thing` |
| Tags | [tags.md](tags.md) | `tag-resource`, `untag-resource`, `list-tags-for-resource` |
