# Backups

### 8.1 `create-backup`

Creates an on-demand backup of a DynamoDB table.

**Synopsis:**
```bash
aws dynamodb create-backup \
    --table-name <value> \
    --backup-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-name` | **Yes** | string | -- | Table name or ARN (1-1024 chars) |
| `--backup-name` | **Yes** | string | -- | Backup name (3-255 chars). Pattern: `[a-zA-Z0-9_.-]+` |

**Output Schema:**
```json
{
    "BackupDetails": {
        "BackupArn": "string",
        "BackupName": "string",
        "BackupSizeBytes": "long",
        "BackupStatus": "CREATING|DELETED|AVAILABLE",
        "BackupType": "USER|SYSTEM|AWS_BACKUP",
        "BackupCreationDateTime": "timestamp",
        "BackupExpiryDateTime": "timestamp"
    }
}
```

---

### 8.2 `delete-backup`

Deletes an existing backup.

**Synopsis:**
```bash
aws dynamodb delete-backup \
    --backup-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-arn` | **Yes** | string | -- | ARN of the backup to delete (37-1024 chars) |

**Output Schema:**
```json
{
    "BackupDescription": {
        "BackupDetails": {
            "BackupArn": "string",
            "BackupName": "string",
            "BackupSizeBytes": "long",
            "BackupStatus": "DELETED",
            "BackupType": "USER|SYSTEM|AWS_BACKUP",
            "BackupCreationDateTime": "timestamp"
        },
        "SourceTableDetails": {
            "TableName": "string",
            "TableId": "string",
            "TableArn": "string",
            "TableSizeBytes": "long",
            "KeySchema": [],
            "TableCreationDateTime": "timestamp",
            "ProvisionedThroughput": {},
            "OnDemandThroughput": {},
            "ItemCount": "long",
            "BillingMode": "PROVISIONED|PAY_PER_REQUEST"
        },
        "SourceTableFeatureDetails": {
            "LocalSecondaryIndexes": [],
            "GlobalSecondaryIndexes": [],
            "StreamDescription": {},
            "TimeToLiveDescription": {},
            "SSEDescription": {}
        }
    }
}
```

---

### 8.3 `describe-backup`

Describes an existing backup with full details about the backup and source table.

**Synopsis:**
```bash
aws dynamodb describe-backup \
    --backup-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-arn` | **Yes** | string | -- | ARN of the backup (37-1024 chars) |

**Output Schema:** Same as `delete-backup` `BackupDescription` object.

---

### 8.4 `list-backups`

Lists existing backups, optionally filtered by table name, type, or time range. **Paginated operation.**

**Synopsis:**
```bash
aws dynamodb list-backups \
    [--table-name <value>] \
    [--time-range-lower-bound <value>] \
    [--time-range-upper-bound <value>] \
    [--backup-type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-name` | No | string | -- | Filter by table name (1-1024 chars) |
| `--time-range-lower-bound` | No | timestamp | -- | Earliest backup creation time (inclusive) |
| `--time-range-upper-bound` | No | timestamp | -- | Latest backup creation time (exclusive) |
| `--backup-type` | No | string | -- | `USER`, `SYSTEM`, `AWS_BACKUP`, or `ALL` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call (1-100) |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "BackupSummaries": [
        {
            "TableName": "string",
            "TableId": "string",
            "TableArn": "string",
            "BackupArn": "string",
            "BackupName": "string",
            "BackupCreationDateTime": "timestamp",
            "BackupExpiryDateTime": "timestamp",
            "BackupStatus": "CREATING|DELETED|AVAILABLE",
            "BackupType": "USER|SYSTEM|AWS_BACKUP",
            "BackupSizeBytes": "long"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.5 `restore-table-from-backup`

Creates a new table from an existing backup. Does not restore auto-scaling policies, tags, or IAM policies.

**Synopsis:**
```bash
aws dynamodb restore-table-from-backup \
    --target-table-name <value> \
    --backup-arn <value> \
    [--billing-mode-override <value>] \
    [--global-secondary-index-override <value>] \
    [--local-secondary-index-override <value>] \
    [--provisioned-throughput-override <value>] \
    [--on-demand-throughput-override <value>] \
    [--sse-specification-override <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-table-name` | **Yes** | string | -- | Name for the restored table (1-255 chars) |
| `--backup-arn` | **Yes** | string | -- | ARN of the backup to restore from (37-1024 chars) |
| `--billing-mode-override` | No | string | -- | Override billing mode: `PROVISIONED` or `PAY_PER_REQUEST` |
| `--global-secondary-index-override` | No | list | -- | Override GSI list for restored table |
| `--local-secondary-index-override` | No | list | -- | Override LSI list for restored table |
| `--provisioned-throughput-override` | No | structure | -- | Override throughput settings |
| `--on-demand-throughput-override` | No | structure | -- | Override on-demand throughput |
| `--sse-specification-override` | No | structure | -- | Override encryption settings |

**Output Schema:**
```json
{
    "TableDescription": {
        "TableName": "string",
        "TableStatus": "CREATING",
        "TableArn": "string",
        "RestoreSummary": {
            "SourceBackupArn": "string",
            "SourceTableArn": "string",
            "RestoreDateTime": "timestamp",
            "RestoreInProgress": "boolean"
        }
    }
}
```

---
