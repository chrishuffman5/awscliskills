# IoT SiteWise — Quick Reference

## All Commands

| Command | Description |
|---------|-------------|
| `associate-assets` | Associate a child asset to a parent asset through a hierarchy |
| `associate-time-series-to-asset-property` | Associate a time series with an asset property |
| `batch-associate-project-assets` | Associate assets to a project in bulk |
| `batch-disassociate-project-assets` | Disassociate assets from a project in bulk |
| `batch-get-asset-property-aggregates` | Get aggregated property values for multiple assets in batch |
| `batch-get-asset-property-value` | Get current property values for multiple assets in batch |
| `batch-get-asset-property-value-history` | Get historical property values for multiple assets in batch |
| `batch-put-asset-property-value` | Send property values to IoT SiteWise in batch |
| `create-access-policy` | Create an access policy for a portal or project |
| `create-asset` | Create an asset from an asset model |
| `create-asset-model` | Create an asset model with properties and hierarchies |
| `create-asset-model-composite-model` | Create a composite model within an asset model |
| `create-bulk-import-job` | Create a bulk import job from S3 |
| `create-dashboard` | Create a dashboard in a project |
| `create-dataset` | Create a dataset |
| `create-gateway` | Create a gateway for edge data collection |
| `create-portal` | Create a SiteWise Monitor portal |
| `create-project` | Create a project in a portal |
| `delete-access-policy` | Delete an access policy |
| `delete-asset` | Delete an asset |
| `delete-asset-model` | Delete an asset model |
| `delete-asset-model-composite-model` | Delete a composite model from an asset model |
| `delete-dashboard` | Delete a dashboard |
| `delete-dataset` | Delete a dataset |
| `delete-gateway` | Delete a gateway |
| `delete-portal` | Delete a portal |
| `delete-project` | Delete a project |
| `delete-time-series` | Delete a time series |
| `describe-access-policy` | Describe an access policy |
| `describe-action` | Describe an action |
| `describe-asset` | Describe an asset |
| `describe-asset-composite-model` | Describe a composite model for an asset |
| `describe-asset-model` | Describe an asset model |
| `describe-asset-model-composite-model` | Describe a composite model for an asset model |
| `describe-asset-property` | Describe an asset property |
| `describe-bulk-import-job` | Describe a bulk import job |
| `describe-dashboard` | Describe a dashboard |
| `describe-dataset` | Describe a dataset |
| `describe-default-encryption-configuration` | Describe the default encryption configuration |
| `describe-gateway` | Describe a gateway |
| `describe-gateway-capability-configuration` | Describe a gateway capability configuration |
| `describe-logging-options` | Describe the logging options |
| `describe-portal` | Describe a portal |
| `describe-project` | Describe a project |
| `describe-storage-configuration` | Describe the storage configuration |
| `describe-time-series` | Describe a time series |
| `disassociate-assets` | Disassociate a child asset from a parent asset |
| `disassociate-time-series-from-asset-property` | Disassociate a time series from an asset property |
| `execute-action` | Execute an action on a target resource |
| `execute-query` | Run a SQL-like query against IoT SiteWise |
| `get-asset-property-aggregates` | Get aggregated property values |
| `get-asset-property-value` | Get the current value of an asset property |
| `get-asset-property-value-history` | Get historical values of an asset property |
| `get-interpolated-asset-property-values` | Get interpolated property values |
| `list-access-policies` | List access policies |
| `list-actions` | List actions for a target resource |
| `list-asset-model-composite-models` | List composite models for an asset model |
| `list-asset-model-properties` | List properties for an asset model |
| `list-asset-models` | List asset models |
| `list-asset-properties` | List properties for an asset |
| `list-asset-relationships` | List relationships for an asset |
| `list-assets` | List assets |
| `list-associated-assets` | List assets associated through a hierarchy |
| `list-bulk-import-jobs` | List bulk import jobs |
| `list-dashboards` | List dashboards in a project |
| `list-datasets` | List datasets |
| `list-gateways` | List gateways |
| `list-portals` | List portals |
| `list-project-assets` | List assets associated with a project |
| `list-projects` | List projects in a portal |
| `list-tags-for-resource` | List tags for a resource |
| `list-time-series` | List time series |
| `put-default-encryption-configuration` | Set the default encryption configuration |
| `put-logging-options` | Set the logging options |
| `put-storage-configuration` | Configure storage settings |
| `tag-resource` | Add tags to a resource |
| `untag-resource` | Remove tags from a resource |
| `update-access-policy` | Update an access policy |
| `update-asset` | Update an asset name or description |
| `update-asset-model` | Update an asset model |
| `update-asset-model-composite-model` | Update a composite model in an asset model |
| `update-asset-property` | Update an asset property alias or notification state |
| `update-dashboard` | Update a dashboard |
| `update-dataset` | Update a dataset |
| `update-gateway` | Update a gateway name |
| `update-gateway-capability-configuration` | Update a gateway capability configuration |
| `update-portal` | Update a portal |
| `update-project` | Update a project |

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

### List all active assets for a model
```bash
aws iotsitewise list-assets --asset-model-id a1b2c3d4-5678-90ab-cdef-11111EXAMPLE \
    --query 'assetSummaries[?status.state==`ACTIVE`].{Name:name,Id:id}'
```

### Get current property value by alias
```bash
aws iotsitewise get-asset-property-value \
    --property-alias "/company/windfarm/3/turbine/7/temperature" \
    --query 'propertyValue.{Value:value,Quality:quality,Time:timestamp.timeInSeconds}'
```

### Get hourly averages for a property
```bash
aws iotsitewise get-asset-property-aggregates \
    --asset-id a1b2c3d4-5678-90ab-cdef-33333EXAMPLE \
    --property-id a1b2c3d4-5678-90ab-cdef-55555EXAMPLE \
    --aggregate-types AVERAGE \
    --resolution 1h \
    --start-date 1580849400 \
    --end-date 1580853000
```

### Check gateway sync status
```bash
aws iotsitewise describe-gateway \
    --gateway-id a1b2c3d4-5678-90ab-cdef-1a1a1EXAMPLE \
    --query '{Name:gatewayName,Capabilities:gatewayCapabilitySummaries[].{Namespace:capabilityNamespace,Status:capabilitySyncStatus}}'
```
