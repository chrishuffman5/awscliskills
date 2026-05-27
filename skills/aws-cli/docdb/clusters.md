# Clusters

### 1.1 `create-db-cluster`

Creates a new Amazon DocumentDB cluster.

**Synopsis:**
```bash
aws docdb create-db-cluster \
    --db-cluster-identifier <value> \
    --engine <value> \
    [--availability-zones <value>] \
    [--backup-retention-period <value>] \
    [--db-cluster-parameter-group-name <value>] \
    [--vpc-security-group-ids <value>] \
    [--db-subnet-group-name <value>] \
    [--engine-version <value>] \
    [--port <value>] \
    [--master-username <value>] \
    [--master-user-password <value>] \
    [--preferred-backup-window <value>] \
    [--preferred-maintenance-window <value>] \
    [--tags <value>] \
    [--storage-encrypted | --no-storage-encrypted] \
    [--kms-key-id <value>] \
    [--enable-cloudwatch-logs-exports <value>] \
    [--deletion-protection | --no-deletion-protection] \
    [--global-cluster-identifier <value>] \
    [--storage-type <value>] \
    [--pre-signed-url <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-identifier` | **Yes** | string | -- | Cluster identifier (1-63 chars: letters, numbers, hyphens) |
| `--engine` | **Yes** | string | -- | Database engine: `docdb` |
| `--availability-zones` | No | list(string) | Auto | AZs for the cluster |
| `--backup-retention-period` | No | integer | 1 | Days to retain backups (1-35) |
| `--db-cluster-parameter-group-name` | No | string | Default | Parameter group name |
| `--vpc-security-group-ids` | No | list(string) | Default VPC SG | VPC security group IDs |
| `--db-subnet-group-name` | No | string | Default | DB subnet group name |
| `--engine-version` | No | string | Latest | Engine version |
| `--port` | No | integer | 27017 | Port number |
| `--master-username` | No | string | -- | Master user name (required for new clusters) |
| `--master-user-password` | No | string | -- | Master user password (required for new clusters) |
| `--preferred-backup-window` | No | string | Auto | Daily backup window (UTC, hh24:mi-hh24:mi) |
| `--preferred-maintenance-window` | No | string | Auto | Weekly maintenance window |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--storage-encrypted` | No | boolean | false | Enable encryption at rest |
| `--kms-key-id` | No | string | Default | KMS key ID for encryption |
| `--enable-cloudwatch-logs-exports` | No | list(string) | None | Log types to export: `audit`, `profiler` |
| `--deletion-protection` | No | boolean | false | Enable deletion protection |
| `--global-cluster-identifier` | No | string | None | Global cluster identifier to join |
| `--storage-type` | No | string | `standard` | Storage type: `standard` or `iopt1` |
| `--pre-signed-url` | No | string | None | Pre-signed URL for cross-region copy |

**Output Schema:**
```json
{
    "DBCluster": {
        "DBClusterIdentifier": "string",
        "DBClusterArn": "string",
        "Status": "string",
        "Engine": "docdb",
        "EngineVersion": "string",
        "Endpoint": "string",
        "ReaderEndpoint": "string",
        "Port": "integer",
        "MasterUsername": "string",
        "PreferredBackupWindow": "string",
        "PreferredMaintenanceWindow": "string",
        "DBClusterMembers": [
            {
                "DBInstanceIdentifier": "string",
                "IsClusterWriter": true|false,
                "DBClusterParameterGroupStatus": "string",
                "PromotionTier": "integer"
            }
        ],
        "VpcSecurityGroups": [
            {
                "VpcSecurityGroupId": "string",
                "Status": "string"
            }
        ],
        "AvailabilityZones": ["string"],
        "BackupRetentionPeriod": "integer",
        "DBSubnetGroup": "string",
        "DBClusterParameterGroup": "string",
        "StorageEncrypted": true|false,
        "KmsKeyId": "string",
        "DbClusterResourceId": "string",
        "ClusterCreateTime": "timestamp",
        "EnabledCloudwatchLogsExports": ["string"],
        "DeletionProtection": true|false,
        "StorageType": "string",
        "MultiAZ": true|false
    }
}
```

---

### 1.2 `delete-db-cluster`

Deletes a previously provisioned cluster. A final snapshot can be created before deletion.

**Synopsis:**
```bash
aws docdb delete-db-cluster \
    --db-cluster-identifier <value> \
    [--skip-final-snapshot | --no-skip-final-snapshot] \
    [--final-db-snapshot-identifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-identifier` | **Yes** | string | -- | Cluster identifier to delete |
| `--skip-final-snapshot` | No | boolean | false | Skip creating a final snapshot |
| `--final-db-snapshot-identifier` | No | string | -- | Identifier for the final snapshot (required if not skipping) |

**Output Schema:** Same as `create-db-cluster` output.

---

### 1.3 `describe-db-clusters`

Returns information about provisioned DocumentDB clusters. **Paginated operation.**

**Synopsis:**
```bash
aws docdb describe-db-clusters \
    [--db-cluster-identifier <value>] \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-identifier` | No | string | All | Cluster identifier to describe |
| `--filters` | No | list | None | Filters. Shorthand: `Name=string,Values=string,string ...` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "DBClusters": [
        {
            "DBClusterIdentifier": "string",
            "DBClusterArn": "string",
            "Status": "string",
            "Engine": "string",
            "EngineVersion": "string",
            "Endpoint": "string",
            "ReaderEndpoint": "string",
            "Port": "integer",
            "MasterUsername": "string",
            "DBClusterMembers": [],
            "VpcSecurityGroups": [],
            "AvailabilityZones": [],
            "BackupRetentionPeriod": "integer",
            "DBSubnetGroup": "string",
            "StorageEncrypted": true|false,
            "DeletionProtection": true|false,
            "StorageType": "string",
            "CloneGroupId": "string"
        }
    ],
    "Marker": "string"
}
```

---

### 1.4 `modify-db-cluster`

Modifies a setting for a DocumentDB cluster.

**Synopsis:**
```bash
aws docdb modify-db-cluster \
    --db-cluster-identifier <value> \
    [--new-db-cluster-identifier <value>] \
    [--apply-immediately | --no-apply-immediately] \
    [--backup-retention-period <value>] \
    [--db-cluster-parameter-group-name <value>] \
    [--vpc-security-group-ids <value>] \
    [--port <value>] \
    [--master-user-password <value>] \
    [--preferred-backup-window <value>] \
    [--preferred-maintenance-window <value>] \
    [--enable-cloudwatch-logs-exports <value>] \
    [--engine-version <value>] \
    [--allow-major-version-upgrade | --no-allow-major-version-upgrade] \
    [--deletion-protection | --no-deletion-protection] \
    [--storage-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-identifier` | **Yes** | string | -- | Cluster identifier |
| `--new-db-cluster-identifier` | No | string | -- | New cluster identifier (rename) |
| `--apply-immediately` | No | boolean | false | Apply changes immediately vs. next maintenance window |
| `--backup-retention-period` | No | integer | -- | Days to retain backups (1-35) |
| `--db-cluster-parameter-group-name` | No | string | -- | New parameter group |
| `--vpc-security-group-ids` | No | list(string) | -- | New security group IDs |
| `--port` | No | integer | -- | New port number |
| `--master-user-password` | No | string | -- | New master password |
| `--preferred-backup-window` | No | string | -- | New backup window |
| `--preferred-maintenance-window` | No | string | -- | New maintenance window |
| `--enable-cloudwatch-logs-exports` | No | structure | -- | CloudWatch log export config |
| `--engine-version` | No | string | -- | New engine version |
| `--allow-major-version-upgrade` | No | boolean | false | Allow major version upgrades |
| `--deletion-protection` | No | boolean | -- | Enable/disable deletion protection |
| `--storage-type` | No | string | -- | Storage type: `standard` or `iopt1` |

**Output Schema:** Same as `create-db-cluster` output.

---

### 1.5 `start-db-cluster`

Starts a stopped DocumentDB cluster.

**Synopsis:**
```bash
aws docdb start-db-cluster \
    --db-cluster-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-identifier` | **Yes** | string | -- | Cluster identifier to start |

**Output Schema:** Same as `create-db-cluster` output.

---

### 1.6 `stop-db-cluster`

Stops a running DocumentDB cluster. The cluster can be stopped for up to 7 days before it is automatically started.

**Synopsis:**
```bash
aws docdb stop-db-cluster \
    --db-cluster-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-identifier` | **Yes** | string | -- | Cluster identifier to stop |

**Output Schema:** Same as `create-db-cluster` output.

---

### 1.7 `failover-db-cluster`

Forces a failover for a DocumentDB cluster. A failover promotes one of the read replicas to be the primary writer instance.

**Synopsis:**
```bash
aws docdb failover-db-cluster \
    [--db-cluster-identifier <value>] \
    [--target-db-instance-identifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-identifier` | No | string | -- | Cluster identifier |
| `--target-db-instance-identifier` | No | string | -- | Instance to promote to primary |

**Output Schema:** Same as `create-db-cluster` output.
