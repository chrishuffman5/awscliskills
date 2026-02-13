# Resources

### 2.1 `create-resource`

Creates a child API resource under a parent resource.

**Synopsis:**
```bash
aws apigateway create-resource \
    --rest-api-id <value> \
    --parent-id <value> \
    --path-part <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--parent-id` | **Yes** | string | -- | ID of the parent resource |
| `--path-part` | **Yes** | string | -- | Path segment for this resource (e.g., `users`, `{id}`) |

**Output Schema:**
```json
{
    "id": "string",
    "parentId": "string",
    "pathPart": "string",
    "path": "string",
    "resourceMethods": {
        "string": {
            "httpMethod": "string",
            "authorizationType": "string",
            "authorizerId": "string",
            "apiKeyRequired": "boolean",
            "requestValidatorId": "string",
            "operationName": "string",
            "requestParameters": {
                "string": "boolean"
            },
            "requestModels": {
                "string": "string"
            },
            "methodResponses": {},
            "methodIntegration": {}
        }
    }
}
```

---

### 2.2 `delete-resource`

Deletes a resource.

**Synopsis:**
```bash
aws apigateway delete-resource \
    --rest-api-id <value> \
    --resource-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--resource-id` | **Yes** | string | -- | ID of the resource to delete |

**Output:** None

---

### 2.3 `get-resource`

Gets information about a resource.

**Synopsis:**
```bash
aws apigateway get-resource \
    --rest-api-id <value> \
    --resource-id <value> \
    [--embed <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--resource-id` | **Yes** | string | -- | ID of the resource |
| `--embed` | No | list(string) | None | Embed related resources: `methods` |

**Output Schema:**
```json
{
    "id": "string",
    "parentId": "string",
    "pathPart": "string",
    "path": "string",
    "resourceMethods": {
        "string": {
            "httpMethod": "string",
            "authorizationType": "string",
            "authorizerId": "string",
            "apiKeyRequired": "boolean",
            "requestValidatorId": "string",
            "operationName": "string",
            "requestParameters": {},
            "requestModels": {},
            "methodResponses": {},
            "methodIntegration": {}
        }
    }
}
```

---

### 2.4 `get-resources`

Lists all resources in a REST API. **Paginated operation.**

**Synopsis:**
```bash
aws apigateway get-resources \
    --rest-api-id <value> \
    [--embed <value>] \
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
| `--embed` | No | list(string) | None | Embed related resources: `methods` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 500) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "items": [
        {
            "id": "string",
            "parentId": "string",
            "pathPart": "string",
            "path": "string",
            "resourceMethods": {}
        }
    ],
    "NextToken": "string"
}
```
