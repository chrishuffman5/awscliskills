# Pipelines

### 1.1 `create-pipeline`

Creates a new, empty pipeline. Use `put-pipeline-definition` to populate the pipeline with objects (data nodes, activities, schedules).

**Synopsis:**
```bash
aws datapipeline create-pipeline \
    --name <value> \
    --unique-id <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the pipeline (1-1024 chars) |
| `--unique-id` | **Yes** | string | -- | Unique identifier for idempotency (1-1024 chars) |
| `--description` | No | string | None | Description of the pipeline |
| `--tags` | No | list | None | Tags. Shorthand: `key=string,value=string ...` |

**Output Schema:**
```json
{
    "pipelineId": "string"
}
```

---

### 1.2 `delete-pipeline`

Deletes a pipeline, its pipeline definition, and its run history. You cannot restore a deleted pipeline. Cannot delete a pipeline that is currently in use.

**Synopsis:**
```bash
aws datapipeline delete-pipeline \
    --pipeline-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-id` | **Yes** | string | -- | Pipeline ID to delete |

**Output:** None (HTTP 200 on success)

---

### 1.3 `describe-pipelines`

Retrieves metadata about one or more pipelines. Returns pipeline name, ID, state, creation date, unique ID, description, and tags.

**Synopsis:**
```bash
aws datapipeline describe-pipelines \
    --pipeline-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-ids` | **Yes** | list(string) | -- | List of pipeline IDs to describe (max 25) |

**Output Schema:**
```json
{
    "pipelineDescriptionList": [
        {
            "pipelineId": "string",
            "name": "string",
            "fields": [
                {
                    "key": "string",
                    "stringValue": "string",
                    "refValue": "string"
                }
            ],
            "description": "string",
            "tags": [
                {
                    "key": "string",
                    "value": "string"
                }
            ]
        }
    ]
}
```

**Common Fields:**

| Key | Description |
|-----|-------------|
| `@pipelineState` | Current state of the pipeline |
| `@creationTime` | When the pipeline was created |
| `@userId` | IAM user who created the pipeline |
| `@accountId` | AWS account ID |
| `@sphere` | Always `PIPELINE` |
| `uniqueId` | Unique identifier provided at creation |
| `@healthStatus` | Health status: `HEALTHY`, `ERROR` |
| `@healthStatusUpdatedTime` | Last health check time |

---

### 1.4 `list-pipelines`

Lists the pipeline identifiers for all active pipelines that you have permission to access. **Paginated operation.**

**Synopsis:**
```bash
aws datapipeline list-pipelines \
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
    "pipelineIdList": [
        {
            "id": "string",
            "name": "string"
        }
    ],
    "marker": "string",
    "hasMoreResults": true|false
}
```

---

### 1.5 `activate-pipeline`

Validates the specified pipeline and starts processing pipeline tasks. If the pipeline does not pass validation, activation fails.

**Synopsis:**
```bash
aws datapipeline activate-pipeline \
    --pipeline-id <value> \
    [--parameter-values <value>] \
    [--start-timestamp <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-id` | **Yes** | string | -- | Pipeline ID to activate |
| `--parameter-values` | No | list | None | Parameter values for the pipeline. Shorthand: `id=string,stringValue=string ...` |
| `--start-timestamp` | No | timestamp | Now | Timestamp from which to start processing |

**Output:** None (HTTP 200 on success)

---

### 1.6 `deactivate-pipeline`

Deactivates the specified running pipeline. When you deactivate a pipeline, it stops processing but retains its definition and run history.

**Synopsis:**
```bash
aws datapipeline deactivate-pipeline \
    --pipeline-id <value> \
    [--cancel-active | --no-cancel-active] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-id` | **Yes** | string | -- | Pipeline ID to deactivate |
| `--cancel-active` | No | boolean | false | Cancel all running objects immediately |

**Output:** None (HTTP 200 on success)
