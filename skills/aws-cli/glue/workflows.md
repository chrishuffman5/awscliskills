# Workflows

### 9.1 `create-workflow`

Creates a new workflow.

**Synopsis:**
```bash
aws glue create-workflow \
    --name <value> \
    [--description <value>] \
    [--default-run-properties <value>] \
    [--tags <value>] \
    [--max-concurrent-runs <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Workflow name |
| `--description` | No | string | -- | Description |
| `--default-run-properties` | No | map | -- | Default run properties as JSON |
| `--tags` | No | map | -- | Tags as JSON |
| `--max-concurrent-runs` | No | integer | -- | Max concurrent runs |

**Output Schema:**
```json
{
    "Name": "string"
}
```

---

### 9.2 `delete-workflow`

Deletes a workflow.

**Synopsis:**
```bash
aws glue delete-workflow \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Workflow name |

**Output Schema:**
```json
{
    "Name": "string"
}
```

---

### 9.3 `get-workflow`

Retrieves a workflow definition.

**Synopsis:**
```bash
aws glue get-workflow \
    --name <value> \
    [--include-graph | --no-include-graph] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Workflow name |
| `--include-graph` | No | boolean | false | Include workflow graph |

**Output Schema:**
```json
{
    "Workflow": {
        "Name": "string",
        "Description": "string",
        "DefaultRunProperties": {},
        "CreatedOn": "timestamp",
        "LastModifiedOn": "timestamp",
        "LastRun": {
            "Name": "string",
            "WorkflowRunId": "string",
            "PreviousRunId": "string",
            "WorkflowRunProperties": {},
            "StartedOn": "timestamp",
            "CompletedOn": "timestamp",
            "Status": "RUNNING|COMPLETED|STOPPING|STOPPED|ERROR",
            "ErrorMessage": "string",
            "Statistics": {
                "TotalActions": "integer",
                "TimeoutActions": "integer",
                "FailedActions": "integer",
                "StoppedActions": "integer",
                "SucceededActions": "integer",
                "RunningActions": "integer",
                "ErroredActions": "integer",
                "WaitingActions": "integer"
            },
            "Graph": {
                "Nodes": [],
                "Edges": []
            },
            "StartingEventBatchCondition": {}
        },
        "Graph": {},
        "MaxConcurrentRuns": "integer",
        "BlueprintDetails": {}
    }
}
```

---

### 9.4 `get-workflows`

Retrieves all workflows (deprecated -- use `list-workflows`). **Paginated operation.**

**Synopsis:**
```bash
aws glue get-workflows \
    [--include-graph | --no-include-graph] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--include-graph` | No | boolean | false | Include workflow graph |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "Workflows": ["<Workflow structure>"],
    "NextToken": "string"
}
```

---

### 9.5 `update-workflow`

Updates a workflow definition.

**Synopsis:**
```bash
aws glue update-workflow \
    --name <value> \
    [--description <value>] \
    [--default-run-properties <value>] \
    [--max-concurrent-runs <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Workflow name |
| `--description` | No | string | -- | Updated description |
| `--default-run-properties` | No | map | -- | Updated default run properties |
| `--max-concurrent-runs` | No | integer | -- | Updated max concurrent runs |

**Output Schema:**
```json
{
    "Name": "string"
}
```

---

### 9.6 `start-workflow-run`

Starts a new run of a workflow.

**Synopsis:**
```bash
aws glue start-workflow-run \
    --name <value> \
    [--run-properties <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Workflow name |
| `--run-properties` | No | map | -- | Run properties as JSON |

**Output Schema:**
```json
{
    "RunId": "string"
}
```

---

### 9.7 `stop-workflow-run`

Stops a workflow run.

**Synopsis:**
```bash
aws glue stop-workflow-run \
    --name <value> \
    --run-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Workflow name |
| `--run-id` | **Yes** | string | -- | Workflow run ID |

No output on success.

---

### 9.8 `get-workflow-run`

Retrieves metadata for a workflow run.

**Synopsis:**
```bash
aws glue get-workflow-run \
    --name <value> \
    --run-id <value> \
    [--include-graph | --no-include-graph] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Workflow name |
| `--run-id` | **Yes** | string | -- | Workflow run ID |
| `--include-graph` | No | boolean | false | Include run graph |

**Output Schema:**
```json
{
    "Run": {
        "Name": "string",
        "WorkflowRunId": "string",
        "PreviousRunId": "string",
        "WorkflowRunProperties": {},
        "StartedOn": "timestamp",
        "CompletedOn": "timestamp",
        "Status": "RUNNING|COMPLETED|STOPPING|STOPPED|ERROR",
        "ErrorMessage": "string",
        "Statistics": {
            "TotalActions": "integer",
            "TimeoutActions": "integer",
            "FailedActions": "integer",
            "StoppedActions": "integer",
            "SucceededActions": "integer",
            "RunningActions": "integer",
            "ErroredActions": "integer",
            "WaitingActions": "integer"
        },
        "Graph": {}
    }
}
```

---

### 9.9 `get-workflow-runs`

Retrieves all runs of a workflow. **Paginated operation.**

**Synopsis:**
```bash
aws glue get-workflow-runs \
    --name <value> \
    [--include-graph | --no-include-graph] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Workflow name |
| `--include-graph` | No | boolean | false | Include run graph |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "Runs": ["<WorkflowRun structure>"],
    "NextToken": "string"
}
```

---

### 9.10 `get-workflow-run-properties`

Retrieves the run properties for a workflow run.

**Synopsis:**
```bash
aws glue get-workflow-run-properties \
    --name <value> \
    --run-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Workflow name |
| `--run-id` | **Yes** | string | -- | Workflow run ID |

**Output Schema:**
```json
{
    "RunProperties": {}
}
```

---

### 9.11 `put-workflow-run-properties`

Sets run properties for a workflow run.

**Synopsis:**
```bash
aws glue put-workflow-run-properties \
    --name <value> \
    --run-id <value> \
    --run-properties <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Workflow name |
| `--run-id` | **Yes** | string | -- | Workflow run ID |
| `--run-properties` | **Yes** | map | -- | Properties as JSON |

No output on success.

---

### 9.12 `batch-get-workflows`

Returns detailed information for a list of workflows.

**Synopsis:**
```bash
aws glue batch-get-workflows \
    --names <value> \
    [--include-graph | --no-include-graph] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--names` | **Yes** | list(string) | -- | Workflow names |
| `--include-graph` | No | boolean | false | Include workflow graph |

**Output Schema:**
```json
{
    "Workflows": ["<Workflow structure>"],
    "MissingWorkflows": ["string"]
}
```

---

### 9.13 `list-workflows`

Lists workflow names. **Paginated operation.**

**Synopsis:**
```bash
aws glue list-workflows \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "Workflows": ["string"],
    "NextToken": "string"
}
```

---

### 9.14 `resume-workflow-run`

Resumes a failed workflow run from the point of failure.

**Synopsis:**
```bash
aws glue resume-workflow-run \
    --name <value> \
    --run-id <value> \
    --node-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Workflow name |
| `--run-id` | **Yes** | string | -- | Run ID to resume |
| `--node-ids` | **Yes** | list(string) | -- | Node IDs to restart from |

**Output Schema:**
```json
{
    "RunId": "string",
    "NodeIds": ["string"]
}
```
