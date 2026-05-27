# Orchestrator Workflows

These commands use the `migrationhuborchestrator` service namespace. They manage migration workflows that coordinate multi-step migration processes.

### 11.1 `create-workflow`

Creates a migration workflow from a template.

**Synopsis:**
```bash
aws migrationhuborchestrator create-workflow \
    --name <value> \
    --template-id <value> \
    --input-parameters <value> \
    [--description <value>] \
    [--application-configuration-id <value>] \
    [--step-targets <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Workflow name (1-100 chars) |
| `--template-id` | **Yes** | string | -- | Template ID |
| `--input-parameters` | **Yes** | map | -- | Input parameters (tagged union values) |
| `--description` | No | string | None | Description (max 500 chars) |
| `--application-configuration-id` | No | string | None | ADS application configuration ID |
| `--step-targets` | No | list(string) | None | Target servers |
| `--tags` | No | map | None | Tags |

**Input Parameters Value Types (tagged union):**
```json
{
    "paramName": {
        "stringValue": "string",
        "integerValue": 123,
        "listOfStringsValue": ["string"],
        "mapOfStringValue": {"key": "value"}
    }
}
```

**Output Schema:**
```json
{
    "id": "string",
    "arn": "string",
    "name": "string",
    "description": "string",
    "templateId": "string",
    "adsApplicationConfigurationId": "string",
    "workflowInputs": {},
    "stepTargets": ["string"],
    "status": "CREATING|NOT_STARTED|CREATION_FAILED|STARTING|IN_PROGRESS|WORKFLOW_FAILED|PAUSED|PAUSING|PAUSING_FAILED|USER_ATTENTION_REQUIRED|DELETING|DELETION_FAILED|DELETED|COMPLETED",
    "creationTime": "timestamp",
    "tags": {"key": "value"}
}
```

---

### 11.2 `get-workflow`

Gets details of a migration workflow.

**Synopsis:**
```bash
aws migrationhuborchestrator get-workflow \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Workflow ID |

**Output Schema:**
```json
{
    "id": "string",
    "arn": "string",
    "name": "string",
    "description": "string",
    "templateId": "string",
    "adsApplicationConfigurationId": "string",
    "adsApplicationName": "string",
    "status": "CREATING|NOT_STARTED|CREATION_FAILED|STARTING|IN_PROGRESS|WORKFLOW_FAILED|PAUSED|PAUSING|PAUSING_FAILED|USER_ATTENTION_REQUIRED|DELETING|DELETION_FAILED|DELETED|COMPLETED",
    "statusMessage": "string",
    "creationTime": "timestamp",
    "lastStartTime": "timestamp",
    "lastStopTime": "timestamp",
    "lastModifiedTime": "timestamp",
    "endTime": "timestamp",
    "tools": [
        {"name": "string", "url": "string"}
    ],
    "totalSteps": "integer",
    "completedSteps": "integer",
    "workflowInputs": {},
    "tags": {"key": "value"},
    "workflowBucket": "string"
}
```

---

### 11.3 `list-workflows`

Lists migration workflows. **Paginated.**

**Synopsis:**
```bash
aws migrationhuborchestrator list-workflows \
    [--template-id <value>] \
    [--ads-application-configuration-name <value>] \
    [--status <value>] \
    [--name <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-id` | No | string | None | Filter by template ID |
| `--ads-application-configuration-name` | No | string | None | Filter by ADS application name |
| `--status` | No | string | None | Filter by status |
| `--name` | No | string | None | Filter by workflow name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "migrationWorkflowSummary": [
        {
            "id": "string",
            "name": "string",
            "templateId": "string",
            "adsApplicationConfigurationName": "string",
            "status": "string",
            "creationTime": "timestamp",
            "endTime": "timestamp",
            "statusMessage": "string",
            "completedSteps": "integer",
            "totalSteps": "integer"
        }
    ],
    "nextToken": "string"
}
```

---

### 11.4 `update-workflow`

Updates a migration workflow.

**Synopsis:**
```bash
aws migrationhuborchestrator update-workflow \
    --id <value> \
    [--name <value>] \
    [--description <value>] \
    [--input-parameters <value>] \
    [--step-targets <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Workflow ID |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |
| `--input-parameters` | No | map | None | Updated input parameters |
| `--step-targets` | No | list(string) | None | Updated step targets |

**Output Schema:** Same as get-workflow.

---

### 11.5 `delete-workflow`

Deletes a migration workflow.

**Synopsis:**
```bash
aws migrationhuborchestrator delete-workflow \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Workflow ID |

**Output Schema:**
```json
{
    "id": "string",
    "arn": "string",
    "status": "string"
}
```

---

### 11.6 `start-workflow`

Starts a migration workflow.

**Synopsis:**
```bash
aws migrationhuborchestrator start-workflow \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Workflow ID |

**Output Schema:**
```json
{
    "id": "string",
    "arn": "string",
    "status": "string",
    "statusMessage": "string",
    "lastStartTime": "timestamp"
}
```

---

### 11.7 `stop-workflow`

Stops a running migration workflow.

**Synopsis:**
```bash
aws migrationhuborchestrator stop-workflow \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Workflow ID |

**Output Schema:**
```json
{
    "id": "string",
    "arn": "string",
    "status": "string",
    "statusMessage": "string",
    "lastStopTime": "timestamp"
}
```
