# Orchestrator Steps & Step Groups

These commands use the `migrationhuborchestrator` service namespace. They manage individual steps and step groups within migration workflows.

## Workflow Steps

### 12.1 `create-workflow-step`

Creates a step within a workflow step group.

**Synopsis:**
```bash
aws migrationhuborchestrator create-workflow-step \
    --name <value> \
    --step-group-id <value> \
    --workflow-id <value> \
    --step-action-type <value> \
    [--description <value>] \
    [--workflow-step-automation-configuration <value>] \
    [--step-target <value>] \
    [--outputs <value>] \
    [--previous <value>] \
    [--next <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Step name (1-100 chars) |
| `--step-group-id` | **Yes** | string | -- | Step group ID |
| `--workflow-id` | **Yes** | string | -- | Workflow ID |
| `--step-action-type` | **Yes** | string | -- | `MANUAL` or `AUTOMATED` |
| `--description` | No | string | None | Description (max 500 chars) |
| `--workflow-step-automation-configuration` | No | structure | None | Automation config (see below) |
| `--step-target` | No | list(string) | None | Target servers |
| `--outputs` | No | list(structure) | None | Expected outputs (see below) |
| `--previous` | No | list(string) | None | Previous step IDs |
| `--next` | No | list(string) | None | Next step IDs |

**Automation Configuration:**
```json
{
    "scriptLocationS3Bucket": "string",
    "scriptLocationS3Key": {
        "linux": "string",
        "windows": "string"
    },
    "command": {
        "linux": "string",
        "windows": "string"
    },
    "runEnvironment": "AWS|ONPREMISE",
    "targetType": "SINGLE|ALL|NONE"
}
```

**Outputs Structure:**
```json
[
    {
        "name": "string",
        "dataType": "STRING|INTEGER|STRINGLIST|STRINGMAP",
        "required": true|false,
        "value": {
            "integerValue": 123,
            "stringValue": "string",
            "listOfStringValue": ["string"]
        }
    }
]
```

**Output Schema:**
```json
{
    "id": "string",
    "stepGroupId": "string",
    "workflowId": "string",
    "name": "string"
}
```

---

### 12.2 `get-workflow-step`

Gets details of a workflow step.

**Synopsis:**
```bash
aws migrationhuborchestrator get-workflow-step \
    --workflow-id <value> \
    --step-group-id <value> \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-id` | **Yes** | string | -- | Workflow ID |
| `--step-group-id` | **Yes** | string | -- | Step group ID |
| `--id` | **Yes** | string | -- | Step ID |

**Output Schema:**
```json
{
    "name": "string",
    "stepGroupId": "string",
    "workflowId": "string",
    "stepId": "string",
    "description": "string",
    "stepActionType": "MANUAL|AUTOMATED",
    "owner": "AWS_MANAGED|CUSTOM",
    "workflowStepAutomationConfiguration": {
        "scriptLocationS3Bucket": "string",
        "scriptLocationS3Key": {"linux": "string", "windows": "string"},
        "command": {"linux": "string", "windows": "string"},
        "runEnvironment": "AWS|ONPREMISE",
        "targetType": "SINGLE|ALL|NONE"
    },
    "stepTarget": ["string"],
    "outputs": [
        {
            "name": "string",
            "dataType": "STRING|INTEGER|STRINGLIST|STRINGMAP",
            "required": true|false,
            "value": {}
        }
    ],
    "previous": ["string"],
    "next": ["string"],
    "status": "AWAITING_DEPENDENCIES|SKIPPED|READY|IN_PROGRESS|COMPLETED|FAILED|PAUSED|USER_ATTENTION_REQUIRED",
    "statusMessage": "string",
    "scriptOutputLocation": "string",
    "creationTime": "timestamp",
    "lastStartTime": "timestamp",
    "endTime": "timestamp",
    "noOfSrvCompleted": "integer",
    "noOfSrvFailed": "integer",
    "totalNoOfSrv": "integer"
}
```

---

### 12.3 `list-workflow-steps`

Lists steps in a workflow step group. **Paginated.**

**Synopsis:**
```bash
aws migrationhuborchestrator list-workflow-steps \
    --workflow-id <value> \
    --step-group-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-id` | **Yes** | string | -- | Workflow ID |
| `--step-group-id` | **Yes** | string | -- | Step group ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "workflowStepsSummary": [
        {
            "stepId": "string",
            "name": "string",
            "stepActionType": "MANUAL|AUTOMATED",
            "owner": "AWS_MANAGED|CUSTOM",
            "previous": ["string"],
            "next": ["string"],
            "status": "AWAITING_DEPENDENCIES|SKIPPED|READY|IN_PROGRESS|COMPLETED|FAILED|PAUSED|USER_ATTENTION_REQUIRED",
            "statusMessage": "string",
            "noOfSrvCompleted": "integer",
            "noOfSrvFailed": "integer",
            "totalNoOfSrv": "integer",
            "description": "string",
            "scriptLocation": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 12.4 `update-workflow-step`

Updates a workflow step.

**Synopsis:**
```bash
aws migrationhuborchestrator update-workflow-step \
    --id <value> \
    --step-group-id <value> \
    --workflow-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--step-action-type <value>] \
    [--workflow-step-automation-configuration <value>] \
    [--step-target <value>] \
    [--outputs <value>] \
    [--previous <value>] \
    [--next <value>] \
    [--status <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Step ID |
| `--step-group-id` | **Yes** | string | -- | Step group ID |
| `--workflow-id` | **Yes** | string | -- | Workflow ID |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |
| `--step-action-type` | No | string | None | `MANUAL` or `AUTOMATED` |
| `--workflow-step-automation-configuration` | No | structure | None | Updated automation config |
| `--step-target` | No | list(string) | None | Updated targets |
| `--outputs` | No | list(structure) | None | Updated outputs |
| `--previous` | No | list(string) | None | Updated previous steps |
| `--next` | No | list(string) | None | Updated next steps |
| `--status` | No | string | None | Updated status |

**Output Schema:**
```json
{
    "id": "string",
    "stepGroupId": "string",
    "workflowId": "string",
    "name": "string"
}
```

---

### 12.5 `delete-workflow-step`

Deletes a workflow step.

**Synopsis:**
```bash
aws migrationhuborchestrator delete-workflow-step \
    --id <value> \
    --step-group-id <value> \
    --workflow-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Step ID |
| `--step-group-id` | **Yes** | string | -- | Step group ID |
| `--workflow-id` | **Yes** | string | -- | Workflow ID |

**Output:** None

---

### 12.6 `retry-workflow-step`

Retries a failed workflow step.

**Synopsis:**
```bash
aws migrationhuborchestrator retry-workflow-step \
    --workflow-id <value> \
    --step-group-id <value> \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-id` | **Yes** | string | -- | Workflow ID |
| `--step-group-id` | **Yes** | string | -- | Step group ID |
| `--id` | **Yes** | string | -- | Step ID |

**Output Schema:**
```json
{
    "id": "string",
    "stepGroupId": "string",
    "workflowId": "string",
    "status": "string"
}
```

---

## Workflow Step Groups

### 12.7 `create-workflow-step-group`

Creates a step group within a workflow.

**Synopsis:**
```bash
aws migrationhuborchestrator create-workflow-step-group \
    --workflow-id <value> \
    --name <value> \
    [--description <value>] \
    [--next <value>] \
    [--previous <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-id` | **Yes** | string | -- | Workflow ID |
| `--name` | **Yes** | string | -- | Step group name (1-100 chars) |
| `--description` | No | string | None | Description (max 500 chars) |
| `--next` | No | list(string) | None | Next step group IDs |
| `--previous` | No | list(string) | None | Previous step group IDs |

**Output Schema:**
```json
{
    "workflowId": "string",
    "name": "string",
    "id": "string",
    "description": "string",
    "tools": [
        {"name": "string", "url": "string"}
    ],
    "next": ["string"],
    "previous": ["string"],
    "creationTime": "timestamp"
}
```

---

### 12.8 `get-workflow-step-group`

Gets details of a workflow step group.

**Synopsis:**
```bash
aws migrationhuborchestrator get-workflow-step-group \
    --id <value> \
    --workflow-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Step group ID |
| `--workflow-id` | **Yes** | string | -- | Workflow ID |

**Output Schema:** Same as create-workflow-step-group plus `status`, `owner`, `lastModifiedTime`, `endTime`, `totalSteps`, `completedSteps`.

---

### 12.9 `list-workflow-step-groups`

Lists step groups in a workflow. **Paginated.**

**Synopsis:**
```bash
aws migrationhuborchestrator list-workflow-step-groups \
    --workflow-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-id` | **Yes** | string | -- | Workflow ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "workflowStepGroupsSummary": [
        {
            "id": "string",
            "name": "string",
            "owner": "AWS_MANAGED|CUSTOM",
            "status": "AWAITING_DEPENDENCIES|READY|IN_PROGRESS|COMPLETED|FAILED|PAUSED|PAUSING|USER_ATTENTION_REQUIRED",
            "previous": ["string"],
            "next": ["string"]
        }
    ],
    "nextToken": "string"
}
```

---

### 12.10 `update-workflow-step-group`

Updates a workflow step group.

**Synopsis:**
```bash
aws migrationhuborchestrator update-workflow-step-group \
    --workflow-id <value> \
    --id <value> \
    [--name <value>] \
    [--description <value>] \
    [--next <value>] \
    [--previous <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-id` | **Yes** | string | -- | Workflow ID |
| `--id` | **Yes** | string | -- | Step group ID |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |
| `--next` | No | list(string) | None | Updated next step groups |
| `--previous` | No | list(string) | None | Updated previous step groups |

**Output Schema:** Same as create-workflow-step-group plus `status`, `lastModifiedTime`, `tools`.

---

### 12.11 `delete-workflow-step-group`

Deletes a workflow step group.

**Synopsis:**
```bash
aws migrationhuborchestrator delete-workflow-step-group \
    --workflow-id <value> \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-id` | **Yes** | string | -- | Workflow ID |
| `--id` | **Yes** | string | -- | Step group ID |

**Output:** None
