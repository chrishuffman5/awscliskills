# Notebooks

### 7.1 `start-notebook-execution`

Starts a notebook execution.

**Synopsis:**
```bash
aws emr start-notebook-execution \
    --editor-id <value> \
    --relative-path <value> \
    --execution-engine <value> \
    --service-role <value> \
    [--notebook-execution-name <value>] \
    [--notebook-params <value>] \
    [--notebook-instance-security-group-id <value>] \
    [--tags <value>] \
    [--notebook-s3-location <value>] \
    [--output-notebook-s3-location <value>] \
    [--output-notebook-format <value>] \
    [--environment-variables <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--editor-id` | **Yes** | string | -- | EMR notebook editor ID |
| `--relative-path` | **Yes** | string | -- | Relative path to the notebook file in S3 |
| `--execution-engine` | **Yes** | structure | -- | Execution engine. Shorthand: `Id=string,Type=EMR,MasterInstanceSecurityGroupId=string,ExecutionRoleArn=string` |
| `--service-role` | **Yes** | string | -- | IAM service role ARN |
| `--notebook-execution-name` | No | string | -- | Name for the execution |
| `--notebook-params` | No | string | -- | JSON string of notebook parameters |
| `--tags` | No | list | -- | Tags |
| `--notebook-s3-location` | No | structure | -- | S3 location for input notebook |
| `--output-notebook-s3-location` | No | structure | -- | S3 location for output notebook |
| `--output-notebook-format` | No | string | -- | Output format: `HTML` |
| `--environment-variables` | No | map | -- | Environment variables |

**Output Schema:**
```json
{
    "NotebookExecutionId": "string"
}
```

---

### 7.2 `describe-notebook-execution`

Describes a notebook execution.

**Synopsis:**
```bash
aws emr describe-notebook-execution \
    --notebook-execution-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--notebook-execution-id` | **Yes** | string | -- | Notebook execution ID |

**Output Schema:**
```json
{
    "NotebookExecution": {
        "NotebookExecutionId": "string",
        "EditorId": "string",
        "ExecutionEngine": {
            "Id": "string",
            "Type": "EMR",
            "MasterInstanceSecurityGroupId": "string",
            "ExecutionRoleArn": "string"
        },
        "NotebookExecutionName": "string",
        "NotebookParams": "string",
        "Status": "START_PENDING|STARTING|RUNNING|FINISHING|FINISHED|FAILING|FAILED|STOP_PENDING|STOPPING|STOPPED",
        "StartTime": "timestamp",
        "EndTime": "timestamp",
        "Arn": "string",
        "OutputNotebookURI": "string",
        "LastStateChangeReason": "string",
        "NotebookInstanceSecurityGroupId": "string",
        "Tags": [{"Key": "string", "Value": "string"}],
        "NotebookS3Location": {},
        "OutputNotebookS3Location": {},
        "OutputNotebookFormat": "string",
        "EnvironmentVariables": {}
    }
}
```

---

### 7.3 `list-notebook-executions`

Lists notebook executions. **Paginated operation.**

**Synopsis:**
```bash
aws emr list-notebook-executions \
    [--editor-id <value>] \
    [--status <value>] \
    [--from <value>] \
    [--to <value>] \
    [--execution-engine-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--editor-id` | No | string | -- | Filter by editor ID |
| `--status` | No | string | -- | Filter by status |
| `--from` | No | timestamp | -- | Filter after this time |
| `--to` | No | timestamp | -- | Filter before this time |
| `--execution-engine-id` | No | string | -- | Filter by execution engine (cluster ID) |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "NotebookExecutions": [
        {
            "NotebookExecutionId": "string",
            "EditorId": "string",
            "NotebookExecutionName": "string",
            "Status": "string",
            "StartTime": "timestamp",
            "EndTime": "timestamp",
            "NotebookS3Location": {},
            "ExecutionEngineId": "string"
        }
    ],
    "Marker": "string"
}
```

---

### 7.4 `stop-notebook-execution`

Stops a running notebook execution.

**Synopsis:**
```bash
aws emr stop-notebook-execution \
    --notebook-execution-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--notebook-execution-id` | **Yes** | string | -- | Notebook execution to stop |

No output on success.
