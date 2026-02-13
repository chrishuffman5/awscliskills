# Workflows

### 10.1 `create-workflow`

Creates a new workflow resource.

**Synopsis:**
```bash
aws imagebuilder create-workflow \
    --name <value> \
    --semantic-version <value> \
    --type <value> \
    [--description <value>] \
    [--change-description <value>] \
    [--data <value>] \
    [--uri <value>] \
    [--kms-key-id <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the workflow |
| `--semantic-version` | **Yes** | string | -- | Semantic version (e.g., `1.0.0`) |
| `--type` | **Yes** | string | -- | Workflow type: `BUILD`, `TEST`, or `DISTRIBUTION` |
| `--description` | No | string | -- | Description |
| `--change-description` | No | string | -- | Description of changes |
| `--data` | No | string | -- | Inline workflow YAML document |
| `--uri` | No | string | -- | S3 URI of the workflow document |
| `--kms-key-id` | No | string | -- | KMS key for encryption |
| `--tags` | No | map | None | Tags |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Output Schema:**
```json
{
    "clientToken": "string",
    "workflowBuildVersionArn": "string"
}
```

---

### 10.2 `get-workflow`

Gets a workflow resource.

**Synopsis:**
```bash
aws imagebuilder get-workflow \
    --workflow-build-version-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-build-version-arn` | **Yes** | string | -- | ARN of the workflow build version |

**Output Schema:**
```json
{
    "workflow": {
        "arn": "string",
        "name": "string",
        "version": "string",
        "description": "string",
        "changeDescription": "string",
        "type": "BUILD|TEST|DISTRIBUTION",
        "state": {
            "status": "ACTIVE|DEPRECATED",
            "reason": "string"
        },
        "owner": "string",
        "data": "string",
        "kmsKeyId": "string",
        "dateCreated": "string",
        "tags": {},
        "parameters": [
            {
                "name": "string",
                "type": "string",
                "defaultValue": ["string"],
                "description": "string"
            }
        ]
    }
}
```

---

### 10.3 `list-workflows`

Lists workflow resources. **Paginated operation.**

**Synopsis:**
```bash
aws imagebuilder list-workflows \
    [--owner <value>] \
    [--filters <value>] \
    [--by-name | --no-by-name] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--owner` | No | string | `Self` | Owner filter: `Self`, `Shared`, `Amazon`, `ThirdParty` |
| `--filters` | No | list | None | Filters. Names: `name`, `type` |
| `--by-name` | No | boolean | false | Return only the latest version |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "workflowVersionList": [
        {
            "arn": "string",
            "name": "string",
            "version": "string",
            "description": "string",
            "type": "BUILD|TEST|DISTRIBUTION",
            "owner": "string",
            "dateCreated": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 10.4 `get-workflow-execution`

Gets a workflow execution.

**Synopsis:**
```bash
aws imagebuilder get-workflow-execution \
    --workflow-execution-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-execution-id` | **Yes** | string | -- | ID of the workflow execution |

**Output Schema:**
```json
{
    "requestId": "string",
    "workflowBuildVersionArn": "string",
    "workflowExecutionId": "string",
    "imageBuildVersionArn": "string",
    "type": "BUILD|TEST|DISTRIBUTION",
    "status": "PENDING|SKIPPED|RUNNING|COMPLETED|FAILED|ROLLBACK_IN_PROGRESS|ROLLBACK_COMPLETED|CANCELLED",
    "message": "string",
    "totalStepCount": "integer",
    "totalStepsSucceeded": "integer",
    "totalStepsFailed": "integer",
    "totalStepsSkipped": "integer",
    "startTime": "string",
    "endTime": "string",
    "parallelGroup": "string"
}
```

---

### 10.5 `list-workflow-executions`

Lists workflow executions for an image. **Paginated operation.**

**Synopsis:**
```bash
aws imagebuilder list-workflow-executions \
    --image-build-version-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--image-build-version-arn` | **Yes** | string | -- | ARN of the image build version |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "requestId": "string",
    "workflowExecutions": [
        {
            "workflowBuildVersionArn": "string",
            "workflowExecutionId": "string",
            "type": "BUILD|TEST|DISTRIBUTION",
            "status": "PENDING|SKIPPED|RUNNING|COMPLETED|FAILED|ROLLBACK_IN_PROGRESS|ROLLBACK_COMPLETED|CANCELLED",
            "message": "string",
            "totalStepCount": "integer",
            "totalStepsSucceeded": "integer",
            "totalStepsFailed": "integer",
            "totalStepsSkipped": "integer",
            "startTime": "string",
            "endTime": "string",
            "parallelGroup": "string"
        }
    ],
    "imageBuildVersionArn": "string",
    "message": "string",
    "nextToken": "string"
}
```

---

### 10.6 `get-workflow-step-execution`

Gets a workflow step execution.

**Synopsis:**
```bash
aws imagebuilder get-workflow-step-execution \
    --step-execution-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--step-execution-id` | **Yes** | string | -- | ID of the step execution |

**Output Schema:**
```json
{
    "requestId": "string",
    "stepExecutionId": "string",
    "workflowBuildVersionArn": "string",
    "workflowExecutionId": "string",
    "imageBuildVersionArn": "string",
    "name": "string",
    "description": "string",
    "action": "string",
    "status": "PENDING|SKIPPED|RUNNING|COMPLETED|FAILED|CANCELLED",
    "rollbackStatus": "RUNNING|COMPLETED|SKIPPED|FAILED",
    "message": "string",
    "inputs": "string",
    "outputs": "string",
    "startTime": "string",
    "endTime": "string",
    "onFailure": "string",
    "timeoutSeconds": "integer"
}
```

---

### 10.7 `list-workflow-step-executions`

Lists workflow step executions. **Paginated operation.**

**Synopsis:**
```bash
aws imagebuilder list-workflow-step-executions \
    --workflow-execution-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-execution-id` | **Yes** | string | -- | ID of the workflow execution |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "requestId": "string",
    "steps": [
        {
            "stepExecutionId": "string",
            "name": "string",
            "description": "string",
            "action": "string",
            "status": "PENDING|SKIPPED|RUNNING|COMPLETED|FAILED|CANCELLED",
            "rollbackStatus": "RUNNING|COMPLETED|SKIPPED|FAILED",
            "message": "string",
            "inputs": "string",
            "outputs": "string",
            "startTime": "string",
            "endTime": "string"
        }
    ],
    "workflowBuildVersionArn": "string",
    "workflowExecutionId": "string",
    "imageBuildVersionArn": "string",
    "message": "string",
    "nextToken": "string"
}
```

---

### 10.8 `list-workflow-build-versions`

Lists workflow build versions. **Paginated operation.**

**Synopsis:**
```bash
aws imagebuilder list-workflow-build-versions \
    --workflow-version-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-version-arn` | **Yes** | string | -- | ARN of the workflow version |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "workflowSummaryList": [
        {
            "arn": "string",
            "name": "string",
            "version": "string",
            "description": "string",
            "changeDescription": "string",
            "type": "BUILD|TEST|DISTRIBUTION",
            "owner": "string",
            "state": {
                "status": "ACTIVE|DEPRECATED",
                "reason": "string"
            },
            "dateCreated": "string",
            "tags": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 10.9 `delete-workflow`

Deletes a workflow resource.

**Synopsis:**
```bash
aws imagebuilder delete-workflow \
    --workflow-build-version-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-build-version-arn` | **Yes** | string | -- | ARN of the workflow build version to delete |

**Output Schema:**
```json
{
    "workflowBuildVersionArn": "string"
}
```
