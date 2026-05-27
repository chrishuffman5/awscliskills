# Resolvers

### 4.1 `create-resolver`

Creates a resolver for a GraphQL field.

**Synopsis:**
```bash
aws appsync create-resolver \
    --api-id <value> \
    --type-name <value> \
    --field-name <value> \
    [--data-source-name <value>] \
    [--request-mapping-template <value>] \
    [--response-mapping-template <value>] \
    [--kind <value>] \
    [--pipeline-config <value>] \
    [--sync-config <value>] \
    [--caching-config <value>] \
    [--max-batch-size <value>] \
    [--runtime <value>] \
    [--code <value>] \
    [--metrics-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--type-name` | **Yes** | string | -- | GraphQL type name (e.g., Query, Mutation) |
| `--field-name` | **Yes** | string | -- | Field name to attach resolver to |
| `--data-source-name` | No | string | None | Data source name (required for UNIT resolvers) |
| `--request-mapping-template` | No | string | None | VTL request template (1-65536 chars) |
| `--response-mapping-template` | No | string | None | VTL response template (1-65536 chars) |
| `--kind` | No | string | `UNIT` | `UNIT` (single data source) or `PIPELINE` (multiple functions) |
| `--pipeline-config` | No | structure | None | Pipeline configuration with function list |
| `--sync-config` | No | structure | None | Conflict detection/resolution config |
| `--caching-config` | No | structure | None | Caching configuration |
| `--max-batch-size` | No | integer | None | Max batch size (0-2000) |
| `--runtime` | No | structure | None | Runtime (required if `--code` is specified) |
| `--code` | No | string | None | JS resolver code (1-32768 chars, requires `--runtime`) |
| `--metrics-config` | No | string | None | `ENABLED` or `DISABLED` |

**PipelineConfig:**
```json
{
    "functions": ["string"]
}
```

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

**CachingConfig:**
```json
{
    "ttl": long,
    "cachingKeys": ["string"]
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
    "resolver": {
        "typeName": "string",
        "fieldName": "string",
        "dataSourceName": "string",
        "resolverArn": "string",
        "requestMappingTemplate": "string",
        "responseMappingTemplate": "string",
        "kind": "UNIT|PIPELINE",
        "pipelineConfig": {"functions": ["string"]},
        "syncConfig": {
            "conflictHandler": "string",
            "conflictDetection": "string",
            "lambdaConflictHandlerConfig": {}
        },
        "cachingConfig": {"ttl": long, "cachingKeys": ["string"]},
        "maxBatchSize": integer,
        "runtime": {"name": "APPSYNC_JS", "runtimeVersion": "string"},
        "code": "string",
        "metricsConfig": "ENABLED|DISABLED"
    }
}
```

---

### 4.2 `get-resolver`

Retrieves a resolver.

**Synopsis:**
```bash
aws appsync get-resolver \
    --api-id <value> \
    --type-name <value> \
    --field-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--type-name` | **Yes** | string | -- | The GraphQL type name |
| `--field-name` | **Yes** | string | -- | The field name |

**Output Schema:** Same as `create-resolver`.

---

### 4.3 `list-resolvers`

Lists resolvers for a GraphQL type. **Paginated operation.**

**Synopsis:**
```bash
aws appsync list-resolvers \
    --api-id <value> \
    --type-name <value> \
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
| `--type-name` | **Yes** | string | -- | The GraphQL type name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Results per page |
| `--max-items` | No | integer | None | Max total results |

**Output Schema:**
```json
{
    "resolvers": [
        {
            "typeName": "string",
            "fieldName": "string",
            "dataSourceName": "string",
            "resolverArn": "string",
            "kind": "UNIT|PIPELINE",
            "pipelineConfig": {},
            "syncConfig": {},
            "cachingConfig": {},
            "maxBatchSize": integer,
            "runtime": {},
            "code": "string",
            "metricsConfig": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 4.4 `update-resolver`

Updates a resolver.

**Synopsis:**
```bash
aws appsync update-resolver \
    --api-id <value> \
    --type-name <value> \
    --field-name <value> \
    [--data-source-name <value>] \
    [--request-mapping-template <value>] \
    [--response-mapping-template <value>] \
    [--kind <value>] \
    [--pipeline-config <value>] \
    [--sync-config <value>] \
    [--caching-config <value>] \
    [--max-batch-size <value>] \
    [--runtime <value>] \
    [--code <value>] \
    [--metrics-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--type-name` | **Yes** | string | -- | The GraphQL type name |
| `--field-name` | **Yes** | string | -- | The field name |
| `--data-source-name` | No | string | None | Updated data source name |
| `--request-mapping-template` | No | string | None | Updated VTL request template |
| `--response-mapping-template` | No | string | None | Updated VTL response template |
| `--kind` | No | string | None | `UNIT` or `PIPELINE` |
| `--pipeline-config` | No | structure | None | Updated pipeline config |
| `--sync-config` | No | structure | None | Updated sync config |
| `--caching-config` | No | structure | None | Updated caching config |
| `--max-batch-size` | No | integer | None | Updated max batch size |
| `--runtime` | No | structure | None | Updated runtime |
| `--code` | No | string | None | Updated JS code |
| `--metrics-config` | No | string | None | `ENABLED` or `DISABLED` |

**Output Schema:** Same as `create-resolver`.

---

### 4.5 `delete-resolver`

Deletes a resolver.

**Synopsis:**
```bash
aws appsync delete-resolver \
    --api-id <value> \
    --type-name <value> \
    --field-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--type-name` | **Yes** | string | -- | The GraphQL type name |
| `--field-name` | **Yes** | string | -- | The field name |

**Output:** None

---

### 4.6 `list-resolvers-by-function`

Lists all resolvers that use a specific function. **Paginated operation.**

**Synopsis:**
```bash
aws appsync list-resolvers-by-function \
    --api-id <value> \
    --function-id <value> \
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
| `--function-id` | **Yes** | string | -- | The function ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Results per page |
| `--max-items` | No | integer | None | Max total results |

**Output Schema:**
```json
{
    "resolvers": [
        {
            "typeName": "string",
            "fieldName": "string",
            "dataSourceName": "string",
            "resolverArn": "string",
            "kind": "UNIT|PIPELINE",
            "pipelineConfig": {},
            "syncConfig": {},
            "cachingConfig": {},
            "maxBatchSize": integer,
            "runtime": {},
            "code": "string",
            "metricsConfig": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 4.7 `evaluate-code`

Evaluates JavaScript resolver code with test context.

**Synopsis:**
```bash
aws appsync evaluate-code \
    --runtime <value> \
    --code <value> \
    --context <value> \
    [--function <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--runtime` | **Yes** | structure | -- | Runtime: `{"name":"APPSYNC_JS","runtimeVersion":"1.0.0"}` |
| `--code` | **Yes** | string | -- | JS code to evaluate (1-32768 chars) |
| `--context` | **Yes** | string | -- | Context map for resolver invocation (2-28000 chars) |
| `--function` | No | string | None | Function to evaluate: `request` or `response` |

**Output Schema:**
```json
{
    "evaluationResult": "string",
    "error": {
        "message": "string",
        "codeErrors": [
            {
                "errorType": "string",
                "value": "string",
                "location": {
                    "line": integer,
                    "column": integer,
                    "span": integer
                }
            }
        ]
    },
    "logs": ["string"],
    "stash": "string",
    "outErrors": "string"
}
```

---

### 4.8 `evaluate-mapping-template`

Evaluates a VTL mapping template with test context.

**Synopsis:**
```bash
aws appsync evaluate-mapping-template \
    --template <value> \
    --context <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template` | **Yes** | string | -- | VTL mapping template (2-65536 chars) |
| `--context` | **Yes** | string | -- | Context map for resolver invocation (2-28000 chars) |

**Output Schema:**
```json
{
    "evaluationResult": "string",
    "error": {
        "message": "string"
    },
    "logs": ["string"],
    "stash": "string",
    "outErrors": "string"
}
```
