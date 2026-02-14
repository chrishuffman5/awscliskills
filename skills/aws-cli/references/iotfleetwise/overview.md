# AWS CLI v2 — IoT FleetWise

## Overview

Complete reference for all `aws iotfleetwise` subcommands in AWS CLI v2. Covers signal catalog management, vehicle model manifests, decoder manifests, vehicle and fleet management, data collection campaigns, state templates, account configuration, and resource tagging. AWS IoT FleetWise enables collecting, transforming, and transferring vehicle data to the cloud for analysis.

## Quick Reference — Common Workflows

### Register account and set up signal catalog
```bash
aws iotfleetwise register-account

aws iotfleetwise create-signal-catalog \
    --name my-signal-catalog \
    --nodes '[{"branch":{"fullyQualifiedName":"Vehicle"}},{"sensor":{"fullyQualifiedName":"Vehicle.Speed","dataType":"DOUBLE","unit":"km/h"}}]'
```

### Create model manifest and decoder manifest
```bash
aws iotfleetwise create-model-manifest \
    --name my-model-manifest \
    --signal-catalog-arn arn:aws:iotfleetwise:us-east-1:123456789012:signal-catalog/my-signal-catalog \
    --nodes "Vehicle.Speed"

aws iotfleetwise update-model-manifest \
    --name my-model-manifest --status ACTIVE

aws iotfleetwise create-decoder-manifest \
    --name my-decoder-manifest \
    --model-manifest-arn arn:aws:iotfleetwise:us-east-1:123456789012:model-manifest/my-model-manifest \
    --network-interfaces '[{"interfaceId":"CAN1","type":"CAN_INTERFACE","canInterface":{"name":"CAN_Bus","protocolName":"CAN","protocolVersion":"2.0"}}]' \
    --signal-decoders '[{"fullyQualifiedName":"Vehicle.Speed","type":"CAN_SIGNAL","interfaceId":"CAN1","canSignal":{"messageId":100,"isBigEndian":false,"isSigned":false,"startBit":0,"offset":0,"factor":0.1,"length":16}}]'

aws iotfleetwise update-decoder-manifest \
    --name my-decoder-manifest --status ACTIVE
```

### Create vehicle and fleet
```bash
aws iotfleetwise create-vehicle \
    --vehicle-name vehicle-001 \
    --model-manifest-arn arn:aws:iotfleetwise:us-east-1:123456789012:model-manifest/my-model-manifest \
    --decoder-manifest-arn arn:aws:iotfleetwise:us-east-1:123456789012:decoder-manifest/my-decoder-manifest \
    --attributes '{"make":"Toyota","model":"Camry","year":"2024"}'

aws iotfleetwise create-fleet \
    --fleet-id my-fleet \
    --signal-catalog-arn arn:aws:iotfleetwise:us-east-1:123456789012:signal-catalog/my-signal-catalog

aws iotfleetwise associate-vehicle-fleet \
    --vehicle-name vehicle-001 \
    --fleet-id my-fleet
```

### Create and approve a data collection campaign
```bash
aws iotfleetwise create-campaign \
    --name speed-collection \
    --signal-catalog-arn arn:aws:iotfleetwise:us-east-1:123456789012:signal-catalog/my-signal-catalog \
    --target-arn arn:aws:iotfleetwise:us-east-1:123456789012:fleet/my-fleet \
    --collection-scheme '{"timeBasedCollectionScheme":{"periodMs":60000}}' \
    --signals-to-collect '[{"name":"Vehicle.Speed","maxSampleCount":100,"minimumSamplingIntervalMs":1000}]' \
    --data-destination-configs '[{"s3Config":{"bucketArn":"arn:aws:s3:::my-bucket","dataFormat":"PARQUET","storageCompressionFormat":"GZIP","prefix":"vehicle-data"}}]'

aws iotfleetwise update-campaign \
    --name speed-collection --action APPROVE
```

### Create a state template
```bash
aws iotfleetwise create-state-template \
    --name my-state-template \
    --signal-catalog-arn arn:aws:iotfleetwise:us-east-1:123456789012:signal-catalog/my-signal-catalog \
    --state-template-properties "Vehicle.Speed" "Vehicle.EngineRPM"
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Signal Catalogs | [signal-catalogs.md](signal-catalogs.md) | `create-signal-catalog`, `get-signal-catalog`, `list-signal-catalogs`, `update-signal-catalog`, `delete-signal-catalog`, `import-signal-catalog`, `list-signal-catalog-nodes` |
| Model Manifests | [model-manifests.md](model-manifests.md) | `create-model-manifest`, `get-model-manifest`, `list-model-manifests`, `update-model-manifest`, `delete-model-manifest`, `list-model-manifest-nodes` |
| Decoder Manifests | [decoder-manifests.md](decoder-manifests.md) | `create-decoder-manifest`, `get-decoder-manifest`, `list-decoder-manifests`, `update-decoder-manifest`, `delete-decoder-manifest`, `import-decoder-manifest`, `list-decoder-manifest-network-interfaces`, `list-decoder-manifest-signals` |
| Vehicles | [vehicles.md](vehicles.md) | `create-vehicle`, `get-vehicle`, `list-vehicles`, `update-vehicle`, `delete-vehicle`, `batch-create-vehicle`, `batch-update-vehicle`, `get-vehicle-status` |
| Fleets | [fleets.md](fleets.md) | `create-fleet`, `get-fleet`, `list-fleets`, `update-fleet`, `delete-fleet`, `associate-vehicle-fleet`, `disassociate-vehicle-fleet`, `list-fleets-for-vehicle`, `list-vehicles-in-fleet` |
| Campaigns | [campaigns.md](campaigns.md) | `create-campaign`, `get-campaign`, `list-campaigns`, `update-campaign`, `delete-campaign` |
| State Templates | [state-templates.md](state-templates.md) | `create-state-template`, `get-state-template`, `list-state-templates`, `update-state-template`, `delete-state-template` |
| Account & Configuration | [account-config.md](account-config.md) | `register-account`, `get-register-account-status`, `put-encryption-configuration`, `get-encryption-configuration`, `put-logging-options`, `get-logging-options` |
| Tags | [tags.md](tags.md) | `tag-resource`, `untag-resource`, `list-tags-for-resource` |
