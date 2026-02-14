# AWS CLI v2 — IoT SiteWise

## Overview

Complete reference for all `aws iotsitewise` subcommands in AWS CLI v2. Covers asset model definitions, asset management, property data ingestion and retrieval, portal and dashboard visualization, gateway management, bulk import, access policies, time series management, actions, datasets, queries, and configuration. IoT SiteWise collects, organizes, and analyzes industrial equipment data at scale to enable data-driven decisions for industrial operations.

## Quick Reference — Common Workflows

### Create an asset model and asset

```bash
aws iotsitewise create-asset-model \
    --asset-model-name "Wind Turbine Model" \
    --asset-model-properties '[{"name":"Serial Number","dataType":"STRING","type":{"attribute":{}}},{"name":"Power Output","dataType":"DOUBLE","unit":"kW","type":{"measurement":{}}}]'

aws iotsitewise create-asset \
    --asset-name "Wind Turbine 1" \
    --asset-model-id a1b2c3d4-5678-90ab-cdef-11111EXAMPLE
```

### Ingest and retrieve property data

```bash
aws iotsitewise batch-put-asset-property-value \
    --entries '[{"entryId":"entry1","assetId":"a1b2c3d4-5678-90ab-cdef-33333EXAMPLE","propertyId":"a1b2c3d4-5678-90ab-cdef-55555EXAMPLE","propertyValues":[{"value":{"doubleValue":4.92},"timestamp":{"timeInSeconds":1580853000},"quality":"GOOD"}]}]'

aws iotsitewise get-asset-property-value \
    --asset-id a1b2c3d4-5678-90ab-cdef-33333EXAMPLE \
    --property-id a1b2c3d4-5678-90ab-cdef-55555EXAMPLE
```

### Build an asset hierarchy

```bash
aws iotsitewise associate-assets \
    --asset-id a1b2c3d4-5678-90ab-cdef-44444EXAMPLE \
    --hierarchy-id a1b2c3d4-5678-90ab-cdef-77777EXAMPLE \
    --child-asset-id a1b2c3d4-5678-90ab-cdef-33333EXAMPLE
```

### Set up a portal with a project and dashboard

```bash
aws iotsitewise create-portal \
    --portal-name "Wind Farm Portal" \
    --portal-contact-email admin@example.com \
    --role-arn arn:aws:iam::123456789012:role/SiteWiseMonitorRole

aws iotsitewise create-project \
    --portal-id a1b2c3d4-5678-90ab-cdef-aaaaaEXAMPLE \
    --project-name "Wind Farm 1"

aws iotsitewise create-dashboard \
    --project-id a1b2c3d4-5678-90ab-cdef-eeeeeEXAMPLE \
    --dashboard-name "Turbine Dashboard" \
    --dashboard-definition file://dashboard-def.json
```

### Create a gateway for edge data collection

```bash
aws iotsitewise create-gateway \
    --gateway-name "Factory Gateway" \
    --gateway-platform '{"greengrassV2":{"coreDeviceThingName":"MyGreengrassCore"}}'
```

### Configure multi-layer storage

```bash
aws iotsitewise put-storage-configuration \
    --storage-type MULTI_LAYER_STORAGE \
    --multi-layer-storage '{"customerManagedS3Storage":{"s3ResourceArn":"arn:aws:s3:::my-sitewise-bucket","roleArn":"arn:aws:iam::123456789012:role/SiteWiseS3Role"}}'
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Asset Models | [asset-models.md](asset-models.md) | `create-asset-model`, `describe-asset-model`, `list-asset-models`, `update-asset-model`, `delete-asset-model`, `list-asset-model-properties`, `create-asset-model-composite-model`, `describe-asset-model-composite-model`, `list-asset-model-composite-models`, `update-asset-model-composite-model`, `delete-asset-model-composite-model` |
| Assets | [assets.md](assets.md) | `create-asset`, `describe-asset`, `list-assets`, `update-asset`, `delete-asset`, `describe-asset-property`, `update-asset-property`, `list-asset-properties`, `describe-asset-composite-model`, `list-asset-relationships`, `associate-assets`, `disassociate-assets`, `list-associated-assets`, `associate-time-series-to-asset-property`, `disassociate-time-series-from-asset-property` |
| Property Data | [property-data.md](property-data.md) | `get-asset-property-value`, `get-asset-property-value-history`, `get-asset-property-aggregates`, `get-interpolated-asset-property-values`, `batch-put-asset-property-value`, `batch-get-asset-property-value`, `batch-get-asset-property-value-history`, `batch-get-asset-property-aggregates` |
| Time Series | [time-series.md](time-series.md) | `describe-time-series`, `list-time-series`, `delete-time-series` |
| Portals | [portals.md](portals.md) | `create-portal`, `describe-portal`, `list-portals`, `update-portal`, `delete-portal` |
| Projects | [projects.md](projects.md) | `create-project`, `describe-project`, `list-projects`, `update-project`, `delete-project`, `batch-associate-project-assets`, `batch-disassociate-project-assets`, `list-project-assets` |
| Dashboards | [dashboards.md](dashboards.md) | `create-dashboard`, `describe-dashboard`, `list-dashboards`, `update-dashboard`, `delete-dashboard` |
| Access Policies | [access-policies.md](access-policies.md) | `create-access-policy`, `describe-access-policy`, `list-access-policies`, `update-access-policy`, `delete-access-policy` |
| Gateways | [gateways.md](gateways.md) | `create-gateway`, `describe-gateway`, `list-gateways`, `update-gateway`, `delete-gateway`, `describe-gateway-capability-configuration`, `update-gateway-capability-configuration` |
| Bulk Import | [bulk-import.md](bulk-import.md) | `create-bulk-import-job`, `describe-bulk-import-job`, `list-bulk-import-jobs` |
| Actions | [actions.md](actions.md) | `execute-action`, `describe-action`, `list-actions` |
| Datasets | [datasets.md](datasets.md) | `create-dataset`, `describe-dataset`, `list-datasets`, `update-dataset`, `delete-dataset` |
| Queries | [queries.md](queries.md) | `execute-query` |
| Configuration | [configuration.md](configuration.md) | `put-default-encryption-configuration`, `describe-default-encryption-configuration`, `put-storage-configuration`, `describe-storage-configuration`, `put-logging-options`, `describe-logging-options` |
| Tags | [tags.md](tags.md) | `tag-resource`, `untag-resource`, `list-tags-for-resource` |
