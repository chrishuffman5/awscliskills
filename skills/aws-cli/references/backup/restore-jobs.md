# Restore Jobs

### 5.1 `start-restore-job`

Restores a resource from a recovery point. The metadata required varies by resource type.

**Synopsis:**
```bash
aws backup start-restore-job \
    --recovery-point-arn <value> \
    --metadata <value> \
    [--iam-role-arn <value>] \
    [--idempotency-token <value>] \
    [--resource-type <value>] \
    [--copy-source-tags-to-restored-resource | --no-copy-source-tags-to-restored-resource] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--recovery-point-arn` | **Yes** | string | -- | Recovery point ARN |
| `--metadata` | **Yes** | map | -- | Restore metadata (resource-type-specific key-value pairs) |
| `--iam-role-arn` | No | string | None | IAM role ARN for restore |
| `--idempotency-token` | No | string | None | Idempotency token |
| `--resource-type` | No | string | None | Resource type: `Aurora`, `DocumentDB`, `CloudFormation`, `DynamoDB`, `EBS`, `EC2`, `EFS`, `FSx`, `Neptune`, `RDS`, `Redshift`, `S3`, `Storage Gateway`, `Timestream`, `VirtualMachine` |
| `--copy-source-tags-to-restored-resource` | No | boolean | None | Copy tags from backup to restored resource |

**Output Schema:**
```json
{
    "RestoreJobId": "string"
}
```

---

### 5.2 `describe-restore-job`

Returns metadata about a restore job.

**Synopsis:**
```bash
aws backup describe-restore-job \
    --restore-job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--restore-job-id` | **Yes** | string | -- | Restore job ID |

**Output Schema:**
```json
{
    "AccountId": "string",
    "RestoreJobId": "string",
    "RecoveryPointArn": "string",
    "CreationDate": "timestamp",
    "CompletionDate": "timestamp",
    "Status": "PENDING|RUNNING|COMPLETED|ABORTED|FAILED",
    "StatusMessage": "string",
    "PercentDone": "string",
    "BackupSizeInBytes": "long",
    "IamRoleArn": "string",
    "ExpectedCompletionTimeMinutes": "long",
    "CreatedResourceArn": "string",
    "ResourceType": "string",
    "RecoveryPointCreationDate": "timestamp",
    "ValidationStatus": "FAILED|SUCCESSFUL|TIMED_OUT|VALIDATING",
    "ValidationStatusMessage": "string",
    "DeletionStatus": "DELETING|FAILED|SUCCESSFUL",
    "DeletionStatusMessage": "string"
}
```

---

### 5.3 `list-restore-jobs`

Lists restore jobs. **Paginated operation.**

**Synopsis:**
```bash
aws backup list-restore-jobs \
    [--by-account-id <value>] \
    [--by-resource-type <value>] \
    [--by-created-before <value>] \
    [--by-created-after <value>] \
    [--by-status <value>] \
    [--by-complete-before <value>] \
    [--by-complete-after <value>] \
    [--by-restore-testing-plan-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "RestoreJobs": [
        {
            "AccountId": "string",
            "RestoreJobId": "string",
            "RecoveryPointArn": "string",
            "CreationDate": "timestamp",
            "CompletionDate": "timestamp",
            "Status": "string",
            "CreatedResourceArn": "string",
            "ResourceType": "string",
            "ValidationStatus": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.4 `put-restore-validation-result`

Submits a validation result for a restore job.

**Synopsis:**
```bash
aws backup put-restore-validation-result \
    --restore-job-id <value> \
    --validation-status <value> \
    [--validation-status-message <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--restore-job-id` | **Yes** | string | -- | Restore job ID |
| `--validation-status` | **Yes** | string | -- | Status: `FAILED`, `SUCCESSFUL`, `TIMED_OUT`, `VALIDATING` |
| `--validation-status-message` | No | string | None | Status message |

**Output:** None
