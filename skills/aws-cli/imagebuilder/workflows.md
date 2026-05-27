# Workflows

### 10.1 `create-workflow`

Creates a new workflow for EC2 Image Builder. Workflows define the steps that run during image build and test phases.

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
| `--type` | **Yes** | string | -- | Workflow type: `BUILD`, `TEST`, `DISTRIBUTION` |
| `--description` | No | string | None | Description of the workflow |
| `--change-description` | No | string | None | Description of changes in this version |
| `--data` | No | string | None | Inline YAML workflow document |
| `--uri` | No | string | None | S3 URI of the workflow document |
| `--kms-key-id` | No | string | None | KMS key ID for encryption |
| `--tags` | No | map | None | Tags. Shorthand: `KeyName1=string,KeyName2=string` |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Output Schema:**
```json
{
    "clientToken": "string",
    "workflowBuildVersionArn": "string"
}
```

---

### 10.2 `delete-workflow`

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

---

### 10.3 `get-workflow`

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
            "status": "ACTIVE",
            "reason": "string"
        },
        "owner": "string",
        "data": "string",
        "kmsKeyId": "string",
        "dateCreated": "string",
        "tags": {
            "string": "string"
        },
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

### 10.4 `list-workflows`

Lists workflow build versions. **Paginated operation.**

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
| `--owner` | No | string | None | Owner filter: `Self`, `Shared`, `Amazon`, `ThirdParty` |
| `--filters` | No | list | None | Filters. Shorthand: `name=string,values=string,string ...` |
| `--by-name` | No | boolean | false | List by name instead of ARN |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Names:**
- `name` -- Workflow name
- `version` -- Workflow version

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

### 10.5 `list-workflow-build-versions`

Lists workflow build versions for a given workflow. **Paginated operation.**

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
| `--workflow-version-arn` | **Yes** | string | -- | ARN of the workflow version (with `x.x.x` wildcard) |
| `--starting-token` | No | string | None | Pagination token from previous response |
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
                "status": "ACTIVE",
                "reason": "string"
            },
            "dateCreated": "string",
            "tags": {
                "string": "string"
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 10.6 `get-workflow-execution`

Gets details for a workflow execution.

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

### 10.7 `list-workflow-executions`

Lists workflow executions for a given image build version. **Paginated operation.**

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
| `--starting-token` | No | string | None | Pagination token from previous response |
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

### 10.8 `get-workflow-step-execution`

Gets details for a workflow step execution.

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
| `--step-execution-id` | **Yes** | string | -- | ID of the workflow step execution |

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

### 10.9 `list-workflow-step-executions`

Lists workflow step executions for a given workflow execution. **Paginated operation.**

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
| `--starting-token` | No | string | None | Pagination token from previous response |
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

### 10.10 `list-waiting-workflow-steps`

Lists workflow steps that are waiting for action. **Paginated operation.**

**Synopsis:**
```bash
aws imagebuilder list-waiting-workflow-steps \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "steps": [
        {
            "stepExecutionId": "string",
            "imageBuildVersionArn": "string",
            "workflowExecutionId": "string",
            "workflowBuildVersionArn": "string",
            "name": "string",
            "action": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 10.11 `send-workflow-step-action`

Sends an action for a workflow step that is waiting for action.

**Synopsis:**
```bash
aws imagebuilder send-workflow-step-action \
    --step-execution-id <value> \
    --image-build-version-arn <value> \
    --action <value> \
    [--reason <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--step-execution-id` | **Yes** | string | -- | ID of the workflow step execution |
| `--image-build-version-arn` | **Yes** | string | -- | ARN of the image build version |
| `--action` | **Yes** | string | -- | Action to take: `RESUME`, `STOP` |
| `--reason` | No | string | None | Reason for the action |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Output Schema:**
```json
{
    "stepExecutionId": "string",
    "imageBuildVersionArn": "string",
    "clientToken": "string"
}
```
