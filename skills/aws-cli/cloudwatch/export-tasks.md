# Export Tasks

### 15.1 `create-export-task`

Exports log data from a log group to an S3 bucket. Only one active export task per account.

**Synopsis:**
```bash
aws logs create-export-task \
    --log-group-name <value> \
    --from <value> \
    --to <value> \
    --destination <value> \
    [--task-name <value>] \
    [--log-stream-name-prefix <value>] \
    [--destination-prefix <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-group-name` | **Yes** | string | -- | Log group name (1-512 chars) |
| `--from` | **Yes** | long | -- | Start time in ms since epoch |
| `--to` | **Yes** | long | -- | End time in ms since epoch |
| `--destination` | **Yes** | string | -- | S3 bucket name (1-512 chars, must be in same Region) |
| `--task-name` | No | string | -- | Export task name (1-512 chars) |
| `--log-stream-name-prefix` | No | string | -- | Export only matching streams (1-512 chars) |
| `--destination-prefix` | No | string | `exportedlogs` | S3 key prefix (max 1024 bytes) |

**Output Schema:**
```json
{
    "taskId": "string"
}
```

---

### 15.2 `describe-export-tasks`

Lists export tasks. **Paginated.**

**Synopsis:**
```bash
aws logs describe-export-tasks \
    [--task-id <value>] \
    [--status-code <value>] \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-id` | No | string | -- | Specific task ID (1-512 chars) |
| `--status-code` | No | string | -- | `CANCELLED`, `COMPLETED`, `FAILED`, `PENDING`, `PENDING_CANCEL`, `RUNNING` |
| `--max-items` | No | integer | -- | Total items to return |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |

**Output Schema:**
```json
{
    "exportTasks": [
        {
            "taskId": "string",
            "taskName": "string",
            "logGroupName": "string",
            "from": long,
            "to": long,
            "destination": "string",
            "destinationPrefix": "string",
            "status": {
                "code": "CANCELLED|COMPLETED|FAILED|PENDING|PENDING_CANCEL|RUNNING",
                "message": "string"
            },
            "executionInfo": {
                "creationTime": long,
                "completionTime": long
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 15.3 `cancel-export-task`

Cancels an export task in PENDING or RUNNING state.

**Synopsis:**
```bash
aws logs cancel-export-task \
    --task-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-id` | **Yes** | string | -- | Export task ID (1-512 chars) |

**Output:** None on success.

---
