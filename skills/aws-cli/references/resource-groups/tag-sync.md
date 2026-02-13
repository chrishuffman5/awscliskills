# Tag Sync

Tag sync tasks keep resource group membership automatically synchronized with tag changes on resources.

### 3.1 `start-tag-sync-task`

Starts a tag sync task that continuously synchronizes resource group membership based on tag changes.

**Synopsis:**
```bash
aws resource-groups start-tag-sync-task \
    --group <value> \
    --tag-key <value> \
    --tag-value <value> \
    [--role-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group` | **Yes** | string | -- | Name or ARN of the resource group |
| `--tag-key` | **Yes** | string | -- | Tag key to sync on |
| `--tag-value` | **Yes** | string | -- | Tag value to sync on |
| `--role-arn` | No | string | -- | IAM role ARN for the tag sync task |

**Output Schema:**
```json
{
    "GroupArn": "string",
    "GroupName": "string",
    "TaskArn": "string",
    "TagKey": "string",
    "TagValue": "string",
    "RoleArn": "string"
}
```

---

### 3.2 `get-tag-sync-task`

Gets information about a specific tag sync task.

**Synopsis:**
```bash
aws resource-groups get-tag-sync-task \
    --task-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-arn` | **Yes** | string | -- | ARN of the tag sync task |

**Output Schema:**
```json
{
    "GroupArn": "string",
    "GroupName": "string",
    "TaskArn": "string",
    "TagKey": "string",
    "TagValue": "string",
    "RoleArn": "string",
    "Status": "ACTIVE|ERROR",
    "ErrorMessage": "string",
    "CreatedAt": "timestamp"
}
```

---

### 3.3 `list-tag-sync-tasks`

Lists tag sync tasks. **Paginated operation.**

**Synopsis:**
```bash
aws resource-groups list-tag-sync-tasks \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | None | Filters. Shorthand: `GroupArn=string,GroupName=string` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "TagSyncTasks": [
        {
            "GroupArn": "string",
            "GroupName": "string",
            "TaskArn": "string",
            "TagKey": "string",
            "TagValue": "string",
            "RoleArn": "string",
            "Status": "ACTIVE|ERROR",
            "ErrorMessage": "string",
            "CreatedAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.4 `cancel-tag-sync-task`

Cancels a tag sync task.

**Synopsis:**
```bash
aws resource-groups cancel-tag-sync-task \
    --task-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-arn` | **Yes** | string | -- | ARN of the tag sync task to cancel |

**Output Schema:**
```json
{}
```
