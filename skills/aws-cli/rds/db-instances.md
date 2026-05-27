# DB Instances

### 1.1 `create-db-instance`

Creates a new DB instance.

**Synopsis:**
```bash
aws rds create-db-instance \
    --db-instance-identifier <value> \
    --db-instance-class <value> \
    --engine <value> \
    [--master-username <value>] \
    [--master-user-password <value>] \
    [--allocated-storage <value>] \
    [--db-name <value>] \
    [--engine-version <value>] \
    [--storage-type <value>] \
    [--vpc-security-group-ids <value>] \
    [--db-subnet-group-name <value>] \
    [--multi-az | --no-multi-az] \
    [--tags <value>]
```

**Required Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--db-instance-identifier` | string | Unique identifier (1-63 chars, lowercase letters/numbers/hyphens) |
| `--db-instance-class` | string | Instance class (e.g. `db.t3.medium`, `db.m5.large`) |
| `--engine` | string | Engine: `mysql`, `postgres`, `mariadb`, `oracle-ee`, `sqlserver-ee`, `aurora-mysql`, `aurora-postgresql` |

**Key Optional Parameters:**

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `--master-username` | string | -- | Master username (1-16 chars, must start with letter) |
| `--master-user-password` | string | -- | Master password (8-41 chars depending on engine) |
| `--allocated-storage` | integer | varies | Storage in GiB (MySQL: 20-65536, PostgreSQL: 20-65536) |
| `--db-name` | string | None | Initial database name |
| `--engine-version` | string | latest | Engine version number |
| `--port` | integer | engine default | Port (MySQL 3306, PostgreSQL 5432, Oracle 1521, SQL Server 1433) |
| `--storage-type` | string | `gp3` | `gp2`, `gp3`, `io1`, `io2`, `standard` |
| `--iops` | integer | None | Provisioned IOPS (for io1/io2/gp3) |
| `--storage-throughput` | integer | None | Throughput in MiBps (gp3 only) |
| `--storage-encrypted` / `--no-storage-encrypted` | boolean | false | Enable encryption at rest |
| `--kms-key-id` | string | default key | KMS key for encryption |
| `--vpc-security-group-ids` | list | default VPC SG | VPC security group IDs |
| `--db-subnet-group-name` | string | default | DB subnet group for VPC placement |
| `--availability-zone` | string | random | Specific AZ |
| `--multi-az` / `--no-multi-az` | boolean | false | Multi-AZ deployment |
| `--publicly-accessible` / `--no-publicly-accessible` | boolean | false | Public accessibility |
| `--db-parameter-group-name` | string | default | Parameter group name |
| `--option-group-name` | string | default | Option group name |
| `--backup-retention-period` | integer | 1 | Days to retain backups (0-35) |
| `--preferred-backup-window` | string | auto | Daily backup window `hh24:mi-hh24:mi` UTC |
| `--preferred-maintenance-window` | string | auto | Weekly maintenance `ddd:hh24:mi-ddd:hh24:mi` UTC |
| `--monitoring-interval` | integer | 0 | Enhanced monitoring interval (0,1,5,10,15,30,60 sec) |
| `--monitoring-role-arn` | string | None | IAM role for enhanced monitoring |
| `--enable-performance-insights` / `--no-enable-performance-insights` | boolean | false | Enable Performance Insights |
| `--enable-cloudwatch-logs-exports` | list | None | Log types to export |
| `--enable-iam-database-authentication` / `--no-enable-iam-database-authentication` | boolean | false | IAM auth |
| `--deletion-protection` / `--no-deletion-protection` | boolean | false | Deletion protection |
| `--max-allocated-storage` | integer | None | Max GiB for storage autoscaling |
| `--copy-tags-to-snapshot` / `--no-copy-tags-to-snapshot` | boolean | false | Copy tags to snapshots |
| `--manage-master-user-password` / `--no-manage-master-user-password` | boolean | false | Manage password via Secrets Manager |
| `--tags` | list | None | `Key=string,Value=string ...` |
| `--db-cluster-identifier` | string | None | Aurora cluster identifier (for Aurora instances) |

**Output Schema:**
```json
{
    "DBInstance": {
        "DBInstanceIdentifier": "string",
        "DBInstanceClass": "string",
        "Engine": "string",
        "DBInstanceStatus": "string",
        "MasterUsername": "string",
        "DBName": "string",
        "Endpoint": {
            "Address": "string",
            "Port": "integer",
            "HostedZoneId": "string"
        },
        "AllocatedStorage": "integer",
        "InstanceCreateTime": "timestamp",
        "PreferredBackupWindow": "string",
        "BackupRetentionPeriod": "integer",
        "VpcSecurityGroups": [
            { "VpcSecurityGroupId": "string", "Status": "string" }
        ],
        "DBParameterGroups": [
            { "DBParameterGroupName": "string", "ParameterApplyStatus": "string" }
        ],
        "DBSubnetGroup": {
            "DBSubnetGroupName": "string",
            "VpcId": "string",
            "SubnetGroupStatus": "string",
            "Subnets": [
                { "SubnetIdentifier": "string", "SubnetAvailabilityZone": { "Name": "string" }, "SubnetStatus": "string" }
            ]
        },
        "PreferredMaintenanceWindow": "string",
        "MultiAZ": "boolean",
        "EngineVersion": "string",
        "AutoMinorVersionUpgrade": "boolean",
        "PubliclyAccessible": "boolean",
        "StorageType": "string",
        "StorageEncrypted": "boolean",
        "KmsKeyId": "string",
        "DbiResourceId": "string",
        "DBInstanceArn": "string",
        "IAMDatabaseAuthenticationEnabled": "boolean",
        "PerformanceInsightsEnabled": "boolean",
        "DeletionProtection": "boolean",
        "MaxAllocatedStorage": "integer",
        "TagList": [{ "Key": "string", "Value": "string" }]
    }
}
```

---

### 1.2 `delete-db-instance`

Deletes a DB instance. Optionally creates a final snapshot.

**Synopsis:**
```bash
aws rds delete-db-instance \
    --db-instance-identifier <value> \
    [--skip-final-snapshot | --no-skip-final-snapshot] \
    [--final-db-snapshot-identifier <value>] \
    [--delete-automated-backups | --no-delete-automated-backups]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-instance-identifier` | **Yes** | string | -- | DB instance identifier |
| `--skip-final-snapshot` / `--no-skip-final-snapshot` | No | boolean | false | Skip final snapshot |
| `--final-db-snapshot-identifier` | No | string | None | Name for the final snapshot (required if not skipping) |
| `--delete-automated-backups` / `--no-delete-automated-backups` | No | boolean | true | Delete automated backups |

**Output Schema:** Same `DBInstance` structure as `create-db-instance`.

---

### 1.3 `describe-db-instances`

Describes provisioned RDS instances. **Paginated.**

**Synopsis:**
```bash
aws rds describe-db-instances \
    [--db-instance-identifier <value>] \
    [--filters <value>] \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-instance-identifier` | No | string | all | Specific instance identifier or ARN |
| `--filters` | No | list | None | Filters: `db-cluster-id`, `db-instance-id`, `dbi-resource-id`, `domain`, `engine`. Syntax: `Name=string,Values=string,string` |
| `--max-items` | No | integer | None | Total items to return |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |

**Output Schema:**
```json
{
    "DBInstances": [
        {
            "DBInstanceIdentifier": "string",
            "DBInstanceClass": "string",
            "Engine": "string",
            "DBInstanceStatus": "string",
            "Endpoint": { "Address": "string", "Port": "integer", "HostedZoneId": "string" },
            "AllocatedStorage": "integer",
            "MultiAZ": "boolean",
            "EngineVersion": "string",
            "StorageType": "string",
            "StorageEncrypted": "boolean",
            "DBInstanceArn": "string",
            "ReadReplicaSourceDBInstanceIdentifier": "string",
            "ReadReplicaDBInstanceIdentifiers": ["string"],
            "DeletionProtection": "boolean",
            "TagList": [{ "Key": "string", "Value": "string" }]
        }
    ],
    "Marker": "string"
}
```

---

### 1.4 `modify-db-instance`

Modifies settings for a DB instance. Changes apply during the next maintenance window unless `--apply-immediately` is specified.

**Synopsis:**
```bash
aws rds modify-db-instance \
    --db-instance-identifier <value> \
    [--db-instance-class <value>] \
    [--allocated-storage <value>] \
    [--apply-immediately | --no-apply-immediately] \
    [--master-user-password <value>] \
    [--multi-az | --no-multi-az] \
    [--engine-version <value>]
```

**Required Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--db-instance-identifier` | string | DB instance identifier |

**Key Optional Parameters:**

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `--db-instance-class` | string | no change | New instance class |
| `--allocated-storage` | integer | no change | New storage in GiB (must be >= 10% increase) |
| `--apply-immediately` / `--no-apply-immediately` | boolean | false | Apply now vs. next maintenance window |
| `--master-user-password` | string | no change | New master password |
| `--backup-retention-period` | integer | no change | Days (0-35) |
| `--preferred-backup-window` | string | no change | Daily backup window |
| `--preferred-maintenance-window` | string | no change | Weekly maintenance window |
| `--multi-az` / `--no-multi-az` | boolean | no change | Multi-AZ deployment |
| `--engine-version` | string | no change | Engine version to upgrade to |
| `--storage-type` | string | no change | `gp2`, `gp3`, `io1`, `io2`, `standard` |
| `--iops` | integer | no change | Provisioned IOPS |
| `--new-db-instance-identifier` | string | no change | Rename the instance |
| `--db-parameter-group-name` | string | no change | Parameter group |
| `--deletion-protection` / `--no-deletion-protection` | boolean | no change | Deletion protection |
| `--max-allocated-storage` | integer | no change | Storage autoscaling upper limit |
| `--vpc-security-group-ids` | list | no change | Security group IDs |
| `--monitoring-interval` | integer | no change | Enhanced monitoring interval |
| `--enable-iam-database-authentication` / `--no-enable-iam-database-authentication` | boolean | no change | IAM auth |
| `--enable-performance-insights` / `--no-enable-performance-insights` | boolean | no change | Performance Insights |
| `--enable-cloudwatch-logs-exports` | list | no change | CloudWatch log exports |
| `--copy-tags-to-snapshot` / `--no-copy-tags-to-snapshot` | boolean | no change | Copy tags |

**Output Schema:** Same `DBInstance` structure as `create-db-instance`.

---

### 1.5 `reboot-db-instance`

Reboots a DB instance. Optionally forces a failover for Multi-AZ instances.

**Synopsis:**
```bash
aws rds reboot-db-instance \
    --db-instance-identifier <value> \
    [--force-failover | --no-force-failover]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-instance-identifier` | **Yes** | string | -- | DB instance identifier |
| `--force-failover` / `--no-force-failover` | No | boolean | false | Force Multi-AZ failover |

**Output Schema:** Same `DBInstance` structure.

---

### 1.6 `start-db-instance`

Starts a DB instance that was previously stopped.

**Synopsis:**
```bash
aws rds start-db-instance \
    --db-instance-identifier <value>
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--db-instance-identifier` | **Yes** | string | DB instance identifier |

**Output Schema:** Same `DBInstance` structure.

---

### 1.7 `stop-db-instance`

Stops a running DB instance. Can be stopped for up to 7 days before auto-restart.

**Synopsis:**
```bash
aws rds stop-db-instance \
    --db-instance-identifier <value> \
    [--db-snapshot-identifier <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-instance-identifier` | **Yes** | string | -- | DB instance identifier |
| `--db-snapshot-identifier` | No | string | None | Create a snapshot before stopping |

**Output Schema:** Same `DBInstance` structure.

---

### 1.8 `create-db-instance-read-replica`

Creates a read replica of an existing DB instance.

**Synopsis:**
```bash
aws rds create-db-instance-read-replica \
    --db-instance-identifier <value> \
    [--source-db-instance-identifier <value>] \
    [--db-instance-class <value>] \
    [--availability-zone <value>] \
    [--storage-type <value>] \
    [--vpc-security-group-ids <value>] \
    [--db-subnet-group-name <value>] \
    [--tags <value>]
```

**Required Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--db-instance-identifier` | string | Identifier for the read replica |

**Key Optional Parameters:**

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `--source-db-instance-identifier` | string | -- | Source DB instance identifier or ARN |
| `--source-db-cluster-identifier` | string | -- | Source Multi-AZ DB cluster identifier |
| `--db-instance-class` | string | same as source | Instance class for the replica |
| `--availability-zone` | string | random | AZ for the replica |
| `--port` | integer | same as source | Port number (1150-65535) |
| `--multi-az` / `--no-multi-az` | boolean | false | Multi-AZ for the replica |
| `--storage-type` | string | same as source | `gp2`, `gp3`, `io1`, `io2`, `standard` |
| `--iops` | integer | same as source | Provisioned IOPS |
| `--allocated-storage` | integer | same as source | Storage in GiB |
| `--publicly-accessible` / `--no-publicly-accessible` | boolean | same as source | Public accessibility |
| `--kms-key-id` | string | same as source | KMS key (required for cross-region encrypted replicas) |
| `--db-subnet-group-name` | string | same as source | Subnet group |
| `--vpc-security-group-ids` | list | same as source | Security groups |
| `--enable-iam-database-authentication` / `--no-enable-iam-database-authentication` | boolean | false | IAM auth |
| `--enable-performance-insights` / `--no-enable-performance-insights` | boolean | false | Performance Insights |
| `--deletion-protection` / `--no-deletion-protection` | boolean | false | Deletion protection |
| `--tags` | list | None | Tags |

> **Limits:** Up to 15 replicas per source (3 for Db2, 5 for Oracle/SQL Server). Source must have backup retention enabled.

**Output Schema:** Same `DBInstance` structure.

---

### 1.9 `promote-read-replica`

Promotes a read replica to a standalone DB instance.

**Synopsis:**
```bash
aws rds promote-read-replica \
    --db-instance-identifier <value> \
    [--backup-retention-period <value>] \
    [--preferred-backup-window <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-instance-identifier` | **Yes** | string | -- | Read replica identifier |
| `--backup-retention-period` | No | integer | 1 | Backup retention days (0-35) |
| `--preferred-backup-window` | No | string | auto | Backup window `hh24:mi-hh24:mi` UTC |

**Output Schema:** Same `DBInstance` structure.

---
