# AWS CLI v2 -- ElastiCache Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/elasticache/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-cache-cluster` | Cluster | Create a new cache cluster |
| `delete-cache-cluster` | Cluster | Delete a cache cluster |
| `describe-cache-clusters` | Cluster | Describe one or more cache clusters |
| `modify-cache-cluster` | Cluster | Modify cache cluster settings |
| `reboot-cache-cluster` | Cluster | Reboot cache nodes in a cluster |
| `create-replication-group` | Replication Group | Create a Redis/Valkey replication group |
| `delete-replication-group` | Replication Group | Delete a replication group |
| `describe-replication-groups` | Replication Group | Describe replication groups |
| `modify-replication-group` | Replication Group | Modify replication group settings |
| `modify-replication-group-shard-configuration` | Replication Group | Add or remove shards |
| `increase-replica-count` | Replication Group | Add read replicas |
| `decrease-replica-count` | Replication Group | Remove read replicas |
| `test-failover` | Replication Group | Test automatic failover on a node group |
| `start-migration` | Replication Group | Start migration from self-managed Redis |
| `complete-migration` | Replication Group | Complete migration from self-managed Redis |
| `create-cache-parameter-group` | Parameter Group | Create a cache parameter group |
| `delete-cache-parameter-group` | Parameter Group | Delete a cache parameter group |
| `describe-cache-parameter-groups` | Parameter Group | Describe cache parameter groups |
| `describe-cache-parameters` | Parameter Group | List parameters in a group |
| `modify-cache-parameter-group` | Parameter Group | Modify parameters in a group |
| `reset-cache-parameter-group` | Parameter Group | Reset parameters to defaults |
| `describe-engine-default-parameters` | Parameter Group | Get default engine parameters |
| `create-cache-subnet-group` | Subnet Group | Create a cache subnet group |
| `delete-cache-subnet-group` | Subnet Group | Delete a cache subnet group |
| `describe-cache-subnet-groups` | Subnet Group | Describe cache subnet groups |
| `modify-cache-subnet-group` | Subnet Group | Modify a cache subnet group |
| `create-snapshot` | Snapshot | Create a snapshot of a cluster or replication group |
| `delete-snapshot` | Snapshot | Delete a snapshot |
| `describe-snapshots` | Snapshot | Describe snapshots |
| `copy-snapshot` | Snapshot | Copy a snapshot |
| `export-serverless-cache-snapshot` | Snapshot | Export a serverless cache snapshot to S3 |
| `create-user` | User | Create a user for RBAC |
| `delete-user` | User | Delete a user |
| `describe-users` | User | Describe users |
| `modify-user` | User | Modify a user |
| `create-user-group` | User | Create a user group for RBAC |
| `delete-user-group` | User | Delete a user group |
| `describe-user-groups` | User | Describe user groups |
| `modify-user-group` | User | Modify a user group |
| `create-serverless-cache` | Serverless | Create a serverless cache |
| `delete-serverless-cache` | Serverless | Delete a serverless cache |
| `describe-serverless-caches` | Serverless | Describe serverless caches |
| `modify-serverless-cache` | Serverless | Modify a serverless cache |
| `create-serverless-cache-snapshot` | Serverless | Create a serverless cache snapshot |
| `delete-serverless-cache-snapshot` | Serverless | Delete a serverless cache snapshot |
| `describe-serverless-cache-snapshots` | Serverless | Describe serverless cache snapshots |
| `create-global-replication-group` | Global Replication | Create a global replication group |
| `delete-global-replication-group` | Global Replication | Delete a global replication group |
| `describe-global-replication-groups` | Global Replication | Describe global replication groups |
| `modify-global-replication-group` | Global Replication | Modify a global replication group |
| `failover-global-replication-group` | Global Replication | Failover a global replication group |
| `increase-node-groups-in-global-replication-group` | Global Replication | Add node groups to a global replication group |
| `decrease-node-groups-in-global-replication-group` | Global Replication | Remove node groups from a global replication group |
| `disassociate-global-replication-group` | Global Replication | Remove a secondary from a global group |
| `rebalance-slots-in-global-replication-group` | Global Replication | Rebalance slots across node groups |
| `describe-service-updates` | Service Update | Describe available service updates |
| `describe-update-actions` | Service Update | Describe update actions for clusters |
| `batch-apply-update-action` | Service Update | Apply service updates to clusters |
| `batch-stop-update-action` | Service Update | Stop applying service updates |
| `add-tags-to-resource` | Tags | Add tags to a resource |
| `remove-tags-from-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |
| `describe-cache-engine-versions` | Info | List available cache engine versions |
| `describe-reserved-cache-nodes` | Reserved | Describe reserved cache nodes |
| `describe-reserved-cache-nodes-offerings` | Reserved | Describe reserved node offerings |
| `purchase-reserved-cache-nodes-offering` | Reserved | Purchase a reserved node offering |
| `describe-events` | Events | Describe ElastiCache events |
| `list-allowed-node-type-modifications` | Info | List valid node type scale-up options |

---

## Global Options

These options are available on ALL `aws elasticache` commands.

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

### Supported Engines
| Engine | Description |
|--------|-------------|
| `redis` | Redis OSS or Valkey engine |
| `memcached` | Memcached engine |
| `valkey` | Valkey engine (available in newer versions) |

### Cache Cluster Status Values
| Status | Description |
|--------|-------------|
| `available` | Cluster is ready |
| `creating` | Cluster is being created |
| `deleted` | Cluster has been deleted |
| `deleting` | Cluster is being deleted |
| `incompatible-network` | Network configuration is incompatible |
| `modifying` | Cluster is being modified |
| `rebooting cluster nodes` | Nodes are being rebooted |
| `restore-failed` | Restore from snapshot failed |
| `snapshotting` | Snapshot is being taken |

### Replication Group Status Values
| Status | Description |
|--------|-------------|
| `available` | Replication group is ready |
| `creating` | Replication group is being created |
| `modifying` | Replication group is being modified |
| `deleting` | Replication group is being deleted |
| `snapshotting` | Snapshot in progress |

### Node Type Families
- **General purpose:** `cache.m7g.*`, `cache.m6g.*`, `cache.m5.*`, `cache.t4g.*`, `cache.t3.*`
- **Memory optimized:** `cache.r7g.*`, `cache.r6g.*`, `cache.r5.*`

### Wait Commands
```bash
aws elasticache wait cache-cluster-available --cache-cluster-id my-cluster
aws elasticache wait cache-cluster-deleted --cache-cluster-id my-cluster
aws elasticache wait replication-group-available --replication-group-id my-redis
aws elasticache wait replication-group-deleted --replication-group-id my-redis
```
