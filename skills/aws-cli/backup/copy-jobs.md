# Copy Jobs

### 4.1 `start-copy-job`

Copies a recovery point to another backup vault (same or different region/account).

**Synopsis:**
```bash
aws backup start-copy-job \
    --recovery-point-arn <value> \
    --source-backup-vault-name <value> \
    --destination-backup-vault-arn <value> \
    --iam-role-arn <value> \
    [--idempotency-token <value>] \
    [--lifecycle <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--recovery-point-arn` | **Yes** | string | -- | Recovery point ARN to copy |
| `--source-backup-vault-name` | **Yes** | string | -- | Source vault name |
| `--destination-backup-vault-arn` | **Yes** | string | -- | Destination vault ARN |
| `--iam-role-arn` | **Yes** | string | -- | IAM role ARN |
| `--idempotency-token` | No | string | None | Idempotency token |
| `--lifecycle` | No | structure | None | Lifecycle for destination copy |

**Output Schema:**
```json
{
    "CopyJobId": "string",
    "CreationDate": "timestamp",
    "IsParent": "boolean"
}
```

---

### 4.2 `describe-copy-job`

Returns metadata about a copy job.

**Synopsis:**
```bash
aws backup describe-copy-job \
    --copy-job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--copy-job-id` | **Yes** | string | -- | Copy job ID |

**Output Schema:**
```json
{
    "CopyJob": {
        "AccountId": "string",
        "CopyJobId": "string",
        "SourceBackupVaultArn": "string",
        "SourceRecoveryPointArn": "string",
        "DestinationBackupVaultArn": "string",
        "DestinationRecoveryPointArn": "string",
        "ResourceArn": "string",
        "CreationDate": "timestamp",
        "CompletionDate": "timestamp",
        "State": "CREATED|RUNNING|COMPLETED|FAILED|PARTIAL",
        "StatusMessage": "string",
        "BackupSizeInBytes": "long",
        "IamRoleArn": "string",
        "ResourceType": "string",
        "ParentJobId": "string",
        "IsParent": "boolean",
        "NumberOfChildJobs": "long",
        "ChildJobsInState": {"string": "long"},
        "MessageCategory": "string"
    }
}
```

---

### 4.3 `list-copy-jobs`

Lists copy jobs. **Paginated operation.**

**Synopsis:**
```bash
aws backup list-copy-jobs \
    [--by-resource-arn <value>] \
    [--by-state <value>] \
    [--by-created-before <value>] \
    [--by-created-after <value>] \
    [--by-resource-type <value>] \
    [--by-destination-vault-arn <value>] \
    [--by-account-id <value>] \
    [--by-complete-before <value>] \
    [--by-complete-after <value>] \
    [--by-parent-job-id <value>] \
    [--by-message-category <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "CopyJobs": [
        {
            "CopyJobId": "string",
            "State": "string",
            "SourceBackupVaultArn": "string",
            "DestinationBackupVaultArn": "string",
            "ResourceArn": "string",
            "ResourceType": "string",
            "CreationDate": "timestamp",
            "CompletionDate": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
