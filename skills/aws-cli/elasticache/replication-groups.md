# Replication Groups

### 2.1 `create-replication-group`

Creates a Redis or Valkey replication group. A replication group is a collection of clusters where one is the primary and the rest are read replicas. Supports cluster mode (sharding) with multiple node groups.

**Synopsis:**
```bash
aws elasticache create-replication-group \
    --replication-group-id <value> \
    --replication-group-description <value> \
    [--global-replication-group-id <value>] \
    [--primary-cluster-id <value>] \
    [--automatic-failover-enabled | --no-automatic-failover-enabled] \
    [--multi-az-enabled | --no-multi-az-enabled] \
    [--num-cache-clusters <value>] \
    [--preferred-cache-cluster-a-zs <value>] \
    [--num-node-groups <value>] \
    [--replicas-per-node-group <value>] \
    [--node-group-configuration <value>] \
    [--cache-node-type <value>] \
    [--engine <value>] \
    [--engine-version <value>] \
    [--cache-parameter-group-name <value>] \
    [--cache-subnet-group-name <value>] \
    [--cache-security-group-names <value>] \
    [--security-group-ids <value>] \
    [--tags <value>] \
    [--snapshot-arns <value>] \
    [--snapshot-name <value>] \
    [--preferred-maintenance-window <value>] \
    [--port <value>] \
    [--notification-topic-arn <value>] \
    [--auto-minor-version-upgrade | --no-auto-minor-version-upgrade] \
    [--snapshot-retention-limit <value>] \
    [--snapshot-window <value>] \
    [--auth-token <value>] \
    [--transit-encryption-enabled | --no-transit-encryption-enabled] \
    [--at-rest-encryption-enabled | --no-at-rest-encryption-enabled] \
    [--kms-key-id <value>] \
    [--user-group-ids <value>] \
    [--log-delivery-configurations <value>] \
    [--data-tiering-enabled | --no-data-tiering-enabled] \
    [--network-type <value>] \
    [--ip-discovery <value>] \
    [--transit-encryption-mode <value>] \
    [--cluster-mode <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-group-id` | **Yes** | string | -- | Unique ID for the replication group (up to 40 chars) |
| `--replication-group-description` | **Yes** | string | -- | Description of the replication group |
| `--global-replication-group-id` | No | string | -- | Global replication group to add this as a secondary |
| `--primary-cluster-id` | No | string | -- | Existing cluster to use as the primary |
| `--automatic-failover-enabled` | No | boolean | false | Enable automatic failover (requires Multi-AZ) |
| `--multi-az-enabled` | No | boolean | false | Enable Multi-AZ |
| `--num-cache-clusters` | No | integer | -- | Total number of clusters (primary + replicas, 1-6). Non-cluster-mode |
| `--preferred-cache-cluster-a-zs` | No | list(string) | -- | AZs for each cluster |
| `--num-node-groups` | No | integer | -- | Number of node groups (shards) for cluster mode |
| `--replicas-per-node-group` | No | integer | -- | Replicas per shard (0-5) |
| `--node-group-configuration` | No | list | -- | Per-shard configuration |
| `--cache-node-type` | No | string | -- | Cache node type (e.g., `cache.r7g.large`) |
| `--engine` | No | string | -- | Engine: `redis` or `valkey` |
| `--engine-version` | No | string | latest | Engine version |
| `--cache-parameter-group-name` | No | string | -- | Parameter group name |
| `--cache-subnet-group-name` | No | string | -- | Subnet group name |
| `--security-group-ids` | No | list(string) | -- | VPC security group IDs |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--snapshot-arns` | No | list(string) | -- | S3 ARN of RDB snapshot to restore from |
| `--snapshot-name` | No | string | -- | ElastiCache snapshot name to restore from |
| `--preferred-maintenance-window` | No | string | -- | Weekly maintenance window |
| `--port` | No | integer | 6379 | Port number |
| `--notification-topic-arn` | No | string | -- | SNS topic ARN |
| `--auto-minor-version-upgrade` | No | boolean | true | Auto-apply minor upgrades |
| `--snapshot-retention-limit` | No | integer | 0 | Snapshot retention days |
| `--snapshot-window` | No | string | -- | Daily snapshot window |
| `--auth-token` | No | string | -- | AUTH token for Redis (16-128 chars) |
| `--transit-encryption-enabled` | No | boolean | false | Enable TLS in-transit encryption |
| `--at-rest-encryption-enabled` | No | boolean | false | Enable at-rest encryption |
| `--kms-key-id` | No | string | -- | KMS key ID for at-rest encryption |
| `--user-group-ids` | No | list(string) | -- | User group IDs for RBAC |
| `--log-delivery-configurations` | No | list | -- | Log delivery configurations |
| `--data-tiering-enabled` | No | boolean | false | Enable data tiering (r6gd node types) |
| `--network-type` | No | string | `ipv4` | Network type: `ipv4`, `ipv6`, `dual_stack` |
| `--ip-discovery` | No | string | `ipv4` | IP discovery: `ipv4` or `ipv6` |
| `--transit-encryption-mode` | No | string | -- | TLS mode: `preferred` or `required` |
| `--cluster-mode` | No | string | -- | Cluster mode: `enabled` or `disabled` or `compatible` |

**Node Group Configuration Structure:**
```json
[
    {
        "NodeGroupId": "string",
        "Slots": "string",
        "ReplicaCount": "integer",
        "PrimaryAvailabilityZone": "string",
        "ReplicaAvailabilityZones": ["string"],
        "PrimaryOutpostArn": "string",
        "ReplicaOutpostArns": ["string"]
    }
]
```

**Output Schema:**
```json
{
    "ReplicationGroup": {
        "ReplicationGroupId": "string",
        "Description": "string",
        "GlobalReplicationGroupInfo": {
            "GlobalReplicationGroupId": "string",
            "GlobalReplicationGroupMemberRole": "PRIMARY|SECONDARY"
        },
        "Status": "creating|available|modifying|deleting|create-failed|snapshotting",
        "PendingModifiedValues": {},
        "MemberClusters": ["string"],
        "NodeGroups": [
            {
                "NodeGroupId": "string",
                "Status": "string",
                "PrimaryEndpoint": {
                    "Address": "string",
                    "Port": "integer"
                },
                "ReaderEndpoint": {
                    "Address": "string",
                    "Port": "integer"
                },
                "Slots": "string",
                "NodeGroupMembers": [
                    {
                        "CacheClusterId": "string",
                        "CacheNodeId": "string",
                        "ReadEndpoint": {
                            "Address": "string",
                            "Port": "integer"
                        },
                        "PreferredAvailabilityZone": "string",
                        "PreferredOutpostArn": "string",
                        "CurrentRole": "primary|replica"
                    }
                ]
            }
        ],
        "SnapshottingClusterId": "string",
        "AutomaticFailover": "enabled|disabled|enabling|disabling",
        "MultiAZ": "enabled|disabled",
        "ConfigurationEndpoint": {
            "Address": "string",
            "Port": "integer"
        },
        "SnapshotRetentionLimit": "integer",
        "SnapshotWindow": "string",
        "ClusterEnabled": "boolean",
        "CacheNodeType": "string",
        "AuthTokenEnabled": "boolean",
        "AuthTokenLastModifiedDate": "timestamp",
        "TransitEncryptionEnabled": "boolean",
        "AtRestEncryptionEnabled": "boolean",
        "MemberClustersOutpostArns": ["string"],
        "KmsKeyId": "string",
        "ARN": "string",
        "UserGroupIds": ["string"],
        "LogDeliveryConfigurations": [],
        "DataTiering": "enabled|disabled",
        "AutoMinorVersionUpgrade": "boolean",
        "NetworkType": "ipv4|ipv6|dual_stack",
        "IpDiscovery": "ipv4|ipv6",
        "TransitEncryptionMode": "preferred|required",
        "ClusterMode": "enabled|disabled|compatible"
    }
}
```

---

### 2.2 `delete-replication-group`

Deletes an existing replication group. Optionally creates a final snapshot before deletion.

**Synopsis:**
```bash
aws elasticache delete-replication-group \
    --replication-group-id <value> \
    [--retain-primary-cluster | --no-retain-primary-cluster] \
    [--final-snapshot-identifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-group-id` | **Yes** | string | -- | ID of the replication group to delete |
| `--retain-primary-cluster` | No | boolean | false | Keep the primary cluster (only deletes read replicas) |
| `--final-snapshot-identifier` | No | string | -- | Name for a final snapshot before deletion |

**Output Schema:** Same as `create-replication-group` output.

---

### 2.3 `describe-replication-groups`

Returns information about a specific or all replication groups. **Paginated operation.**

**Synopsis:**
```bash
aws elasticache describe-replication-groups \
    [--replication-group-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-group-id` | No | string | -- | Specific replication group to describe |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ReplicationGroups": [
        {
            "ReplicationGroupId": "string",
            "Description": "string",
            "Status": "string",
            "NodeGroups": [],
            "AutomaticFailover": "string",
            "MultiAZ": "string",
            "CacheNodeType": "string",
            "ARN": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.4 `modify-replication-group`

Modifies the settings for a replication group. Can change failover settings, node type, engine version, and more.

**Synopsis:**
```bash
aws elasticache modify-replication-group \
    --replication-group-id <value> \
    [--replication-group-description <value>] \
    [--primary-cluster-id <value>] \
    [--snapshotting-cluster-id <value>] \
    [--automatic-failover-enabled | --no-automatic-failover-enabled] \
    [--multi-az-enabled | --no-multi-az-enabled] \
    [--node-group-id <value>] \
    [--cache-security-group-names <value>] \
    [--security-group-ids <value>] \
    [--preferred-maintenance-window <value>] \
    [--notification-topic-arn <value>] \
    [--cache-parameter-group-name <value>] \
    [--notification-topic-status <value>] \
    [--apply-immediately | --no-apply-immediately] \
    [--engine-version <value>] \
    [--auto-minor-version-upgrade | --no-auto-minor-version-upgrade] \
    [--snapshot-retention-limit <value>] \
    [--snapshot-window <value>] \
    [--cache-node-type <value>] \
    [--auth-token <value>] \
    [--auth-token-update-strategy <value>] \
    [--user-group-ids-to-add <value>] \
    [--user-group-ids-to-remove <value>] \
    [--log-delivery-configurations <value>] \
    [--ip-discovery <value>] \
    [--transit-encryption-enabled | --no-transit-encryption-enabled] \
    [--transit-encryption-mode <value>] \
    [--cluster-mode <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-group-id` | **Yes** | string | -- | ID of the replication group |
| `--replication-group-description` | No | string | -- | New description |
| `--primary-cluster-id` | No | string | -- | Promote a different cluster to primary |
| `--automatic-failover-enabled` | No | boolean | -- | Enable/disable automatic failover |
| `--multi-az-enabled` | No | boolean | -- | Enable/disable Multi-AZ |
| `--security-group-ids` | No | list(string) | -- | New security group IDs |
| `--preferred-maintenance-window` | No | string | -- | New maintenance window |
| `--cache-parameter-group-name` | No | string | -- | New parameter group |
| `--apply-immediately` | No | boolean | false | Apply immediately or next maintenance window |
| `--engine-version` | No | string | -- | New engine version |
| `--cache-node-type` | No | string | -- | New node type (vertical scaling) |
| `--auth-token` | No | string | -- | New AUTH token |
| `--auth-token-update-strategy` | No | string | -- | Strategy: `SET`, `ROTATE`, `DELETE` |
| `--user-group-ids-to-add` | No | list(string) | -- | User group IDs to add |
| `--user-group-ids-to-remove` | No | list(string) | -- | User group IDs to remove |
| `--transit-encryption-enabled` | No | boolean | -- | Enable/disable in-transit encryption |
| `--transit-encryption-mode` | No | string | -- | TLS mode: `preferred` or `required` |
| `--cluster-mode` | No | string | -- | Cluster mode: `enabled`, `disabled`, `compatible` |

**Output Schema:** Same as `create-replication-group` output.

---

### 2.5 `modify-replication-group-shard-configuration`

Modifies the number of node groups (shards) in a cluster-mode enabled replication group.

**Synopsis:**
```bash
aws elasticache modify-replication-group-shard-configuration \
    --replication-group-id <value> \
    --node-group-count <value> \
    --apply-immediately | --no-apply-immediately \
    [--resharding-configuration <value>] \
    [--node-groups-to-remove <value>] \
    [--node-groups-to-retain <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-group-id` | **Yes** | string | -- | ID of the replication group |
| `--node-group-count` | **Yes** | integer | -- | New number of node groups (shards) |
| `--apply-immediately` | **Yes** | boolean | -- | Must be true for this operation |
| `--resharding-configuration` | No | list | -- | Custom slot distribution for new shards |
| `--node-groups-to-remove` | No | list(string) | -- | Node group IDs to remove (when scaling in) |
| `--node-groups-to-retain` | No | list(string) | -- | Node group IDs to retain (when scaling in) |

**Output Schema:** Same as `create-replication-group` output.

---

### 2.6 `increase-replica-count`

Dynamically increases the number of replicas in a Redis/Valkey replication group.

**Synopsis:**
```bash
aws elasticache increase-replica-count \
    --replication-group-id <value> \
    --apply-immediately | --no-apply-immediately \
    [--new-replica-count <value>] \
    [--replica-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-group-id` | **Yes** | string | -- | ID of the replication group |
| `--apply-immediately` | **Yes** | boolean | -- | Must be true |
| `--new-replica-count` | No | integer | -- | New replica count per shard (uniform across all shards) |
| `--replica-configuration` | No | list | -- | Per-shard replica configuration |

**Output Schema:** Same as `create-replication-group` output.

---

### 2.7 `decrease-replica-count`

Dynamically decreases the number of replicas in a Redis/Valkey replication group.

**Synopsis:**
```bash
aws elasticache decrease-replica-count \
    --replication-group-id <value> \
    --apply-immediately | --no-apply-immediately \
    [--new-replica-count <value>] \
    [--replica-configuration <value>] \
    [--replicas-to-remove <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-group-id` | **Yes** | string | -- | ID of the replication group |
| `--apply-immediately` | **Yes** | boolean | -- | Must be true |
| `--new-replica-count` | No | integer | -- | New replica count per shard |
| `--replica-configuration` | No | list | -- | Per-shard replica configuration |
| `--replicas-to-remove` | No | list(string) | -- | Specific replica cluster IDs to remove |

**Output Schema:** Same as `create-replication-group` output.

---

### 2.8 `test-failover`

Tests automatic failover on a specified node group in a replication group. Simulates a primary node failure.

**Synopsis:**
```bash
aws elasticache test-failover \
    --replication-group-id <value> \
    --node-group-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-group-id` | **Yes** | string | -- | ID of the replication group |
| `--node-group-id` | **Yes** | string | -- | Node group (shard) ID to test failover on (e.g., `0001`) |

**Output Schema:** Same as `create-replication-group` output.

---

### 2.9 `start-migration`

Start the migration of data from self-hosted Redis on EC2 to ElastiCache.

**Synopsis:**
```bash
aws elasticache start-migration \
    --replication-group-id <value> \
    --customer-node-endpoint-list <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-group-id` | **Yes** | string | -- | ID of the replication group |
| `--customer-node-endpoint-list` | **Yes** | list | -- | Source endpoints. Shorthand: `Address=string,Port=integer ...` |

**Output Schema:** Same as `create-replication-group` output.

---

### 2.10 `complete-migration`

Completes migration from self-hosted Redis to ElastiCache. Stops replication from the source and promotes ElastiCache to primary.

**Synopsis:**
```bash
aws elasticache complete-migration \
    --replication-group-id <value> \
    [--force | --no-force] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-group-id` | **Yes** | string | -- | ID of the replication group |
| `--force` | No | boolean | false | Force completion even if data is not fully synced |

**Output Schema:** Same as `create-replication-group` output.
