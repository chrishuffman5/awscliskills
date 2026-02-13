# Export & Import

### 4.1 `start-export-task`

Begins exporting discovered data to an S3 bucket. Max 5 concurrent exports, max 2 per day for detailed agent data.

**Synopsis:**
```bash
aws discovery start-export-task \
    [--export-data-format <value>] \
    [--filters <value>] \
    [--start-time <value>] \
    [--end-time <value>] \
    [--preferences <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--export-data-format` | No | list(string) | `CSV` | Export format (currently only `CSV`) |
| `--filters` | No | list | None | Filter by agent IDs |
| `--start-time` | No | timestamp | None | Start time for exported data |
| `--end-time` | No | timestamp | None | End time for exported data |
| `--preferences` | No | structure | None | EC2 recommendation preferences |

**Filter Structure (shorthand):**
```
name=agentIds,values=string,string,condition=EQUALS
```

**EC2 Recommendations Preferences Structure (JSON):**
```json
{
    "ec2RecommendationsPreferences": {
        "enabled": true,
        "cpuPerformanceMetricBasis": {
            "name": "string",
            "percentageAdjust": "double"
        },
        "ramPerformanceMetricBasis": {
            "name": "string",
            "percentageAdjust": "double"
        },
        "tenancy": "DEDICATED|SHARED",
        "excludedInstanceTypes": ["string"],
        "preferredRegion": "string",
        "reservedInstanceOptions": {
            "purchasingOption": "ALL_UPFRONT|PARTIAL_UPFRONT|NO_UPFRONT",
            "offeringClass": "STANDARD|CONVERTIBLE",
            "termLength": "ONE_YEAR|THREE_YEAR"
        }
    }
}
```

**Output Schema:**
```json
{
    "exportId": "string"
}
```

---

### 4.2 `describe-export-tasks`

Retrieves the status of export tasks. **Paginated operation.**

**Synopsis:**
```bash
aws discovery describe-export-tasks \
    [--export-ids <value>] \
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
| `--export-ids` | No | list(string) | None | Export IDs to query (max 100) |
| `--filters` | No | list | None | Filter by agent IDs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "exportsInfo": [
        {
            "exportId": "string",
            "exportStatus": "IN_PROGRESS|SUCCEEDED|FAILED",
            "statusMessage": "string",
            "configurationsDownloadUrl": "string",
            "exportRequestTime": "timestamp",
            "isTruncated": "boolean",
            "requestedStartTime": "timestamp",
            "requestedEndTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 4.3 `start-continuous-export`

Starts continuous export of discovered data to S3 and Amazon Athena.

**Synopsis:**
```bash
aws discovery start-continuous-export \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No required parameters.

**Output Schema:**
```json
{
    "exportId": "string",
    "s3Bucket": "string",
    "startTime": "timestamp",
    "dataSource": "AGENT",
    "schemaStorageConfig": {
        "databaseName": "string"
    }
}
```

---

### 4.4 `stop-continuous-export`

Stops continuous export.

**Synopsis:**
```bash
aws discovery stop-continuous-export \
    --export-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--export-id` | **Yes** | string | -- | Export ID to stop |

**Output Schema:**
```json
{
    "startTime": "timestamp",
    "stopTime": "timestamp"
}
```

---

### 4.5 `describe-continuous-exports`

Describes continuous exports. **Paginated operation.**

**Synopsis:**
```bash
aws discovery describe-continuous-exports \
    [--export-ids <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--export-ids` | No | list(string) | None | Export IDs to describe |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "descriptions": [
        {
            "exportId": "string",
            "status": "START_IN_PROGRESS|START_FAILED|ACTIVE|ERROR|STOP_IN_PROGRESS|STOP_FAILED|INACTIVE",
            "statusDetail": "string",
            "s3Bucket": "string",
            "startTime": "timestamp",
            "stopTime": "timestamp",
            "dataSource": "AGENT",
            "schemaStorageConfig": {
                "databaseName": "string"
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 4.6 `start-import-task`

Starts an import task to import data from a CSV file in S3.

**Synopsis:**
```bash
aws discovery start-import-task \
    --name <value> \
    --import-url <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Import task name (1-255 chars) |
| `--import-url` | **Yes** | string | -- | S3 URL of CSV file (e.g., `s3://bucket/file.csv`) |
| `--client-request-token` | No | string | auto-generated | Idempotency token (1-100 chars) |

**Output Schema:**
```json
{
    "task": {
        "importTaskId": "string",
        "clientRequestToken": "string",
        "name": "string",
        "importUrl": "string",
        "status": "IMPORT_IN_PROGRESS|IMPORT_COMPLETE|IMPORT_COMPLETE_WITH_ERRORS|IMPORT_FAILED|...",
        "importRequestTime": "timestamp",
        "importCompletionTime": "timestamp",
        "importDeletedTime": "timestamp",
        "fileClassification": "MODELIZEIT_EXPORT|RVTOOLS_EXPORT|VMWARE_NSX_EXPORT|IMPORT_TEMPLATE",
        "serverImportSuccess": "integer",
        "serverImportFailure": "integer",
        "applicationImportSuccess": "integer",
        "applicationImportFailure": "integer",
        "errorsAndFailedEntriesZip": "string"
    }
}
```

---

### 4.7 `describe-import-tasks`

Describes import tasks. **Paginated operation.**

**Synopsis:**
```bash
aws discovery describe-import-tasks \
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
| `--filters` | No | list | None | Filter by IMPORT_TASK_ID, STATUS, NAME, or FILE_CLASSIFICATION |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Structure (shorthand):**
```
name=IMPORT_TASK_ID|STATUS|NAME|FILE_CLASSIFICATION,values=string,string
```

**Output Schema:**
```json
{
    "tasks": [
        {
            "importTaskId": "string",
            "clientRequestToken": "string",
            "name": "string",
            "importUrl": "string",
            "status": "string",
            "importRequestTime": "timestamp",
            "importCompletionTime": "timestamp",
            "importDeletedTime": "timestamp",
            "fileClassification": "string",
            "serverImportSuccess": "integer",
            "serverImportFailure": "integer",
            "applicationImportSuccess": "integer",
            "applicationImportFailure": "integer",
            "errorsAndFailedEntriesZip": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 4.8 `batch-delete-import-data`

Deletes one or more import tasks and their associated data.

**Synopsis:**
```bash
aws discovery batch-delete-import-data \
    --import-task-ids <value> \
    [--delete-history | --no-delete-history] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--import-task-ids` | **Yes** | list(string) | -- | Import task IDs to delete (max 10) |
| `--delete-history` | No | boolean | false | Also delete migration history data |

**Output Schema:**
```json
{
    "errors": [
        {
            "importTaskId": "string",
            "errorCode": "NOT_FOUND|INTERNAL_SERVER_ERROR|OVER_LIMIT",
            "errorDescription": "string"
        }
    ]
}
```
