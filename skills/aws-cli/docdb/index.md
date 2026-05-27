# AWS CLI v2 -- DocumentDB Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/docdb/ , https://docs.aws.amazon.com/cli/latest/reference/docdb-elastic/

---

## Quick Reference — `aws docdb`

| Command | Category | Description |
|---------|----------|-------------|
| `create-db-cluster` | Cluster | Create a new DocumentDB cluster |
| `delete-db-cluster` | Cluster | Delete a DocumentDB cluster |
| `describe-db-clusters` | Cluster | Describe one or more clusters |
| `modify-db-cluster` | Cluster | Modify cluster configuration |
| `start-db-cluster` | Cluster | Start a stopped cluster |
| `stop-db-cluster` | Cluster | Stop a running cluster |
| `failover-db-cluster` | Cluster | Force a failover for a cluster |
| `create-db-instance` | Instance | Create a new instance in a cluster |
| `delete-db-instance` | Instance | Delete an instance |
| `describe-db-instances` | Instance | Describe one or more instances |
| `modify-db-instance` | Instance | Modify instance configuration |
| `reboot-db-instance` | Instance | Reboot an instance |
| `create-db-cluster-snapshot` | Snapshot | Create a manual cluster snapshot |
| `delete-db-cluster-snapshot` | Snapshot | Delete a cluster snapshot |
| `describe-db-cluster-snapshots` | Snapshot | Describe cluster snapshots |
| `describe-db-cluster-snapshot-attributes` | Snapshot | Describe snapshot sharing attributes |
| `modify-db-cluster-snapshot-attribute` | Snapshot | Modify snapshot sharing attributes |
| `copy-db-cluster-snapshot` | Snapshot | Copy a cluster snapshot |
| `restore-db-cluster-from-snapshot` | Snapshot | Restore a cluster from a snapshot |
| `restore-db-cluster-to-point-in-time` | Snapshot | Restore a cluster to a point in time |
| `create-db-cluster-parameter-group` | Parameter Group | Create a cluster parameter group |
| `delete-db-cluster-parameter-group` | Parameter Group | Delete a cluster parameter group |
| `describe-db-cluster-parameter-groups` | Parameter Group | Describe cluster parameter groups |
| `describe-db-cluster-parameters` | Parameter Group | Describe parameters in a group |
| `modify-db-cluster-parameter-group` | Parameter Group | Modify parameters in a group |
| `reset-db-cluster-parameter-group` | Parameter Group | Reset parameters to defaults |
| `copy-db-cluster-parameter-group` | Parameter Group | Copy a cluster parameter group |
| `create-db-subnet-group` | Subnet Group | Create a DB subnet group |
| `delete-db-subnet-group` | Subnet Group | Delete a DB subnet group |
| `describe-db-subnet-groups` | Subnet Group | Describe DB subnet groups |
| `modify-db-subnet-group` | Subnet Group | Modify a DB subnet group |
| `create-global-cluster` | Global Cluster | Create a global cluster |
| `delete-global-cluster` | Global Cluster | Delete a global cluster |
| `describe-global-clusters` | Global Cluster | Describe global clusters |
| `modify-global-cluster` | Global Cluster | Modify a global cluster |
| `remove-from-global-cluster` | Global Cluster | Remove a cluster from a global cluster |
| `failover-global-cluster` | Global Cluster | Failover a global cluster |
| `switchover-global-cluster` | Global Cluster | Switchover a global cluster |
| `describe-events` | Events | Describe events for resources |
| `describe-event-categories` | Events | Describe event categories |
| `create-event-subscription` | Events | Create an event notification subscription |
| `delete-event-subscription` | Events | Delete an event subscription |
| `describe-event-subscriptions` | Events | Describe event subscriptions |
| `modify-event-subscription` | Events | Modify an event subscription |
| `add-source-identifier-to-subscription` | Events | Add a source to an event subscription |
| `remove-source-identifier-from-subscription` | Events | Remove a source from an event subscription |
| `add-tags-to-resource` | Tags | Add tags to a resource |
| `remove-tags-from-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |
| `apply-pending-maintenance-action` | Maintenance | Apply a pending maintenance action |
| `describe-pending-maintenance-actions` | Maintenance | Describe pending maintenance actions |
| `describe-certificates` | Info | Describe available certificates |
| `describe-db-engine-versions` | Info | Describe available engine versions |
| `describe-orderable-db-instance-options` | Info | Describe orderable instance options |
| `wait` | Wait | Wait for a resource to reach a state |

## Quick Reference — `aws docdb-elastic`

| Command | Category | Description |
|---------|----------|-------------|
| `create-cluster` | Elastic Cluster | Create a new elastic cluster |
| `delete-cluster` | Elastic Cluster | Delete an elastic cluster |
| `get-cluster` | Elastic Cluster | Get details of an elastic cluster |
| `list-clusters` | Elastic Cluster | List all elastic clusters |
| `update-cluster` | Elastic Cluster | Update an elastic cluster |
| `start-cluster` | Elastic Cluster | Start a stopped elastic cluster |
| `stop-cluster` | Elastic Cluster | Stop an elastic cluster |
| `restore-cluster-from-snapshot` | Elastic Cluster | Restore an elastic cluster from a snapshot |
| `create-cluster-snapshot` | Elastic Snapshot | Create an elastic cluster snapshot |
| `delete-cluster-snapshot` | Elastic Snapshot | Delete an elastic cluster snapshot |
| `get-cluster-snapshot` | Elastic Snapshot | Get details of an elastic cluster snapshot |
| `list-cluster-snapshots` | Elastic Snapshot | List elastic cluster snapshots |
| `copy-cluster-snapshot` | Elastic Snapshot | Copy an elastic cluster snapshot |
| `apply-pending-maintenance-action` | Maintenance | Apply a pending maintenance action |
| `get-pending-maintenance-action` | Maintenance | Get a pending maintenance action |
| `list-pending-maintenance-actions` | Maintenance | List pending maintenance actions |
| `tag-resource` | Tags | Add tags to an elastic cluster resource |
| `untag-resource` | Tags | Remove tags from an elastic cluster resource |
| `list-tags-for-resource` | Tags | List tags for an elastic cluster resource |

---

## Global Options

These options are available on ALL `aws docdb` and `aws docdb-elastic` commands.

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
| `--no-sign-request` | boolean | false | Do not sign requests (for anonymous access) |
| `--ca-bundle` | string | -- | Path to custom CA certificate bundle for SSL |
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

### Cluster Statuses

| Status | Description |
|--------|-------------|
| `available` | Cluster is ready for use |
| `creating` | Cluster is being created |
| `deleting` | Cluster is being deleted |
| `failing-over` | Cluster is failing over |
| `modifying` | Cluster is being modified |
| `starting` | Cluster is starting |
| `stopped` | Cluster is stopped |
| `stopping` | Cluster is stopping |
| `backing-up` | Cluster backup is in progress |

### Instance Statuses

| Status | Description |
|--------|-------------|
| `available` | Instance is ready for use |
| `creating` | Instance is being created |
| `deleting` | Instance is being deleted |
| `rebooting` | Instance is rebooting |
| `modifying` | Instance is being modified |
| `configuring-enhanced-monitoring` | Enhanced monitoring is being configured |

### Supported Engines

| Engine | Description |
|--------|-------------|
| `docdb` | Amazon DocumentDB (MongoDB-compatible) |
