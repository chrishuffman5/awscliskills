# Continuous Backups / PITR

### 9.1 `describe-continuous-backups`

Describes the continuous backups and point-in-time recovery (PITR) status for a table.

**Synopsis:**
```bash
aws dynamodb describe-continuous-backups \
    --table-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-name` | **Yes** | string | -- | Table name or ARN (1-1024 chars) |

**Output Schema:**
```json
{
    "ContinuousBackupsDescription": {
        "ContinuousBackupsStatus": "ENABLED|DISABLED",
        "PointInTimeRecoveryDescription": {
            "PointInTimeRecoveryStatus": "ENABLED|DISABLED",
            "EarliestRestorableDateTime": "timestamp",
            "LatestRestorableDateTime": "timestamp"
        }
    }
}
```

---

### 9.2 `update-continuous-backups`

Enables or disables point-in-time recovery for a table.

**Synopsis:**
```bash
aws dynamodb update-continuous-backups \
    --table-name <value> \
    --point-in-time-recovery-specification <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-name` | **Yes** | string | -- | Table name or ARN (1-1024 chars) |
| `--point-in-time-recovery-specification` | **Yes** | structure | -- | Shorthand: `PointInTimeRecoveryEnabled=true\|false` |

**Output Schema:** Same as `describe-continuous-backups`.

---

### 9.3 `restore-table-to-point-in-time`

Restores a table to a specific point in time within the backup window (up to 35 days).

**Synopsis:**
```bash
aws dynamodb restore-table-to-point-in-time \
    --target-table-name <value> \
    [--source-table-name <value>] \
    [--source-table-arn <value>] \
    [--restore-date-time <value>] \
    [--use-latest-restorable-time | --no-use-latest-restorable-time] \
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
| `--source-table-name` | No | string | -- | Source table name (provide this or `--source-table-arn`) |
| `--source-table-arn` | No | string | -- | Source table ARN |
| `--restore-date-time` | No | timestamp | -- | Point in time to restore to (within PITR window) |
| `--use-latest-restorable-time` | No | boolean | false | Restore to the latest restorable time |
| `--billing-mode-override` | No | string | -- | `PROVISIONED` or `PAY_PER_REQUEST` |
| `--global-secondary-index-override` | No | list | -- | Override GSI list |
| `--local-secondary-index-override` | No | list | -- | Override LSI list |
| `--provisioned-throughput-override` | No | structure | -- | Override throughput |
| `--on-demand-throughput-override` | No | structure | -- | Override on-demand throughput |
| `--sse-specification-override` | No | structure | -- | Override encryption |

**Output Schema:**
```json
{
    "TableDescription": {
        "TableName": "string",
        "TableStatus": "CREATING",
        "RestoreSummary": {
            "SourceTableArn": "string",
            "RestoreDateTime": "timestamp",
            "RestoreInProgress": "boolean"
        }
    }
}
```

---
