# Snapshots

### 5.1 `create-snapshot`

Creates a copy of an entire Redis/Valkey cluster or replication group at a specific moment in time.

**Synopsis:**
```bash
aws elasticache create-snapshot \
    --snapshot-name <value> \
    [--replication-group-id <value>] \
    [--cache-cluster-id <value>] \
    [--kms-key-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--snapshot-name` | **Yes** | string | -- | Name for the snapshot |
| `--replication-group-id` | No | string | -- | Replication group to snapshot (provide this or cache-cluster-id) |
| `--cache-cluster-id` | No | string | -- | Cache cluster to snapshot |
| `--kms-key-id` | No | string | -- | KMS key ID for encryption |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "Snapshot": {
        "SnapshotName": "string",
        "ReplicationGroupId": "string",
        "ReplicationGroupDescription": "string",
        "CacheClusterId": "string",
        "SnapshotStatus": "creating|available|restoring|copying|deleting",
        "SnapshotSource": "manual|automated",
        "CacheNodeType": "string",
        "Engine": "string",
        "EngineVersion": "string",
        "NumCacheNodes": "integer",
        "PreferredAvailabilityZone": "string",
        "CacheClusterCreateTime": "timestamp",
        "PreferredMaintenanceWindow": "string",
        "TopicArn": "string",
        "Port": "integer",
        "CacheParameterGroupName": "string",
        "CacheSubnetGroupName": "string",
        "VpcId": "string",
        "AutoMinorVersionUpgrade": "boolean",
        "SnapshotRetentionLimit": "integer",
        "SnapshotWindow": "string",
        "NumNodeGroups": "integer",
        "AutomaticFailover": "enabled|disabled",
        "NodeSnapshots": [
            {
                "CacheClusterId": "string",
                "NodeGroupId": "string",
                "CacheNodeId": "string",
                "NodeGroupConfiguration": {
                    "NodeGroupId": "string",
                    "Slots": "string",
                    "ReplicaCount": "integer",
                    "PrimaryAvailabilityZone": "string",
                    "ReplicaAvailabilityZones": ["string"],
                    "PrimaryOutpostArn": "string",
                    "ReplicaOutpostArns": ["string"]
                },
                "CacheSize": "string",
                "CacheNodeCreateTime": "timestamp",
                "SnapshotCreateTime": "timestamp"
            }
        ],
        "KmsKeyId": "string",
        "ARN": "string",
        "DataTiering": "enabled|disabled"
    }
}
```

---

### 5.2 `delete-snapshot`

Deletes an existing snapshot.

**Synopsis:**
```bash
aws elasticache delete-snapshot \
    --snapshot-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--snapshot-name` | **Yes** | string | -- | Name of the snapshot to delete |

**Output Schema:** Same as `create-snapshot` output.

---

### 5.3 `describe-snapshots`

Returns information about cache cluster or replication group snapshots. **Paginated operation.**

**Synopsis:**
```bash
aws elasticache describe-snapshots \
    [--replication-group-id <value>] \
    [--cache-cluster-id <value>] \
    [--snapshot-name <value>] \
    [--snapshot-source <value>] \
    [--show-node-group-config | --no-show-node-group-config] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-group-id` | No | string | -- | Filter by replication group |
| `--cache-cluster-id` | No | string | -- | Filter by cache cluster |
| `--snapshot-name` | No | string | -- | Specific snapshot name |
| `--snapshot-source` | No | string | -- | Filter: `user` or `automated` |
| `--show-node-group-config` | No | boolean | false | Include node group configuration details |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Snapshots": [
        {
            "SnapshotName": "string",
            "ReplicationGroupId": "string",
            "CacheClusterId": "string",
            "SnapshotStatus": "string",
            "SnapshotSource": "string",
            "CacheNodeType": "string",
            "Engine": "string",
            "EngineVersion": "string",
            "NodeSnapshots": [],
            "ARN": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.4 `copy-snapshot`

Makes a copy of an existing snapshot. Can copy within the same region, cross-region, or to an S3 bucket for export.

**Synopsis:**
```bash
aws elasticache copy-snapshot \
    --source-snapshot-name <value> \
    --target-snapshot-name <value> \
    [--target-bucket <value>] \
    [--kms-key-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-snapshot-name` | **Yes** | string | -- | Name of the source snapshot |
| `--target-snapshot-name` | **Yes** | string | -- | Name for the target snapshot |
| `--target-bucket` | No | string | -- | S3 bucket name to export the snapshot to |
| `--kms-key-id` | No | string | -- | KMS key for encrypting the target snapshot |
| `--tags` | No | list | None | Tags for the target snapshot |

**Output Schema:** Same as `create-snapshot` output.

---

### 5.5 `export-serverless-cache-snapshot`

Exports a serverless cache snapshot data to an S3 bucket. Only available for serverless cache snapshots.

**Synopsis:**
```bash
aws elasticache export-serverless-cache-snapshot \
    --serverless-cache-snapshot-name <value> \
    --s3-bucket-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--serverless-cache-snapshot-name` | **Yes** | string | -- | Name of the serverless cache snapshot |
| `--s3-bucket-name` | **Yes** | string | -- | S3 bucket name for export |

**Output Schema:**
```json
{
    "ServerlessCacheSnapshot": {
        "ServerlessCacheSnapshotName": "string",
        "ARN": "string",
        "KmsKeyId": "string",
        "SnapshotType": "string",
        "Status": "string",
        "CreateTime": "timestamp",
        "ExpiryTime": "timestamp",
        "BytesUsedForCache": "string",
        "ServerlessCacheConfiguration": {
            "ServerlessCacheName": "string",
            "Engine": "string",
            "MajorEngineVersion": "string"
        }
    }
}
```
