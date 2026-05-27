# Functions

### 5.1 `create-function`

Creates a pipeline function for use in pipeline resolvers.

**Synopsis:**
```bash
aws appsync create-function \
    --api-id <value> \
    --name <value> \
    --data-source-name <value> \
    [--description <value>] \
    [--request-mapping-template <value>] \
    [--response-mapping-template <value>] \
    [--function-version <value>] \
    [--sync-config <value>] \
    [--max-batch-size <value>] \
    [--runtime <value>] \
    [--code <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--name` | **Yes** | string | -- | Function name (1-65536 chars) |
| `--data-source-name` | **Yes** | string | -- | Data source name (1-65536 chars) |
| `--description` | No | string | None | Function description |
| `--request-mapping-template` | No | string | None | VTL request template (version 2018-05-29 only) |
| `--response-mapping-template` | No | string | None | VTL response template |
| `--function-version` | No | string | None | VTL mapping template version (`2018-05-29`) |
| `--sync-config` | No | structure | None | Conflict detection/resolution config |
| `--max-batch-size` | No | integer | None | Max batch size (0-2000) |
| `--runtime` | No | structure | None | Runtime (required if `--code` specified) |
| `--code` | No | string | None | JS function code (1-32768 chars, requires `--runtime`) |

**SyncConfig:**
```json
{
    "conflictHandler": "OPTIMISTIC_CONCURRENCY|LAMBDA|AUTOMERGE|NONE",
    "conflictDetection": "VERSION|NONE",
    "lambdaConflictHandlerConfig": {
        "lambdaConflictHandlerArn": "string"
    }
}
```

**Runtime:**
```json
{
    "name": "APPSYNC_JS",
    "runtimeVersion": "string"
}
```

**Output Schema:**
```json
{
    "functionConfiguration": {
        "functionId": "string",
        "functionArn": "string",
        "name": "string",
        "description": "string",
        "dataSourceName": "string",
        "requestMappingTemplate": "string",
        "responseMappingTemplate": "string",
        "functionVersion": "string",
        "syncConfig": {
            "conflictHandler": "string",
            "conflictDetection": "string",
            "lambdaConflictHandlerConfig": {}
        },
        "maxBatchSize": integer,
        "runtime": {"name": "APPSYNC_JS", "runtimeVersion": "string"},
        "code": "string"
    }
}
```

---

### 5.2 `get-function`

Retrieves a pipeline function.

**Synopsis:**
```bash
aws appsync get-function \
    --api-id <value> \
    --function-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--function-id` | **Yes** | string | -- | The function ID |

**Output Schema:** Same as `create-function`.

---

### 5.3 `list-functions`

Lists pipeline functions for a GraphQL API. **Paginated operation.**

**Synopsis:**
```bash
aws appsync list-functions \
    --api-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Results per page |
| `--max-items` | No | integer | None | Max total results |

**Output Schema:**
```json
{
    "functions": [
        {
            "functionId": "string",
            "functionArn": "string",
            "name": "string",
            "description": "string",
            "dataSourceName": "string",
            "requestMappingTemplate": "string",
            "responseMappingTemplate": "string",
            "functionVersion": "string",
            "syncConfig": {},
            "maxBatchSize": integer,
            "runtime": {},
            "code": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 5.4 `update-function`

Updates a pipeline function.

**Synopsis:**
```bash
aws appsync update-function \
    --api-id <value> \
    --name <value> \
    --function-id <value> \
    --data-source-name <value> \
    [--description <value>] \
    [--request-mapping-template <value>] \
    [--response-mapping-template <value>] \
    [--function-version <value>] \
    [--sync-config <value>] \
    [--max-batch-size <value>] \
    [--runtime <value>] \
    [--code <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--name` | **Yes** | string | -- | The function name |
| `--function-id` | **Yes** | string | -- | The function ID |
| `--data-source-name` | **Yes** | string | -- | The data source name |
| `--description` | No | string | None | Updated description |
| `--request-mapping-template` | No | string | None | Updated VTL request template |
| `--response-mapping-template` | No | string | None | Updated VTL response template |
| `--function-version` | No | string | None | VTL version (`2018-05-29`) |
| `--sync-config` | No | structure | None | Updated sync config |
| `--max-batch-size` | No | integer | None | Updated max batch size |
| `--runtime` | No | structure | None | Updated runtime |
| `--code` | No | string | None | Updated JS code |

**Output Schema:** Same as `create-function`.

---

### 5.5 `delete-function`

Deletes a pipeline function.

**Synopsis:**
```bash
aws appsync delete-function \
    --api-id <value> \
    --function-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--function-id` | **Yes** | string | -- | The function ID to delete |

**Output:** None
