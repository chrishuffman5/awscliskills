# Tasks

### 2.1 `create-task`

Creates a transfer task between a source and destination location.

**Synopsis:**
```bash
aws datasync create-task \
    --source-location-arn <value> \
    --destination-location-arn <value> \
    [--cloud-watch-log-group-arn <value>] \
    [--name <value>] \
    [--options <value>] \
    [--excludes <value>] \
    [--includes <value>] \
    [--schedule <value>] \
    [--tags <value>] \
    [--manifest-config <value>] \
    [--task-report-config <value>] \
    [--task-mode <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-location-arn` | **Yes** | string | -- | ARN of the source location |
| `--destination-location-arn` | **Yes** | string | -- | ARN of the destination location |
| `--cloud-watch-log-group-arn` | No | string | None | CloudWatch log group ARN for monitoring |
| `--name` | No | string | None | Task name (max 256 chars) |
| `--options` | No | structure | None | Transfer options (see below) |
| `--excludes` | No | list | None | Exclude filter (max 1) |
| `--includes` | No | list | None | Include filter (max 1) |
| `--schedule` | No | structure | None | Cron/rate schedule expression |
| `--tags` | No | list | None | Tags (max 50) |
| `--manifest-config` | No | structure | None | Manifest-based transfer config |
| `--task-report-config` | No | structure | None | Task report config |
| `--task-mode` | No | string | `BASIC` | `BASIC` or `ENHANCED` |

**Options Structure (shorthand):**
```
VerifyMode=POINT_IN_TIME_CONSISTENT|ONLY_FILES_TRANSFERRED|NONE,
OverwriteMode=ALWAYS|NEVER,
Atime=NONE|BEST_EFFORT,
Mtime=NONE|PRESERVE,
Uid=NONE|INT_VALUE|NAME|BOTH,
Gid=NONE|INT_VALUE|NAME|BOTH,
PreserveDeletedFiles=PRESERVE|REMOVE,
PreserveDevices=NONE|PRESERVE,
PosixPermissions=NONE|PRESERVE,
BytesPerSecond=long,
TaskQueueing=ENABLED|DISABLED,
LogLevel=OFF|BASIC|TRANSFER,
TransferMode=CHANGED|ALL,
SecurityDescriptorCopyFlags=NONE|OWNER_DACL|OWNER_DACL_SACL,
ObjectTags=PRESERVE|NONE
```

**Filter Structure (shorthand):**
```
FilterType=SIMPLE_PATTERN,Value=string
```

**Schedule Structure (shorthand):**
```
ScheduleExpression=string
```

**Output Schema:**
```json
{
    "TaskArn": "string"
}
```

---

### 2.2 `delete-task`

Deletes a task.

**Synopsis:**
```bash
aws datasync delete-task \
    --task-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-arn` | **Yes** | string | -- | ARN of the task to delete |

**Output:** None on success.

---

### 2.3 `describe-task`

Gets details about a task.

**Synopsis:**
```bash
aws datasync describe-task \
    --task-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-arn` | **Yes** | string | -- | ARN of the task |

**Output Schema:**
```json
{
    "TaskArn": "string",
    "Status": "AVAILABLE|CREATING|QUEUED|RUNNING|UNAVAILABLE",
    "Name": "string",
    "CurrentTaskExecutionArn": "string",
    "SourceLocationArn": "string",
    "DestinationLocationArn": "string",
    "CloudWatchLogGroupArn": "string",
    "SourceNetworkInterfaceArns": ["string"],
    "DestinationNetworkInterfaceArns": ["string"],
    "Options": {
        "VerifyMode": "string",
        "OverwriteMode": "string",
        "TransferMode": "string",
        "BytesPerSecond": "long",
        "LogLevel": "string",
        "ObjectTags": "string"
    },
    "Excludes": [{"FilterType": "SIMPLE_PATTERN", "Value": "string"}],
    "Includes": [{"FilterType": "SIMPLE_PATTERN", "Value": "string"}],
    "Schedule": {"ScheduleExpression": "string", "Status": "ENABLED|DISABLED"},
    "ErrorCode": "string",
    "ErrorDetail": "string",
    "CreationTime": "timestamp",
    "TaskMode": "BASIC|ENHANCED"
}
```

---

### 2.4 `list-tasks`

Lists all tasks. **Paginated operation.**

**Synopsis:**
```bash
aws datasync list-tasks \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--filters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |
| `--filters` | No | list | None | Filter by LocationId, CreationTime |

**Output Schema:**
```json
{
    "Tasks": [
        {
            "TaskArn": "string",
            "Status": "AVAILABLE|CREATING|QUEUED|RUNNING|UNAVAILABLE",
            "Name": "string",
            "TaskMode": "BASIC|ENHANCED"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.5 `update-task`

Updates task configuration.

**Synopsis:**
```bash
aws datasync update-task \
    --task-arn <value> \
    [--options <value>] \
    [--excludes <value>] \
    [--includes <value>] \
    [--schedule <value>] \
    [--name <value>] \
    [--cloud-watch-log-group-arn <value>] \
    [--manifest-config <value>] \
    [--task-report-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same optional parameters as `create-task` plus required `--task-arn`.

**Output:** None on success.

---

### 2.6 `start-task-execution`

Starts a task execution. Only one execution can run per task at a time.

**Synopsis:**
```bash
aws datasync start-task-execution \
    --task-arn <value> \
    [--override-options <value>] \
    [--includes <value>] \
    [--excludes <value>] \
    [--manifest-config <value>] \
    [--task-report-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-arn` | **Yes** | string | -- | ARN of the task |
| `--override-options` | No | structure | None | Override task options for this execution |
| `--includes` | No | list | None | Include filter override |
| `--excludes` | No | list | None | Exclude filter override |
| `--manifest-config` | No | structure | None | Manifest config override |
| `--task-report-config` | No | structure | None | Report config override |
| `--tags` | No | list | None | Tags for execution |

**Output Schema:**
```json
{
    "TaskExecutionArn": "string"
}
```

---

### 2.7 `cancel-task-execution`

Cancels a running task execution.

**Synopsis:**
```bash
aws datasync cancel-task-execution \
    --task-execution-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-execution-arn` | **Yes** | string | -- | ARN of the task execution |

**Output:** None on success.

---

### 2.8 `describe-task-execution`

Gets details about a task execution, including transfer statistics.

**Synopsis:**
```bash
aws datasync describe-task-execution \
    --task-execution-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-execution-arn` | **Yes** | string | -- | ARN of the task execution |

**Output Schema:**
```json
{
    "TaskExecutionArn": "string",
    "Status": "QUEUED|CANCELLING|LAUNCHING|PREPARING|TRANSFERRING|VERIFYING|SUCCESS|ERROR",
    "Options": {"..."},
    "Excludes": ["..."],
    "Includes": ["..."],
    "ManifestConfig": {"..."},
    "StartTime": "timestamp",
    "EstimatedFilesToTransfer": "long",
    "EstimatedBytesToTransfer": "long",
    "FilesTransferred": "long",
    "BytesWritten": "long",
    "BytesTransferred": "long",
    "BytesCompressed": "long",
    "Result": {
        "PrepareDuration": "long",
        "PrepareStatus": "PENDING|SUCCESS|ERROR",
        "TotalDuration": "long",
        "TransferDuration": "long",
        "TransferStatus": "PENDING|SUCCESS|ERROR",
        "VerifyDuration": "long",
        "VerifyStatus": "PENDING|SUCCESS|ERROR",
        "ErrorCode": "string",
        "ErrorDetail": "string"
    },
    "TaskReportConfig": {"..."},
    "FilesDeleted": "long",
    "FilesSkipped": "long",
    "FilesVerified": "long",
    "ReportResult": {
        "Status": "PENDING|SUCCESS|ERROR",
        "ErrorCode": "string",
        "ErrorDetail": "string"
    },
    "EstimatedFilesToDelete": "long",
    "TaskMode": "BASIC|ENHANCED"
}
```

---

### 2.9 `list-task-executions`

Lists task executions for a task. **Paginated operation.**

**Synopsis:**
```bash
aws datasync list-task-executions \
    [--task-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-arn` | No | string | None | ARN of the task (filter by task) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "TaskExecutions": [
        {
            "TaskExecutionArn": "string",
            "Status": "string",
            "TaskMode": "BASIC|ENHANCED"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.10 `update-task-execution`

Updates options for a running task execution (e.g., bandwidth throttling).

**Synopsis:**
```bash
aws datasync update-task-execution \
    --task-execution-arn <value> \
    --options <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-execution-arn` | **Yes** | string | -- | ARN of the task execution |
| `--options` | **Yes** | structure | -- | Updated options (only `BytesPerSecond` can be changed during execution) |

**Output:** None on success.
