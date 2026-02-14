# AWS CLI v2 — IoT TwinMaker

## Overview

Complete reference for all `aws iottwinmaker` subcommands in AWS CLI v2. Covers workspace management, entity and component type modeling, 3D scene creation, property value operations, sync jobs, metadata transfer jobs, queries, pricing, and tagging. IoT TwinMaker builds digital twins of real-world systems by connecting data from IoT sensors, cameras, and enterprise applications to create virtual representations of physical environments.

## Quick Reference — Common Workflows

### Create a workspace

```bash
aws iottwinmaker create-workspace \
    --workspace-id my-factory \
    --description "Digital twin of manufacturing facility" \
    --s3-location arn:aws:s3:::my-twinmaker-bucket \
    --role arn:aws:iam::123456789012:role/TwinMakerRole
```

### Define a component type and create an entity

```bash
aws iottwinmaker create-component-type \
    --workspace-id my-factory \
    --component-type-id com.example.TemperatureSensor \
    --property-definitions '{"temperature":{"dataType":{"type":"DOUBLE","unitOfMeasure":"Celsius"},"isTimeSeries":true}}'

aws iottwinmaker create-entity \
    --workspace-id my-factory \
    --entity-name "Conveyor Belt 1" \
    --components '{"sensor":{"componentTypeId":"com.example.TemperatureSensor"}}'
```

### Create a 3D scene

```bash
aws iottwinmaker create-scene \
    --workspace-id my-factory \
    --scene-id factory-floor \
    --content-location s3://my-twinmaker-bucket/scenes/factory-floor.json
```

### Read and write property values

```bash
aws iottwinmaker get-property-value \
    --workspace-id my-factory \
    --entity-id my-entity-id \
    --component-name sensor \
    --selected-properties temperature

aws iottwinmaker batch-put-property-values \
    --workspace-id my-factory \
    --entries '[{"entityPropertyReference":{"entityId":"my-entity-id","componentName":"sensor","propertyName":"temperature"},"propertyValues":[{"value":{"doubleValue":23.5},"time":"2024-01-15T10:30:00Z"}]}]'
```

### Set up SiteWise sync

```bash
aws iottwinmaker create-sync-job \
    --workspace-id my-factory \
    --sync-source SITEWISE \
    --sync-role arn:aws:iam::123456789012:role/TwinMakerSyncRole
```

### Query the digital twin knowledge graph

```bash
aws iottwinmaker execute-query \
    --workspace-id my-factory \
    --query-statement "SELECT e FROM EntityGraph MATCH (e) WHERE e.entityName = 'Conveyor Belt 1'"
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Workspaces | [workspaces.md](workspaces.md) | `create-workspace`, `get-workspace`, `list-workspaces`, `update-workspace`, `delete-workspace` |
| Component Types | [component-types.md](component-types.md) | `create-component-type`, `get-component-type`, `list-component-types`, `update-component-type`, `delete-component-type` |
| Entities | [entities.md](entities.md) | `create-entity`, `get-entity`, `list-entities`, `update-entity`, `delete-entity`, `list-components`, `list-properties` |
| Scenes | [scenes.md](scenes.md) | `create-scene`, `get-scene`, `list-scenes`, `update-scene`, `delete-scene` |
| Property Values | [property-values.md](property-values.md) | `get-property-value`, `get-property-value-history`, `batch-put-property-values` |
| Sync Jobs | [sync-jobs.md](sync-jobs.md) | `create-sync-job`, `get-sync-job`, `list-sync-jobs`, `delete-sync-job`, `list-sync-resources` |
| Metadata Transfer | [metadata-transfer.md](metadata-transfer.md) | `create-metadata-transfer-job`, `get-metadata-transfer-job`, `list-metadata-transfer-jobs`, `cancel-metadata-transfer-job` |
| Queries | [queries.md](queries.md) | `execute-query` |
| Pricing | [pricing.md](pricing.md) | `get-pricing-plan`, `update-pricing-plan` |
| Tags | [tags.md](tags.md) | `tag-resource`, `untag-resource`, `list-tags-for-resource` |
