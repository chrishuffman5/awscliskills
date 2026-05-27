# Backup Jobs

### 3.1 `start-backup-job`

Starts an on-demand backup job for the specified resource.

**Synopsis:**
```bash
aws backup start-backup-job \
    --backup-vault-name <value> \
    --resource-arn <value> \
    --iam-role-arn <value> \
    [--idempotency-token <value>] \
    [--start-window-minutes <value>] \
    [--complete-window-minutes <value>] \
    [--lifecycle <value>] \
    [--recovery-point-tags <value>] \
    [--backup-options <value>] \
    [--logically-air-gapped-backup-vault-arn <value>] \
    [--index <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-vault-name` | **Yes** | string | -- | Target vault name (2-50 chars) |
| `--resource-arn` | **Yes** | string | -- | Resource ARN to back up |
| `--iam-role-arn` | **Yes** | string | -- | IAM role ARN for backup operations |
| `--idempotency-token` | No | string | None | Idempotency token |
| `--start-window-minutes` | No | long | 480 | Minutes before cancellation if not started (min: 60) |
| `--complete-window-minutes` | No | long | None | Minutes to complete backup |
| `--lifecycle` | No | structure | None | Cold storage transition and retention |
| `--recovery-point-tags` | No | map | None | Tags for the recovery point |
| `--backup-options` | No | map | None | Options (e.g., WindowsVSS) |
| `--logically-air-gapped-backup-vault-arn` | No | string | None | Air-gapped vault ARN |
| `--index` | No | string | None | Enable indexing: `ENABLED`, `DISABLED` (EBS, S3) |

**Output Schema:**
```json
{
    "BackupJobId": "string",
    "RecoveryPointArn": "string",
    "CreationDate": "timestamp",
    "IsParent": "boolean"
}
```

---

### 3.2 `describe-backup-job`

Returns metadata about a backup job.

**Synopsis:**
```bash
aws backup describe-backup-job \
    --backup-job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-job-id` | **Yes** | string | -- | Backup job ID |

**Output Schema:**
```json
{
    "AccountId": "string",
    "BackupJobId": "string",
    "BackupVaultName": "string",
    "BackupVaultArn": "string",
    "RecoveryPointArn": "string",
    "ResourceArn": "string",
    "CreationDate": "timestamp",
    "CompletionDate": "timestamp",
    "State": "CREATED|PENDING|RUNNING|ABORTING|ABORTED|COMPLETED|FAILED|EXPIRED|PARTIAL",
    "StatusMessage": "string",
    "PercentDone": "string",
    "BackupSizeInBytes": "long",
    "IamRoleArn": "string",
    "ResourceType": "string",
    "BytesTransferred": "long",
    "ExpectedCompletionDate": "timestamp",
    "StartBy": "timestamp",
    "BackupOptions": {"string": "string"},
    "BackupType": "string",
    "ParentJobId": "string",
    "IsParent": "boolean",
    "InitiationDate": "timestamp",
    "MessageCategory": "string"
}
```

---

### 3.3 `list-backup-jobs`

Lists backup jobs. **Paginated operation.**

**Synopsis:**
```bash
aws backup list-backup-jobs \
    [--by-resource-arn <value>] \
    [--by-state <value>] \
    [--by-backup-vault-name <value>] \
    [--by-created-before <value>] \
    [--by-created-after <value>] \
    [--by-resource-type <value>] \
    [--by-account-id <value>] \
    [--by-complete-after <value>] \
    [--by-complete-before <value>] \
    [--by-parent-job-id <value>] \
    [--by-message-category <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--by-resource-arn` | No | string | None | Filter by resource ARN |
| `--by-state` | No | string | None | Filter by state |
| `--by-backup-vault-name` | No | string | None | Filter by vault name |
| `--by-created-before` | No | timestamp | None | Created before date |
| `--by-created-after` | No | timestamp | None | Created after date |
| `--by-resource-type` | No | string | None | Filter by resource type |
| `--by-account-id` | No | string | None | Filter by account ID |
| `--by-parent-job-id` | No | string | None | Filter by parent job |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "BackupJobs": [
        {
            "AccountId": "string",
            "BackupJobId": "string",
            "BackupVaultName": "string",
            "BackupVaultArn": "string",
            "RecoveryPointArn": "string",
            "ResourceArn": "string",
            "CreationDate": "timestamp",
            "CompletionDate": "timestamp",
            "State": "string",
            "StatusMessage": "string",
            "PercentDone": "string",
            "BackupSizeInBytes": "long",
            "IamRoleArn": "string",
            "ResourceType": "string",
            "BytesTransferred": "long",
            "BackupOptions": {},
            "BackupType": "string",
            "ParentJobId": "string",
            "IsParent": "boolean",
            "InitiationDate": "timestamp",
            "MessageCategory": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.4 `stop-backup-job`

Stops a currently running backup job.

**Synopsis:**
```bash
aws backup stop-backup-job \
    --backup-job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-job-id` | **Yes** | string | -- | Backup job ID to stop |

**Output:** None
