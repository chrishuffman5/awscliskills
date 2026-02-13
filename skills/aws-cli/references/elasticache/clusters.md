# Clusters

### 1.1 `create-cache-cluster`

Creates a cache cluster. A cache cluster is a collection of one or more cache nodes.

**Synopsis:**
```bash
aws elasticache create-cache-cluster \
    --cache-cluster-id <value> \
    [--replication-group-id <value>] \
    [--az-mode <value>] \
    [--preferred-availability-zone <value>] \
    [--preferred-availability-zones <value>] \
    [--num-cache-nodes <value>] \
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
    [--outpost-mode <value>] \
    [--preferred-outpost-arn <value>] \
    [--preferred-outpost-arns <value>] \
    [--log-delivery-configurations <value>] \
    [--transit-encryption-enabled | --no-transit-encryption-enabled] \
    [--network-type <value>] \
    [--ip-discovery <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cache-cluster-id` | **Yes** | string | -- | Unique identifier for the cluster (up to 50 chars: letters, numbers, hyphens) |
| `--replication-group-id` | No | string | -- | ID of the replication group to add this cluster to (as a read replica) |
| `--az-mode` | No | string | `single-az` | AZ mode for Memcached: `single-az` or `cross-az` |
| `--preferred-availability-zone` | No | string | -- | AZ for the cluster |
| `--preferred-availability-zones` | No | list(string) | -- | AZ list for Memcached nodes (one per node) |
| `--num-cache-nodes` | No | integer | 1 | Number of cache nodes (Memcached: 1-40, Redis: always 1) |
| `--cache-node-type` | No | string | -- | Cache node type (e.g., `cache.r7g.large`) |
| `--engine` | No | string | -- | Engine: `memcached`, `redis`, or `valkey` |
| `--engine-version` | No | string | latest | Engine version |
| `--cache-parameter-group-name` | No | string | engine default | Name of the cache parameter group |
| `--cache-subnet-group-name` | No | string | -- | Name of the cache subnet group |
| `--cache-security-group-names` | No | list(string) | -- | (EC2-Classic) Security group names |
| `--security-group-ids` | No | list(string) | -- | VPC security group IDs |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--snapshot-arns` | No | list(string) | -- | S3 ARN of an RDB snapshot to restore from |
| `--snapshot-name` | No | string | -- | Name of an ElastiCache snapshot to restore from |
| `--preferred-maintenance-window` | No | string | -- | Weekly maintenance window (e.g., `sun:05:00-sun:06:00`) |
| `--port` | No | integer | 6379/11211 | Port number (Redis default 6379, Memcached default 11211) |
| `--notification-topic-arn` | No | string | -- | SNS topic ARN for notifications |
| `--auto-minor-version-upgrade` | No | boolean | true | Auto-apply minor engine upgrades |
| `--snapshot-retention-limit` | No | integer | 0 | Days to retain automatic snapshots (0 = disabled) |
| `--snapshot-window` | No | string | -- | Daily time range for snapshots (e.g., `05:00-09:00`) |
| `--auth-token` | No | string | -- | AUTH token for Redis (requires transit encryption) |
| `--outpost-mode` | No | string | -- | Outpost mode: `single-outpost` or `cross-outpost` |
| `--log-delivery-configurations` | No | list | -- | Log delivery configurations (slow-log, engine-log) |
| `--transit-encryption-enabled` | No | boolean | false | Enable in-transit encryption |
| `--network-type` | No | string | `ipv4` | Network type: `ipv4`, `ipv6`, `dual_stack` |
| `--ip-discovery` | No | string | `ipv4` | IP discovery: `ipv4` or `ipv6` |

**Output Schema:**
```json
{
    "CacheCluster": {
        "CacheClusterId": "string",
        "ConfigurationEndpoint": {
            "Address": "string",
            "Port": "integer"
        },
        "ClientDownloadLandingPage": "string",
        "CacheNodeType": "string",
        "Engine": "string",
        "EngineVersion": "string",
        "CacheClusterStatus": "string",
        "NumCacheNodes": "integer",
        "PreferredAvailabilityZone": "string",
        "CacheClusterCreateTime": "timestamp",
        "PreferredMaintenanceWindow": "string",
        "PendingModifiedValues": {
            "NumCacheNodes": "integer",
            "CacheNodeIdsToRemove": ["string"],
            "EngineVersion": "string",
            "CacheNodeType": "string",
            "AuthTokenStatus": "SETTING|ROTATING",
            "LogDeliveryConfigurations": [],
            "TransitEncryptionEnabled": "boolean",
            "TransitEncryptionMode": "string"
        },
        "NotificationConfiguration": {
            "TopicArn": "string",
            "TopicStatus": "active|inactive"
        },
        "CacheSecurityGroups": [],
        "CacheParameterGroup": {
            "CacheParameterGroupName": "string",
            "ParameterApplyStatus": "string",
            "CacheNodeIdsToReboot": ["string"]
        },
        "CacheSubnetGroupName": "string",
        "CacheNodes": [
            {
                "CacheNodeId": "string",
                "CacheNodeStatus": "string",
                "CacheNodeCreateTime": "timestamp",
                "Endpoint": {
                    "Address": "string",
                    "Port": "integer"
                },
                "ParameterGroupStatus": "string",
                "SourceCacheNodeId": "string",
                "CustomerAvailabilityZone": "string",
                "CustomerOutpostArn": "string"
            }
        ],
        "AutoMinorVersionUpgrade": "boolean",
        "SecurityGroups": [
            {
                "SecurityGroupId": "string",
                "Status": "string"
            }
        ],
        "ReplicationGroupId": "string",
        "SnapshotRetentionLimit": "integer",
        "SnapshotWindow": "string",
        "AuthTokenEnabled": "boolean",
        "AuthTokenLastModifiedDate": "timestamp",
        "TransitEncryptionEnabled": "boolean",
        "AtRestEncryptionEnabled": "boolean",
        "ARN": "string",
        "ReplicationGroupLogDeliveryEnabled": "boolean",
        "LogDeliveryConfigurations": [
            {
                "LogType": "slow-log|engine-log",
                "DestinationType": "cloudwatch-logs|kinesis-firehose",
                "DestinationDetails": {
                    "CloudWatchLogsDetails": {
                        "LogGroup": "string"
                    },
                    "KinesisFirehoseDetails": {
                        "DeliveryStream": "string"
                    }
                },
                "LogFormat": "text|json",
                "Status": "active|enabling|modifying|disabling|error",
                "Message": "string"
            }
        ],
        "NetworkType": "ipv4|ipv6|dual_stack",
        "IpDiscovery": "ipv4|ipv6",
        "TransitEncryptionMode": "preferred|required"
    }
}
```

---

### 1.2 `delete-cache-cluster`

Deletes a previously provisioned cache cluster. The cluster must not be in the `creating` or `deleting` state.

**Synopsis:**
```bash
aws elasticache delete-cache-cluster \
    --cache-cluster-id <value> \
    [--final-snapshot-identifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cache-cluster-id` | **Yes** | string | -- | ID of the cache cluster to delete |
| `--final-snapshot-identifier` | No | string | -- | Name for a final snapshot before deletion (Redis only) |

**Output Schema:** Same as `create-cache-cluster` output.

---

### 1.3 `describe-cache-clusters`

Returns information about all provisioned cache clusters. **Paginated operation.**

**Synopsis:**
```bash
aws elasticache describe-cache-clusters \
    [--cache-cluster-id <value>] \
    [--show-cache-node-info | --no-show-cache-node-info] \
    [--show-cache-clusters-not-in-replication-groups | --no-show-cache-clusters-not-in-replication-groups] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cache-cluster-id` | No | string | -- | Specific cluster to describe |
| `--show-cache-node-info` | No | boolean | false | Include individual cache node information |
| `--show-cache-clusters-not-in-replication-groups` | No | boolean | false | Only show clusters not in a replication group |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CacheClusters": [
        {
            "CacheClusterId": "string",
            "CacheNodeType": "string",
            "Engine": "string",
            "EngineVersion": "string",
            "CacheClusterStatus": "string",
            "NumCacheNodes": "integer",
            "PreferredAvailabilityZone": "string",
            "CacheClusterCreateTime": "timestamp",
            "CacheNodes": [],
            "CacheParameterGroup": {},
            "CacheSubnetGroupName": "string",
            "SecurityGroups": [],
            "ReplicationGroupId": "string",
            "ARN": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.4 `modify-cache-cluster`

Modifies the settings for a cache cluster. You can scale up/down, change the number of nodes (Memcached), and modify parameters.

**Synopsis:**
```bash
aws elasticache modify-cache-cluster \
    --cache-cluster-id <value> \
    [--num-cache-nodes <value>] \
    [--cache-node-ids-to-remove <value>] \
    [--az-mode <value>] \
    [--new-availability-zones <value>] \
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
    [--log-delivery-configurations <value>] \
    [--ip-discovery <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cache-cluster-id` | **Yes** | string | -- | ID of the cache cluster to modify |
| `--num-cache-nodes` | No | integer | -- | New number of cache nodes (Memcached scale out/in) |
| `--cache-node-ids-to-remove` | No | list(string) | -- | Node IDs to remove when scaling in |
| `--az-mode` | No | string | -- | New AZ mode for Memcached |
| `--new-availability-zones` | No | list(string) | -- | AZs for new nodes |
| `--security-group-ids` | No | list(string) | -- | New VPC security group IDs |
| `--preferred-maintenance-window` | No | string | -- | New maintenance window |
| `--notification-topic-arn` | No | string | -- | New SNS topic ARN |
| `--cache-parameter-group-name` | No | string | -- | New parameter group name |
| `--notification-topic-status` | No | string | -- | Topic status: `active` or `inactive` |
| `--apply-immediately` | No | boolean | false | Apply changes immediately vs. next maintenance window |
| `--engine-version` | No | string | -- | New engine version |
| `--auto-minor-version-upgrade` | No | boolean | -- | Auto-apply minor upgrades |
| `--snapshot-retention-limit` | No | integer | -- | New snapshot retention days |
| `--snapshot-window` | No | string | -- | New snapshot window |
| `--cache-node-type` | No | string | -- | New node type (vertical scaling) |
| `--auth-token` | No | string | -- | New AUTH token |
| `--auth-token-update-strategy` | No | string | -- | Strategy: `SET`, `ROTATE`, `DELETE` |
| `--log-delivery-configurations` | No | list | -- | Log delivery configuration |
| `--ip-discovery` | No | string | -- | IP discovery: `ipv4` or `ipv6` |

**Output Schema:** Same as `create-cache-cluster` output.

---

### 1.5 `reboot-cache-cluster`

Reboots some or all of the cache nodes within a provisioned cache cluster. Can be used to apply parameter group changes.

**Synopsis:**
```bash
aws elasticache reboot-cache-cluster \
    --cache-cluster-id <value> \
    --cache-node-ids-to-reboot <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cache-cluster-id` | **Yes** | string | -- | ID of the cache cluster |
| `--cache-node-ids-to-reboot` | **Yes** | list(string) | -- | Node IDs to reboot (e.g., `0001 0002`) |

**Output Schema:** Same as `create-cache-cluster` output.
