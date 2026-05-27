# Tiering & Scanning

### 14.1 `update-recovery-point-lifecycle`

Updates the lifecycle (transition to cold storage and deletion) of a recovery point.

**Synopsis:**
```bash
aws backup update-recovery-point-lifecycle \
    --backup-vault-name <value> \
    --recovery-point-arn <value> \
    [--lifecycle <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-vault-name` | **Yes** | string | -- | Vault name |
| `--recovery-point-arn` | **Yes** | string | -- | Recovery point ARN |
| `--lifecycle` | No | structure | None | Lifecycle configuration |

**Lifecycle Structure:**
```json
{
    "MoveToColdStorageAfterDays": "long",
    "DeleteAfterDays": "long",
    "OptInToArchiveForSupportedResources": "boolean"
}
```

**Output Schema:**
```json
{
    "BackupVaultArn": "string",
    "RecoveryPointArn": "string",
    "Lifecycle": {
        "MoveToColdStorageAfterDays": "long",
        "DeleteAfterDays": "long",
        "OptInToArchiveForSupportedResources": "boolean"
    },
    "CalculatedLifecycle": {
        "MoveToColdStorageAt": "timestamp",
        "DeleteAt": "timestamp"
    }
}
```

---

### 14.2 `start-backup-job` (with lifecycle)

When starting a backup job, you can specify lifecycle tiering in the request. See [backup-jobs.md](backup-jobs.md) for full `start-backup-job` reference. The `--lifecycle` parameter controls cold storage transition and deletion timing.

---

### 14.3 `list-recovery-points-by-backup-vault` (filtering by date)

Recovery points can be filtered by creation date to identify candidates for tiering changes. See [recovery-points.md](recovery-points.md) for full reference. Use `--by-created-before` and `--by-created-after` filters.

---

### 14.4 `describe-backup-job` (scan status)

Backup jobs may include malware scan results. When a backup job completes with scanning enabled, the job status includes scan information. See [backup-jobs.md](backup-jobs.md) for full `describe-backup-job` reference.

**Scan-related output fields:**
```json
{
    "MessageCategory": "string",
    "InitiationDate": "timestamp",
    "ResourceType": "string",
    "State": "CREATED|PENDING|RUNNING|ABORTING|ABORTED|COMPLETED|FAILED|EXPIRED|PARTIAL"
}
```

---

### 14.5 `list-backup-job-summaries` (scan aggregation)

Use `--message-category` filter with `list-backup-job-summaries` to aggregate scan results. See [settings.md](settings.md) for full reference.

**Example:**
```bash
# List backup job summaries filtered by message category
aws backup list-backup-job-summaries \
    --message-category Success \
    --aggregation-period SEVEN_DAYS
```
