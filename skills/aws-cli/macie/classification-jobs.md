# Classification Jobs

### 2.1 `create-classification-job`

Creates and defines the settings for a classification job.

**Synopsis:**
```bash
aws macie2 create-classification-job \
    --job-type <value> \
    --name <value> \
    --s3-job-definition <value> \
    [--client-token <value>] \
    [--custom-data-identifier-ids <value>] \
    [--description <value>] \
    [--initial-run | --no-initial-run] \
    [--managed-data-identifier-ids <value>] \
    [--managed-data-identifier-selector <value>] \
    [--allow-list-ids <value>] \
    [--sampling-percentage <value>] \
    [--schedule-frequency-expression <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-type` | **Yes** | string | -- | Job type: `ONE_TIME` or `SCHEDULED` |
| `--name` | **Yes** | string | -- | Job name |
| `--s3-job-definition` | **Yes** | structure | -- | S3 buckets and objects to analyze |
| `--client-token` | No | string | None | Idempotency token |
| `--custom-data-identifier-ids` | No | list(string) | None | Custom data identifier IDs to use |
| `--description` | No | string | None | Job description |
| `--initial-run` | No | boolean | None | Run immediately for scheduled jobs |
| `--managed-data-identifier-ids` | No | list(string) | None | Managed data identifier IDs |
| `--managed-data-identifier-selector` | No | string | None | Selection criteria: `ALL`, `EXCLUDE`, `INCLUDE`, `NONE`, `RECOMMENDED` |
| `--allow-list-ids` | No | list(string) | None | Allow list IDs to use |
| `--sampling-percentage` | No | integer | None | Percentage of objects to sample (1-100) |
| `--schedule-frequency-expression` | No | string | None | Schedule expression for scheduled jobs |
| `--tags` | No | map | None | Tags to add |

**S3 Job Definition Structure:**
```json
{
    "bucketDefinitions": [
        {
            "accountId": "string",
            "buckets": ["string"]
        }
    ],
    "scoping": {
        "includes": {
            "and": [
                {
                    "simpleScopeTerm": {
                        "comparator": "EQ|GT|GTE|LT|LTE|NE|CONTAINS|STARTS_WITH",
                        "key": "OBJECT_EXTENSION|OBJECT_LAST_MODIFIED_DATE|OBJECT_SIZE|OBJECT_KEY",
                        "values": ["string"]
                    },
                    "tagScopeTerm": {
                        "comparator": "EQ|GT|GTE|LT|LTE|NE|CONTAINS|STARTS_WITH",
                        "key": "string",
                        "tagValues": [
                            {
                                "key": "string",
                                "value": "string"
                            }
                        ],
                        "target": "S3_OBJECT"
                    }
                }
            ]
        },
        "excludes": {}
    },
    "bucketCriteria": {
        "includes": {
            "and": [
                {
                    "simpleCriterion": {
                        "comparator": "EQ|GT|GTE|LT|LTE|NE|CONTAINS|STARTS_WITH",
                        "key": "ACCOUNT_ID|S3_BUCKET_NAME|S3_BUCKET_EFFECTIVE_PERMISSION|S3_BUCKET_SHARED_ACCESS",
                        "values": ["string"]
                    },
                    "tagCriterion": {
                        "comparator": "EQ|GT|GTE|LT|LTE|NE|CONTAINS|STARTS_WITH",
                        "tagValues": [
                            {
                                "key": "string",
                                "value": "string"
                            }
                        ]
                    }
                }
            ]
        },
        "excludes": {}
    }
}
```

**Output Schema:**
```json
{
    "jobArn": "string",
    "jobId": "string"
}
```

---

### 2.2 `describe-classification-job`

Returns information about a classification job.

**Synopsis:**
```bash
aws macie2 describe-classification-job \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | The job ID |

**Output Schema:**
```json
{
    "clientToken": "string",
    "createdAt": "timestamp",
    "customDataIdentifierIds": ["string"],
    "description": "string",
    "initialRun": "boolean",
    "jobArn": "string",
    "jobId": "string",
    "jobStatus": "RUNNING|PAUSED|CANCELLED|COMPLETE|IDLE|USER_PAUSED",
    "jobType": "ONE_TIME|SCHEDULED",
    "lastRunErrorStatus": {
        "code": "NONE|ERROR"
    },
    "lastRunTime": "timestamp",
    "managedDataIdentifierIds": ["string"],
    "managedDataIdentifierSelector": "ALL|EXCLUDE|INCLUDE|NONE|RECOMMENDED",
    "name": "string",
    "s3JobDefinition": {},
    "samplingPercentage": "integer",
    "scheduleFrequencyExpression": "string",
    "statistics": {
        "approximateNumberOfObjectsToProcess": "double",
        "numberOfRuns": "double"
    },
    "tags": {"string": "string"},
    "userPausedDetails": {
        "jobExpiresAt": "timestamp",
        "jobImminentExpirationHealthEventArn": "string",
        "jobPausedAt": "timestamp"
    },
    "allowListIds": ["string"]
}
```

---

### 2.3 `list-classification-jobs`

Lists all classification jobs. **Paginated operation.**

**Synopsis:**
```bash
aws macie2 list-classification-jobs \
    [--filter-criteria <value>] \
    [--sort-criteria <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter-criteria` | No | structure | None | Filter criteria for jobs |
| `--sort-criteria` | No | structure | None | Sort criteria |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "items": [
        {
            "bucketDefinitions": [],
            "createdAt": "timestamp",
            "jobId": "string",
            "jobStatus": "RUNNING|PAUSED|CANCELLED|COMPLETE|IDLE|USER_PAUSED",
            "jobType": "ONE_TIME|SCHEDULED",
            "name": "string",
            "bucketCriteria": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 2.4 `update-classification-job`

Changes the status of a classification job.

**Synopsis:**
```bash
aws macie2 update-classification-job \
    --job-id <value> \
    --job-status <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | The job ID |
| `--job-status` | **Yes** | string | -- | New status: `RUNNING`, `USER_PAUSED`, `CANCELLED` |

**Output:** None (HTTP 200 on success)
