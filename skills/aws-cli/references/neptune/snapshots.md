# Snapshots

### 4.1 `create-db-cluster-snapshot`

Creates a snapshot of a Neptune DB cluster.

**Synopsis:**
```bash
aws neptune create-db-cluster-snapshot \
    --db-cluster-identifier <value> \
    --db-cluster-snapshot-identifier <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-identifier` | **Yes** | string | -- | Cluster identifier |
| `--db-cluster-snapshot-identifier` | **Yes** | string | -- | Snapshot identifier |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "DBClusterSnapshot": {
        "DBClusterSnapshotIdentifier": "string",
        "DBClusterIdentifier": "string",
        "SnapshotCreateTime": "timestamp",
        "Engine": "neptune",
        "Status": "creating",
        "Port": "integer",
        "VpcId": "string",
        "ClusterCreateTime": "timestamp",
        "EngineVersion": "string",
        "StorageEncrypted": "boolean",
        "KmsKeyId": "string",
        "DBClusterSnapshotArn": "string",
        "StorageType": "string"
    }
}
```

---

### 4.2 `copy-db-cluster-snapshot`

Copies a Neptune DB cluster snapshot.

**Synopsis:**
```bash
aws neptune copy-db-cluster-snapshot \
    --source-db-cluster-snapshot-identifier <value> \
    --target-db-cluster-snapshot-identifier <value> \
    [--kms-key-id <value>] \
    [--copy-tags | --no-copy-tags] \
    [--tags <value>] \
    [--source-region <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-db-cluster-snapshot-identifier` | **Yes** | string | -- | Source snapshot identifier or ARN |
| `--target-db-cluster-snapshot-identifier` | **Yes** | string | -- | Target snapshot identifier |
| `--kms-key-id` | No | string | -- | KMS key for encryption (required for cross-region encrypted copies) |
| `--copy-tags` | No | boolean | false | Copy tags from source |
| `--tags` | No | list | None | Tags for the copy |
| `--source-region` | No | string | -- | Source region for cross-region copy |

**Output Schema:**
```json
{
    "DBClusterSnapshot": {
        "DBClusterSnapshotIdentifier": "string",
        "DBClusterIdentifier": "string",
        "Status": "copying",
        "Engine": "neptune",
        "EngineVersion": "string",
        "StorageEncrypted": "boolean",
        "DBClusterSnapshotArn": "string"
    }
}
```

---

### 4.3 `delete-db-cluster-snapshot`

Deletes a Neptune DB cluster snapshot.

**Synopsis:**
```bash
aws neptune delete-db-cluster-snapshot \
    --db-cluster-snapshot-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-snapshot-identifier` | **Yes** | string | -- | Snapshot identifier |

**Output Schema:**
```json
{
    "DBClusterSnapshot": {
        "DBClusterSnapshotIdentifier": "string",
        "DBClusterIdentifier": "string",
        "Status": "deleting",
        "DBClusterSnapshotArn": "string"
    }
}
```

---

### 4.4 `describe-db-cluster-snapshots`

Describes Neptune DB cluster snapshots. **Paginated operation.**

**Synopsis:**
```bash
aws neptune describe-db-cluster-snapshots \
    [--db-cluster-identifier <value>] \
    [--db-cluster-snapshot-identifier <value>] \
    [--snapshot-type <value>] \
    [--filters <value>] \
    [--include-shared | --no-include-shared] \
    [--include-public | --no-include-public] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-identifier` | No | string | -- | Filter by cluster identifier |
| `--db-cluster-snapshot-identifier` | No | string | -- | Specific snapshot to describe |
| `--snapshot-type` | No | string | -- | Filter: `automated`, `manual`, `shared`, `public` |
| `--include-shared` | No | boolean | false | Include shared snapshots |
| `--include-public` | No | boolean | false | Include public snapshots |

**Output Schema:**
```json
{
    "DBClusterSnapshots": [
        {
            "DBClusterSnapshotIdentifier": "string",
            "DBClusterIdentifier": "string",
            "SnapshotCreateTime": "timestamp",
            "Engine": "neptune",
            "Status": "string",
            "Port": "integer",
            "VpcId": "string",
            "EngineVersion": "string",
            "SnapshotType": "string",
            "StorageEncrypted": "boolean",
            "KmsKeyId": "string",
            "DBClusterSnapshotArn": "string",
            "StorageType": "string"
        }
    ]
}
```

---

### 4.5 `describe-db-cluster-snapshot-attributes`

Returns the snapshot attribute values for a Neptune DB cluster snapshot.

**Synopsis:**
```bash
aws neptune describe-db-cluster-snapshot-attributes \
    --db-cluster-snapshot-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-snapshot-identifier` | **Yes** | string | -- | Snapshot identifier |

**Output Schema:**
```json
{
    "DBClusterSnapshotAttributesResult": {
        "DBClusterSnapshotIdentifier": "string",
        "DBClusterSnapshotAttributes": [
            {
                "AttributeName": "string",
                "AttributeValues": ["string"]
            }
        ]
    }
}
```

---

### 4.6 `modify-db-cluster-snapshot-attribute`

Modifies the sharing attributes of a Neptune DB cluster snapshot.

**Synopsis:**
```bash
aws neptune modify-db-cluster-snapshot-attribute \
    --db-cluster-snapshot-identifier <value> \
    --attribute-name <value> \
    [--values-to-add <value>] \
    [--values-to-remove <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-snapshot-identifier` | **Yes** | string | -- | Snapshot identifier |
| `--attribute-name` | **Yes** | string | -- | Attribute name (e.g., `restore`) |
| `--values-to-add` | No | list(string) | None | Account IDs to grant access (`all` for public) |
| `--values-to-remove` | No | list(string) | None | Account IDs to revoke access |

**Output Schema:**
```json
{
    "DBClusterSnapshotAttributesResult": {
        "DBClusterSnapshotIdentifier": "string",
        "DBClusterSnapshotAttributes": [
            {
                "AttributeName": "restore",
                "AttributeValues": ["string"]
            }
        ]
    }
}
```

---

### 4.7 `restore-db-cluster-from-snapshot`

Restores a Neptune DB cluster from a snapshot.

**Synopsis:**
```bash
aws neptune restore-db-cluster-from-snapshot \
    --db-cluster-identifier <value> \
    --snapshot-identifier <value> \
    --engine <value> \
    [--engine-version <value>] \
    [--port <value>] \
    [--db-subnet-group-name <value>] \
    [--vpc-security-group-ids <value>] \
    [--tags <value>] \
    [--kms-key-id <value>] \
    [--enable-iam-database-authentication | --no-enable-iam-database-authentication] \
    [--enable-cloudwatch-logs-exports <value>] \
    [--db-cluster-parameter-group-name <value>] \
    [--deletion-protection | --no-deletion-protection] \
    [--copy-tags-to-snapshot | --no-copy-tags-to-snapshot] \
    [--serverless-v2-scaling-configuration <value>] \
    [--storage-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-identifier` | **Yes** | string | -- | New cluster identifier |
| `--snapshot-identifier` | **Yes** | string | -- | Snapshot to restore from |
| `--engine` | **Yes** | string | -- | Engine: `neptune` |
| `--engine-version` | No | string | -- | Engine version |
| `--port` | No | integer | 8182 | Port number |
| `--db-subnet-group-name` | No | string | -- | DB subnet group |
| `--vpc-security-group-ids` | No | list(string) | -- | VPC security groups |
| `--kms-key-id` | No | string | -- | KMS key for encryption |
| `--deletion-protection` | No | boolean | false | Enable deletion protection |
| `--serverless-v2-scaling-configuration` | No | structure | None | Serverless scaling config |
| `--storage-type` | No | string | -- | `standard` or `iopt1` |

**Output Schema:**
```json
{
    "DBCluster": {
        "DBClusterIdentifier": "string",
        "DBClusterArn": "string",
        "Status": "creating",
        "Endpoint": "string",
        "ReaderEndpoint": "string",
        "Engine": "neptune",
        "EngineVersion": "string",
        "Port": "integer",
        "StorageEncrypted": "boolean"
    }
}
```

---

### 4.8 `restore-db-cluster-to-point-in-time`

Restores a Neptune DB cluster to a specific point in time.

**Synopsis:**
```bash
aws neptune restore-db-cluster-to-point-in-time \
    --db-cluster-identifier <value> \
    --source-db-cluster-identifier <value> \
    [--restore-to-time <value>] \
    [--use-latest-restorable-time | --no-use-latest-restorable-time] \
    [--port <value>] \
    [--db-subnet-group-name <value>] \
    [--vpc-security-group-ids <value>] \
    [--tags <value>] \
    [--kms-key-id <value>] \
    [--enable-iam-database-authentication | --no-enable-iam-database-authentication] \
    [--enable-cloudwatch-logs-exports <value>] \
    [--db-cluster-parameter-group-name <value>] \
    [--deletion-protection | --no-deletion-protection] \
    [--serverless-v2-scaling-configuration <value>] \
    [--storage-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-identifier` | **Yes** | string | -- | New cluster identifier |
| `--source-db-cluster-identifier` | **Yes** | string | -- | Source cluster to restore from |
| `--restore-to-time` | No | timestamp | -- | Point in time (ISO 8601 format) |
| `--use-latest-restorable-time` | No | boolean | false | Use latest restorable time |
| `--port` | No | integer | 8182 | Port number |
| `--db-subnet-group-name` | No | string | -- | DB subnet group |
| `--vpc-security-group-ids` | No | list(string) | -- | VPC security groups |
| `--deletion-protection` | No | boolean | false | Enable deletion protection |
| `--serverless-v2-scaling-configuration` | No | structure | None | Serverless scaling config |
| `--storage-type` | No | string | -- | `standard` or `iopt1` |

**Output Schema:**
```json
{
    "DBCluster": {
        "DBClusterIdentifier": "string",
        "DBClusterArn": "string",
        "Status": "creating",
        "Endpoint": "string",
        "ReaderEndpoint": "string",
        "Engine": "neptune",
        "EngineVersion": "string"
    }
}
```
