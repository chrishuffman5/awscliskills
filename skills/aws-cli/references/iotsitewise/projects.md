# Projects

### 6.1 `create-project`

Creates a project in a portal.

**Synopsis:**
```bash
aws iotsitewise create-project \
    --portal-id <value> \
    --project-name <value> \
    [--project-description <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--portal-id` | **Yes** | string | -- | Portal ID (UUID) |
| `--project-name` | **Yes** | string | -- | Project name (1-256 chars) |
| `--project-description` | No | string | None | Description (1-2048 chars) |
| `--tags` | No | map | None | Tags (max 50) |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "projectId": "string",
    "projectArn": "string"
}
```

---

### 6.2 `describe-project`

Describes a project.

**Synopsis:**
```bash
aws iotsitewise describe-project \
    --project-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-id` | **Yes** | string | -- | Project ID (UUID) |

**Output Schema:**
```json
{
    "projectId": "string",
    "projectArn": "string",
    "projectName": "string",
    "portalId": "string",
    "projectDescription": "string",
    "projectCreationDate": "timestamp",
    "projectLastUpdateDate": "timestamp"
}
```

---

### 6.3 `list-projects`

Lists projects in a portal. **Paginated operation.**

**Synopsis:**
```bash
aws iotsitewise list-projects \
    --portal-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--portal-id` | **Yes** | string | -- | Portal ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "projectSummaries": [
        {
            "id": "string",
            "name": "string",
            "description": "string",
            "creationDate": "timestamp",
            "lastUpdateDate": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 6.4 `update-project`

Updates a project.

**Synopsis:**
```bash
aws iotsitewise update-project \
    --project-id <value> \
    --project-name <value> \
    [--project-description <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-id` | **Yes** | string | -- | Project ID |
| `--project-name` | **Yes** | string | -- | Updated name |
| `--project-description` | No | string | None | Updated description |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None

---

### 6.5 `delete-project`

Deletes a project. All dashboards must be deleted first.

**Synopsis:**
```bash
aws iotsitewise delete-project \
    --project-id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-id` | **Yes** | string | -- | Project ID |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None

---

### 6.6 `batch-associate-project-assets`

Associates assets to a project in bulk.

**Synopsis:**
```bash
aws iotsitewise batch-associate-project-assets \
    --project-id <value> \
    --asset-ids <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-id` | **Yes** | string | -- | Project ID |
| `--asset-ids` | **Yes** | list | -- | List of asset IDs |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "errors": [
        {
            "assetId": "string",
            "code": "INTERNAL_FAILURE",
            "message": "string"
        }
    ]
}
```

---

### 6.7 `batch-disassociate-project-assets`

Disassociates assets from a project in bulk.

**Synopsis:**
```bash
aws iotsitewise batch-disassociate-project-assets \
    --project-id <value> \
    --asset-ids <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-id` | **Yes** | string | -- | Project ID |
| `--asset-ids` | **Yes** | list | -- | List of asset IDs |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "errors": [
        {
            "assetId": "string",
            "code": "INTERNAL_FAILURE",
            "message": "string"
        }
    ]
}
```

---

### 6.8 `list-project-assets`

Lists assets associated with a project. **Paginated operation.**

**Synopsis:**
```bash
aws iotsitewise list-project-assets \
    --project-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-id` | **Yes** | string | -- | Project ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "assetIds": ["string"],
    "nextToken": "string"
}
```
