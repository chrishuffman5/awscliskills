# Automated Backups

### 8.1 `describe-db-instance-automated-backups`

Describes automated backups. **Paginated.**

```bash
aws rds describe-db-instance-automated-backups \
    [--dbi-resource-id <value>] \
    [--db-instance-identifier <value>] \
    [--filters <value>] \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--db-instance-automated-backups-arn <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dbi-resource-id` | No | string | all | DBI resource ID filter |
| `--db-instance-identifier` | No | string | all | Instance identifier filter |
| `--db-instance-automated-backups-arn` | No | string | all | Automated backup ARN |
| `--filters` | No | list | None | Filters: `db-instance-id`, `dbi-resource-id`, `db-instance-automated-backups-arn`, `status` |

**Output Schema:**
```json
{
    "DBInstanceAutomatedBackups": [
        {
            "DBInstanceArn": "string",
            "DbiResourceId": "string",
            "Region": "string",
            "DBInstanceIdentifier": "string",
            "RestoreWindow": {
                "EarliestTime": "timestamp",
                "LatestTime": "timestamp"
            },
            "AllocatedStorage": "integer",
            "Status": "string",
            "Port": "integer",
            "AvailabilityZone": "string",
            "VpcId": "string",
            "InstanceCreateTime": "timestamp",
            "MasterUsername": "string",
            "Engine": "string",
            "EngineVersion": "string",
            "LicenseModel": "string",
            "Iops": "integer",
            "OptionGroupName": "string",
            "TdeCredentialArn": "string",
            "Encrypted": "boolean",
            "StorageType": "string",
            "KmsKeyId": "string",
            "Timezone": "string",
            "IAMDatabaseAuthenticationEnabled": "boolean",
            "BackupRetentionPeriod": "integer",
            "DBInstanceAutomatedBackupsArn": "string",
            "DBInstanceAutomatedBackupsReplications": [
                { "DBInstanceAutomatedBackupsArn": "string" }
            ],
            "BackupTarget": "string",
            "DedicatedLogVolume": "boolean"
        }
    ],
    "Marker": "string"
}
```

---

### 8.2 `delete-db-instance-automated-backup`

Deletes an automated backup.

```bash
aws rds delete-db-instance-automated-backup \
    [--dbi-resource-id <value>] \
    [--db-instance-automated-backups-arn <value>]
```

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--dbi-resource-id` | No | string | DBI resource ID (for local backups) |
| `--db-instance-automated-backups-arn` | No | string | Automated backup ARN (for cross-region) |

> One of `--dbi-resource-id` or `--db-instance-automated-backups-arn` is required.

**Output Schema:** Same `DBInstanceAutomatedBackup` structure (single item).

---

### 8.3 `start-db-instance-automated-backups-replication`

Starts cross-region replication of automated backups.

```bash
aws rds start-db-instance-automated-backups-replication \
    --source-db-instance-arn <value> \
    [--backup-retention-period <value>] \
    [--kms-key-id <value>] \
    [--source-region <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-db-instance-arn` | **Yes** | string | -- | Source DB instance ARN |
| `--backup-retention-period` | No | integer | 7 | Days to retain replicated backups |
| `--kms-key-id` | No | string | default | KMS key for encryption |
| `--source-region` | No | string | None | Source region |

**Output Schema:** Same `DBInstanceAutomatedBackup` structure.

---

### 8.4 `stop-db-instance-automated-backups-replication`

Stops cross-region replication of automated backups.

```bash
aws rds stop-db-instance-automated-backups-replication \
    --source-db-instance-arn <value>
```

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--source-db-instance-arn` | **Yes** | string | Source DB instance ARN |

**Output Schema:** Same `DBInstanceAutomatedBackup` structure.

---
