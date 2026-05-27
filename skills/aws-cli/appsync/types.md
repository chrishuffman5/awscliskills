# Types

### 6.1 `create-type`

Creates a GraphQL type definition.

**Synopsis:**
```bash
aws appsync create-type \
    --api-id <value> \
    --definition <value> \
    --format <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--definition` | **Yes** | string | -- | Type definition in GraphQL SDL format |
| `--format` | **Yes** | string | -- | `SDL` or `JSON` |

**Output Schema:**
```json
{
    "type": {
        "name": "string",
        "description": "string",
        "arn": "string",
        "definition": "string",
        "format": "SDL|JSON"
    }
}
```

---

### 6.2 `get-type`

Retrieves a GraphQL type.

**Synopsis:**
```bash
aws appsync get-type \
    --api-id <value> \
    --type-name <value> \
    --format <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--type-name` | **Yes** | string | -- | The type name |
| `--format` | **Yes** | string | -- | `SDL` or `JSON` |

**Output Schema:**
```json
{
    "type": {
        "name": "string",
        "description": "string",
        "arn": "string",
        "definition": "string",
        "format": "SDL|JSON"
    }
}
```

---

### 6.3 `list-types`

Lists GraphQL types for a GraphQL API. **Paginated operation.**

**Synopsis:**
```bash
aws appsync list-types \
    --api-id <value> \
    --format <value> \
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
| `--format` | **Yes** | string | -- | `SDL` or `JSON` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Results per page |
| `--max-items` | No | integer | None | Max total results |

**Output Schema:**
```json
{
    "types": [
        {
            "name": "string",
            "description": "string",
            "arn": "string",
            "definition": "string",
            "format": "SDL|JSON"
        }
    ],
    "nextToken": "string"
}
```

---

### 6.4 `update-type`

Updates a GraphQL type.

**Synopsis:**
```bash
aws appsync update-type \
    --api-id <value> \
    --type-name <value> \
    --format <value> \
    [--definition <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--type-name` | **Yes** | string | -- | The type name |
| `--format` | **Yes** | string | -- | `SDL` or `JSON` |
| `--definition` | No | string | None | Updated type definition |

**Output Schema:**
```json
{
    "type": {
        "name": "string",
        "description": "string",
        "arn": "string",
        "definition": "string",
        "format": "SDL|JSON"
    }
}
```

---

### 6.5 `delete-type`

Deletes a GraphQL type.

**Synopsis:**
```bash
aws appsync delete-type \
    --api-id <value> \
    --type-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--type-name` | **Yes** | string | -- | The type name to delete |

**Output:** None

---

### 6.6 `list-types-by-association`

Lists types associated with a source API association for a merged API. **Paginated operation.**

**Synopsis:**
```bash
aws appsync list-types-by-association \
    --merged-api-identifier <value> \
    --association-id <value> \
    --format <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--merged-api-identifier` | **Yes** | string | -- | Merged API ID or ARN |
| `--association-id` | **Yes** | string | -- | The source API association ID |
| `--format` | **Yes** | string | -- | `SDL` or `JSON` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Results per page |
| `--max-items` | No | integer | None | Max total results |

**Output Schema:**
```json
{
    "types": [
        {
            "name": "string",
            "description": "string",
            "arn": "string",
            "definition": "string",
            "format": "SDL|JSON"
        }
    ],
    "nextToken": "string"
}
```
