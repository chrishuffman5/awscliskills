# Containers

### 1.1 `create-container`

Creates a storage container for media objects.

**Synopsis:**
```bash
aws mediastore create-container \
    --container-name <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-name` | **Yes** | string | -- | Container name (1-255 chars, `[\w-]+`) |
| `--tags` | No | list | None | Tags as Key/Value structures (max 50) |

**Output Schema:**
```json
{
    "Container": {
        "ARN": "string",
        "Name": "string",
        "CreationTime": "timestamp",
        "Status": "CREATING|ACTIVE|DELETING",
        "Endpoint": "string",
        "AccessLoggingEnabled": "boolean"
    }
}
```

---

### 1.2 `describe-container`

Describes a container's details including its endpoint.

**Synopsis:**
```bash
aws mediastore describe-container \
    [--container-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-name` | No | string | None | Name of the container (1-255 chars) |

**Output Schema:**
```json
{
    "Container": {
        "ARN": "string",
        "Name": "string",
        "CreationTime": "timestamp",
        "Status": "CREATING|ACTIVE|DELETING",
        "Endpoint": "string",
        "AccessLoggingEnabled": "boolean"
    }
}
```

---

### 1.3 `list-containers`

Lists all containers in the account. **Paginated operation.**

**Synopsis:**
```bash
aws mediastore list-containers \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Maximum results per page (1-100) |

**Output Schema:**
```json
{
    "Containers": [
        {
            "ARN": "string",
            "Name": "string",
            "CreationTime": "timestamp",
            "Status": "CREATING|ACTIVE|DELETING",
            "Endpoint": "string",
            "AccessLoggingEnabled": "boolean"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.4 `delete-container`

Deletes a container. The container must be empty before deletion.

**Synopsis:**
```bash
aws mediastore delete-container \
    --container-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-name` | **Yes** | string | -- | Name of the container to delete |

**Output:** None
