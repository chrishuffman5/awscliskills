# Snapshots

### 3.1 `create-db-cluster-snapshot`

Creates a manual snapshot of a DocumentDB cluster.

**Synopsis:**
```bash
aws docdb create-db-cluster-snapshot \
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
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "DBClusterSnapshot": {
        "DBClusterSnapshotIdentifier": "string",
        "DBClusterIdentifier": "string",
        "DBClusterSnapshotArn": "string",
        "SnapshotCreateTime": "timestamp",
        "Engine": "string",
        "EngineVersion": "string",
        "Status": "string",
        "Port": "integer",
        "VpcId": "string",
        "ClusterCreateTime": "timestamp",
        "MasterUsername": "string",
        "AvailabilityZones": ["string"],
        "SnapshotType": "string",
        "PercentProgress": "integer",
        "StorageEncrypted": true|false,
        "KmsKeyId": "string",
        "SourceDBClusterSnapshotArn": "string",
        "StorageType": "string"
    }
}
```

---

### 3.2 `delete-db-cluster-snapshot`

Deletes a cluster snapshot. The snapshot must be in the `available` state.

**Synopsis:**
```bash
aws docdb delete-db-cluster-snapshot \
    --db-cluster-snapshot-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-snapshot-identifier` | **Yes** | string | -- | Snapshot identifier to delete |

**Output Schema:** Same as `create-db-cluster-snapshot` output.

---

### 3.3 `describe-db-cluster-snapshots`

Returns information about cluster snapshots. **Paginated operation.**

**Synopsis:**
```bash
aws docdb describe-db-cluster-snapshots \
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
| `--db-cluster-identifier` | No | string | All | Filter by cluster identifier |
| `--db-cluster-snapshot-identifier` | No | string | All | Specific snapshot identifier |
| `--snapshot-type` | No | string | All | Type: `automated`, `manual`, `shared`, `public` |
| `--filters` | No | list | None | Filters |
| `--include-shared` | No | boolean | false | Include shared snapshots |
| `--include-public` | No | boolean | false | Include public snapshots |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "DBClusterSnapshots": [
        {
            "DBClusterSnapshotIdentifier": "string",
            "DBClusterIdentifier": "string",
            "DBClusterSnapshotArn": "string",
            "SnapshotCreateTime": "timestamp",
            "Engine": "string",
            "Status": "string",
            "SnapshotType": "string",
            "PercentProgress": "integer",
            "StorageEncrypted": true|false,
            "StorageType": "string"
        }
    ],
    "Marker": "string"
}
```

---

### 3.4 `describe-db-cluster-snapshot-attributes`

Returns a list of attributes and values for a cluster snapshot that can be shared with other accounts.

**Synopsis:**
```bash
aws docdb describe-db-cluster-snapshot-attributes \
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

### 3.5 `modify-db-cluster-snapshot-attribute`

Adds or removes an attribute and values from a cluster snapshot. Used to share/unshare snapshots with other accounts.

**Synopsis:**
```bash
aws docdb modify-db-cluster-snapshot-attribute \
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
| `--values-to-add` | No | list(string) | None | Account IDs to add (or `all` for public) |
| `--values-to-remove` | No | list(string) | None | Account IDs to remove |

**Output Schema:** Same as `describe-db-cluster-snapshot-attributes` output.

---

### 3.6 `copy-db-cluster-snapshot`

Copies a cluster snapshot. Can be used for cross-region copies.

**Synopsis:**
```bash
aws docdb copy-db-cluster-snapshot \
    --source-db-cluster-snapshot-identifier <value> \
    --target-db-cluster-snapshot-identifier <value> \
    [--kms-key-id <value>] \
    [--pre-signed-url <value>] \
    [--copy-tags | --no-copy-tags] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-db-cluster-snapshot-identifier` | **Yes** | string | -- | Source snapshot identifier or ARN |
| `--target-db-cluster-snapshot-identifier` | **Yes** | string | -- | Target snapshot identifier |
| `--kms-key-id` | No | string | -- | KMS key for encrypted copies |
| `--pre-signed-url` | No | string | -- | Pre-signed URL for cross-region copies |
| `--copy-tags` | No | boolean | false | Copy tags from source |
| `--tags` | No | list | None | Additional tags |

**Output Schema:** Same as `create-db-cluster-snapshot` output.

---

### 3.7 `restore-db-cluster-from-snapshot`

Creates a new cluster from a snapshot.

**Synopsis:**
```bash
aws docdb restore-db-cluster-from-snapshot \
    --db-cluster-identifier <value> \
    --snapshot-identifier <value> \
    --engine <value> \
    [--availability-zones <value>] \
    [--engine-version <value>] \
    [--port <value>] \
    [--db-subnet-group-name <value>] \
    [--vpc-security-group-ids <value>] \
    [--tags <value>] \
    [--kms-key-id <value>] \
    [--enable-cloudwatch-logs-exports <value>] \
    [--deletion-protection | --no-deletion-protection] \
    [--db-cluster-parameter-group-name <value>] \
    [--storage-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-identifier` | **Yes** | string | -- | New cluster identifier |
| `--snapshot-identifier` | **Yes** | string | -- | Snapshot identifier or ARN |
| `--engine` | **Yes** | string | -- | Engine: `docdb` |
| `--availability-zones` | No | list(string) | Auto | AZs for the cluster |
| `--engine-version` | No | string | -- | Engine version |
| `--port` | No | integer | 27017 | Port number |
| `--db-subnet-group-name` | No | string | -- | Subnet group |
| `--vpc-security-group-ids` | No | list(string) | -- | Security group IDs |
| `--tags` | No | list | None | Tags |
| `--kms-key-id` | No | string | -- | KMS key for encryption |
| `--enable-cloudwatch-logs-exports` | No | list(string) | -- | Log types to export |
| `--deletion-protection` | No | boolean | -- | Enable deletion protection |
| `--db-cluster-parameter-group-name` | No | string | -- | Parameter group |
| `--storage-type` | No | string | -- | Storage type |

**Output Schema:** Same as `create-db-cluster` output (clusters.md).

---

### 3.8 `restore-db-cluster-to-point-in-time`

Restores a cluster to a specific point in time. A new cluster is created from the source.

**Synopsis:**
```bash
aws docdb restore-db-cluster-to-point-in-time \
    --db-cluster-identifier <value> \
    --source-db-cluster-identifier <value> \
    [--restore-to-time <value>] \
    [--use-latest-restorable-time | --no-use-latest-restorable-time] \
    [--port <value>] \
    [--db-subnet-group-name <value>] \
    [--vpc-security-group-ids <value>] \
    [--tags <value>] \
    [--kms-key-id <value>] \
    [--enable-cloudwatch-logs-exports <value>] \
    [--deletion-protection | --no-deletion-protection] \
    [--storage-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-identifier` | **Yes** | string | -- | New cluster identifier |
| `--source-db-cluster-identifier` | **Yes** | string | -- | Source cluster identifier or ARN |
| `--restore-to-time` | No | timestamp | -- | Point in time (ISO 8601) |
| `--use-latest-restorable-time` | No | boolean | false | Use latest restorable time |
| `--port` | No | integer | -- | Port number |
| `--db-subnet-group-name` | No | string | -- | Subnet group |
| `--vpc-security-group-ids` | No | list(string) | -- | Security group IDs |
| `--tags` | No | list | None | Tags |
| `--kms-key-id` | No | string | -- | KMS key for encryption |
| `--enable-cloudwatch-logs-exports` | No | list(string) | -- | Log types to export |
| `--deletion-protection` | No | boolean | -- | Enable deletion protection |
| `--storage-type` | No | string | -- | Storage type |

**Output Schema:** Same as `create-db-cluster` output (clusters.md).
