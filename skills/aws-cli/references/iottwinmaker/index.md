# IoT TwinMaker — Quick Reference

## All Commands

| Command | Description |
|---------|-------------|
| `batch-put-property-values` | Send property values to a component in batch |
| `cancel-metadata-transfer-job` | Cancel a metadata transfer job |
| `create-component-type` | Create a component type in a workspace |
| `create-entity` | Create an entity in a workspace |
| `create-metadata-transfer-job` | Create a metadata transfer job |
| `create-scene` | Create a 3D scene in a workspace |
| `create-sync-job` | Create a sync job to sync from external sources |
| `create-workspace` | Create a workspace for digital twin modeling |
| `delete-component-type` | Delete a component type |
| `delete-entity` | Delete an entity |
| `delete-scene` | Delete a scene |
| `delete-sync-job` | Delete a sync job |
| `delete-workspace` | Delete a workspace |
| `execute-query` | Query the digital twin knowledge graph |
| `get-component-type` | Get details of a component type |
| `get-entity` | Get details of an entity |
| `get-metadata-transfer-job` | Get details of a metadata transfer job |
| `get-pricing-plan` | Get the current pricing plan |
| `get-property-value` | Get the current value of properties |
| `get-property-value-history` | Get historical values of time-series properties |
| `get-scene` | Get details of a scene |
| `get-sync-job` | Get details of a sync job |
| `get-workspace` | Get details of a workspace |
| `list-component-types` | List component types in a workspace |
| `list-components` | List components of an entity |
| `list-entities` | List entities in a workspace |
| `list-metadata-transfer-jobs` | List metadata transfer jobs |
| `list-properties` | List properties of a component |
| `list-scenes` | List scenes in a workspace |
| `list-sync-jobs` | List sync jobs in a workspace |
| `list-sync-resources` | List resources managed by a sync job |
| `list-tags-for-resource` | List tags for a resource |
| `list-workspaces` | List workspaces |
| `tag-resource` | Add tags to a resource |
| `untag-resource` | Remove tags from a resource |
| `update-component-type` | Update a component type |
| `update-entity` | Update an entity and its components |
| `update-pricing-plan` | Update the pricing plan |
| `update-scene` | Update a scene |
| `update-workspace` | Update a workspace |

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

### List all active entities in a workspace
```bash
aws iottwinmaker list-entities --workspace-id my-workspace \
    --query 'entitySummaries[?status.state==`ACTIVE`].{Name:entityName,Id:entityId}'
```

### Get a property value with JMESPath
```bash
aws iottwinmaker get-property-value \
    --workspace-id my-workspace \
    --entity-id my-entity \
    --component-name sensor \
    --selected-properties temperature \
    --query 'propertyValues.temperature.propertyValue'
```

### List all component types
```bash
aws iottwinmaker list-component-types --workspace-id my-workspace \
    --query 'componentTypeSummaries[].{Id:componentTypeId,Description:description}'
```
