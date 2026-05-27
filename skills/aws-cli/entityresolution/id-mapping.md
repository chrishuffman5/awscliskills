# ID Mapping

### 2.1 `create-id-mapping-workflow`

Creates an ID mapping workflow that maps identifiers across different data sources using rules or a provider.

**Synopsis:**
```bash
aws entityresolution create-id-mapping-workflow \
    --workflow-name <value> \
    --input-source-config <value> \
    --id-mapping-techniques <value> \
    [--description <value>] \
    [--output-source-config <value>] \
    [--role-arn <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-name` | **Yes** | string | -- | Workflow name (1-255 chars) |
| `--input-source-config` | **Yes** | list | -- | Input sources with SOURCE/TARGET types (1-20) |
| `--id-mapping-techniques` | **Yes** | structure | -- | ID mapping technique: `PROVIDER` or `RULE_BASED` |
| `--description` | No | string | None | Workflow description (max 255 chars) |
| `--output-source-config` | No | list | None | Output S3 configuration (max 1) |
| `--role-arn` | No | string | None | IAM role ARN |
| `--tags` | No | map | None | Tags (max 200) |

**InputSourceConfig:**
```json
[
    {
        "inputSourceARN": "arn:aws:glue:...:table/db/table",
        "schemaName": "my-schema",
        "type": "SOURCE|TARGET"
    }
]
```

**IdMappingTechniques:**
```json
{
    "idMappingType": "PROVIDER|RULE_BASED",
    "ruleBasedProperties": {
        "rules": [{"ruleName": "string", "matchingKeys": ["string"]}],
        "ruleDefinitionType": "SOURCE|TARGET",
        "attributeMatchingModel": "ONE_TO_ONE|MANY_TO_MANY",
        "recordMatchingModel": "ONE_SOURCE_TO_ONE_TARGET|MANY_SOURCE_TO_ONE_TARGET"
    },
    "providerProperties": {
        "providerServiceArn": "string",
        "providerConfiguration": {},
        "intermediateSourceConfiguration": {"intermediateS3Path": "string"}
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
    "idMappingTechniques": {},
    "roleArn": "string"
}
```

---

### 2.2 `get-id-mapping-workflow`

Gets details of an ID mapping workflow.

**Synopsis:**
```bash
aws entityresolution get-id-mapping-workflow \
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
    "idMappingTechniques": {},
    "roleArn": "string",
    "createdAt": "timestamp",
    "updatedAt": "timestamp",
    "tags": {"string": "string"}
}
```

---

### 2.3 `list-id-mapping-workflows`

Lists ID mapping workflows. **Paginated operation.**

**Synopsis:**
```bash
aws entityresolution list-id-mapping-workflows \
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
            "updatedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.4 `update-id-mapping-workflow`

Updates an ID mapping workflow.

**Synopsis:**
```bash
aws entityresolution update-id-mapping-workflow \
    --workflow-name <value> \
    --input-source-config <value> \
    --id-mapping-techniques <value> \
    [--description <value>] \
    [--output-source-config <value>] \
    [--role-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-name` | **Yes** | string | -- | Name of the workflow |
| `--input-source-config` | **Yes** | list | -- | Updated input sources |
| `--id-mapping-techniques` | **Yes** | structure | -- | Updated mapping techniques |
| `--description` | No | string | None | Updated description |
| `--output-source-config` | No | list | None | Updated output configuration |
| `--role-arn` | No | string | None | Updated IAM role ARN |

**Output Schema:**
```json
{
    "workflowName": "string",
    "workflowArn": "string",
    "description": "string",
    "inputSourceConfig": [],
    "outputSourceConfig": [],
    "idMappingTechniques": {},
    "roleArn": "string"
}
```

---

### 2.5 `delete-id-mapping-workflow`

Deletes an ID mapping workflow.

**Synopsis:**
```bash
aws entityresolution delete-id-mapping-workflow \
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

### 2.6 `start-id-mapping-job`

Starts an ID mapping job for the specified workflow.

**Synopsis:**
```bash
aws entityresolution start-id-mapping-job \
    --workflow-name <value> \
    [--output-source-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-name` | **Yes** | string | -- | Name of the workflow |
| `--output-source-config` | No | list | None | Override output configuration |

**Output Schema:**
```json
{
    "jobId": "string"
}
```

---

### 2.7 `get-id-mapping-job`

Gets the status and metrics for an ID mapping job.

**Synopsis:**
```bash
aws entityresolution get-id-mapping-job \
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
        "totalMappedRecords": "integer",
        "totalMappedSourceRecords": "integer",
        "totalMappedTargetRecords": "integer"
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

### 2.8 `list-id-mapping-jobs`

Lists ID mapping jobs for a workflow. **Paginated operation.**

**Synopsis:**
```bash
aws entityresolution list-id-mapping-jobs \
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
