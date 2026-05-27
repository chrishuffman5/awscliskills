# Clusters

### 1.1 `create-db-cluster`

Creates a new Neptune DB cluster.

**Synopsis:**
```bash
aws neptune create-db-cluster \
    --db-cluster-identifier <value> \
    --engine <value> \
    [--engine-version <value>] \
    [--db-cluster-parameter-group-name <value>] \
    [--db-subnet-group-name <value>] \
    [--vpc-security-group-ids <value>] \
    [--availability-zones <value>] \
    [--backup-retention-period <value>] \
    [--preferred-backup-window <value>] \
    [--preferred-maintenance-window <value>] \
    [--storage-encrypted | --no-storage-encrypted] \
    [--kms-key-id <value>] \
    [--enable-iam-database-authentication | --no-enable-iam-database-authentication] \
    [--enable-cloudwatch-logs-exports <value>] \
    [--deletion-protection | --no-deletion-protection] \
    [--serverless-v2-scaling-configuration <value>] \
    [--global-cluster-identifier <value>] \
    [--storage-type <value>] \
    [--copy-tags-to-snapshot | --no-copy-tags-to-snapshot] \
    [--tags <value>] \
    [--port <value>] \
    [--replication-source-identifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-identifier` | **Yes** | string | -- | Cluster identifier (1-63 chars, letters/numbers/hyphens) |
| `--engine` | **Yes** | string | -- | Database engine: `neptune` |
| `--engine-version` | No | string | latest | Engine version (e.g., `1.3.1.0`) |
| `--db-cluster-parameter-group-name` | No | string | default | Cluster parameter group |
| `--db-subnet-group-name` | No | string | -- | DB subnet group |
| `--vpc-security-group-ids` | No | list(string) | -- | VPC security group IDs |
| `--availability-zones` | No | list(string) | -- | Availability zones |
| `--backup-retention-period` | No | integer | 1 | Days to retain backups (1-35) |
| `--preferred-backup-window` | No | string | -- | Daily backup window (e.g., `07:00-07:30`) |
| `--preferred-maintenance-window` | No | string | -- | Weekly maintenance window |
| `--storage-encrypted` | No | boolean | false | Enable encryption at rest |
| `--kms-key-id` | No | string | -- | KMS key for encryption |
| `--enable-iam-database-authentication` | No | boolean | false | Enable IAM auth |
| `--enable-cloudwatch-logs-exports` | No | list(string) | -- | Log types: `audit`, `slowquery` |
| `--deletion-protection` | No | boolean | false | Enable deletion protection |
| `--serverless-v2-scaling-configuration` | No | structure | None | Serverless scaling. Shorthand: `MinCapacity=double,MaxCapacity=double` |
| `--global-cluster-identifier` | No | string | -- | Global cluster ID |
| `--storage-type` | No | string | `standard` | `standard` or `iopt1` |
| `--copy-tags-to-snapshot` | No | boolean | false | Copy tags to snapshots |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--port` | No | integer | 8182 | Port number |

**Output Schema:**
```json
{
    "DBCluster": {
        "DBClusterIdentifier": "string",
        "DBClusterArn": "string",
        "Status": "string",
        "Endpoint": "string",
        "ReaderEndpoint": "string",
        "Port": "integer",
        "Engine": "neptune",
        "EngineVersion": "string",
        "StorageEncrypted": "boolean",
        "KmsKeyId": "string",
        "DeletionProtection": "boolean",
        "BackupRetentionPeriod": "integer",
        "VpcSecurityGroups": [{"VpcSecurityGroupId": "string", "Status": "string"}],
        "DBClusterMembers": [],
        "ServerlessV2ScalingConfiguration": {"MinCapacity": "double", "MaxCapacity": "double"},
        "StorageType": "string",
        "GlobalClusterIdentifier": "string"
    }
}
```

---

### 1.2 `modify-db-cluster`

Modifies an existing Neptune DB cluster.

**Synopsis:**
```bash
aws neptune modify-db-cluster \
    --db-cluster-identifier <value> \
    [--new-db-cluster-identifier <value>] \
    [--apply-immediately | --no-apply-immediately] \
    [--backup-retention-period <value>] \
    [--db-cluster-parameter-group-name <value>] \
    [--vpc-security-group-ids <value>] \
    [--preferred-backup-window <value>] \
    [--preferred-maintenance-window <value>] \
    [--engine-version <value>] \
    [--allow-major-version-upgrade | --no-allow-major-version-upgrade] \
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
| `--db-cluster-identifier` | **Yes** | string | -- | Cluster identifier |
| `--new-db-cluster-identifier` | No | string | -- | New cluster identifier |
| `--apply-immediately` | No | boolean | false | Apply changes immediately |
| `--backup-retention-period` | No | integer | -- | Updated backup retention (1-35 days) |
| `--vpc-security-group-ids` | No | list(string) | -- | Updated security groups |
| `--engine-version` | No | string | -- | New engine version |
| `--deletion-protection` | No | boolean | -- | Toggle deletion protection |
| `--serverless-v2-scaling-configuration` | No | structure | -- | Updated serverless scaling |
| `--storage-type` | No | string | -- | Updated storage type |

**Output Schema:**
```json
{
    "DBCluster": {
        "DBClusterIdentifier": "string",
        "Status": "string",
        "Endpoint": "string",
        "EngineVersion": "string"
    }
}
```

---

### 1.3 `delete-db-cluster`

Deletes a Neptune DB cluster.

**Synopsis:**
```bash
aws neptune delete-db-cluster \
    --db-cluster-identifier <value> \
    [--skip-final-snapshot | --no-skip-final-snapshot] \
    [--final-db-snapshot-identifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-identifier` | **Yes** | string | -- | Cluster identifier |
| `--skip-final-snapshot` | No | boolean | false | Skip final snapshot on deletion |
| `--final-db-snapshot-identifier` | No | string | -- | Final snapshot identifier (required if not skipping) |

**Output Schema:**
```json
{
    "DBCluster": {
        "DBClusterIdentifier": "string",
        "Status": "deleting",
        "DBClusterArn": "string"
    }
}
```

---

### 1.4 `describe-db-clusters`

Describes one or more Neptune DB clusters. **Paginated operation.**

**Synopsis:**
```bash
aws neptune describe-db-clusters \
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
| `--db-cluster-identifier` | No | string | -- | Specific cluster to describe |
| `--filters` | No | list | None | Filters. Shorthand: `Name=string,Values=string,string ...` |

**Output Schema:**
```json
{
    "DBClusters": [
        {
            "DBClusterIdentifier": "string",
            "DBClusterArn": "string",
            "Status": "string",
            "Endpoint": "string",
            "ReaderEndpoint": "string",
            "Port": "integer",
            "Engine": "string",
            "EngineVersion": "string",
            "StorageEncrypted": "boolean",
            "DeletionProtection": "boolean",
            "BackupRetentionPeriod": "integer",
            "DBClusterMembers": [
                {
                    "DBInstanceIdentifier": "string",
                    "IsClusterWriter": "boolean",
                    "DBClusterParameterGroupStatus": "string"
                }
            ],
            "VpcSecurityGroups": [],
            "ServerlessV2ScalingConfiguration": {},
            "StorageType": "string"
        }
    ]
}
```

---

### 1.5 `start-db-cluster`

Starts a stopped Neptune DB cluster.

**Synopsis:**
```bash
aws neptune start-db-cluster \
    --db-cluster-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-identifier` | **Yes** | string | -- | Cluster identifier |

**Output Schema:**
```json
{
    "DBCluster": {
        "DBClusterIdentifier": "string",
        "Status": "starting"
    }
}
```

---

### 1.6 `stop-db-cluster`

Stops a running Neptune DB cluster. The cluster can be stopped for up to 7 days.

**Synopsis:**
```bash
aws neptune stop-db-cluster \
    --db-cluster-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-identifier` | **Yes** | string | -- | Cluster identifier |

**Output Schema:**
```json
{
    "DBCluster": {
        "DBClusterIdentifier": "string",
        "Status": "stopping"
    }
}
```

---

### 1.7 `failover-db-cluster`

Forces a failover for a Neptune DB cluster. Promotes a read replica to the primary instance.

**Synopsis:**
```bash
aws neptune failover-db-cluster \
    [--db-cluster-identifier <value>] \
    [--target-db-instance-identifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-identifier` | No | string | -- | Cluster identifier |
| `--target-db-instance-identifier` | No | string | -- | Target instance to promote |

**Output Schema:**
```json
{
    "DBCluster": {
        "DBClusterIdentifier": "string",
        "Status": "failing-over"
    }
}
```

---

### 1.8 `promote-read-replica-db-cluster`

Promotes a read replica DB cluster to a standalone cluster.

**Synopsis:**
```bash
aws neptune promote-read-replica-db-cluster \
    --db-cluster-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-identifier` | **Yes** | string | -- | Read replica cluster identifier |

**Output Schema:**
```json
{
    "DBCluster": {
        "DBClusterIdentifier": "string",
        "Status": "string"
    }
}
```

---

### 1.9 `add-role-to-db-cluster`

Associates an IAM role with a Neptune DB cluster for accessing other AWS services.

**Synopsis:**
```bash
aws neptune add-role-to-db-cluster \
    --db-cluster-identifier <value> \
    --role-arn <value> \
    [--feature-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-identifier` | **Yes** | string | -- | Cluster identifier |
| `--role-arn` | **Yes** | string | -- | IAM role ARN |
| `--feature-name` | No | string | -- | Feature name (e.g., `s3Export`) |

**Output:** None

---

### 1.10 `remove-role-from-db-cluster`

Removes an IAM role from a Neptune DB cluster.

**Synopsis:**
```bash
aws neptune remove-role-from-db-cluster \
    --db-cluster-identifier <value> \
    --role-arn <value> \
    [--feature-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-identifier` | **Yes** | string | -- | Cluster identifier |
| `--role-arn` | **Yes** | string | -- | IAM role ARN to remove |
| `--feature-name` | No | string | -- | Feature name |

**Output:** None
