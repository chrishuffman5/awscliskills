# AWS CLI v2 -- RDS Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/rds/

---


## All RDS Subcommands (Quick Reference)

| Command | Category | Description |
|---------|----------|-------------|
| `add-tags-to-resource` | Tags | Add tags to an RDS resource |
| `apply-pending-maintenance-action` | Maintenance | Apply a pending maintenance action |
| `copy-db-cluster-snapshot` | Snapshots | Copy an Aurora cluster snapshot |
| `copy-db-snapshot` | Snapshots | Copy a DB instance snapshot |
| `copy-option-group` | Option Groups | Copy an option group |
| `create-db-cluster` | Clusters | Create an Aurora DB cluster |
| `create-db-cluster-endpoint` | Clusters | Create a custom endpoint for Aurora |
| `create-db-cluster-parameter-group` | Parameter Groups | Create a cluster parameter group |
| `create-db-cluster-snapshot` | Snapshots | Create an Aurora cluster snapshot |
| `create-db-instance` | Instances | Create a DB instance |
| `create-db-instance-read-replica` | Instances | Create a read replica |
| `create-db-parameter-group` | Parameter Groups | Create a DB parameter group |
| `create-db-proxy` | Proxy | Create an RDS Proxy |
| `create-db-snapshot` | Snapshots | Create a DB instance snapshot |
| `create-db-subnet-group` | Subnet Groups | Create a DB subnet group |
| `create-event-subscription` | Events | Create an event notification subscription |
| `create-option-group` | Option Groups | Create an option group |
| `delete-db-cluster` | Clusters | Delete an Aurora DB cluster |
| `delete-db-cluster-endpoint` | Clusters | Delete a custom cluster endpoint |
| `delete-db-cluster-parameter-group` | Parameter Groups | Delete a cluster parameter group |
| `delete-db-cluster-snapshot` | Snapshots | Delete an Aurora cluster snapshot |
| `delete-db-instance` | Instances | Delete a DB instance |
| `delete-db-instance-automated-backup` | Backups | Delete an automated backup |
| `delete-db-parameter-group` | Parameter Groups | Delete a DB parameter group |
| `delete-db-proxy` | Proxy | Delete an RDS Proxy |
| `delete-db-snapshot` | Snapshots | Delete a DB instance snapshot |
| `delete-db-subnet-group` | Subnet Groups | Delete a DB subnet group |
| `delete-event-subscription` | Events | Delete an event subscription |
| `delete-option-group` | Option Groups | Delete an option group |
| `deregister-db-proxy-targets` | Proxy | Remove targets from a proxy |
| `describe-db-cluster-endpoints` | Clusters | Describe custom cluster endpoints |
| `describe-db-cluster-parameter-groups` | Parameter Groups | Describe cluster parameter groups |
| `describe-db-cluster-parameters` | Parameter Groups | Describe parameters in a cluster group |
| `describe-db-cluster-snapshots` | Snapshots | Describe Aurora cluster snapshots |
| `describe-db-clusters` | Clusters | Describe Aurora DB clusters |
| `describe-db-engine-versions` | Maintenance | Describe available engine versions |
| `describe-db-instance-automated-backups` | Backups | Describe automated backups |
| `describe-db-instances` | Instances | Describe DB instances |
| `describe-db-parameter-groups` | Parameter Groups | Describe DB parameter groups |
| `describe-db-parameters` | Parameter Groups | Describe parameters in a group |
| `describe-db-proxies` | Proxy | Describe RDS Proxies |
| `describe-db-proxy-target-groups` | Proxy | Describe proxy target groups |
| `describe-db-proxy-targets` | Proxy | Describe proxy targets |
| `describe-db-snapshots` | Snapshots | Describe DB instance snapshots |
| `describe-db-subnet-groups` | Subnet Groups | Describe DB subnet groups |
| `describe-event-categories` | Events | Describe event categories |
| `describe-event-subscriptions` | Events | Describe event subscriptions |
| `describe-events` | Events | Describe RDS events |
| `describe-option-group-options` | Option Groups | Describe available options for an engine |
| `describe-option-groups` | Option Groups | Describe option groups |
| `describe-orderable-db-instance-options` | Maintenance | Describe orderable instance options |
| `describe-pending-maintenance-actions` | Maintenance | Describe pending maintenance actions |
| `failover-db-cluster` | Clusters | Force a failover for an Aurora cluster |
| `list-tags-for-resource` | Tags | List tags for an RDS resource |
| `modify-db-cluster` | Clusters | Modify an Aurora DB cluster |
| `modify-db-cluster-endpoint` | Clusters | Modify a custom cluster endpoint |
| `modify-db-cluster-parameter-group` | Parameter Groups | Modify cluster parameter group |
| `modify-db-instance` | Instances | Modify a DB instance |
| `modify-db-parameter-group` | Parameter Groups | Modify a DB parameter group |
| `modify-db-proxy` | Proxy | Modify an RDS Proxy |
| `modify-db-snapshot` | Snapshots | Modify a DB snapshot |
| `modify-db-subnet-group` | Subnet Groups | Modify a DB subnet group |
| `modify-event-subscription` | Events | Modify an event subscription |
| `modify-option-group` | Option Groups | Modify an option group |
| `promote-read-replica` | Instances | Promote a read replica to standalone |
| `reboot-db-instance` | Instances | Reboot a DB instance |
| `register-db-proxy-targets` | Proxy | Register targets with a proxy |
| `remove-tags-from-resource` | Tags | Remove tags from an RDS resource |
| `reset-db-cluster-parameter-group` | Parameter Groups | Reset cluster parameter group |
| `reset-db-parameter-group` | Parameter Groups | Reset a DB parameter group |
| `restore-db-cluster-from-snapshot` | Snapshots | Restore Aurora cluster from snapshot |
| `restore-db-instance-from-db-snapshot` | Snapshots | Restore DB instance from snapshot |
| `start-db-cluster` | Clusters | Start a stopped Aurora cluster |
| `start-db-instance` | Instances | Start a stopped DB instance |
| `start-db-instance-automated-backups-replication` | Backups | Start cross-region backup replication |
| `stop-db-cluster` | Clusters | Stop an Aurora cluster |
| `stop-db-instance` | Instances | Stop a running DB instance |
| `stop-db-instance-automated-backups-replication` | Backups | Stop cross-region backup replication |

---


## Global Options Reference

These options are available on ALL `aws rds` commands.

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `--debug` | boolean | false | Enable debug logging to stderr |
| `--endpoint-url` | string | -- | Override default service endpoint URL |
| `--no-verify-ssl` | boolean | false | Disable SSL certificate verification |
| `--no-paginate` | boolean | false | Disable automatic pagination |
| `--output` | string | `json` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | -- | JMESPath query to filter output |
| `--profile` | string | `default` | Named AWS credential profile |
| `--region` | string | from config | AWS region |
| `--version` | string | -- | Display CLI version |
| `--color` | string | `auto` | Color output: `on`, `off`, `auto` |
| `--no-sign-request` | boolean | false | Do not sign requests |
| `--ca-bundle` | string | -- | Custom CA certificate bundle path |
| `--cli-read-timeout` | integer | 60 | Socket read timeout (seconds) |
| `--cli-connect-timeout` | integer | 60 | Socket connect timeout (seconds) |
| `--cli-binary-format` | string | `base64` | Binary blob format: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | false | Disable output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print skeleton: `input`, `yaml-input`, `output` |

---


## Common Patterns

### DB Instance Status Values

| Status | Description |
|--------|-------------|
| `available` | Instance is ready for use |
| `creating` | Instance is being created |
| `deleting` | Instance is being deleted |
| `modifying` | Instance is being modified |
| `rebooting` | Instance is rebooting |
| `starting` | Instance is starting |
| `stopping` | Instance is stopping |
| `stopped` | Instance is stopped |
| `backing-up` | Automated backup in progress |
| `storage-optimization` | Storage is being optimized |
| `failed` | Instance has failed |

### DB Cluster Status Values

| Status | Description |
|--------|-------------|
| `available` | Cluster is ready |
| `creating` | Cluster is being created |
| `deleting` | Cluster is being deleted |
| `failing-over` | Failover in progress |
| `modifying` | Cluster is being modified |
| `starting` | Cluster is starting |
| `stopping` | Cluster is stopping |
| `stopped` | Cluster is stopped |

### Supported Engines

| Engine | `--engine` Value | Default Port |
|--------|-----------------|-------------|
| MySQL | `mysql` | 3306 |
| PostgreSQL | `postgres` | 5432 |
| MariaDB | `mariadb` | 3306 |
| Oracle Enterprise | `oracle-ee` | 1521 |
| Oracle Standard | `oracle-se2` | 1521 |
| SQL Server Enterprise | `sqlserver-ee` | 1433 |
| SQL Server Standard | `sqlserver-se` | 1433 |
| SQL Server Express | `sqlserver-ex` | 1433 |
| SQL Server Web | `sqlserver-web` | 1433 |
| Aurora MySQL | `aurora-mysql` | 3306 |
| Aurora PostgreSQL | `aurora-postgresql` | 5432 |

### Wait Commands

| Wait Command | Description |
|-------------|-------------|
| `aws rds wait db-instance-available` | Wait until instance is available |
| `aws rds wait db-instance-deleted` | Wait until instance is deleted |
| `aws rds wait db-snapshot-available` | Wait until snapshot is available |
| `aws rds wait db-snapshot-deleted` | Wait until snapshot is deleted |
| `aws rds wait db-cluster-available` | Wait until cluster is available |
| `aws rds wait db-cluster-deleted` | Wait until cluster is deleted |
| `aws rds wait db-cluster-snapshot-available` | Wait until cluster snapshot is available |
