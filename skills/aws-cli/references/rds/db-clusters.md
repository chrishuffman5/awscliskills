# DB Clusters (Aurora)

### 2.1 `create-db-cluster`

Creates a new Aurora DB cluster or Multi-AZ DB cluster.

**Synopsis:**
```bash
aws rds create-db-cluster \
    --db-cluster-identifier <value> \
    --engine <value> \
    [--master-username <value>] \
    [--master-user-password <value>] \
    [--engine-version <value>] \
    [--db-subnet-group-name <value>] \
    [--vpc-security-group-ids <value>] \
    [--tags <value>]
```

**Required Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--db-cluster-identifier` | string | Unique cluster identifier (1-63 chars for Aurora, 1-52 for Multi-AZ) |
| `--engine` | string | `aurora-mysql`, `aurora-postgresql`, `mysql`, `postgres` |

**Key Optional Parameters:**

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `--master-username` | string | -- | Master username (1-16 chars) |
| `--master-user-password` | string | -- | Master password (8-41 chars) |
| `--engine-version` | string | latest | Engine version |
| `--port` | integer | engine default | Port (1150-65535) |
| `--database-name` | string | None | Initial database name |
| `--db-subnet-group-name` | string | default | Subnet group |
| `--vpc-security-group-ids` | list | default | Security groups |
| `--availability-zones` | list | auto | AZs (max 3 for Aurora) |
| `--backup-retention-period` | integer | 1 | Days to retain backups (1-35) |
| `--preferred-backup-window` | string | auto | Daily backup window `hh24:mi-hh24:mi` |
| `--preferred-maintenance-window` | string | auto | Weekly maintenance window |
| `--storage-encrypted` / `--no-storage-encrypted` | boolean | false | Encryption at rest |
| `--kms-key-id` | string | default | KMS key for encryption |
| `--deletion-protection` / `--no-deletion-protection` | boolean | false | Deletion protection |
| `--copy-tags-to-snapshot` / `--no-copy-tags-to-snapshot` | boolean | false | Copy tags to snapshots |
| `--enable-iam-database-authentication` / `--no-enable-iam-database-authentication` | boolean | false | IAM auth |
| `--enable-cloudwatch-logs-exports` | list | None | Log types to export |
| `--enable-http-endpoint` / `--no-enable-http-endpoint` | boolean | false | RDS Data API |
| `--manage-master-user-password` / `--no-manage-master-user-password` | boolean | false | Secrets Manager password |
| `--serverless-v2-scaling-configuration` | structure | None | `MinCapacity=double,MaxCapacity=double` |
| `--db-cluster-parameter-group-name` | string | default | Cluster parameter group |
| `--backtrack-window` | long | 0 | Backtrack window in seconds (0-259200, Aurora MySQL only) |
| `--global-cluster-identifier` | string | None | Global database cluster ID |
| `--tags` | list | None | Tags |
| `--db-cluster-instance-class` | string | None | Instance class (Multi-AZ clusters) |
| `--allocated-storage` | integer | None | Storage in GiB (Multi-AZ clusters) |
| `--storage-type` | string | `aurora` | `aurora`, `aurora-iopt1` (Aurora); `io1`, `io2`, `gp3` (Multi-AZ) |
| `--iops` | integer | None | Provisioned IOPS (Multi-AZ clusters) |

**Output Schema:**
```json
{
    "DBCluster": {
        "DBClusterIdentifier": "string",
        "DBClusterArn": "string",
        "Status": "string",
        "Engine": "string",
        "EngineVersion": "string",
        "Endpoint": "string",
        "ReaderEndpoint": "string",
        "Port": "integer",
        "MasterUsername": "string",
        "DatabaseName": "string",
        "MultiAZ": "boolean",
        "AllocatedStorage": "integer",
        "AvailabilityZones": ["string"],
        "BackupRetentionPeriod": "integer",
        "PreferredBackupWindow": "string",
        "PreferredMaintenanceWindow": "string",
        "DBClusterMembers": [
            {
                "DBInstanceIdentifier": "string",
                "IsClusterWriter": "boolean",
                "DBClusterParameterGroupStatus": "string",
                "PromotionTier": "integer"
            }
        ],
        "VpcSecurityGroups": [
            { "VpcSecurityGroupId": "string", "Status": "string" }
        ],
        "DBSubnetGroup": "string",
        "DBClusterParameterGroup": "string",
        "StorageEncrypted": "boolean",
        "KmsKeyId": "string",
        "DbClusterResourceId": "string",
        "IAMDatabaseAuthenticationEnabled": "boolean",
        "EnabledCloudwatchLogsExports": ["string"],
        "DeletionProtection": "boolean",
        "HttpEndpointEnabled": "boolean",
        "CopyTagsToSnapshot": "boolean",
        "TagList": [{ "Key": "string", "Value": "string" }]
    }
}
```

---

### 2.2 `delete-db-cluster`

Deletes an Aurora DB cluster.

**Synopsis:**
```bash
aws rds delete-db-cluster \
    --db-cluster-identifier <value> \
    [--skip-final-snapshot | --no-skip-final-snapshot] \
    [--final-db-snapshot-identifier <value>] \
    [--delete-automated-backups | --no-delete-automated-backups]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-identifier` | **Yes** | string | -- | Cluster identifier |
| `--skip-final-snapshot` / `--no-skip-final-snapshot` | No | boolean | false | Skip final snapshot |
| `--final-db-snapshot-identifier` | No | string | None | Final snapshot name |
| `--delete-automated-backups` / `--no-delete-automated-backups` | No | boolean | true | Delete automated backups |

**Output Schema:** Same `DBCluster` structure.

---

### 2.3 `describe-db-clusters`

Describes Aurora DB clusters. **Paginated.**

**Synopsis:**
```bash
aws rds describe-db-clusters \
    [--db-cluster-identifier <value>] \
    [--filters <value>] \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-identifier` | No | string | all | Specific cluster identifier |
| `--filters` | No | list | None | Filters: `db-cluster-id`, `db-cluster-resource-id`, `domain`, `engine`. Syntax: `Name=string,Values=string,string` |
| `--max-items` | No | integer | None | Total items |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per call |

**Output Schema:**
```json
{
    "DBClusters": [
        { "...same DBCluster structure..." }
    ],
    "Marker": "string"
}
```

---

### 2.4 `modify-db-cluster`

Modifies an Aurora DB cluster.

**Synopsis:**
```bash
aws rds modify-db-cluster \
    --db-cluster-identifier <value> \
    [--new-db-cluster-identifier <value>] \
    [--apply-immediately | --no-apply-immediately] \
    [--master-user-password <value>] \
    [--engine-version <value>]
```

**Required Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--db-cluster-identifier` | string | Cluster identifier |

**Key Optional Parameters:**

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `--new-db-cluster-identifier` | string | no change | Rename the cluster |
| `--apply-immediately` / `--no-apply-immediately` | boolean | false | Apply now vs. maintenance window |
| `--master-user-password` | string | no change | New master password |
| `--engine-version` | string | no change | Engine version to upgrade to |
| `--backup-retention-period` | integer | no change | Days (1-35) |
| `--preferred-backup-window` | string | no change | Backup window |
| `--preferred-maintenance-window` | string | no change | Maintenance window |
| `--vpc-security-group-ids` | list | no change | Security groups |
| `--port` | integer | no change | Port number |
| `--db-cluster-parameter-group-name` | string | no change | Parameter group |
| `--deletion-protection` / `--no-deletion-protection` | boolean | no change | Deletion protection |
| `--enable-iam-database-authentication` / `--no-enable-iam-database-authentication` | boolean | no change | IAM auth |
| `--enable-http-endpoint` / `--no-enable-http-endpoint` | boolean | no change | Data API |
| `--serverless-v2-scaling-configuration` | structure | no change | Serverless v2 scaling |
| `--enable-cloudwatch-logs-exports` | list | no change | Log exports |

**Output Schema:** Same `DBCluster` structure.

---

### 2.5 `failover-db-cluster`

Forces a failover for an Aurora DB cluster.

**Synopsis:**
```bash
aws rds failover-db-cluster \
    --db-cluster-identifier <value> \
    [--target-db-instance-identifier <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-identifier` | **Yes** | string | -- | Cluster identifier |
| `--target-db-instance-identifier` | No | string | auto | Target instance for new primary |

**Output Schema:** Same `DBCluster` structure.

---

### 2.6 `start-db-cluster`

Starts a stopped Aurora DB cluster.

**Synopsis:**
```bash
aws rds start-db-cluster \
    --db-cluster-identifier <value>
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--db-cluster-identifier` | **Yes** | string | Cluster identifier |

**Output Schema:** Same `DBCluster` structure.

---

### 2.7 `stop-db-cluster`

Stops an Aurora DB cluster. Can be stopped for up to 7 days.

**Synopsis:**
```bash
aws rds stop-db-cluster \
    --db-cluster-identifier <value>
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--db-cluster-identifier` | **Yes** | string | Cluster identifier |

**Output Schema:** Same `DBCluster` structure.

---

### 2.8 `create-db-cluster-endpoint`

Creates a custom endpoint for an Aurora cluster.

**Synopsis:**
```bash
aws rds create-db-cluster-endpoint \
    --db-cluster-identifier <value> \
    --db-cluster-endpoint-identifier <value> \
    --endpoint-type <value> \
    [--static-members <value>] \
    [--excluded-members <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--db-cluster-identifier` | **Yes** | string | Cluster identifier |
| `--db-cluster-endpoint-identifier` | **Yes** | string | Endpoint identifier |
| `--endpoint-type` | **Yes** | string | `READER`, `ANY` |
| `--static-members` | No | list | Instance identifiers for static membership |
| `--excluded-members` | No | list | Instance identifiers to exclude |
| `--tags` | No | list | Tags |

**Output Schema:**
```json
{
    "DBClusterEndpointIdentifier": "string",
    "DBClusterIdentifier": "string",
    "DBClusterEndpointResourceIdentifier": "string",
    "Endpoint": "string",
    "Status": "string",
    "EndpointType": "string",
    "CustomEndpointType": "READER|ANY",
    "StaticMembers": ["string"],
    "ExcludedMembers": ["string"],
    "DBClusterEndpointArn": "string"
}
```

---

### 2.9 `describe-db-cluster-endpoints`

Describes custom endpoints for Aurora clusters. **Paginated.**

**Synopsis:**
```bash
aws rds describe-db-cluster-endpoints \
    [--db-cluster-identifier <value>] \
    [--db-cluster-endpoint-identifier <value>] \
    [--filters <value>] \
    [--max-items <value>] \
    [--starting-token <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-identifier` | No | string | all | Cluster identifier |
| `--db-cluster-endpoint-identifier` | No | string | all | Endpoint identifier |
| `--filters` | No | list | None | Filters: `db-cluster-endpoint-type`, `db-cluster-endpoint-custom-type`, `db-cluster-endpoint-id`, `db-cluster-endpoint-status` |

**Output Schema:**
```json
{
    "DBClusterEndpoints": [
        { "...same structure as create-db-cluster-endpoint output..." }
    ],
    "Marker": "string"
}
```

---

### 2.10 `modify-db-cluster-endpoint`

Modifies a custom endpoint for an Aurora cluster.

**Synopsis:**
```bash
aws rds modify-db-cluster-endpoint \
    --db-cluster-endpoint-identifier <value> \
    [--endpoint-type <value>] \
    [--static-members <value>] \
    [--excluded-members <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--db-cluster-endpoint-identifier` | **Yes** | string | Endpoint identifier |
| `--endpoint-type` | No | string | `READER`, `ANY` |
| `--static-members` | No | list | Static member instances |
| `--excluded-members` | No | list | Excluded member instances |

**Output Schema:** Same as `create-db-cluster-endpoint`.

---

### 2.11 `delete-db-cluster-endpoint`

Deletes a custom endpoint for an Aurora cluster.

**Synopsis:**
```bash
aws rds delete-db-cluster-endpoint \
    --db-cluster-endpoint-identifier <value>
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--db-cluster-endpoint-identifier` | **Yes** | string | Endpoint identifier |

**Output Schema:** Same as `create-db-cluster-endpoint`.

---
