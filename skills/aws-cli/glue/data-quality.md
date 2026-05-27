# Data Quality

### 13.1 `create-data-quality-ruleset`

Creates a data quality ruleset.

**Synopsis:**
```bash
aws glue create-data-quality-ruleset \
    --name <value> \
    --ruleset <value> \
    [--description <value>] \
    [--tags <value>] \
    [--target-table <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Ruleset name |
| `--ruleset` | **Yes** | string | -- | DQDL ruleset definition string |
| `--description` | No | string | -- | Description |
| `--tags` | No | map | -- | Tags as JSON |
| `--target-table` | No | structure | -- | Target table. Shorthand: `TableName=string,DatabaseName=string,CatalogId=string` |
| `--client-token` | No | string | -- | Idempotency token |

**Output Schema:**
```json
{
    "Name": "string"
}
```

---

### 13.2 `delete-data-quality-ruleset`

Deletes a data quality ruleset.

**Synopsis:**
```bash
aws glue delete-data-quality-ruleset \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Ruleset name |

No output on success.

---

### 13.3 `get-data-quality-ruleset`

Retrieves a data quality ruleset.

**Synopsis:**
```bash
aws glue get-data-quality-ruleset \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Ruleset name |

**Output Schema:**
```json
{
    "Name": "string",
    "Description": "string",
    "Ruleset": "string",
    "TargetTable": {
        "TableName": "string",
        "DatabaseName": "string",
        "CatalogId": "string"
    },
    "CreatedOn": "timestamp",
    "LastModifiedOn": "timestamp",
    "RecommendationRunId": "string"
}
```

---

### 13.4 `get-data-quality-result`

Retrieves a data quality evaluation result.

**Synopsis:**
```bash
aws glue get-data-quality-result \
    --result-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--result-id` | **Yes** | string | -- | Result ID |

**Output Schema:**
```json
{
    "ResultId": "string",
    "Score": "double",
    "DataSource": {
        "GlueTable": {
            "DatabaseName": "string",
            "TableName": "string",
            "CatalogId": "string"
        }
    },
    "RulesetName": "string",
    "EvaluationContext": "string",
    "StartedOn": "timestamp",
    "CompletedOn": "timestamp",
    "JobName": "string",
    "JobRunId": "string",
    "RulesetEvaluationRunId": "string",
    "RuleResults": [
        {
            "Name": "string",
            "Description": "string",
            "EvaluationMessage": "string",
            "Result": "PASS|FAIL|ERROR",
            "EvaluatedMetrics": {}
        }
    ]
}
```

---

### 13.5 `list-data-quality-rulesets`

Lists data quality rulesets. **Paginated operation.**

**Synopsis:**
```bash
aws glue list-data-quality-rulesets \
    [--filter <value>] \
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
| `--tags` | No | map | -- | Filter by tags |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "Rulesets": [
        {
            "Name": "string",
            "Description": "string",
            "CreatedOn": "timestamp",
            "LastModifiedOn": "timestamp",
            "TargetTable": {},
            "RecommendationRunId": "string",
            "RuleCount": "integer"
        }
    ],
    "NextToken": "string"
}
```

---

### 13.6 `list-data-quality-results`

Lists data quality results. **Paginated operation.**

**Synopsis:**
```bash
aws glue list-data-quality-results \
    [--filter <value>] \
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
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "Results": [
        {
            "ResultId": "string",
            "DataSource": {},
            "JobName": "string",
            "JobRunId": "string",
            "StartedOn": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 13.7 `start-data-quality-ruleset-evaluation-run`

Starts a data quality ruleset evaluation run.

**Synopsis:**
```bash
aws glue start-data-quality-ruleset-evaluation-run \
    --data-source <value> \
    --role <value> \
    --ruleset-names <value> \
    [--number-of-workers <value>] \
    [--timeout <value>] \
    [--client-token <value>] \
    [--additional-run-options <value>] \
    [--additional-data-sources <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-source` | **Yes** | structure | -- | Data source (JSON) |
| `--role` | **Yes** | string | -- | IAM role ARN |
| `--ruleset-names` | **Yes** | list(string) | -- | Ruleset names to evaluate |
| `--number-of-workers` | No | integer | -- | Number of workers |
| `--timeout` | No | integer | -- | Timeout in minutes |
| `--client-token` | No | string | -- | Idempotency token |
| `--additional-run-options` | No | structure | -- | Additional options (JSON) |
| `--additional-data-sources` | No | map | -- | Additional data sources |

**Output Schema:**
```json
{
    "RunId": "string"
}
```

---

### 13.8 `start-data-quality-rule-recommendation-run`

Starts a rule recommendation run to suggest rules for a dataset.

**Synopsis:**
```bash
aws glue start-data-quality-rule-recommendation-run \
    --data-source <value> \
    --role <value> \
    [--number-of-workers <value>] \
    [--timeout <value>] \
    [--created-ruleset-name <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-source` | **Yes** | structure | -- | Data source (JSON) |
| `--role` | **Yes** | string | -- | IAM role ARN |
| `--number-of-workers` | No | integer | -- | Number of workers |
| `--timeout` | No | integer | -- | Timeout in minutes |
| `--created-ruleset-name` | No | string | -- | Name for auto-created ruleset |
| `--client-token` | No | string | -- | Idempotency token |

**Output Schema:**
```json
{
    "RunId": "string"
}
```

---

### 13.9 `cancel-data-quality-ruleset-evaluation-run`

Cancels a data quality evaluation run.

**Synopsis:**
```bash
aws glue cancel-data-quality-ruleset-evaluation-run \
    --run-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--run-id` | **Yes** | string | -- | Run ID to cancel |

No output on success.

---

### 13.10 `get-data-quality-ruleset-evaluation-run`

Retrieves a data quality evaluation run.

**Synopsis:**
```bash
aws glue get-data-quality-ruleset-evaluation-run \
    --run-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--run-id` | **Yes** | string | -- | Run ID |

**Output Schema:**
```json
{
    "RunId": "string",
    "DataSource": {},
    "Role": "string",
    "NumberOfWorkers": "integer",
    "Timeout": "integer",
    "AdditionalRunOptions": {},
    "Status": "STARTING|RUNNING|STOPPING|STOPPED|SUCCEEDED|FAILED|TIMEOUT",
    "ErrorString": "string",
    "StartedOn": "timestamp",
    "LastModifiedOn": "timestamp",
    "CompletedOn": "timestamp",
    "ExecutionTime": "integer",
    "RulesetNames": ["string"],
    "ResultIds": ["string"],
    "AdditionalDataSources": {}
}
```

---

### 13.11 `list-data-quality-ruleset-evaluation-runs`

Lists data quality evaluation runs. **Paginated operation.**

**Synopsis:**
```bash
aws glue list-data-quality-ruleset-evaluation-runs \
    [--filter <value>] \
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
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "Runs": [
        {
            "RunId": "string",
            "Status": "string",
            "StartedOn": "timestamp",
            "DataSource": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 13.12 `batch-get-data-quality-result`

Retrieves multiple data quality results.

**Synopsis:**
```bash
aws glue batch-get-data-quality-result \
    --result-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--result-ids` | **Yes** | list(string) | -- | Result IDs |

**Output Schema:**
```json
{
    "Results": ["<DataQualityResult structure>"],
    "ResultsNotFound": ["string"]
}
```

---

### 13.13 `update-data-quality-ruleset`

Updates a data quality ruleset.

**Synopsis:**
```bash
aws glue update-data-quality-ruleset \
    --name <value> \
    [--description <value>] \
    [--ruleset <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Ruleset name |
| `--description` | No | string | -- | Updated description |
| `--ruleset` | No | string | -- | Updated DQDL ruleset definition |

**Output Schema:**
```json
{
    "Name": "string",
    "Description": "string",
    "Ruleset": "string"
}
```
