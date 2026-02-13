# Test Sets

### 8.1 `start-test-execution`

Starts running a test set against a bot.

**Synopsis:**
```bash
aws lexv2-models start-test-execution \
    --test-set-id <value> \
    --target <value> \
    --api-mode <value> \
    [--test-execution-modality <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--test-set-id` | **Yes** | string | -- | Test set identifier (10 chars) |
| `--target` | **Yes** | structure | -- | Bot alias target for the test |
| `--api-mode` | **Yes** | string | -- | API mode: `Streaming` or `NonStreaming` |
| `--test-execution-modality` | No | string | None | Modality: `Text` or `Audio` |

**Target Structure:**
```json
{
    "botAliasTarget": {
        "botId": "string",
        "botAliasId": "string",
        "localeId": "string"
    }
}
```

**Output Schema:**
```json
{
    "testExecutionId": "string",
    "creationDateTime": "timestamp",
    "testSetId": "string",
    "target": {},
    "apiMode": "Streaming|NonStreaming",
    "testExecutionModality": "Text|Audio"
}
```

---

### 8.2 `describe-test-execution`

Gets metadata for a test execution.

**Synopsis:**
```bash
aws lexv2-models describe-test-execution \
    --test-execution-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--test-execution-id` | **Yes** | string | -- | Test execution identifier (10 chars) |

**Output Schema:**
```json
{
    "testExecutionId": "string",
    "testSetId": "string",
    "testSetName": "string",
    "target": {},
    "apiMode": "Streaming|NonStreaming",
    "testExecutionModality": "Text|Audio",
    "testExecutionStatus": "Pending|Waiting|InProgress|Completed|Failed|Stopping|Stopped",
    "failureReasons": ["string"],
    "creationDateTime": "timestamp",
    "lastUpdatedDateTime": "timestamp"
}
```

---

### 8.3 `list-test-executions`

Lists all test executions.

**Synopsis:**
```bash
aws lexv2-models list-test-executions \
    [--sort-by <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sort-by` | No | structure | None | Sort field and order |
| `--max-results` | No | integer | None | Maximum results (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "testExecutions": [
        {
            "testExecutionId": "string",
            "testSetId": "string",
            "testSetName": "string",
            "target": {},
            "apiMode": "string",
            "testExecutionModality": "string",
            "testExecutionStatus": "string",
            "creationDateTime": "timestamp",
            "lastUpdatedDateTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 8.4 `list-test-execution-result-items`

Lists result items for a test execution.

**Synopsis:**
```bash
aws lexv2-models list-test-execution-result-items \
    --test-execution-id <value> \
    --result-filter-by <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--test-execution-id` | **Yes** | string | -- | Test execution identifier |
| `--result-filter-by` | **Yes** | structure | -- | Filter for result items |
| `--max-results` | No | integer | None | Maximum results (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "testExecutionResults": {
        "overallTestResults": {},
        "conversationLevelTestResults": {},
        "intentClassificationTestResults": {},
        "intentLevelSlotResolutionTestResults": {},
        "utteranceLevelTestResults": {}
    },
    "nextToken": "string"
}
```

---

### 8.5 `get-test-execution-artifacts-url`

Gets a URL for downloading test execution artifacts.

**Synopsis:**
```bash
aws lexv2-models get-test-execution-artifacts-url \
    --test-execution-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--test-execution-id` | **Yes** | string | -- | Test execution identifier |

**Output Schema:**
```json
{
    "testExecutionId": "string",
    "downloadArtifactsUrl": "string"
}
```

---

### 8.6 `describe-test-set`

Gets metadata for a test set.

**Synopsis:**
```bash
aws lexv2-models describe-test-set \
    --test-set-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--test-set-id` | **Yes** | string | -- | Test set identifier (10 chars) |

**Output Schema:**
```json
{
    "testSetId": "string",
    "testSetName": "string",
    "description": "string",
    "modality": "Text|Audio",
    "status": "Importing|PendingAnnotation|Deleting|ValidationError|Ready",
    "roleArn": "string",
    "numTurns": "integer",
    "storageLocation": {
        "s3BucketName": "string",
        "s3Path": "string",
        "kmsKeyArn": "string"
    },
    "creationDateTime": "timestamp",
    "lastUpdatedDateTime": "timestamp"
}
```

---

### 8.7 `list-test-sets`

Lists all test sets.

**Synopsis:**
```bash
aws lexv2-models list-test-sets \
    [--sort-by <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sort-by` | No | structure | None | Sort field and order |
| `--max-results` | No | integer | None | Maximum results (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "testSets": [
        {
            "testSetId": "string",
            "testSetName": "string",
            "description": "string",
            "modality": "Text|Audio",
            "status": "string",
            "roleArn": "string",
            "numTurns": "integer",
            "storageLocation": {},
            "creationDateTime": "timestamp",
            "lastUpdatedDateTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 8.8 `delete-test-set`

Deletes a test set.

**Synopsis:**
```bash
aws lexv2-models delete-test-set \
    --test-set-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--test-set-id` | **Yes** | string | -- | Test set identifier (10 chars) |

**Output:** None

---

### 8.9 `list-test-set-records`

Lists records in a test set.

**Synopsis:**
```bash
aws lexv2-models list-test-set-records \
    --test-set-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--test-set-id` | **Yes** | string | -- | Test set identifier |
| `--max-results` | No | integer | None | Maximum records (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "testSetRecords": [
        {
            "recordNumber": "integer",
            "conversationId": "string",
            "turnNumber": "integer",
            "turnSpecification": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 8.10 `start-test-set-generation`

Starts generating a test set from a bot's conversation logs.

**Synopsis:**
```bash
aws lexv2-models start-test-set-generation \
    --test-set-name <value> \
    --storage-location <value> \
    --generation-data-source <value> \
    --role-arn <value> \
    [--description <value>] \
    [--test-set-tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--test-set-name` | **Yes** | string | -- | Name for the test set (1-100 chars) |
| `--storage-location` | **Yes** | structure | -- | S3 location for storing the test set |
| `--generation-data-source` | **Yes** | structure | -- | Data source for generating the test set |
| `--role-arn` | **Yes** | string | -- | IAM role ARN |
| `--description` | No | string | None | Description (0-2000 chars) |
| `--test-set-tags` | No | map | None | Tags (max 200) |

**Output Schema:**
```json
{
    "testSetGenerationId": "string",
    "creationDateTime": "timestamp",
    "testSetGenerationStatus": "Generating|Ready|Failed|Pending",
    "testSetName": "string",
    "description": "string",
    "storageLocation": {},
    "generationDataSource": {},
    "roleArn": "string",
    "testSetTags": {}
}
```

---

### 8.11 `describe-test-set-generation`

Gets details about a test set generation.

**Synopsis:**
```bash
aws lexv2-models describe-test-set-generation \
    --test-set-generation-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--test-set-generation-id` | **Yes** | string | -- | Test set generation identifier (10 chars) |

**Output Schema:**
```json
{
    "testSetGenerationId": "string",
    "testSetGenerationStatus": "Generating|Ready|Failed|Pending",
    "failureReasons": ["string"],
    "testSetId": "string",
    "testSetName": "string",
    "description": "string",
    "storageLocation": {},
    "generationDataSource": {},
    "roleArn": "string",
    "creationDateTime": "timestamp",
    "lastUpdatedDateTime": "timestamp"
}
```

---

### 8.12 `create-test-set-discrepancy-report`

Creates a discrepancy report comparing test set results.

**Synopsis:**
```bash
aws lexv2-models create-test-set-discrepancy-report \
    --test-set-id <value> \
    --target <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--test-set-id` | **Yes** | string | -- | Test set identifier |
| `--target` | **Yes** | structure | -- | Bot alias target for comparison |

**Output Schema:**
```json
{
    "testSetDiscrepancyReportId": "string",
    "creationDateTime": "timestamp",
    "testSetId": "string",
    "target": {}
}
```

---

### 8.13 `describe-test-set-discrepancy-report`

Gets details about a test set discrepancy report.

**Synopsis:**
```bash
aws lexv2-models describe-test-set-discrepancy-report \
    --test-set-discrepancy-report-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--test-set-discrepancy-report-id` | **Yes** | string | -- | Report identifier (10 chars) |

**Output Schema:**
```json
{
    "testSetDiscrepancyReportId": "string",
    "testSetId": "string",
    "creationDateTime": "timestamp",
    "target": {},
    "testSetDiscrepancyReportStatus": "InProgress|Completed|Failed",
    "lastUpdatedDataDateTime": "timestamp",
    "testSetDiscrepancyTopErrors": {},
    "testSetDiscrepancyRawOutputUrl": "string",
    "failureReasons": ["string"]
}
```
