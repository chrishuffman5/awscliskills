# Objects & Runs

### 3.1 `describe-objects`

Gets the object definitions for a set of objects associated with the pipeline. Object definitions are composed of a set of fields that define the properties of the object. **Paginated operation.**

**Synopsis:**
```bash
aws datapipeline describe-objects \
    --pipeline-id <value> \
    --object-ids <value> \
    [--evaluate-expressions | --no-evaluate-expressions] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-id` | **Yes** | string | -- | Pipeline ID |
| `--object-ids` | **Yes** | list(string) | -- | IDs of the pipeline objects to describe |
| `--evaluate-expressions` | No | boolean | false | Evaluate expressions in the object definition |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "pipelineObjects": [
        {
            "id": "string",
            "name": "string",
            "fields": [
                {
                    "key": "string",
                    "stringValue": "string",
                    "refValue": "string"
                }
            ]
        }
    ],
    "marker": "string",
    "hasMoreResults": true|false
}
```

---

### 3.2 `query-objects`

Queries the specified pipeline for the names of objects that match the specified set of conditions. **Paginated operation.**

**Synopsis:**
```bash
aws datapipeline query-objects \
    --pipeline-id <value> \
    --sphere <value> \
    [--objects-query <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-id` | **Yes** | string | -- | Pipeline ID |
| `--sphere` | **Yes** | string | -- | Object type to query: `COMPONENT`, `INSTANCE`, `ATTEMPT` |
| `--objects-query` | No | structure | None | Query filter. JSON structure with selectors |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Query Structure:**
```json
{
    "selectors": [
        {
            "fieldName": "string",
            "operator": {
                "type": "EQ|REF_EQ|LE|GE|BETWEEN",
                "values": ["string"]
            }
        }
    ]
}
```

**Sphere Values:**

| Sphere | Description |
|--------|-------------|
| `COMPONENT` | Pipeline objects in the definition (activities, data nodes, etc.) |
| `INSTANCE` | Running instances of components (one per scheduled execution) |
| `ATTEMPT` | Individual task attempts within an instance |

**Output Schema:**
```json
{
    "ids": ["string"],
    "marker": "string",
    "hasMoreResults": true|false
}
```

---

### 3.3 `evaluate-expression`

Evaluates a string in the context of the specified object. A task runner can use this to evaluate pipeline expressions.

**Synopsis:**
```bash
aws datapipeline evaluate-expression \
    --pipeline-id <value> \
    --object-id <value> \
    --expression <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-id` | **Yes** | string | -- | Pipeline ID |
| `--object-id` | **Yes** | string | -- | Object ID (context for the expression) |
| `--expression` | **Yes** | string | -- | Expression to evaluate (e.g., `#{node.scheduledStartTime}`) |

**Output Schema:**
```json
{
    "evaluatedExpression": "string"
}
```

---

### 3.4 `set-status`

Requests that the status of the specified physical or logical pipeline objects be updated. This can be used to manually set status to `PAUSED`, `RERUN`, or `CANCELED`.

**Synopsis:**
```bash
aws datapipeline set-status \
    --pipeline-id <value> \
    --object-ids <value> \
    --status <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-id` | **Yes** | string | -- | Pipeline ID |
| `--object-ids` | **Yes** | list(string) | -- | IDs of the objects to update |
| `--status` | **Yes** | string | -- | New status: `PAUSED`, `RERUN`, `CANCELED`, etc. |

**Output:** None (HTTP 200 on success)
