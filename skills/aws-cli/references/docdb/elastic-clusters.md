# Elastic Clusters (`aws docdb-elastic`)

### 8.1 `create-cluster`

Creates a new DocumentDB elastic cluster.

**Synopsis:**
```bash
aws docdb-elastic create-cluster \
    --cluster-name <value> \
    --auth-type <value> \
    --admin-user-name <value> \
    --admin-user-password <value> \
    --shard-capacity <value> \
    --shard-count <value> \
    [--shard-instance-count <value>] \
    [--vpc-security-group-ids <value>] \
    [--subnet-ids <value>] \
    [--kms-key-id <value>] \
    [--preferred-maintenance-window <value>] \
    [--tags <value>] \
    [--backup-retention-period <value>] \
    [--preferred-backup-window <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name (1-63 chars: letters, numbers, hyphens) |
| `--auth-type` | **Yes** | string | -- | Authentication type: `PLAIN_TEXT` or `SECRET_ARN` |
| `--admin-user-name` | **Yes** | string | -- | Admin user name |
| `--admin-user-password` | **Yes** | string | -- | Admin user password (or Secrets Manager ARN) |
| `--shard-capacity` | **Yes** | integer | -- | vCPU capacity per shard (2, 4, 8, 16, 32, 64) |
| `--shard-count` | **Yes** | integer | -- | Number of shards (1-32) |
| `--shard-instance-count` | No | integer | 1 | Number of replica instances per shard |
| `--vpc-security-group-ids` | No | list(string) | Default | VPC security group IDs |
| `--subnet-ids` | No | list(string) | Default | Subnet IDs |
| `--kms-key-id` | No | string | AWS managed | KMS key ID for encryption |
| `--preferred-maintenance-window` | No | string | Auto | Weekly maintenance window |
| `--tags` | No | map | None | Tags. Shorthand: `KeyName1=string,KeyName2=string` |
| `--backup-retention-period` | No | integer | 1 | Backup retention period in days (1-35) |
| `--preferred-backup-window` | No | string | Auto | Daily backup window |

**Output Schema:**
```json
{
    "cluster": {
        "clusterName": "string",
        "clusterArn": "string",
        "status": "CREATING|ACTIVE|DELETING|UPDATING|VPC_ENDPOINT_LIMIT_EXCEEDED|IP_ADDRESS_LIMIT_EXCEEDED|INVALID_SECURITY_GROUP_ID|INVALID_SUBNET_ID|INACCESSIBLE_ENCRYPTION_CREDS|INACCESSIBLE_SECRET_ARN|INACCESSIBLE_VPC_ENDPOINT|INCOMPATIBLE_NETWORK|MERGING|MODIFYING|SPLITTING|COPYING|STARTING|STOPPING|STOPPED",
        "clusterEndpoint": "string",
        "createTime": "string",
        "adminUserName": "string",
        "authType": "PLAIN_TEXT|SECRET_ARN",
        "shardCapacity": "integer",
        "shardCount": "integer",
        "shardInstanceCount": "integer",
        "vpcSecurityGroupIds": ["string"],
        "subnetIds": ["string"],
        "kmsKeyId": "string",
        "preferredMaintenanceWindow": "string",
        "preferredBackupWindow": "string",
        "backupRetentionPeriod": "integer",
        "shards": [
            {
                "shardId": "string",
                "createTime": "string",
                "status": "string"
            }
        ]
    }
}
```

---

### 8.2 `delete-cluster`

Deletes an elastic cluster.

**Synopsis:**
```bash
aws docdb-elastic delete-cluster \
    --cluster-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the elastic cluster to delete |

**Output Schema:** Same as `create-cluster` output.

---

### 8.3 `get-cluster`

Returns information about a specific elastic cluster.

**Synopsis:**
```bash
aws docdb-elastic get-cluster \
    --cluster-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the elastic cluster |

**Output Schema:** Same as `create-cluster` output.

---

### 8.4 `list-clusters`

Returns information about provisioned elastic clusters. **Paginated operation.**

**Synopsis:**
```bash
aws docdb-elastic list-clusters \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Maximum results per page (1-100) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "clusters": [
        {
            "clusterName": "string",
            "clusterArn": "string",
            "status": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 8.5 `update-cluster`

Modifies an elastic cluster. This includes scaling shards, changing capacity, modifying security groups, and more.

**Synopsis:**
```bash
aws docdb-elastic update-cluster \
    --cluster-arn <value> \
    [--auth-type <value>] \
    [--admin-user-password <value>] \
    [--shard-capacity <value>] \
    [--shard-count <value>] \
    [--shard-instance-count <value>] \
    [--vpc-security-group-ids <value>] \
    [--subnet-ids <value>] \
    [--preferred-maintenance-window <value>] \
    [--backup-retention-period <value>] \
    [--preferred-backup-window <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the elastic cluster |
| `--auth-type` | No | string | -- | New authentication type |
| `--admin-user-password` | No | string | -- | New admin password |
| `--shard-capacity` | No | integer | -- | New shard capacity |
| `--shard-count` | No | integer | -- | New shard count |
| `--shard-instance-count` | No | integer | -- | New replica count per shard |
| `--vpc-security-group-ids` | No | list(string) | -- | New security group IDs |
| `--subnet-ids` | No | list(string) | -- | New subnet IDs |
| `--preferred-maintenance-window` | No | string | -- | New maintenance window |
| `--backup-retention-period` | No | integer | -- | New backup retention period |
| `--preferred-backup-window` | No | string | -- | New backup window |

**Output Schema:** Same as `create-cluster` output.

---

### 8.6 `start-cluster`

Starts a stopped elastic cluster.

**Synopsis:**
```bash
aws docdb-elastic start-cluster \
    --cluster-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the elastic cluster to start |

**Output Schema:** Same as `create-cluster` output.

---

### 8.7 `stop-cluster`

Stops a running elastic cluster.

**Synopsis:**
```bash
aws docdb-elastic stop-cluster \
    --cluster-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the elastic cluster to stop |

**Output Schema:** Same as `create-cluster` output.

---

### 8.8 `restore-cluster-from-snapshot`

Restores an elastic cluster from a snapshot.

**Synopsis:**
```bash
aws docdb-elastic restore-cluster-from-snapshot \
    --cluster-name <value> \
    --snapshot-arn <value> \
    [--vpc-security-group-ids <value>] \
    [--subnet-ids <value>] \
    [--kms-key-id <value>] \
    [--tags <value>] \
    [--shard-capacity <value>] \
    [--shard-instance-count <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | New cluster name |
| `--snapshot-arn` | **Yes** | string | -- | ARN of the snapshot to restore from |
| `--vpc-security-group-ids` | No | list(string) | -- | VPC security group IDs |
| `--subnet-ids` | No | list(string) | -- | Subnet IDs |
| `--kms-key-id` | No | string | -- | KMS key for encryption |
| `--tags` | No | map | None | Tags |
| `--shard-capacity` | No | integer | -- | Override shard capacity |
| `--shard-instance-count` | No | integer | -- | Override shard instance count |

**Output Schema:** Same as `create-cluster` output.
