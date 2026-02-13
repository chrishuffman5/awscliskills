# Snapshots

### 3.1 `create-db-snapshot`

Creates a snapshot of a DB instance.

**Synopsis:**
```bash
aws rds create-db-snapshot \
    --db-snapshot-identifier <value> \
    --db-instance-identifier <value> \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--db-snapshot-identifier` | **Yes** | string | Snapshot identifier (1-255 chars) |
| `--db-instance-identifier` | **Yes** | string | Source DB instance identifier |
| `--tags` | No | list | Tags |

**Output Schema:**
```json
{
    "DBSnapshot": {
        "DBSnapshotIdentifier": "string",
        "DBInstanceIdentifier": "string",
        "SnapshotCreateTime": "timestamp",
        "Engine": "string",
        "AllocatedStorage": "integer",
        "Status": "string",
        "Port": "integer",
        "AvailabilityZone": "string",
        "VpcId": "string",
        "InstanceCreateTime": "timestamp",
        "MasterUsername": "string",
        "EngineVersion": "string",
        "LicenseModel": "string",
        "SnapshotType": "string",
        "Iops": "integer",
        "StorageThroughput": "integer",
        "StorageType": "string",
        "Encrypted": "boolean",
        "KmsKeyId": "string",
        "DBSnapshotArn": "string",
        "IAMDatabaseAuthenticationEnabled": "boolean",
        "DbiResourceId": "string",
        "TagList": [{ "Key": "string", "Value": "string" }],
        "PercentProgress": "integer"
    }
}
```

---

### 3.2 `delete-db-snapshot`

Deletes a DB instance snapshot.

**Synopsis:**
```bash
aws rds delete-db-snapshot \
    --db-snapshot-identifier <value>
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--db-snapshot-identifier` | **Yes** | string | Snapshot identifier |

**Output Schema:** Same `DBSnapshot` structure.

---

### 3.3 `describe-db-snapshots`

Describes DB instance snapshots. **Paginated.**

**Synopsis:**
```bash
aws rds describe-db-snapshots \
    [--db-instance-identifier <value>] \
    [--db-snapshot-identifier <value>] \
    [--snapshot-type <value>] \
    [--filters <value>] \
    [--max-items <value>] \
    [--starting-token <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-instance-identifier` | No | string | all | Filter by source instance |
| `--db-snapshot-identifier` | No | string | all | Specific snapshot |
| `--snapshot-type` | No | string | all | `automated`, `manual`, `shared`, `public`, `awsbackup` |
| `--filters` | No | list | None | Filters: `db-instance-id`, `db-snapshot-id`, `dbi-resource-id`, `snapshot-type`, `engine` |
| `--max-items` | No | integer | None | Total items |
| `--starting-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "DBSnapshots": [
        { "...same DBSnapshot structure..." }
    ],
    "Marker": "string"
}
```

---

### 3.4 `copy-db-snapshot`

Copies a DB instance snapshot. Can copy across regions.

**Synopsis:**
```bash
aws rds copy-db-snapshot \
    --source-db-snapshot-identifier <value> \
    --target-db-snapshot-identifier <value> \
    [--kms-key-id <value>] \
    [--tags <value>] \
    [--copy-tags | --no-copy-tags] \
    [--copy-option-group | --no-copy-option-group] \
    [--source-region <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-db-snapshot-identifier` | **Yes** | string | -- | Source snapshot identifier or ARN |
| `--target-db-snapshot-identifier` | **Yes** | string | -- | Target snapshot identifier |
| `--kms-key-id` | No | string | same as source | KMS key for encryption |
| `--tags` | No | list | None | Tags for the copy |
| `--copy-tags` / `--no-copy-tags` | No | boolean | false | Copy tags from source |
| `--copy-option-group` / `--no-copy-option-group` | No | boolean | false | Copy option group |
| `--source-region` | No | string | None | Source region (for cross-region copy) |

**Output Schema:** Same `DBSnapshot` structure.

---

### 3.5 `restore-db-instance-from-db-snapshot`

Creates a new DB instance from a snapshot.

**Synopsis:**
```bash
aws rds restore-db-instance-from-db-snapshot \
    --db-instance-identifier <value> \
    [--db-snapshot-identifier <value>] \
    [--db-instance-class <value>] \
    [--availability-zone <value>] \
    [--db-subnet-group-name <value>] \
    [--multi-az | --no-multi-az] \
    [--engine <value>] \
    [--storage-type <value>] \
    [--vpc-security-group-ids <value>] \
    [--tags <value>]
```

**Required Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--db-instance-identifier` | string | New DB instance identifier |

**Key Optional Parameters:**

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `--db-snapshot-identifier` | string | -- | Source snapshot identifier or ARN |
| `--db-cluster-snapshot-identifier` | string | -- | Multi-AZ cluster snapshot (alternative to above) |
| `--db-instance-class` | string | same as original | Instance class |
| `--availability-zone` | string | random | AZ for new instance |
| `--db-subnet-group-name` | string | same as original | Subnet group |
| `--multi-az` / `--no-multi-az` | boolean | false | Multi-AZ deployment |
| `--publicly-accessible` / `--no-publicly-accessible` | boolean | same as original | Public access |
| `--engine` | string | same as snapshot | Engine type |
| `--storage-type` | string | same as snapshot | Storage type |
| `--iops` | integer | same as snapshot | Provisioned IOPS |
| `--port` | integer | same as snapshot | Port (1150-65535) |
| `--vpc-security-group-ids` | list | same as snapshot | Security groups |
| `--db-parameter-group-name` | string | default | Parameter group |
| `--option-group-name` | string | default | Option group |
| `--deletion-protection` / `--no-deletion-protection` | boolean | false | Deletion protection |
| `--enable-iam-database-authentication` / `--no-enable-iam-database-authentication` | boolean | false | IAM auth |
| `--enable-cloudwatch-logs-exports` | list | None | Log exports |
| `--tags` | list | None | Tags |

**Output Schema:** Same `DBInstance` structure as `create-db-instance`.

---

### 3.6 `modify-db-snapshot`

Modifies a DB snapshot (e.g. upgrade engine version).

**Synopsis:**
```bash
aws rds modify-db-snapshot \
    --db-snapshot-identifier <value> \
    [--engine-version <value>] \
    [--option-group-name <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--db-snapshot-identifier` | **Yes** | string | Snapshot identifier |
| `--engine-version` | No | string | New engine version |
| `--option-group-name` | No | string | New option group |

**Output Schema:** Same `DBSnapshot` structure.

---

### 3.7 `create-db-cluster-snapshot`

Creates a snapshot of an Aurora cluster.

**Synopsis:**
```bash
aws rds create-db-cluster-snapshot \
    --db-cluster-snapshot-identifier <value> \
    --db-cluster-identifier <value> \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--db-cluster-snapshot-identifier` | **Yes** | string | Cluster snapshot identifier |
| `--db-cluster-identifier` | **Yes** | string | Source cluster identifier |
| `--tags` | No | list | Tags |

**Output Schema:**
```json
{
    "DBClusterSnapshot": {
        "DBClusterSnapshotIdentifier": "string",
        "DBClusterIdentifier": "string",
        "SnapshotCreateTime": "timestamp",
        "Engine": "string",
        "EngineVersion": "string",
        "Status": "string",
        "Port": "integer",
        "VpcId": "string",
        "ClusterCreateTime": "timestamp",
        "MasterUsername": "string",
        "AllocatedStorage": "integer",
        "AvailabilityZones": ["string"],
        "SnapshotType": "string",
        "PercentProgress": "integer",
        "StorageEncrypted": "boolean",
        "KmsKeyId": "string",
        "DBClusterSnapshotArn": "string",
        "IAMDatabaseAuthenticationEnabled": "boolean",
        "TagList": [{ "Key": "string", "Value": "string" }],
        "StorageType": "string",
        "DbClusterResourceId": "string"
    }
}
```

---

### 3.8 `delete-db-cluster-snapshot`

Deletes an Aurora cluster snapshot.

**Synopsis:**
```bash
aws rds delete-db-cluster-snapshot \
    --db-cluster-snapshot-identifier <value>
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--db-cluster-snapshot-identifier` | **Yes** | string | Cluster snapshot identifier |

**Output Schema:** Same `DBClusterSnapshot` structure.

---

### 3.9 `describe-db-cluster-snapshots`

Describes Aurora cluster snapshots. **Paginated.**

**Synopsis:**
```bash
aws rds describe-db-cluster-snapshots \
    [--db-cluster-identifier <value>] \
    [--db-cluster-snapshot-identifier <value>] \
    [--snapshot-type <value>] \
    [--filters <value>] \
    [--max-items <value>] \
    [--starting-token <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-identifier` | No | string | all | Filter by cluster |
| `--db-cluster-snapshot-identifier` | No | string | all | Specific snapshot |
| `--snapshot-type` | No | string | all | `automated`, `manual`, `shared`, `public` |
| `--filters` | No | list | None | Filters: `db-cluster-id`, `db-cluster-snapshot-id`, `snapshot-type`, `engine` |
| `--max-items` | No | integer | None | Total items |
| `--starting-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "DBClusterSnapshots": [
        { "...same DBClusterSnapshot structure..." }
    ],
    "Marker": "string"
}
```

---

### 3.10 `copy-db-cluster-snapshot`

Copies an Aurora cluster snapshot. Can copy across regions.

**Synopsis:**
```bash
aws rds copy-db-cluster-snapshot \
    --source-db-cluster-snapshot-identifier <value> \
    --target-db-cluster-snapshot-identifier <value> \
    [--kms-key-id <value>] \
    [--tags <value>] \
    [--copy-tags | --no-copy-tags] \
    [--source-region <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-db-cluster-snapshot-identifier` | **Yes** | string | -- | Source identifier or ARN |
| `--target-db-cluster-snapshot-identifier` | **Yes** | string | -- | Target identifier |
| `--kms-key-id` | No | string | same as source | KMS key |
| `--tags` | No | list | None | Tags |
| `--copy-tags` / `--no-copy-tags` | No | boolean | false | Copy source tags |
| `--source-region` | No | string | None | Source region |

**Output Schema:** Same `DBClusterSnapshot` structure.

---

### 3.11 `restore-db-cluster-from-snapshot`

Restores an Aurora cluster from a snapshot.

**Synopsis:**
```bash
aws rds restore-db-cluster-from-snapshot \
    --db-cluster-identifier <value> \
    --snapshot-identifier <value> \
    --engine <value> \
    [--engine-version <value>] \
    [--db-subnet-group-name <value>] \
    [--vpc-security-group-ids <value>] \
    [--tags <value>]
```

**Required Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--db-cluster-identifier` | string | New cluster identifier |
| `--snapshot-identifier` | string | Source snapshot identifier or ARN |
| `--engine` | string | Engine type |

**Key Optional Parameters:**

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `--engine-version` | string | same as snapshot | Engine version |
| `--port` | integer | same as snapshot | Port number |
| `--db-subnet-group-name` | string | same as snapshot | Subnet group |
| `--vpc-security-group-ids` | list | same as snapshot | Security groups |
| `--availability-zones` | list | auto | AZs |
| `--db-cluster-parameter-group-name` | string | default | Parameter group |
| `--deletion-protection` / `--no-deletion-protection` | boolean | false | Deletion protection |
| `--enable-iam-database-authentication` / `--no-enable-iam-database-authentication` | boolean | false | IAM auth |
| `--enable-cloudwatch-logs-exports` | list | None | Log exports |
| `--kms-key-id` | string | same as snapshot | KMS key |
| `--serverless-v2-scaling-configuration` | structure | None | Serverless v2 scaling |
| `--tags` | list | None | Tags |

**Output Schema:** Same `DBCluster` structure.

---
