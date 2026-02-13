# AWS CLI v2 -- DMS (Database Migration Service) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/dms/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-replication-instance` | Replication Instance | Create a replication instance |
| `delete-replication-instance` | Replication Instance | Delete a replication instance |
| `describe-replication-instances` | Replication Instance | Describe replication instances |
| `modify-replication-instance` | Replication Instance | Modify a replication instance |
| `reboot-replication-instance` | Replication Instance | Reboot a replication instance |
| `describe-orderable-replication-instances` | Replication Instance | List orderable replication instance classes |
| `describe-replication-instance-task-logs` | Replication Instance | Describe task logs on a replication instance |
| `create-endpoint` | Endpoint | Create a replication endpoint |
| `delete-endpoint` | Endpoint | Delete an endpoint |
| `describe-endpoints` | Endpoint | Describe endpoints |
| `modify-endpoint` | Endpoint | Modify an endpoint |
| `describe-endpoint-settings` | Endpoint | Describe available endpoint settings for an engine |
| `describe-endpoint-types` | Endpoint | Describe supported endpoint types |
| `test-connection` | Endpoint | Test a connection to an endpoint |
| `describe-connections` | Endpoint | Describe connections |
| `delete-connection` | Endpoint | Delete a connection |
| `create-replication-task` | Replication Task | Create a replication task |
| `delete-replication-task` | Replication Task | Delete a replication task |
| `describe-replication-tasks` | Replication Task | Describe replication tasks |
| `modify-replication-task` | Replication Task | Modify a replication task |
| `move-replication-task` | Replication Task | Move a replication task to a different instance |
| `start-replication-task` | Replication Task | Start a replication task |
| `stop-replication-task` | Replication Task | Stop a replication task |
| `reload-tables` | Replication Task | Reload tables during a task |
| `describe-table-statistics` | Replication Task | Describe table statistics for a task |
| `start-replication-task-assessment` | Replication Task | Start a task assessment |
| `start-replication-task-assessment-run` | Replication Task | Start a task assessment run |
| `cancel-replication-task-assessment-run` | Replication Task | Cancel a task assessment run |
| `delete-replication-task-assessment-run` | Replication Task | Delete a task assessment run |
| `describe-replication-task-assessment-results` | Replication Task | Describe task assessment results |
| `describe-replication-task-assessment-runs` | Replication Task | Describe task assessment runs |
| `describe-replication-task-individual-assessments` | Replication Task | Describe individual assessments |
| `describe-applicable-individual-assessments` | Replication Task | Describe applicable individual assessments |
| `create-replication-subnet-group` | Subnet Group | Create a replication subnet group |
| `delete-replication-subnet-group` | Subnet Group | Delete a replication subnet group |
| `describe-replication-subnet-groups` | Subnet Group | Describe replication subnet groups |
| `modify-replication-subnet-group` | Subnet Group | Modify a replication subnet group |
| `create-replication-config` | Serverless Replication | Create a serverless replication configuration |
| `delete-replication-config` | Serverless Replication | Delete a serverless replication configuration |
| `describe-replication-configs` | Serverless Replication | Describe serverless replication configurations |
| `modify-replication-config` | Serverless Replication | Modify a serverless replication configuration |
| `start-replication` | Serverless Replication | Start a serverless replication |
| `stop-replication` | Serverless Replication | Stop a serverless replication |
| `describe-replications` | Serverless Replication | Describe serverless replications |
| `reload-replication-tables` | Serverless Replication | Reload tables for a serverless replication |
| `describe-replication-table-statistics` | Serverless Replication | Describe table statistics for serverless replication |
| `create-data-migration` | Data Migration | Create a data migration |
| `delete-data-migration` | Data Migration | Delete a data migration |
| `describe-data-migrations` | Data Migration | Describe data migrations |
| `modify-data-migration` | Data Migration | Modify a data migration |
| `start-data-migration` | Data Migration | Start a data migration |
| `stop-data-migration` | Data Migration | Stop a data migration |
| `create-migration-project` | Migration Project | Create a migration project |
| `delete-migration-project` | Migration Project | Delete a migration project |
| `describe-migration-projects` | Migration Project | Describe migration projects |
| `modify-migration-project` | Migration Project | Modify a migration project |
| `create-data-provider` | Migration Project | Create a data provider |
| `delete-data-provider` | Migration Project | Delete a data provider |
| `describe-data-providers` | Migration Project | Describe data providers |
| `modify-data-provider` | Migration Project | Modify a data provider |
| `create-instance-profile` | Migration Project | Create an instance profile |
| `delete-instance-profile` | Migration Project | Delete an instance profile |
| `describe-instance-profiles` | Migration Project | Describe instance profiles |
| `modify-instance-profile` | Migration Project | Modify an instance profile |
| `describe-metadata-model-assessments` | Metadata Model | Describe metadata model assessments |
| `describe-metadata-model-conversions` | Metadata Model | Describe metadata model conversions |
| `describe-metadata-model-creations` | Metadata Model | Describe metadata model creations |
| `start-metadata-model-assessment` | Metadata Model | Start metadata model assessment |
| `start-metadata-model-conversion` | Metadata Model | Start metadata model conversion |
| `start-metadata-model-creation` | Metadata Model | Start metadata model creation |
| `cancel-metadata-model-conversion` | Metadata Model | Cancel metadata model conversion |
| `cancel-metadata-model-creation` | Metadata Model | Cancel metadata model creation |
| `start-metadata-model-export-as-script` | Metadata Model | Export metadata model as script |
| `start-metadata-model-export-to-target` | Metadata Model | Export metadata model to target |
| `start-metadata-model-import` | Metadata Model | Import metadata model |
| `describe-metadata-model-exports-as-script` | Metadata Model | Describe metadata model script exports |
| `describe-metadata-model-exports-to-target` | Metadata Model | Describe metadata model target exports |
| `describe-metadata-model-imports` | Metadata Model | Describe metadata model imports |
| `export-metadata-model-assessment` | Metadata Model | Export metadata model assessment |
| `create-fleet-advisor-collector` | Fleet Advisor | Create a Fleet Advisor collector |
| `delete-fleet-advisor-collector` | Fleet Advisor | Delete a Fleet Advisor collector |
| `describe-fleet-advisor-collectors` | Fleet Advisor | Describe Fleet Advisor collectors |
| `delete-fleet-advisor-databases` | Fleet Advisor | Delete Fleet Advisor databases |
| `describe-fleet-advisor-databases` | Fleet Advisor | Describe Fleet Advisor databases |
| `describe-fleet-advisor-lsa-analysis` | Fleet Advisor | Describe LSA analysis results |
| `describe-fleet-advisor-schema-object-summary` | Fleet Advisor | Describe schema object summary |
| `describe-fleet-advisor-schemas` | Fleet Advisor | Describe Fleet Advisor schemas |
| `run-fleet-advisor-lsa-analysis` | Fleet Advisor | Run LSA analysis |
| `create-event-subscription` | Event | Create an event notification subscription |
| `delete-event-subscription` | Event | Delete an event subscription |
| `describe-event-subscriptions` | Event | Describe event subscriptions |
| `modify-event-subscription` | Event | Modify an event subscription |
| `describe-event-categories` | Event | Describe event categories |
| `describe-events` | Event | Describe events |
| `update-subscriptions-to-event-bridge` | Event | Update subscriptions to EventBridge |
| `describe-schemas` | Schema | Describe schemas for an endpoint |
| `refresh-schemas` | Schema | Refresh schemas for an endpoint |
| `describe-refresh-schemas-status` | Schema | Describe refresh schemas status |
| `import-certificate` | Certificate | Import a SSL certificate |
| `delete-certificate` | Certificate | Delete a certificate |
| `describe-certificates` | Certificate | Describe certificates |
| `batch-start-recommendations` | Recommendation | Start batch recommendations |
| `start-recommendations` | Recommendation | Start recommendations |
| `describe-recommendations` | Recommendation | Describe recommendations |
| `describe-recommendation-limitations` | Recommendation | Describe recommendation limitations |
| `apply-pending-maintenance-action` | Maintenance | Apply a pending maintenance action |
| `describe-pending-maintenance-actions` | Maintenance | Describe pending maintenance actions |
| `describe-account-attributes` | Maintenance | Describe account attributes and quotas |
| `describe-engine-versions` | Maintenance | Describe available engine versions |
| `describe-conversion-configuration` | Maintenance | Describe conversion configuration |
| `modify-conversion-configuration` | Maintenance | Modify conversion configuration |
| `describe-extension-pack-associations` | Maintenance | Describe extension pack associations |
| `start-extension-pack-association` | Maintenance | Start extension pack association |
| `add-tags-to-resource` | Tags | Add tags to a DMS resource |
| `remove-tags-from-resource` | Tags | Remove tags from a DMS resource |
| `list-tags-for-resource` | Tags | List tags for a DMS resource |
| `wait` | Wait | Wait for DMS resources to reach desired states |

---

## Global Options

These options are available on ALL `aws dms` commands.

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `--debug` | boolean | false | Enable debug logging to stderr |
| `--endpoint-url` | string | -- | Override the default service endpoint URL |
| `--no-verify-ssl` | boolean | false | Disable SSL certificate verification |
| `--no-paginate` | boolean | false | Disable automatic pagination |
| `--output` | string | `json` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | -- | JMESPath query to filter output |
| `--profile` | string | `default` | Named AWS credential profile |
| `--region` | string | from config | AWS region to send requests to |
| `--version` | string | -- | Display the CLI version |
| `--color` | string | `auto` | Toggle color output: `on`, `off`, `auto` |
| `--no-sign-request` | boolean | false | Do not sign requests |
| `--ca-bundle` | string | -- | Path to custom CA certificate bundle |
| `--cli-read-timeout` | integer | 60 | Socket read timeout in seconds |
| `--cli-connect-timeout` | integer | 60 | Socket connect timeout in seconds |
| `--cli-binary-format` | string | `base64` | Format for binary blob input: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from a JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from a YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton: `input`, `yaml-input`, `output` |

---

## Common Patterns

### Replication Instance Status Values
| Status | Description |
|--------|-------------|
| `available` | Instance is ready for use |
| `creating` | Instance is being created |
| `deleting` | Instance is being deleted |
| `failed` | Instance creation failed |
| `modifying` | Instance is being modified |
| `rebooting` | Instance is rebooting |
| `storage-full` | Instance storage is full |
| `upgrading` | Instance engine is upgrading |

### Replication Task Status Values
| Status | Description |
|--------|-------------|
| `creating` | Task is being created |
| `ready` | Task is ready to start |
| `running` | Task is actively replicating |
| `stopped` | Task has been stopped |
| `stopping` | Task is stopping |
| `starting` | Task is starting |
| `failed` | Task failed |
| `modifying` | Task is being modified |
| `moving` | Task is being moved to another instance |
| `deleting` | Task is being deleted |
| `testing` | Task is testing endpoint connections |

### Migration Type Values
| Type | Description |
|------|-------------|
| `full-load` | Migrate existing data only |
| `cdc` | Replicate ongoing changes only (change data capture) |
| `full-load-and-cdc` | Migrate existing data then replicate ongoing changes |

### SSL Mode Values
| Mode | Description |
|------|-------------|
| `none` | No SSL encryption |
| `require` | SSL required but no certificate verification |
| `verify-ca` | SSL required with CA certificate verification |
| `verify-full` | SSL required with full certificate verification |

### Filter Structure
Many describe commands support a `--filters` parameter:
```json
[
  {
    "Name": "string",
    "Values": ["string", "..."]
  }
]
```

### Wait Commands
The `aws dms wait` subcommand blocks until a resource reaches a specific state:

| Waiter | Poll Interval | Max Checks | Description |
|--------|---------------|------------|-------------|
| `replication-instance-available` | 60s | 60 | Wait until replication instance is available |
| `replication-instance-deleted` | 15s | 60 | Wait until replication instance is deleted |
| `replication-task-ready` | 15s | 60 | Wait until replication task is ready |
| `replication-task-stopped` | 15s | 60 | Wait until replication task is stopped |
| `replication-task-running` | 15s | 60 | Wait until replication task is running |
| `replication-task-deleted` | 15s | 60 | Wait until replication task is deleted |
| `endpoint-deleted` | 5s | 60 | Wait until endpoint is deleted |
| `test-connection-succeeds` | 5s | 60 | Wait until test connection succeeds |
