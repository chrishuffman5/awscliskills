# Attribute Groups

### 2.1 `create-attribute-group`

Creates a new attribute group to hold application metadata attributes.

**Synopsis:**
```bash
aws servicecatalog-appregistry create-attribute-group \
    --name <value> \
    --attributes <value> \
    [--description <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Attribute group name (1-256 chars, pattern: `[-.\w]+`) |
| `--attributes` | **Yes** | string | -- | JSON string of nested key-value pairs (1-8000 chars) |
| `--description` | No | string | None | Description (max 1024 chars) |
| `--tags` | No | map | None | Key-value pairs (max 50 tags). Shorthand: `Key1=Value1,Key2=Value2` |
| `--client-token` | No | string | Auto | Idempotency token (1-128 chars) |

**Output Schema:**
```json
{
    "attributeGroup": {
        "id": "string",
        "arn": "string",
        "name": "string",
        "description": "string",
        "creationTime": "timestamp",
        "lastUpdateTime": "timestamp",
        "tags": {
            "string": "string"
        }
    }
}
```

---

### 2.2 `get-attribute-group`

Retrieves an attribute group by its name, ID, or ARN, including its JSON attributes.

**Synopsis:**
```bash
aws servicecatalog-appregistry get-attribute-group \
    --attribute-group <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attribute-group` | **Yes** | string | -- | The name, ID, or ARN of the attribute group (1-512 chars) |

**Output Schema:**
```json
{
    "id": "string",
    "arn": "string",
    "name": "string",
    "description": "string",
    "attributes": "string",
    "creationTime": "timestamp",
    "lastUpdateTime": "timestamp",
    "tags": {
        "string": "string"
    },
    "createdBy": "string"
}
```

---

### 2.3 `list-attribute-groups`

Lists all attribute groups in the account. **Paginated operation.**

**Synopsis:**
```bash
aws servicecatalog-appregistry list-attribute-groups \
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
    "attributeGroups": [
        {
            "id": "string",
            "arn": "string",
            "name": "string",
            "description": "string",
            "creationTime": "timestamp",
            "lastUpdateTime": "timestamp",
            "createdBy": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.4 `update-attribute-group`

Updates an existing attribute group's metadata or attributes.

**Synopsis:**
```bash
aws servicecatalog-appregistry update-attribute-group \
    --attribute-group <value> \
    [--name <value>] \
    [--description <value>] \
    [--attributes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attribute-group` | **Yes** | string | -- | The name, ID, or ARN of the attribute group (1-512 chars) |
| `--name` | No | string | None | New name (deprecated). Must be unique in the region |
| `--description` | No | string | None | New description (max 1024 chars) |
| `--attributes` | No | string | None | New JSON attributes string (1-8000 chars) |

**Output Schema:**
```json
{
    "attributeGroup": {
        "id": "string",
        "arn": "string",
        "name": "string",
        "description": "string",
        "creationTime": "timestamp",
        "lastUpdateTime": "timestamp",
        "tags": {
            "string": "string"
        }
    }
}
```

---

### 2.5 `delete-attribute-group`

Deletes an attribute group. Must be disassociated from all applications first.

**Synopsis:**
```bash
aws servicecatalog-appregistry delete-attribute-group \
    --attribute-group <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attribute-group` | **Yes** | string | -- | The name, ID, or ARN of the attribute group (1-512 chars) |

**Output Schema:**
```json
{
    "attributeGroup": {
        "id": "string",
        "arn": "string",
        "name": "string",
        "description": "string",
        "creationTime": "timestamp",
        "lastUpdateTime": "timestamp",
        "createdBy": "string"
    }
}
```

---

### 2.6 `list-attribute-groups-for-application`

Lists attribute groups associated with a specific application. **Paginated operation.**

**Synopsis:**
```bash
aws servicecatalog-appregistry list-attribute-groups-for-application \
    --application <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application` | **Yes** | string | -- | The name, ID, or ARN of the application (1-256 chars) |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Number of items per page |
| `--max-items` | No | integer | None | Total number of items to return |

**Output Schema:**
```json
{
    "attributeGroupsDetails": [
        {
            "id": "string",
            "arn": "string",
            "name": "string",
            "createdBy": "string"
        }
    ],
    "nextToken": "string"
}
```
