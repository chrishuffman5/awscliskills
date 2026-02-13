# Tag Sync

### 3.1 `start-tag-sync-task`

Creates a tag-sync task that continuously syncs tagged resources into a specified application group. The task keeps group membership up to date as tags change on resources.

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
| `--role-arn` | No | string | None | IAM role ARN for the tag sync task |

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

### 3.2 `cancel-tag-sync-task`

Cancels a tag-sync task.

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

---

### 3.3 `get-tag-sync-task`

Gets information about a specified tag-sync task.

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

### 3.4 `list-tag-sync-tasks`

Lists the tag-sync tasks. **Paginated operation.**

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
| `--starting-token` | No | string | None | Pagination token from previous response |
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
