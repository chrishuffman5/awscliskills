# Allow Lists

### 5.1 `create-allow-list`

Creates and defines settings for an allow list. Allow lists specify text or patterns to ignore during sensitive data discovery.

**Synopsis:**
```bash
aws macie2 create-allow-list \
    --name <value> \
    --criteria <value> \
    [--client-token <value>] \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Allow list name |
| `--criteria` | **Yes** | structure | -- | Criteria for the allow list |
| `--client-token` | No | string | None | Idempotency token |
| `--description` | No | string | None | Allow list description |
| `--tags` | No | map | None | Tags to add |

**Criteria Structure:**
```json
{
    "regex": "string",
    "s3WordsList": {
        "bucketName": "string",
        "objectKey": "string"
    }
}
```

**Output Schema:**
```json
{
    "arn": "string",
    "id": "string"
}
```

---

### 5.2 `delete-allow-list`

Deletes an allow list.

**Synopsis:**
```bash
aws macie2 delete-allow-list \
    --id <value> \
    [--ignore-job-checks <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Allow list ID to delete |
| `--ignore-job-checks` | No | string | None | Ignore checks for associated jobs |

**Output:** None (HTTP 200 on success)

---

### 5.3 `get-allow-list`

Retrieves the settings and status of an allow list.

**Synopsis:**
```bash
aws macie2 get-allow-list \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Allow list ID to retrieve |

**Output Schema:**
```json
{
    "arn": "string",
    "createdAt": "timestamp",
    "criteria": {
        "regex": "string",
        "s3WordsList": {
            "bucketName": "string",
            "objectKey": "string"
        }
    },
    "description": "string",
    "id": "string",
    "name": "string",
    "status": {
        "code": "OK|S3_OBJECT_NOT_FOUND|S3_USER_ACCESS_DENIED|S3_OBJECT_ACCESS_DENIED|S3_THROTTLED|S3_OBJECT_OVERSIZE|S3_OBJECT_EMPTY|UNKNOWN_ERROR",
        "description": "string"
    },
    "tags": {"string": "string"},
    "updatedAt": "timestamp"
}
```

---

### 5.4 `list-allow-lists`

Retrieves a subset of information about all allow lists. **Paginated operation.**

**Synopsis:**
```bash
aws macie2 list-allow-lists \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "allowLists": [
        {
            "arn": "string",
            "createdAt": "timestamp",
            "description": "string",
            "id": "string",
            "name": "string",
            "updatedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 5.5 `update-allow-list`

Updates the settings for an allow list.

**Synopsis:**
```bash
aws macie2 update-allow-list \
    --id <value> \
    --name <value> \
    --criteria <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Allow list ID to update |
| `--name` | **Yes** | string | -- | Updated name |
| `--criteria` | **Yes** | structure | -- | Updated criteria |
| `--description` | No | string | None | Updated description |

**Output Schema:**
```json
{
    "arn": "string",
    "id": "string"
}
```
