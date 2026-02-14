# Dashboards

### 7.1 `create-dashboard`

Creates a dashboard in a project.

**Synopsis:**
```bash
aws iotsitewise create-dashboard \
    --project-id <value> \
    --dashboard-name <value> \
    --dashboard-definition <value> \
    [--dashboard-description <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-id` | **Yes** | string | -- | Project ID (UUID) |
| `--dashboard-name` | **Yes** | string | -- | Dashboard name (1-256 chars) |
| `--dashboard-definition` | **Yes** | string | -- | Dashboard definition JSON (max 204800 chars) |
| `--dashboard-description` | No | string | None | Description (1-2048 chars) |
| `--tags` | No | map | None | Tags (max 50) |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "dashboardId": "string",
    "dashboardArn": "string"
}
```

---

### 7.2 `describe-dashboard`

Describes a dashboard.

**Synopsis:**
```bash
aws iotsitewise describe-dashboard \
    --dashboard-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dashboard-id` | **Yes** | string | -- | Dashboard ID (UUID) |

**Output Schema:**
```json
{
    "dashboardId": "string",
    "dashboardArn": "string",
    "dashboardName": "string",
    "projectId": "string",
    "dashboardDescription": "string",
    "dashboardDefinition": "string",
    "dashboardCreationDate": "timestamp",
    "dashboardLastUpdateDate": "timestamp"
}
```

---

### 7.3 `list-dashboards`

Lists dashboards in a project. **Paginated operation.**

**Synopsis:**
```bash
aws iotsitewise list-dashboards \
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
    "dashboardSummaries": [
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

### 7.4 `update-dashboard`

Updates a dashboard.

**Synopsis:**
```bash
aws iotsitewise update-dashboard \
    --dashboard-id <value> \
    --dashboard-name <value> \
    --dashboard-definition <value> \
    [--dashboard-description <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dashboard-id` | **Yes** | string | -- | Dashboard ID |
| `--dashboard-name` | **Yes** | string | -- | Updated name |
| `--dashboard-definition` | **Yes** | string | -- | Updated definition JSON |
| `--dashboard-description` | No | string | None | Updated description |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None

---

### 7.5 `delete-dashboard`

Deletes a dashboard.

**Synopsis:**
```bash
aws iotsitewise delete-dashboard \
    --dashboard-id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dashboard-id` | **Yes** | string | -- | Dashboard ID |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None
