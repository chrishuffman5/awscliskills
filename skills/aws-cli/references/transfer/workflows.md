# Workflows

Commands for managing Transfer Family post-upload workflows.

### 7.1 `create-workflow`

Creates a workflow for processing files after upload.

**Synopsis:**
```bash
aws transfer create-workflow \
    --steps <value> \
    [--description <value>] \
    [--on-exception-steps <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--steps` | **Yes** | list | -- | Workflow steps (0-8 steps) |
| `--description` | No | string | None | Description (0-256 chars) |
| `--on-exception-steps` | No | list | None | Error-handling steps (0-8 steps) |
| `--tags` | No | list | None | Tags |

**Step Types:**

| Type | Description |
|------|-------------|
| `COPY` | Copy file to another location |
| `CUSTOM` | Invoke Lambda function |
| `TAG` | Add tags to file |
| `DELETE` | Delete the file |
| `DECRYPT` | Decrypt PGP-encrypted file |

**Step Structure (JSON):**
```json
[
    {
        "Type": "COPY|CUSTOM|TAG|DELETE|DECRYPT",
        "CopyStepDetails": {
            "Name": "string",
            "DestinationFileLocation": {
                "S3FileLocation": {"Bucket": "string", "Key": "string"},
                "EfsFileLocation": {"FileSystemId": "string", "Path": "string"}
            },
            "OverwriteExisting": "TRUE|FALSE",
            "SourceFileLocation": "${previous.file}|${original.file}"
        },
        "CustomStepDetails": {
            "Name": "string",
            "Target": "lambda-arn",
            "TimeoutSeconds": "integer (1-1800)",
            "SourceFileLocation": "string"
        },
        "TagStepDetails": {
            "Name": "string",
            "Tags": [{"Key": "string", "Value": "string"}],
            "SourceFileLocation": "string"
        },
        "DeleteStepDetails": {
            "Name": "string",
            "SourceFileLocation": "string"
        },
        "DecryptStepDetails": {
            "Name": "string",
            "Type": "PGP",
            "SourceFileLocation": "string",
            "OverwriteExisting": "TRUE|FALSE",
            "DestinationFileLocation": {
                "S3FileLocation": {"Bucket": "string", "Key": "string"},
                "EfsFileLocation": {"FileSystemId": "string", "Path": "string"}
            }
        }
    }
]
```

**Output Schema:**
```json
{
    "WorkflowId": "string"
}
```

---

### 7.2 `delete-workflow`

Deletes a workflow.

**Synopsis:**
```bash
aws transfer delete-workflow \
    --workflow-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-id` | **Yes** | string | -- | Workflow ID |

**Output:** None on success.

---

### 7.3 `describe-workflow`

Gets details about a workflow.

**Synopsis:**
```bash
aws transfer describe-workflow \
    --workflow-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-id` | **Yes** | string | -- | Workflow ID |

**Output Schema:**
```json
{
    "Workflow": {
        "Arn": "string",
        "Description": "string",
        "Steps": ["..."],
        "OnExceptionSteps": ["..."],
        "WorkflowId": "string",
        "Tags": [{"Key": "string", "Value": "string"}]
    }
}
```

---

### 7.4 `list-workflows`

Lists all workflows. **Paginated operation.**

**Synopsis:**
```bash
aws transfer list-workflows \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "Workflows": [
        {
            "Arn": "string",
            "Description": "string",
            "WorkflowId": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.5 `describe-execution`

Gets details about a workflow execution.

**Synopsis:**
```bash
aws transfer describe-execution \
    --execution-id <value> \
    --workflow-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--execution-id` | **Yes** | string | -- | Execution ID |
| `--workflow-id` | **Yes** | string | -- | Workflow ID |

**Output Schema:**
```json
{
    "WorkflowId": "string",
    "Execution": {
        "ExecutionId": "string",
        "InitialFileLocation": {
            "S3FileLocation": {"Bucket": "string", "Key": "string", "VersionId": "string", "Etag": "string"},
            "EfsFileLocation": {"FileSystemId": "string", "Path": "string"}
        },
        "ServiceMetadata": {
            "UserDetails": {
                "UserName": "string",
                "ServerId": "string",
                "SessionId": "string"
            }
        },
        "ExecutionRole": "string",
        "LoggingConfiguration": {
            "LoggingRole": "string",
            "LogGroupName": "string"
        },
        "PosixProfile": {"Uid": "long", "Gid": "long", "SecondaryGids": ["long"]},
        "Status": "IN_PROGRESS|COMPLETED|EXCEPTION|HANDLING_EXCEPTION",
        "Results": {
            "Steps": [
                {
                    "StepType": "COPY|CUSTOM|TAG|DELETE|DECRYPT",
                    "Outputs": "string",
                    "Error": {"Type": "string", "Message": "string"}
                }
            ],
            "OnExceptionSteps": ["..."]
        }
    }
}
```

---

### 7.6 `list-executions`

Lists workflow executions. **Paginated operation.**

**Synopsis:**
```bash
aws transfer list-executions \
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
    "WorkflowId": "string",
    "Executions": [
        {
            "ExecutionId": "string",
            "InitialFileLocation": {"S3FileLocation": {"..."}},
            "ServiceMetadata": {"UserDetails": {"..."}},
            "Status": "IN_PROGRESS|COMPLETED|EXCEPTION|HANDLING_EXCEPTION"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.7 `send-workflow-step-state`

Sends the state of a custom workflow step (success or failure) back to Transfer Family.

**Synopsis:**
```bash
aws transfer send-workflow-step-state \
    --workflow-id <value> \
    --execution-id <value> \
    --token <value> \
    --status <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-id` | **Yes** | string | -- | Workflow ID |
| `--execution-id` | **Yes** | string | -- | Execution ID |
| `--token` | **Yes** | string | -- | Token provided to Lambda function |
| `--status` | **Yes** | string | -- | `SUCCESS` or `FAILURE` |

**Output:** None on success.
