# Backups

### 3.1 `describe-backups`

Returns information about CloudHSM backups. **Paginated operation.**

**Synopsis:**
```bash
aws cloudhsmv2 describe-backups \
    [--filters <value>] \
    [--shared | --no-shared] \
    [--sort-ascending | --no-sort-ascending] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | map | None | Filter by `backupIds`, `sourceBackupIds`, `clusterIds`, `states`, `neverExpires` (max 30) |
| `--shared \| --no-shared` | No | boolean | false | Include backups shared with you |
| `--sort-ascending \| --no-sort-ascending` | No | boolean | false | Sort by ascending chronological order |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Backups": [
        {
            "BackupId": "string",
            "BackupArn": "string",
            "BackupState": "CREATE_IN_PROGRESS|READY|DELETED|PENDING_DELETION",
            "ClusterId": "string",
            "CreateTimestamp": "timestamp",
            "CopyTimestamp": "timestamp",
            "NeverExpires": true|false,
            "SourceRegion": "string",
            "SourceBackup": "string",
            "SourceCluster": "string",
            "DeleteTimestamp": "timestamp",
            "TagList": [
                {
                    "Key": "string",
                    "Value": "string"
                }
            ],
            "HsmType": "string",
            "Mode": "FIPS|NON_FIPS"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.2 `delete-backup`

Deletes the specified CloudHSM backup. A backup can be restored with `restore-backup` after deletion until permanently removed.

**Synopsis:**
```bash
aws cloudhsmv2 delete-backup \
    --backup-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-id` | **Yes** | string | -- | ID of the backup to delete |

**Output Schema:**
```json
{
    "Backup": {
        "BackupId": "string",
        "BackupArn": "string",
        "BackupState": "PENDING_DELETION",
        "ClusterId": "string",
        "CreateTimestamp": "timestamp",
        "DeleteTimestamp": "timestamp"
    }
}
```

---

### 3.3 `copy-backup-to-region`

Copies a CloudHSM cluster backup to a different AWS region for disaster recovery.

**Synopsis:**
```bash
aws cloudhsmv2 copy-backup-to-region \
    --destination-region <value> \
    --backup-id <value> \
    [--tag-list <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--destination-region` | **Yes** | string | -- | Target AWS region |
| `--backup-id` | **Yes** | string | -- | ID of the backup to copy |
| `--tag-list` | No | list | None | Tags for the new backup copy |

**Output Schema:**
```json
{
    "DestinationBackup": {
        "CreateTimestamp": "timestamp",
        "SourceRegion": "string",
        "SourceBackup": "string",
        "SourceCluster": "string"
    }
}
```

---

### 3.4 `restore-backup`

Restores a backup that is in `PENDING_DELETION` state back to `READY` state.

**Synopsis:**
```bash
aws cloudhsmv2 restore-backup \
    --backup-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-id` | **Yes** | string | -- | ID of the backup to restore |

**Output Schema:**
```json
{
    "Backup": {
        "BackupId": "string",
        "BackupArn": "string",
        "BackupState": "READY",
        "ClusterId": "string",
        "CreateTimestamp": "timestamp"
    }
}
```

---

### 3.5 `modify-backup-attributes`

Modifies attributes of a backup, such as the expiration setting.

**Synopsis:**
```bash
aws cloudhsmv2 modify-backup-attributes \
    --backup-id <value> \
    --never-expires <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-id` | **Yes** | string | -- | ID of the backup to modify |
| `--never-expires` | **Yes** | boolean | -- | Set to `true` to prevent automatic expiration |

**Output Schema:**
```json
{
    "Backup": {
        "BackupId": "string",
        "BackupArn": "string",
        "BackupState": "string",
        "ClusterId": "string",
        "CreateTimestamp": "timestamp",
        "NeverExpires": true|false
    }
}
```
