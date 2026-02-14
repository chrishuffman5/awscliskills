# AWS CLI v2 — MediaLive

## Overview

Complete reference for all `aws medialive` subcommands in AWS CLI v2. Covers live video channel management, input configuration, input security groups, input device management, multiplexing, schedule actions, reservations and offerings, Anywhere clusters and nodes, networks, channel placement groups, signal maps, CloudWatch alarm templates, EventBridge rule templates, SDI sources, tagging, and batch operations. AWS Elemental MediaLive is a real-time video encoding service for creating live video streams for broadcast and internet delivery.

## Quick Reference — Common Workflows

### Create an input and channel
```bash
aws medialive create-input \
    --name "my-rtmp-input" \
    --type RTMP_PUSH \
    --destinations '[{"StreamName":"live/stream1"},{"StreamName":"live/stream2"}]' \
    --input-security-groups '["12345678"]'

aws medialive create-channel \
    --name "my-channel" \
    --channel-class SINGLE_PIPELINE \
    --input-attachments '[{"InputId":"1234567"}]' \
    --destinations file://destinations.json \
    --encoder-settings file://encoder-settings.json \
    --role-arn arn:aws:iam::123456789012:role/MediaLiveRole
```

### Start and stop a channel
```bash
aws medialive start-channel --channel-id 1234567

aws medialive stop-channel --channel-id 1234567
```

### Create a multiplex for channel bonding
```bash
aws medialive create-multiplex \
    --name "my-multiplex" \
    --availability-zones us-east-1a us-east-1b \
    --multiplex-settings '{"TransportStreamBitrate":10000000,"TransportStreamId":1}'

aws medialive create-multiplex-program \
    --multiplex-id 1234567 \
    --program-name "program-1" \
    --multiplex-program-settings file://program-settings.json
```

### Schedule an input switch
```bash
aws medialive batch-update-schedule \
    --channel-id 1234567 \
    --creates '{"ScheduleActions":[{"ActionName":"switch-input","ScheduleActionStartSettings":{"FixedModeScheduleActionStartSettings":{"Time":"2025-06-01T12:00:00Z"}},"ScheduleActionSettings":{"InputSwitchSettings":{"InputAttachmentNameReference":"backup-input"}}}]}'
```

### Purchase a reservation
```bash
aws medialive list-offerings \
    --query 'Offerings[?ResourceSpecification.ResourceType==`INPUT`]'

aws medialive purchase-offering \
    --offering-id 87654321 \
    --count 1 \
    --name "my-input-reservation"
```

### Create a signal map for monitoring
```bash
aws medialive create-signal-map \
    --name "production-signal-map" \
    --discovery-entry-point-arn arn:aws:medialive:us-east-1:123456789012:channel:1234567
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Channels | [channels.md](channels.md) | `create-channel`, `describe-channel`, `update-channel`, `update-channel-class`, `delete-channel`, `start-channel`, `stop-channel`, `restart-channel-pipelines`, `list-channels` |
| Inputs | [inputs.md](inputs.md) | `create-input`, `describe-input`, `update-input`, `delete-input`, `list-inputs`, `create-partner-input` |
| Input Security Groups | [input-security-groups.md](input-security-groups.md) | `create-input-security-group`, `describe-input-security-group`, `update-input-security-group`, `delete-input-security-group`, `list-input-security-groups` |
| Input Devices | [input-devices.md](input-devices.md) | `describe-input-device`, `update-input-device`, `list-input-devices`, `start-input-device`, `stop-input-device`, `reboot-input-device`, `describe-input-device-thumbnail`, `transfer-input-device`, `accept-input-device-transfer`, `cancel-input-device-transfer`, `reject-input-device-transfer`, `list-input-device-transfers`, `start-input-device-maintenance-window` |
| Multiplexes | [multiplexes.md](multiplexes.md) | `create-multiplex`, `describe-multiplex`, `update-multiplex`, `delete-multiplex`, `start-multiplex`, `stop-multiplex`, `list-multiplexes`, `create-multiplex-program`, `describe-multiplex-program`, `update-multiplex-program`, `delete-multiplex-program`, `list-multiplex-programs`, `list-multiplex-alerts` |
| Schedules | [schedules.md](schedules.md) | `batch-update-schedule`, `describe-schedule`, `delete-schedule` |
| Reservations & Offerings | [reservations.md](reservations.md) | `purchase-offering`, `describe-offering`, `list-offerings`, `describe-reservation`, `update-reservation`, `delete-reservation`, `list-reservations` |
| Clusters & Nodes | [clusters-nodes.md](clusters-nodes.md) | `create-cluster`, `describe-cluster`, `update-cluster`, `delete-cluster`, `list-clusters`, `create-node`, `describe-node`, `update-node`, `update-node-state`, `delete-node`, `list-nodes`, `create-node-registration-script`, `list-cluster-alerts` |
| Networks | [networks.md](networks.md) | `create-network`, `describe-network`, `update-network`, `delete-network`, `list-networks` |
| Channel Placement Groups | [channel-placement-groups.md](channel-placement-groups.md) | `create-channel-placement-group`, `describe-channel-placement-group`, `update-channel-placement-group`, `delete-channel-placement-group`, `list-channel-placement-groups` |
| Signal Maps | [signal-maps.md](signal-maps.md) | `create-signal-map`, `get-signal-map`, `start-update-signal-map`, `delete-signal-map`, `list-signal-maps`, `start-monitor-deployment`, `start-delete-monitor-deployment` |
| CloudWatch Alarm Templates | [alarm-templates.md](alarm-templates.md) | `create-cloud-watch-alarm-template`, `get-cloud-watch-alarm-template`, `update-cloud-watch-alarm-template`, `delete-cloud-watch-alarm-template`, `list-cloud-watch-alarm-templates`, `create-cloud-watch-alarm-template-group`, `get-cloud-watch-alarm-template-group`, `update-cloud-watch-alarm-template-group`, `delete-cloud-watch-alarm-template-group`, `list-cloud-watch-alarm-template-groups` |
| EventBridge Rule Templates | [rule-templates.md](rule-templates.md) | `create-event-bridge-rule-template`, `get-event-bridge-rule-template`, `update-event-bridge-rule-template`, `delete-event-bridge-rule-template`, `list-event-bridge-rule-templates`, `create-event-bridge-rule-template-group`, `get-event-bridge-rule-template-group`, `update-event-bridge-rule-template-group`, `delete-event-bridge-rule-template-group`, `list-event-bridge-rule-template-groups` |
| SDI Sources | [sdi-sources.md](sdi-sources.md) | `create-sdi-source`, `describe-sdi-source`, `update-sdi-source`, `delete-sdi-source`, `list-sdi-sources` |
| Tags, Batch & Account | [tags-batch-account.md](tags-batch-account.md) | `create-tags`, `delete-tags`, `list-tags-for-resource`, `batch-delete`, `batch-start`, `batch-stop`, `describe-account-configuration`, `update-account-configuration`, `list-versions`, `list-alerts`, `describe-thumbnails`, `claim-device` |
