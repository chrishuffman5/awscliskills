# IoT FleetWise — Quick Reference

## All Commands

| Command | Description |
|---------|-------------|
| `associate-vehicle-fleet` | Associate a vehicle with a fleet |
| `batch-create-vehicle` | Create multiple vehicles in a batch |
| `batch-update-vehicle` | Update multiple vehicles in a batch |
| `create-campaign` | Create a data collection campaign |
| `create-decoder-manifest` | Create a decoder manifest for signal decoding |
| `create-fleet` | Create a fleet of vehicles |
| `create-model-manifest` | Create a vehicle model manifest |
| `create-signal-catalog` | Create a signal catalog |
| `create-state-template` | Create a state template for vehicle state tracking |
| `create-vehicle` | Create a vehicle |
| `delete-campaign` | Delete a campaign |
| `delete-decoder-manifest` | Delete a decoder manifest |
| `delete-fleet` | Delete a fleet |
| `delete-model-manifest` | Delete a model manifest |
| `delete-signal-catalog` | Delete a signal catalog |
| `delete-state-template` | Delete a state template |
| `delete-vehicle` | Delete a vehicle |
| `disassociate-vehicle-fleet` | Remove a vehicle from a fleet |
| `get-campaign` | Retrieve campaign details |
| `get-decoder-manifest` | Retrieve decoder manifest details |
| `get-encryption-configuration` | Get encryption configuration |
| `get-fleet` | Retrieve fleet details |
| `get-logging-options` | Get logging options |
| `get-model-manifest` | Retrieve model manifest details |
| `get-register-account-status` | Get account registration status |
| `get-signal-catalog` | Retrieve signal catalog details |
| `get-state-template` | Retrieve state template details |
| `get-vehicle` | Retrieve vehicle details |
| `get-vehicle-status` | Get vehicle provisioning status |
| `import-decoder-manifest` | Import a decoder manifest from DBC files |
| `import-signal-catalog` | Import a signal catalog from VSS |
| `list-campaigns` | List campaigns |
| `list-decoder-manifest-network-interfaces` | List network interfaces in a decoder manifest |
| `list-decoder-manifest-signals` | List signals in a decoder manifest |
| `list-decoder-manifests` | List decoder manifests |
| `list-fleets` | List fleets |
| `list-fleets-for-vehicle` | List fleets a vehicle belongs to |
| `list-model-manifest-nodes` | List nodes in a model manifest |
| `list-model-manifests` | List model manifests |
| `list-signal-catalog-nodes` | List nodes in a signal catalog |
| `list-signal-catalogs` | List signal catalogs |
| `list-state-templates` | List state templates |
| `list-tags-for-resource` | List tags for a resource |
| `list-vehicles` | List vehicles |
| `list-vehicles-in-fleet` | List vehicles in a fleet |
| `put-encryption-configuration` | Set encryption configuration |
| `put-logging-options` | Set logging options |
| `register-account` | Register account for IoT FleetWise |
| `tag-resource` | Add tags to a resource |
| `untag-resource` | Remove tags from a resource |
| `update-campaign` | Update or change campaign status |
| `update-decoder-manifest` | Update a decoder manifest |
| `update-fleet` | Update a fleet description |
| `update-model-manifest` | Update a model manifest |
| `update-signal-catalog` | Update a signal catalog |
| `update-state-template` | Update a state template |
| `update-vehicle` | Update a vehicle |

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

### List all vehicles with attributes
```bash
aws iotfleetwise list-vehicles \
    --query 'vehicleSummaries[].{Name:vehicleName,Model:modelManifestArn,Created:creationTime}'
```

### Check campaign status
```bash
aws iotfleetwise get-campaign --name my-campaign \
    --query '{Name:name,Status:status,Target:targetArn}'
```

### List all signals in a catalog
```bash
aws iotfleetwise list-signal-catalog-nodes \
    --name my-signal-catalog \
    --query 'nodes[?sensor].sensor.{Name:fullyQualifiedName,Type:dataType,Unit:unit}'
```
