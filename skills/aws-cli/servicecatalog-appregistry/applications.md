# Applications

### 1.1 `create-application`

Creates a new application in Service Catalog AppRegistry.

**Synopsis:**
```bash
aws servicecatalog-appregistry create-application \
    --name <value> \
    [--description <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Application name (1-256 chars, pattern: `[-.\w]+`). Must be unique in the region |
| `--description` | No | string | None | Description of the application (max 1024 chars) |
| `--tags` | No | map | None | Key-value pairs (max 50 tags). Shorthand: `Key1=Value1,Key2=Value2` |
| `--client-token` | No | string | Auto | Idempotency token (1-128 chars) |

**Output Schema:**
```json
{
    "application": {
        "id": "string",
        "arn": "string",
        "name": "string",
        "description": "string",
        "creationTime": "timestamp",
        "lastUpdateTime": "timestamp",
        "tags": {
            "string": "string"
        },
        "applicationTag": {
            "string": "string"
        }
    }
}
```

---

### 1.2 `get-application`

Retrieves metadata information about an application.

**Synopsis:**
```bash
aws servicecatalog-appregistry get-application \
    --application <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application` | **Yes** | string | -- | The name, ID, or ARN of the application (1-256 chars) |

**Output Schema:**
```json
{
    "id": "string",
    "arn": "string",
    "name": "string",
    "description": "string",
    "creationTime": "timestamp",
    "lastUpdateTime": "timestamp",
    "associatedResourceCount": "integer",
    "tags": {
        "string": "string"
    },
    "integrations": {
        "resourceGroup": {
            "state": "CREATING|CREATE_COMPLETE|CREATE_FAILED|UPDATING|UPDATE_COMPLETE|UPDATE_FAILED",
            "arn": "string",
            "errorMessage": "string"
        },
        "applicationTagResourceGroup": {
            "state": "CREATING|CREATE_COMPLETE|CREATE_FAILED|UPDATING|UPDATE_COMPLETE|UPDATE_FAILED",
            "arn": "string",
            "errorMessage": "string"
        }
    },
    "applicationTag": {
        "string": "string"
    }
}
```

---

### 1.3 `list-applications`

Lists all applications in the account. **Paginated operation.**

**Synopsis:**
```bash
aws servicecatalog-appregistry list-applications \
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
| `--page-size` | No | integer | None | Number of items per page |
| `--max-items` | No | integer | None | Total number of items to return |

**Output Schema:**
```json
{
    "applications": [
        {
            "id": "string",
            "arn": "string",
            "name": "string",
            "description": "string",
            "creationTime": "timestamp",
            "lastUpdateTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.4 `update-application`

Updates an existing application's metadata.

**Synopsis:**
```bash
aws servicecatalog-appregistry update-application \
    --application <value> \
    [--name <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application` | **Yes** | string | -- | The name, ID, or ARN of the application (1-256 chars) |
| `--name` | No | string | None | New name for the application (deprecated) |
| `--description` | No | string | None | New description (max 1024 chars) |

**Output Schema:**
```json
{
    "application": {
        "id": "string",
        "arn": "string",
        "name": "string",
        "description": "string",
        "creationTime": "timestamp",
        "lastUpdateTime": "timestamp",
        "tags": {
            "string": "string"
        },
        "applicationTag": {
            "string": "string"
        }
    }
}
```

---

### 1.5 `delete-application`

Deletes an application. All associated attribute groups and resources must be disassociated first.

**Synopsis:**
```bash
aws servicecatalog-appregistry delete-application \
    --application <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application` | **Yes** | string | -- | The name, ID, or ARN of the application (1-256 chars) |

**Output Schema:**
```json
{
    "application": {
        "id": "string",
        "arn": "string",
        "name": "string",
        "description": "string",
        "creationTime": "timestamp",
        "lastUpdateTime": "timestamp"
    }
}
```
