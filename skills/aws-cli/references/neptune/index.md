# AWS CLI v2 — Neptune (Database + Analytics Graph) Command Reference Index

> Based on AWS CLI v2 documentation. Sources: https://docs.aws.amazon.com/cli/latest/reference/neptune/ , https://docs.aws.amazon.com/cli/latest/reference/neptune-graph/

---

## Quick Reference — `aws neptune`

| Command | Category | Description |
|---------|----------|-------------|
| `create-db-cluster` | Cluster | Create a Neptune DB cluster |
| `modify-db-cluster` | Cluster | Modify a DB cluster |
| `delete-db-cluster` | Cluster | Delete a DB cluster |
| `describe-db-clusters` | Cluster | Describe DB clusters |
| `start-db-cluster` | Cluster | Start a stopped cluster |
| `stop-db-cluster` | Cluster | Stop a running cluster |
| `failover-db-cluster` | Cluster | Force a failover |
| `promote-read-replica-db-cluster` | Cluster | Promote read replica |
| `add-role-to-db-cluster` | Cluster | Add IAM role to cluster |
| `remove-role-from-db-cluster` | Cluster | Remove IAM role from cluster |
| `create-db-instance` | Instance | Create a DB instance |
| `modify-db-instance` | Instance | Modify a DB instance |
| `delete-db-instance` | Instance | Delete a DB instance |
| `describe-db-instances` | Instance | Describe DB instances |
| `reboot-db-instance` | Instance | Reboot a DB instance |
| `describe-orderable-db-instance-options` | Instance | List available instance options |
| `describe-valid-db-instance-modifications` | Instance | List valid modifications |
| `describe-db-engine-versions` | Instance | List engine versions |
| `create-db-cluster-endpoint` | Endpoint | Create a custom cluster endpoint |
| `modify-db-cluster-endpoint` | Endpoint | Modify a cluster endpoint |
| `delete-db-cluster-endpoint` | Endpoint | Delete a cluster endpoint |
| `describe-db-cluster-endpoints` | Endpoint | Describe cluster endpoints |
| `create-db-cluster-snapshot` | Snapshot | Create a cluster snapshot |
| `copy-db-cluster-snapshot` | Snapshot | Copy a cluster snapshot |
| `delete-db-cluster-snapshot` | Snapshot | Delete a cluster snapshot |
| `describe-db-cluster-snapshots` | Snapshot | Describe cluster snapshots |
| `describe-db-cluster-snapshot-attributes` | Snapshot | View snapshot sharing attributes |
| `modify-db-cluster-snapshot-attribute` | Snapshot | Modify snapshot sharing |
| `restore-db-cluster-from-snapshot` | Snapshot | Restore cluster from snapshot |
| `restore-db-cluster-to-point-in-time` | Snapshot | Point-in-time restore |
| `create-db-cluster-parameter-group` | Parameter Group | Create cluster parameter group |
| `modify-db-cluster-parameter-group` | Parameter Group | Modify cluster parameters |
| `delete-db-cluster-parameter-group` | Parameter Group | Delete cluster parameter group |
| `describe-db-cluster-parameter-groups` | Parameter Group | List cluster parameter groups |
| `describe-db-cluster-parameters` | Parameter Group | List cluster parameters |
| `reset-db-cluster-parameter-group` | Parameter Group | Reset cluster parameters |
| `describe-engine-default-cluster-parameters` | Parameter Group | Get default cluster parameters |
| `create-db-parameter-group` | Parameter Group | Create instance parameter group |
| `modify-db-parameter-group` | Parameter Group | Modify instance parameters |
| `delete-db-parameter-group` | Parameter Group | Delete instance parameter group |
| `describe-db-parameter-groups` | Parameter Group | List instance parameter groups |
| `describe-db-parameters` | Parameter Group | List instance parameters |
| `reset-db-parameter-group` | Parameter Group | Reset instance parameters |
| `describe-engine-default-parameters` | Parameter Group | Get default instance parameters |
| `create-db-subnet-group` | Subnet Group | Create a DB subnet group |
| `modify-db-subnet-group` | Subnet Group | Modify a DB subnet group |
| `delete-db-subnet-group` | Subnet Group | Delete a DB subnet group |
| `describe-db-subnet-groups` | Subnet Group | Describe DB subnet groups |
| `create-global-cluster` | Global Cluster | Create a global database |
| `modify-global-cluster` | Global Cluster | Modify a global database |
| `delete-global-cluster` | Global Cluster | Delete a global database |
| `describe-global-clusters` | Global Cluster | Describe global databases |
| `failover-global-cluster` | Global Cluster | Failover global database |
| `switchover-global-cluster` | Global Cluster | Switchover global database |
| `remove-from-global-cluster` | Global Cluster | Remove cluster from global database |
| `create-event-subscription` | Event | Create event subscription |
| `modify-event-subscription` | Event | Modify event subscription |
| `delete-event-subscription` | Event | Delete event subscription |
| `describe-event-subscriptions` | Event | Describe event subscriptions |
| `describe-events` | Event | List events |
| `describe-event-categories` | Event | List event categories |
| `add-source-identifier-to-subscription` | Event | Add source to subscription |
| `remove-source-identifier-from-subscription` | Event | Remove source from subscription |
| `add-tags-to-resource` | Tags | Add tags to a resource |
| `remove-tags-from-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List resource tags |
| `apply-pending-maintenance-action` | Maintenance | Apply pending maintenance |
| `describe-pending-maintenance-actions` | Maintenance | List pending maintenance |
| `wait db-instance-available` | Wait | Wait until DB instance is available |
| `wait db-instance-deleted` | Wait | Wait until DB instance is deleted |

---

## Quick Reference — `aws neptune-graph`

| Command | Category | Description |
|---------|----------|-------------|
| `create-graph` | Graph | Create a Neptune Analytics graph |
| `delete-graph` | Graph | Delete a graph |
| `get-graph` | Graph | Get graph details |
| `list-graphs` | Graph | List all graphs |
| `update-graph` | Graph | Update graph configuration |
| `reset-graph` | Graph | Reset a graph |
| `start-graph` | Graph | Start a stopped graph |
| `stop-graph` | Graph | Stop a running graph |
| `get-graph-summary` | Graph | Get graph summary statistics |
| `create-graph-snapshot` | Snapshot | Create a graph snapshot |
| `delete-graph-snapshot` | Snapshot | Delete a graph snapshot |
| `get-graph-snapshot` | Snapshot | Get snapshot details |
| `list-graph-snapshots` | Snapshot | List graph snapshots |
| `restore-graph-from-snapshot` | Snapshot | Restore graph from snapshot |
| `start-import-task` | Import/Export | Start data import |
| `cancel-import-task` | Import/Export | Cancel an import |
| `get-import-task` | Import/Export | Get import status |
| `list-import-tasks` | Import/Export | List import tasks |
| `start-export-task` | Import/Export | Start data export |
| `cancel-export-task` | Import/Export | Cancel an export |
| `get-export-task` | Import/Export | Get export status |
| `list-export-tasks` | Import/Export | List export tasks |
| `create-private-graph-endpoint` | Endpoint | Create a private endpoint |
| `delete-private-graph-endpoint` | Endpoint | Delete a private endpoint |
| `get-private-graph-endpoint` | Endpoint | Get endpoint details |
| `list-private-graph-endpoints` | Endpoint | List private endpoints |
| `execute-query` | Query | Execute a graph query |
| `cancel-query` | Query | Cancel a running query |
| `get-query` | Query | Get query details |
| `list-queries` | Query | List queries |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List resource tags |
| `wait graph-available` | Wait | Wait until graph is available |
| `wait graph-deleted` | Wait | Wait until graph is deleted |
| `wait graph-snapshot-available` | Wait | Wait until snapshot is available |
| `wait graph-snapshot-deleted` | Wait | Wait until snapshot is deleted |
| `wait graph-stopped` | Wait | Wait until graph is stopped |
| `wait import-task-successful` | Wait | Wait until import succeeds |
| `wait import-task-cancelled` | Wait | Wait until import is cancelled |
| `wait export-task-successful` | Wait | Wait until export succeeds |
| `wait export-task-cancelled` | Wait | Wait until export is cancelled |
| `wait private-graph-endpoint-available` | Wait | Wait until endpoint is available |
| `wait private-graph-endpoint-deleted` | Wait | Wait until endpoint is deleted |

---

## Global Options

These options are available on ALL `aws neptune` and `aws neptune-graph` commands.

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
| `--cli-binary-format` | string | `base64` | Format for binary blob input |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from a JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from a YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton |

---

## Common Patterns

### DB Cluster Status Values
| Status | Description |
|--------|-------------|
| `available` | Cluster is ready |
| `creating` | Cluster is being created |
| `deleting` | Cluster is being deleted |
| `failing-over` | Cluster is failing over |
| `modifying` | Cluster is being modified |
| `starting` | Cluster is starting |
| `stopped` | Cluster is stopped |
| `stopping` | Cluster is stopping |
| `upgrading` | Engine upgrade in progress |

### Graph Status Values (Neptune Analytics)
| Status | Description |
|--------|-------------|
| `CREATING` | Graph is being created |
| `AVAILABLE` | Graph is ready |
| `DELETING` | Graph is being deleted |
| `RESETTING` | Graph is being reset |
| `UPDATING` | Graph is being updated |
| `SNAPSHOTTING` | Snapshot is being taken |
| `FAILED` | Graph creation/update failed |
| `IMPORTING` | Data import in progress |
| `STARTING` | Graph is starting |
| `STOPPING` | Graph is stopping |
| `STOPPED` | Graph is stopped |

### Instance Classes (Common)
| Class | Description |
|-------|-------------|
| `db.r6g.large` | Memory-optimized (Graviton2) |
| `db.r6g.xlarge` | Memory-optimized (Graviton2) |
| `db.r5.large` | Memory-optimized (Intel) |
| `db.t3.medium` | Burstable (development/testing) |
| `db.serverless` | Neptune Serverless |

### Storage Types
| Type | Description |
|------|-------------|
| `standard` | Standard I/O storage (default) |
| `iopt1` | I/O-Optimized storage |
