# Sync Jobs

### 6.1 `create-sync-job`

Creates a sync job to synchronize data from an external source (e.g., SiteWise).

**Synopsis:**
```bash
aws iottwinmaker create-sync-job \
    --workspace-id <value> \
    --sync-source <value> \
    --sync-role <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | Workspace ID |
| `--sync-source` | **Yes** | string | -- | Sync source (e.g., `SITEWISE`) |
| `--sync-role` | **Yes** | string | -- | IAM role ARN for sync access |
| `--tags` | No | map | None | Tags (max 50) |

**Output Schema:**
```json
{
    "arn": "string",
    "creationDateTime": "timestamp",
    "state": "CREATING|INITIALIZING|ACTIVE|DELETING|ERROR"
}
```

---

### 6.2 `get-sync-job`

Gets details of a sync job.

**Synopsis:**
```bash
aws iottwinmaker get-sync-job \
    --sync-source <value> \
    [--workspace-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sync-source` | **Yes** | string | -- | Sync source |
| `--workspace-id` | No | string | None | Workspace ID |

**Output Schema:**
```json
{
    "arn": "string",
    "workspaceId": "string",
    "syncSource": "string",
    "syncRole": "string",
    "status": {
        "state": "CREATING|INITIALIZING|ACTIVE|DELETING|ERROR",
        "error": {"code": "string", "message": "string"}
    },
    "creationDateTime": "timestamp",
    "updateDateTime": "timestamp"
}
```

---

### 6.3 `list-sync-jobs`

Lists sync jobs in a workspace. **Paginated operation.**

**Synopsis:**
```bash
aws iottwinmaker list-sync-jobs \
    --workspace-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | Workspace ID |
| `--max-results` | No | integer | 25 | Max results per page (1-250) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "syncJobSummaries": [
        {
            "arn": "string",
            "workspaceId": "string",
            "syncSource": "string",
            "status": {"state": "string", "error": {}},
            "creationDateTime": "timestamp",
            "updateDateTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 6.4 `delete-sync-job`

Deletes a sync job.

**Synopsis:**
```bash
aws iottwinmaker delete-sync-job \
    --workspace-id <value> \
    --sync-source <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | Workspace ID |
| `--sync-source` | **Yes** | string | -- | Sync source |

**Output Schema:**
```json
{
    "state": "CREATING|INITIALIZING|ACTIVE|DELETING|ERROR"
}
```

---

### 6.5 `list-sync-resources`

Lists resources managed by a sync job. **Paginated operation.**

**Synopsis:**
```bash
aws iottwinmaker list-sync-resources \
    --workspace-id <value> \
    --sync-source <value> \
    [--filters <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | Workspace ID |
| `--sync-source` | **Yes** | string | -- | Sync source |
| `--filters` | No | list | None | Filters (by `state`, `resourceType`, or `externalId`) |
| `--max-results` | No | integer | 25 | Max results per page (1-250) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "syncResources": [
        {
            "resourceType": "ENTITY|COMPONENT_TYPE",
            "externalId": "string",
            "status": {
                "state": "INITIALIZING|PROCESSING|DELETED|IN_SYNC|ERROR",
                "error": {"code": "string", "message": "string"}
            },
            "updateDateTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```
