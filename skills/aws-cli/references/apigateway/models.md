# Models

### 7.1 `create-model`

Creates a model for a REST API. Models define the data structure of request/response payloads.

**Synopsis:**
```bash
aws apigateway create-model \
    --rest-api-id <value> \
    --name <value> \
    --content-type <value> \
    [--description <value>] \
    [--schema <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--name` | **Yes** | string | -- | Name of the model |
| `--content-type` | **Yes** | string | -- | Content type (e.g., `application/json`) |
| `--description` | No | string | None | Description |
| `--schema` | No | string | None | JSON Schema definition for the model |

**Output Schema:**
```json
{
    "id": "string",
    "name": "string",
    "description": "string",
    "schema": "string",
    "contentType": "string"
}
```

---

### 7.2 `delete-model`

Deletes a model.

**Synopsis:**
```bash
aws apigateway delete-model \
    --rest-api-id <value> \
    --model-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--model-name` | **Yes** | string | -- | Name of the model |

**Output:** None

---

### 7.3 `get-model`

Gets information about a model.

**Synopsis:**
```bash
aws apigateway get-model \
    --rest-api-id <value> \
    --model-name <value> \
    [--flatten | --no-flatten] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--model-name` | **Yes** | string | -- | Name of the model |
| `--flatten` | No | boolean | false | Resolve all external model references and return a flattened schema |

**Output Schema:** Same as `create-model`.

---

### 7.4 `get-models`

Lists models for a REST API. **Paginated operation.**

**Synopsis:**
```bash
aws apigateway get-models \
    --rest-api-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "items": [
        {
            "id": "string",
            "name": "string",
            "description": "string",
            "schema": "string",
            "contentType": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.5 `update-model`

Updates a model using patch operations.

**Synopsis:**
```bash
aws apigateway update-model \
    --rest-api-id <value> \
    --model-name <value> \
    [--patch-operations <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--model-name` | **Yes** | string | -- | Name of the model |
| `--patch-operations` | No | list | None | Patch operations |

**Supported Patch Paths:** `/name`, `/description`, `/schema`

**Output Schema:** Same as `create-model`.
