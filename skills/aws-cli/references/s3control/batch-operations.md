# Batch Operations

### 5.1 `create-job`

Creates an S3 Batch Operations job to perform a specified operation on every object in the manifest.

**Synopsis:**
```bash
aws s3control create-job \
    --account-id <value> \
    --operation <value> \
    --report <value> \
    --priority <value> \
    --role-arn <value> \
    [--manifest <value>] \
    [--manifest-generator <value>] \
    [--description <value>] \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--confirmation-required | --no-confirmation-required] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--operation` | **Yes** | structure | -- | Operation to perform (see below) |
| `--report` | **Yes** | structure | -- | Job completion report configuration |
| `--priority` | **Yes** | integer | -- | Job priority (0 to 2,147,483,647). Higher = higher priority |
| `--role-arn` | **Yes** | string | -- | IAM role ARN for the job |
| `--manifest` | No | structure | None | Manifest file configuration |
| `--manifest-generator` | No | structure | None | Auto-generate manifest from S3 bucket |
| `--description` | No | string | None | Job description (1-256 chars) |
| `--client-request-token` | No | string | None | Idempotency token (1-64 chars) |
| `--tags` | No | list | None | Key-value tags |
| `--confirmation-required` | No | boolean | None | Require confirmation before running |

**Operation Structure (one of):**
```json
{
    "LambdaInvoke": {
        "FunctionArn": "string",
        "InvocationSchemaVersion": "string",
        "UserArguments": {"key": "value"}
    },
    "S3PutObjectCopy": {
        "TargetResource": "string",
        "CannedAccessControlList": "private|public-read|...",
        "StorageClass": "STANDARD|STANDARD_IA|ONEZONE_IA|GLACIER|...",
        "TargetKeyPrefix": "string",
        "ObjectLockLegalHoldStatus": "OFF|ON",
        "ObjectLockMode": "COMPLIANCE|GOVERNANCE",
        "ObjectLockRetainUntilDate": "timestamp"
    },
    "S3PutObjectTagging": {
        "TagSet": [{"Key": "string", "Value": "string"}]
    },
    "S3DeleteObjectTagging": {},
    "S3PutObjectAcl": {
        "AccessControlPolicy": {
            "AccessControlList": {
                "Owner": {"ID": "string", "DisplayName": "string"},
                "Grants": [{"Grantee": {}, "Permission": "string"}]
            },
            "CannedAccessControlList": "string"
        }
    },
    "S3InitiateRestoreObject": {
        "ExpirationInDays": "integer",
        "GlacierJobTier": "BULK|STANDARD"
    },
    "S3PutObjectLegalHold": {
        "LegalHold": {"Status": "OFF|ON"}
    },
    "S3PutObjectRetention": {
        "BypassGovernanceRetention": true|false,
        "Retention": {"RetainUntilDate": "timestamp", "Mode": "COMPLIANCE|GOVERNANCE"}
    },
    "S3ReplicateObject": {}
}
```

**Manifest Structure:**
```json
{
    "Spec": {
        "Format": "S3BatchOperations_CSV_20180820|S3InventoryReport_CSV_20161130",
        "Fields": ["Ignore", "Bucket", "Key", "VersionId"]
    },
    "Location": {
        "ObjectArn": "string",
        "ObjectVersionId": "string",
        "ETag": "string"
    }
}
```

**Report Structure:**
```json
{
    "Bucket": "string",
    "Format": "Report_CSV_20180820",
    "Enabled": true|false,
    "Prefix": "string",
    "ReportScope": "AllTasks|FailedTasksOnly"
}
```

**Output Schema:**
```json
{
    "JobId": "string"
}
```

---

### 5.2 `describe-job`

Retrieves the configuration parameters and status for a Batch Operations job.

**Synopsis:**
```bash
aws s3control describe-job \
    --account-id <value> \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--job-id` | **Yes** | string | -- | Job ID (5-36 chars) |

**Output Schema:**
```json
{
    "Job": {
        "JobId": "string",
        "ConfirmationRequired": true|false,
        "Description": "string",
        "JobArn": "string",
        "Status": "Active|Cancelled|Cancelling|Complete|Completing|Failed|Failing|New|Paused|Pausing|Preparing|Ready|Suspended",
        "Manifest": {
            "Spec": {
                "Format": "string",
                "Fields": ["string"]
            },
            "Location": {
                "ObjectArn": "string",
                "ObjectVersionId": "string",
                "ETag": "string"
            }
        },
        "Operation": {},
        "Priority": "integer",
        "ProgressSummary": {
            "TotalNumberOfTasks": "long",
            "NumberOfTasksSucceeded": "long",
            "NumberOfTasksFailed": "long",
            "Timers": {
                "ElapsedTimeInActiveSeconds": "long"
            }
        },
        "StatusUpdateReason": "string",
        "FailureReasons": [
            {
                "FailureCode": "string",
                "FailureReason": "string"
            }
        ],
        "Report": {
            "Bucket": "string",
            "Format": "string",
            "Enabled": true|false,
            "Prefix": "string",
            "ReportScope": "string"
        },
        "CreationTime": "timestamp",
        "TerminationDate": "timestamp",
        "RoleArn": "string",
        "SuspendedDate": "timestamp",
        "SuspendedCause": "string"
    }
}
```

---

### 5.3 `list-jobs`

Lists current Batch Operations jobs and recently completed jobs. **Paginated.**

**Synopsis:**
```bash
aws s3control list-jobs \
    --account-id <value> \
    [--job-statuses <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--job-statuses` | No | list(string) | None | Filter by statuses: `Active`, `Cancelled`, `Cancelling`, `Complete`, `Completing`, `Failed`, `Failing`, `New`, `Paused`, `Pausing`, `Preparing`, `Ready`, `Suspended` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 1000) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Jobs": [
        {
            "JobId": "string",
            "Description": "string",
            "Operation": "LambdaInvoke|S3PutObjectCopy|S3PutObjectAcl|S3PutObjectTagging|S3DeleteObjectTagging|S3InitiateRestoreObject|S3PutObjectLegalHold|S3PutObjectRetention|S3ReplicateObject",
            "Priority": "integer",
            "Status": "string",
            "CreationTime": "timestamp",
            "TerminationDate": "timestamp",
            "ProgressSummary": {
                "TotalNumberOfTasks": "long",
                "NumberOfTasksSucceeded": "long",
                "NumberOfTasksFailed": "long"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 5.4 `update-job-priority`

Updates the priority of an existing Batch Operations job.

**Synopsis:**
```bash
aws s3control update-job-priority \
    --account-id <value> \
    --job-id <value> \
    --priority <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--job-id` | **Yes** | string | -- | Job ID |
| `--priority` | **Yes** | integer | -- | New priority (0 to 2,147,483,647) |

**Output Schema:**
```json
{
    "JobId": "string",
    "Priority": "integer"
}
```

---

### 5.5 `update-job-status`

Updates the status of a Batch Operations job. Used to confirm, cancel, or resume jobs.

**Synopsis:**
```bash
aws s3control update-job-status \
    --account-id <value> \
    --job-id <value> \
    --requested-job-status <value> \
    [--status-update-reason <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--job-id` | **Yes** | string | -- | Job ID |
| `--requested-job-status` | **Yes** | string | -- | New status: `Cancelled`, `Ready` |
| `--status-update-reason` | No | string | None | Reason for the status change |

**Output Schema:**
```json
{
    "JobId": "string",
    "Status": "string",
    "StatusUpdateReason": "string"
}
```

---

### 5.6 `get-job-tagging`

Returns the tag set of a Batch Operations job.

**Synopsis:**
```bash
aws s3control get-job-tagging \
    --account-id <value> \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--job-id` | **Yes** | string | -- | Job ID |

**Output Schema:**
```json
{
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```

---

### 5.7 `put-job-tagging`

Sets the tag set for a Batch Operations job.

**Synopsis:**
```bash
aws s3control put-job-tagging \
    --account-id <value> \
    --job-id <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--job-id` | **Yes** | string | -- | Job ID |
| `--tags` | **Yes** | list | -- | Tag set. Shorthand: `Key=string,Value=string ...` |

**Output:** None

---

### 5.8 `delete-job-tagging`

Removes the entire tag set from a Batch Operations job.

**Synopsis:**
```bash
aws s3control delete-job-tagging \
    --account-id <value> \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--job-id` | **Yes** | string | -- | Job ID |

**Output:** None
