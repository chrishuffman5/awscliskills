# ML Transforms

### 12.1 `create-ml-transform`

Creates a machine learning transform (FindMatches).

**Synopsis:**
```bash
aws glue create-ml-transform \
    --name <value> \
    --input-record-tables <value> \
    --parameters <value> \
    --role <value> \
    [--description <value>] \
    [--glue-version <value>] \
    [--max-capacity <value>] \
    [--worker-type <value>] \
    [--number-of-workers <value>] \
    [--timeout <value>] \
    [--max-retries <value>] \
    [--tags <value>] \
    [--transform-encryption <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Transform name |
| `--input-record-tables` | **Yes** | list | -- | Input tables (JSON) |
| `--parameters` | **Yes** | structure | -- | Transform parameters. Shorthand: `TransformType=FIND_MATCHES,FindMatchesParameters={PrimaryKeyColumnName=string,PrecisionRecallTradeoff=double,AccuracyCostTradeoff=double,EnforceProvidedLabels=boolean}` |
| `--role` | **Yes** | string | -- | IAM role ARN |
| `--description` | No | string | -- | Description |
| `--glue-version` | No | string | -- | Glue version |
| `--max-capacity` | No | double | -- | Max DPUs |
| `--worker-type` | No | string | -- | `Standard`, `G.1X`, `G.2X` |
| `--number-of-workers` | No | integer | -- | Number of workers |
| `--timeout` | No | integer | -- | Timeout in minutes |
| `--max-retries` | No | integer | -- | Max retries |
| `--tags` | No | map | -- | Tags as JSON |

**Output Schema:**
```json
{
    "TransformId": "string"
}
```

---

### 12.2 `delete-ml-transform`

Deletes an ML transform.

**Synopsis:**
```bash
aws glue delete-ml-transform \
    --transform-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--transform-id` | **Yes** | string | -- | Transform ID |

**Output Schema:**
```json
{
    "TransformId": "string"
}
```

---

### 12.3 `get-ml-transform`

Retrieves an ML transform.

**Synopsis:**
```bash
aws glue get-ml-transform \
    --transform-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--transform-id` | **Yes** | string | -- | Transform ID |

**Output Schema:**
```json
{
    "TransformId": "string",
    "Name": "string",
    "Description": "string",
    "Status": "NOT_READY|READY|DELETING",
    "CreatedOn": "timestamp",
    "LastModifiedOn": "timestamp",
    "InputRecordTables": [
        {
            "DatabaseName": "string",
            "TableName": "string",
            "CatalogId": "string",
            "ConnectionName": "string"
        }
    ],
    "Parameters": {
        "TransformType": "FIND_MATCHES",
        "FindMatchesParameters": {
            "PrimaryKeyColumnName": "string",
            "PrecisionRecallTradeoff": "double",
            "AccuracyCostTradeoff": "double",
            "EnforceProvidedLabels": "boolean"
        }
    },
    "EvaluationMetrics": {
        "TransformType": "FIND_MATCHES",
        "FindMatchesMetrics": {
            "AreaUnderPRCurve": "double",
            "Precision": "double",
            "Recall": "double",
            "F1": "double",
            "ConfusionMatrix": {
                "NumTruePositives": "long",
                "NumFalsePositives": "long",
                "NumTrueNegatives": "long",
                "NumFalseNegatives": "long"
            },
            "ColumnImportances": []
        }
    },
    "LabelCount": "integer",
    "Schema": [
        {
            "Name": "string",
            "DataType": "string"
        }
    ],
    "Role": "string",
    "GlueVersion": "string",
    "MaxCapacity": "double",
    "WorkerType": "string",
    "NumberOfWorkers": "integer",
    "Timeout": "integer",
    "MaxRetries": "integer",
    "TransformEncryption": {}
}
```

---

### 12.4 `get-ml-transforms`

Retrieves all ML transforms. **Paginated operation.**

**Synopsis:**
```bash
aws glue get-ml-transforms \
    [--filter <value>] \
    [--sort <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter` | No | structure | -- | Filter criteria (JSON) |
| `--sort` | No | structure | -- | Sort criteria. Shorthand: `Column=NAME|TRANSFORM_TYPE|STATUS|CREATED|LAST_MODIFIED,SortDirection=DESCENDING|ASCENDING` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "Transforms": ["<MLTransform structure>"],
    "NextToken": "string"
}
```

---

### 12.5 `update-ml-transform`

Updates an ML transform.

**Synopsis:**
```bash
aws glue update-ml-transform \
    --transform-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--parameters <value>] \
    [--role <value>] \
    [--glue-version <value>] \
    [--max-capacity <value>] \
    [--worker-type <value>] \
    [--number-of-workers <value>] \
    [--timeout <value>] \
    [--max-retries <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--transform-id` | **Yes** | string | -- | Transform ID |
| `--name` | No | string | -- | Updated name |
| `--description` | No | string | -- | Updated description |
| `--parameters` | No | structure | -- | Updated parameters |
| `--role` | No | string | -- | Updated IAM role |
| `--glue-version` | No | string | -- | Updated Glue version |
| `--max-capacity` | No | double | -- | Updated max DPUs |
| `--worker-type` | No | string | -- | Updated worker type |
| `--number-of-workers` | No | integer | -- | Updated number of workers |
| `--timeout` | No | integer | -- | Updated timeout |
| `--max-retries` | No | integer | -- | Updated max retries |

**Output Schema:**
```json
{
    "TransformId": "string"
}
```

---

### 12.6 `start-ml-evaluation-task-run`

Starts an evaluation task run for an ML transform.

**Synopsis:**
```bash
aws glue start-ml-evaluation-task-run \
    --transform-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--transform-id` | **Yes** | string | -- | Transform ID |

**Output Schema:**
```json
{
    "TaskRunId": "string"
}
```

---

### 12.7 `start-ml-labeling-set-generation-task-run`

Starts generating a labeling set for an ML transform.

**Synopsis:**
```bash
aws glue start-ml-labeling-set-generation-task-run \
    --transform-id <value> \
    --output-s3-path <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--transform-id` | **Yes** | string | -- | Transform ID |
| `--output-s3-path` | **Yes** | string | -- | S3 output path for the labeling set |

**Output Schema:**
```json
{
    "TaskRunId": "string"
}
```

---

### 12.8 `cancel-ml-task-run`

Cancels a running ML task run.

**Synopsis:**
```bash
aws glue cancel-ml-task-run \
    --transform-id <value> \
    --task-run-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--transform-id` | **Yes** | string | -- | Transform ID |
| `--task-run-id` | **Yes** | string | -- | Task run ID |

**Output Schema:**
```json
{
    "TransformId": "string",
    "TaskRunId": "string",
    "Status": "STARTING|RUNNING|STOPPING|STOPPED|SUCCEEDED|FAILED|TIMEOUT"
}
```

---

### 12.9 `get-ml-task-run`

Retrieves an ML task run.

**Synopsis:**
```bash
aws glue get-ml-task-run \
    --transform-id <value> \
    --task-run-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--transform-id` | **Yes** | string | -- | Transform ID |
| `--task-run-id` | **Yes** | string | -- | Task run ID |

**Output Schema:**
```json
{
    "TransformId": "string",
    "TaskRunId": "string",
    "Status": "STARTING|RUNNING|STOPPING|STOPPED|SUCCEEDED|FAILED|TIMEOUT",
    "LogGroupName": "string",
    "Properties": {
        "TaskType": "EVALUATION|LABELING_SET_GENERATION|IMPORT_LABELS|EXPORT_LABELS|FIND_MATCHES",
        "ImportLabelsTaskRunProperties": {},
        "ExportLabelsTaskRunProperties": {},
        "LabelingSetGenerationTaskRunProperties": {},
        "FindMatchesTaskRunProperties": {},
        "EvaluationMetrics": {}
    },
    "ErrorString": "string",
    "StartedOn": "timestamp",
    "LastModifiedOn": "timestamp",
    "CompletedOn": "timestamp",
    "ExecutionTime": "integer"
}
```

---

### 12.10 `get-ml-task-runs`

Retrieves all ML task runs for a transform. **Paginated operation.**

**Synopsis:**
```bash
aws glue get-ml-task-runs \
    --transform-id <value> \
    [--filter <value>] \
    [--sort <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--transform-id` | **Yes** | string | -- | Transform ID |
| `--filter` | No | structure | -- | Filter criteria (JSON) |
| `--sort` | No | structure | -- | Sort criteria |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "TaskRuns": ["<TaskRun structure>"],
    "NextToken": "string"
}
```

---

### 12.11 `list-ml-transforms`

Lists ML transform IDs. **Paginated operation.**

**Synopsis:**
```bash
aws glue list-ml-transforms \
    [--filter <value>] \
    [--sort <value>] \
    [--tags <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter` | No | structure | -- | Filter criteria (JSON) |
| `--sort` | No | structure | -- | Sort criteria |
| `--tags` | No | map | -- | Filter by tags |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "TransformIds": ["string"],
    "NextToken": "string"
}
```
