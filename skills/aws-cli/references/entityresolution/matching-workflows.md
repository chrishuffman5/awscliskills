# Matching Workflows

### 1.1 `create-matching-workflow`

Creates a matching workflow that defines how records from input sources are matched using rules, ML, or a third-party provider.

**Synopsis:**
```bash
aws entityresolution create-matching-workflow \
    --workflow-name <value> \
    --input-source-config <value> \
    --output-source-config <value> \
    --resolution-techniques <value> \
    --role-arn <value> \
    [--description <value>] \
    [--incremental-run-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-name` | **Yes** | string | -- | Workflow name (1-255 chars) |
| `--input-source-config` | **Yes** | list | -- | Input sources (1-20) |
| `--output-source-config` | **Yes** | list | -- | Output configuration (1 item) |
| `--resolution-techniques` | **Yes** | structure | -- | Resolution type and properties |
| `--role-arn` | **Yes** | string | -- | IAM role ARN |
| `--description` | No | string | None | Workflow description (max 255 chars) |
| `--incremental-run-config` | No | structure | None | Incremental run type (`IMMEDIATE`). Not for ML/Provider. |
| `--tags` | No | map | None | Tags (max 200) |

**InputSourceConfig:**
```json
[
    {
        "inputSourceARN": "arn:aws:glue:...:table/db/table",
        "schemaName": "my-schema",
        "applyNormalization": true
    }
]
```

**OutputSourceConfig:**
```json
[
    {
        "outputS3Path": "s3://bucket/output/",
        "output": [
            {"name": "field_name", "hashed": false}
        ],
        "KMSArn": "string",
        "applyNormalization": true
    }
]
```

**ResolutionTechniques:**
```json
{
    "resolutionType": "RULE_MATCHING|ML_MATCHING|PROVIDER",
    "ruleBasedProperties": {
        "rules": [
            {"ruleName": "string", "matchingKeys": ["string"]}
        ],
        "attributeMatchingModel": "ONE_TO_ONE|MANY_TO_MANY",
        "matchPurpose": "IDENTIFIER_GENERATION|INDEXING"
    },
    "providerProperties": {
        "providerServiceArn": "string",
        "providerConfiguration": {},
        "intermediateSourceConfiguration": {
            "intermediateS3Path": "string"
        }
    }
}
```

**Output Schema:**
```json
{
    "workflowName": "string",
    "workflowArn": "string",
    "description": "string",
    "inputSourceConfig": [],
    "outputSourceConfig": [],
    "resolutionTechniques": {},
    "incrementalRunConfig": {"incrementalRunType": "IMMEDIATE"},
    "roleArn": "string"
}
```

---

### 1.2 `get-matching-workflow`

Gets details of a matching workflow.

**Synopsis:**
```bash
aws entityresolution get-matching-workflow \
    --workflow-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-name` | **Yes** | string | -- | Name of the workflow |

**Output Schema:**
```json
{
    "workflowName": "string",
    "workflowArn": "string",
    "description": "string",
    "inputSourceConfig": [],
    "outputSourceConfig": [],
    "resolutionTechniques": {},
    "incrementalRunConfig": {},
    "roleArn": "string",
    "createdAt": "timestamp",
    "updatedAt": "timestamp",
    "tags": {"string": "string"}
}
```

---

### 1.3 `list-matching-workflows`

Lists matching workflows. **Paginated operation.**

**Synopsis:**
```bash
aws entityresolution list-matching-workflows \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page (1-25) |

**Output Schema:**
```json
{
    "workflowSummaries": [
        {
            "workflowName": "string",
            "workflowArn": "string",
            "createdAt": "timestamp",
            "updatedAt": "timestamp",
            "resolutionType": "RULE_MATCHING|ML_MATCHING|PROVIDER"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.4 `update-matching-workflow`

Updates a matching workflow configuration.

**Synopsis:**
```bash
aws entityresolution update-matching-workflow \
    --workflow-name <value> \
    --input-source-config <value> \
    --output-source-config <value> \
    --resolution-techniques <value> \
    --role-arn <value> \
    [--description <value>] \
    [--incremental-run-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-name` | **Yes** | string | -- | Name of the workflow |
| `--input-source-config` | **Yes** | list | -- | Updated input sources |
| `--output-source-config` | **Yes** | list | -- | Updated output configuration |
| `--resolution-techniques` | **Yes** | structure | -- | Updated resolution techniques |
| `--role-arn` | **Yes** | string | -- | Updated IAM role ARN |
| `--description` | No | string | None | Updated description |
| `--incremental-run-config` | No | structure | None | Updated incremental config |

**Output Schema:**
```json
{
    "workflowName": "string",
    "description": "string",
    "inputSourceConfig": [],
    "outputSourceConfig": [],
    "resolutionTechniques": {},
    "incrementalRunConfig": {},
    "roleArn": "string"
}
```

---

### 1.5 `delete-matching-workflow`

Deletes a matching workflow.

**Synopsis:**
```bash
aws entityresolution delete-matching-workflow \
    --workflow-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-name` | **Yes** | string | -- | Name of the workflow to delete |

**Output Schema:**
```json
{
    "message": "string"
}
```

---

### 1.6 `start-matching-job`

Starts a matching job for the specified workflow.

**Synopsis:**
```bash
aws entityresolution start-matching-job \
    --workflow-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-name` | **Yes** | string | -- | Name of the workflow |

**Output Schema:**
```json
{
    "jobId": "string"
}
```

---

### 1.7 `get-matching-job`

Gets the status, metrics, and errors for a matching job.

**Synopsis:**
```bash
aws entityresolution get-matching-job \
    --workflow-name <value> \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-name` | **Yes** | string | -- | Name of the workflow |
| `--job-id` | **Yes** | string | -- | The job ID |

**Output Schema:**
```json
{
    "jobId": "string",
    "status": "RUNNING|SUCCEEDED|FAILED|QUEUED",
    "startTime": "timestamp",
    "endTime": "timestamp",
    "metrics": {
        "inputRecords": "integer",
        "totalRecordsProcessed": "integer",
        "recordsNotProcessed": "integer",
        "deleteRecordsProcessed": "integer",
        "matchIDs": "integer"
    },
    "errorDetails": {
        "errorMessage": "string"
    },
    "outputSourceConfig": [
        {
            "roleArn": "string",
            "outputS3Path": "string",
            "KMSArn": "string"
        }
    ]
}
```

---

### 1.8 `list-matching-jobs`

Lists matching jobs for a workflow. **Paginated operation.**

**Synopsis:**
```bash
aws entityresolution list-matching-jobs \
    --workflow-name <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-name` | **Yes** | string | -- | Name of the workflow |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page (1-25) |

**Output Schema:**
```json
{
    "jobs": [
        {
            "jobId": "string",
            "status": "RUNNING|SUCCEEDED|FAILED|QUEUED",
            "startTime": "timestamp",
            "endTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.9 `get-match-id`

Gets the match ID for a single record against a matching workflow.

**Synopsis:**
```bash
aws entityresolution get-match-id \
    --workflow-name <value> \
    --record <value> \
    [--apply-normalization | --no-apply-normalization] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-name` | **Yes** | string | -- | Name of the workflow |
| `--record` | **Yes** | map | -- | Key-value pairs of the record to match |
| `--apply-normalization` | No | boolean | None | Normalize attributes before matching |

**Output Schema:**
```json
{
    "matchId": "string",
    "matchRule": "string"
}
```

---

### 1.10 `generate-match-id`

Generates a match ID for a record with processing type options (consistent, eventual, or no-lookup).

**Synopsis:**
```bash
aws entityresolution generate-match-id \
    --workflow-name <value> \
    --records <value> \
    [--processing-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-name` | **Yes** | string | -- | Name of the workflow |
| `--records` | **Yes** | list | -- | Records to match (max 1) |
| `--processing-type` | No | string | `CONSISTENT` | `CONSISTENT`, `EVENTUAL`, or `EVENTUAL_NO_LOOKUP` |

**Record Structure:**
```json
[
    {
        "inputSourceARN": "string",
        "uniqueId": "string",
        "recordAttributeMap": {"key": "value"}
    }
]
```

**Output Schema:**
```json
{
    "matchGroups": [
        {
            "records": [
                {"inputSourceARN": "string", "recordId": "string"}
            ],
            "matchId": "string",
            "matchRule": "string"
        }
    ],
    "failedRecords": [
        {
            "inputSourceARN": "string",
            "uniqueId": "string",
            "errorMessage": "string"
        }
    ]
}
```

---

### 1.11 `batch-delete-unique-id`

Batch deletes unique IDs from a matching workflow.

**Synopsis:**
```bash
aws entityresolution batch-delete-unique-id \
    --workflow-name <value> \
    --unique-ids <value> \
    [--input-source <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-name` | **Yes** | string | -- | Name of the workflow |
| `--unique-ids` | **Yes** | list(string) | -- | Unique IDs to delete |
| `--input-source` | No | string | None | Glue table ARN for the input source |

**Output Schema:**
```json
{
    "status": "COMPLETED|ACCEPTED",
    "deleted": [{"uniqueId": "string"}],
    "disconnectedUniqueIds": ["string"],
    "errors": [
        {
            "uniqueId": "string",
            "errorType": "SERVICE_ERROR|VALIDATION_ERROR"
        }
    ]
}
```
