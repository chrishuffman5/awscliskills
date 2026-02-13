# Backups

### 2.1 `create-backup`

Creates a manual backup of a file system or ONTAP volume.

**Synopsis:**
```bash
aws fsx create-backup \
    [--file-system-id <value>] \
    [--volume-id <value>] \
    [--tags <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-id` | No* | string | None | File system ID (for Windows, Lustre, OpenZFS) |
| `--volume-id` | No* | string | None | Volume ID (for ONTAP volumes) |
| `--tags` | No | list | None | Tags (max 50) |
| `--client-request-token` | No | string | Auto | Idempotency token |

*One of `--file-system-id` or `--volume-id` is required.

**Output Schema:**
```json
{
    "Backup": {
        "BackupId": "string",
        "Lifecycle": "AVAILABLE|CREATING|TRANSFERRING|DELETED|FAILED|PENDING|COPYING",
        "Type": "AUTOMATIC|USER_INITIATED|AWS_BACKUP",
        "ProgressPercent": "integer",
        "CreationTime": "timestamp",
        "KmsKeyId": "string",
        "ResourceARN": "string",
        "Tags": [],
        "FileSystem": {},
        "Volume": {},
        "FailureDetails": {
            "Message": "string"
        }
    }
}
```

---

### 2.2 `copy-backup`

Copies a backup to another region or account.

**Synopsis:**
```bash
aws fsx copy-backup \
    --source-backup-id <value> \
    [--source-region <value>] \
    [--kms-key-id <value>] \
    [--copy-tags | --no-copy-tags] \
    [--tags <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-backup-id` | **Yes** | string | -- | Source backup ID or ARN |
| `--source-region` | No | string | None | Source region (for cross-region copy) |
| `--kms-key-id` | No | string | None | KMS key in destination region |
| `--copy-tags` | No | boolean | None | Copy tags from source |
| `--tags` | No | list | None | Additional tags |

**Output:** Same as `create-backup`

---

### 2.3 `describe-backups`

Returns descriptions of backups. **Paginated operation.**

**Synopsis:**
```bash
aws fsx describe-backups \
    [--backup-ids <value>] \
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
| `--backup-ids` | No | list | None | Backup IDs (max 50) |
| `--filters` | No | list | None | Filters: `file-system-id`, `backup-type`, `file-system-type`, `volume-id` |

**Filter Structure:**
```json
[
    {
        "Name": "file-system-id|backup-type|file-system-type|volume-id",
        "Values": ["string"]
    }
]
```

**Output Schema:**
```json
{
    "Backups": [
        {
            "BackupId": "string",
            "Lifecycle": "string",
            "Type": "AUTOMATIC|USER_INITIATED|AWS_BACKUP",
            "ProgressPercent": "integer",
            "CreationTime": "timestamp",
            "KmsKeyId": "string",
            "ResourceARN": "string",
            "Tags": [],
            "FileSystem": {},
            "Volume": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 2.4 `delete-backup`

Deletes a backup.

**Synopsis:**
```bash
aws fsx delete-backup \
    --backup-id <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-id` | **Yes** | string | -- | Backup ID |

**Output Schema:**
```json
{
    "BackupId": "string",
    "Lifecycle": "DELETED"
}
```
