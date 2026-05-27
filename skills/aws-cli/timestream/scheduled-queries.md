# Scheduled Queries

### 4.1 `create-scheduled-query`

Creates a scheduled query that runs on a schedule and writes results to a target Timestream table.

**Synopsis:**
```bash
aws timestream-query create-scheduled-query \
    --name <value> \
    --query-string <value> \
    --schedule-configuration <value> \
    --notification-configuration <value> \
    --scheduled-query-execution-role-arn <value> \
    --error-report-configuration <value> \
    [--target-configuration <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--kms-key-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Scheduled query name (1-64 chars) |
| `--query-string` | **Yes** | string | -- | Query to execute (1-262144 chars). Supports `@scheduled_runtime` parameter |
| `--schedule-configuration` | **Yes** | structure | -- | Schedule expression (cron or rate) |
| `--notification-configuration` | **Yes** | structure | -- | SNS topic for execution notifications |
| `--scheduled-query-execution-role-arn` | **Yes** | string | -- | IAM role ARN for Timestream to assume (1-2048 chars) |
| `--error-report-configuration` | **Yes** | structure | -- | S3 location for error reports |
| `--target-configuration` | No | structure | None | Target Timestream table and column mappings for results |
| `--client-token` | No | string | auto-generated | Idempotency token (32-128 chars, valid for 8 hours) |
| `--tags` | No | list | None | Key-value tags (max 200) |
| `--kms-key-id` | No | string | Timestream-owned key | KMS key for encryption (1-2048 chars) |

**Schedule Configuration:**
```json
{
    "ScheduleExpression": "rate(1 hour)"
}
```
Supports cron expressions (e.g., `cron(0 * * * ? *)`) or rate expressions (e.g., `rate(1 hour)`).

**Notification Configuration:**
```json
{
    "SnsConfiguration": {
        "TopicArn": "arn:aws:sns:us-east-1:123456789012:my-topic"
    }
}
```

**Error Report Configuration:**
```json
{
    "S3Configuration": {
        "BucketName": "string",
        "ObjectKeyPrefix": "string",
        "EncryptionOption": "SSE_S3|SSE_KMS"
    }
}
```

**Target Configuration:**
```json
{
    "TimestreamConfiguration": {
        "DatabaseName": "string",
        "TableName": "string",
        "TimeColumn": "string",
        "DimensionMappings": [
            {
                "Name": "string",
                "DimensionValueType": "VARCHAR"
            }
        ],
        "MultiMeasureMappings": {
            "TargetMultiMeasureName": "string",
            "MultiMeasureAttributeMappings": [
                {
                    "SourceColumn": "string",
                    "TargetMultiMeasureAttributeName": "string",
                    "MeasureValueType": "BIGINT|BOOLEAN|DOUBLE|VARCHAR|TIMESTAMP"
                }
            ]
        },
        "MixedMeasureMappings": [
            {
                "MeasureName": "string",
                "SourceColumn": "string",
                "TargetMeasureName": "string",
                "MeasureValueType": "BIGINT|BOOLEAN|DOUBLE|VARCHAR|MULTI",
                "MultiMeasureAttributeMappings": []
            }
        ],
        "MeasureNameColumn": "string"
    }
}
```

**Output Schema:**
```json
{
    "Arn": "string"
}
```

---

### 4.2 `describe-scheduled-query`

Describes a scheduled query including its configuration, state, and recent run history.

**Synopsis:**
```bash
aws timestream-query describe-scheduled-query \
    --scheduled-query-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scheduled-query-arn` | **Yes** | string | -- | ARN of the scheduled query (1-2048 chars) |

**Output Schema:**
```json
{
    "ScheduledQuery": {
        "Arn": "string",
        "Name": "string",
        "QueryString": "string",
        "CreationTime": "timestamp",
        "State": "ENABLED|DISABLED",
        "PreviousInvocationTime": "timestamp",
        "NextInvocationTime": "timestamp",
        "ScheduleConfiguration": {
            "ScheduleExpression": "string"
        },
        "NotificationConfiguration": {
            "SnsConfiguration": {
                "TopicArn": "string"
            }
        },
        "TargetConfiguration": {
            "TimestreamConfiguration": {
                "DatabaseName": "string",
                "TableName": "string",
                "TimeColumn": "string",
                "DimensionMappings": [],
                "MultiMeasureMappings": {},
                "MixedMeasureMappings": [],
                "MeasureNameColumn": "string"
            }
        },
        "ScheduledQueryExecutionRoleArn": "string",
        "KmsKeyId": "string",
        "ErrorReportConfiguration": {
            "S3Configuration": {
                "BucketName": "string",
                "ObjectKeyPrefix": "string",
                "EncryptionOption": "SSE_S3|SSE_KMS"
            }
        },
        "LastRunSummary": {
            "InvocationTime": "timestamp",
            "TriggerTime": "timestamp",
            "RunStatus": "AUTO_TRIGGER_SUCCESS|AUTO_TRIGGER_FAILURE|MANUAL_TRIGGER_SUCCESS|MANUAL_TRIGGER_FAILURE",
            "ExecutionStats": {
                "ExecutionTimeInMillis": "long",
                "DataWrites": "long",
                "BytesMetered": "long",
                "CumulativeBytesScanned": "long",
                "RecordsIngested": "long",
                "QueryResultRows": "long"
            },
            "ErrorReportLocation": {
                "S3ReportLocation": {
                    "BucketName": "string",
                    "ObjectKey": "string"
                }
            },
            "FailureReason": "string"
        },
        "RecentlyFailedRuns": []
    }
}
```

---

### 4.3 `update-scheduled-query`

Enables or disables a scheduled query.

**Synopsis:**
```bash
aws timestream-query update-scheduled-query \
    --scheduled-query-arn <value> \
    --state <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scheduled-query-arn` | **Yes** | string | -- | ARN of the scheduled query |
| `--state` | **Yes** | string | -- | New state: `ENABLED` or `DISABLED` |

**Output:** None

---

### 4.4 `delete-scheduled-query`

Deletes a scheduled query.

**Synopsis:**
```bash
aws timestream-query delete-scheduled-query \
    --scheduled-query-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scheduled-query-arn` | **Yes** | string | -- | ARN of the scheduled query to delete |

**Output:** None

---

### 4.5 `execute-scheduled-query`

Manually triggers an execution of a scheduled query.

**Synopsis:**
```bash
aws timestream-query execute-scheduled-query \
    --scheduled-query-arn <value> \
    --invocation-time <value> \
    [--client-token <value>] \
    [--query-insights <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scheduled-query-arn` | **Yes** | string | -- | ARN of the scheduled query |
| `--invocation-time` | **Yes** | timestamp | -- | Timestamp used as `@scheduled_runtime` in the query |
| `--client-token` | No | string | auto-generated | Idempotency token |
| `--query-insights` | No | structure | None | Enable query insights |

**Output:** None

---

### 4.6 `list-scheduled-queries`

Lists all scheduled queries. **Paginated operation.**

**Synopsis:**
```bash
aws timestream-query list-scheduled-queries \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ScheduledQueries": [
        {
            "Arn": "string",
            "Name": "string",
            "CreationTime": "timestamp",
            "State": "ENABLED|DISABLED",
            "PreviousInvocationTime": "timestamp",
            "NextInvocationTime": "timestamp",
            "ErrorReportConfiguration": {
                "S3Configuration": {
                    "BucketName": "string",
                    "ObjectKeyPrefix": "string",
                    "EncryptionOption": "SSE_S3|SSE_KMS"
                }
            },
            "TargetDestination": {
                "TimestreamDestination": {
                    "DatabaseName": "string",
                    "TableName": "string"
                }
            },
            "LastRunStatus": "AUTO_TRIGGER_SUCCESS|AUTO_TRIGGER_FAILURE|MANUAL_TRIGGER_SUCCESS|MANUAL_TRIGGER_FAILURE"
        }
    ],
    "NextToken": "string"
}
```
