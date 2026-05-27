# Workspaces

### 1.1 `create-workspace`

Creates a workspace for digital twin modeling.

**Synopsis:**
```bash
aws iottwinmaker create-workspace \
    --workspace-id <value> \
    [--description <value>] \
    [--s3-location <value>] \
    [--role <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | Workspace ID (1-128 chars) |
| `--description` | No | string | None | Description (0-2048 chars) |
| `--s3-location` | No | string | None | S3 bucket ARN for workspace resources |
| `--role` | No | string | None | Execution role ARN (20-2048 chars) |
| `--tags` | No | map | None | Tags (max 50) |

**Output Schema:**
```json
{
    "arn": "string",
    "creationDateTime": "timestamp"
}
```

---

### 1.2 `get-workspace`

Gets details of a workspace.

**Synopsis:**
```bash
aws iottwinmaker get-workspace \
    --workspace-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | Workspace ID |

**Output Schema:**
```json
{
    "workspaceId": "string",
    "arn": "string",
    "description": "string",
    "linkedServices": ["string"],
    "s3Location": "string",
    "role": "string",
    "creationDateTime": "timestamp",
    "updateDateTime": "timestamp"
}
```

---

### 1.3 `list-workspaces`

Lists workspaces. **Paginated operation.**

**Synopsis:**
```bash
aws iottwinmaker list-workspaces \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | 25 | Max results per page (1-250) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "workspaceSummaries": [
        {
            "workspaceId": "string",
            "arn": "string",
            "description": "string",
            "linkedServices": ["string"],
            "creationDateTime": "timestamp",
            "updateDateTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.4 `update-workspace`

Updates a workspace's description, role, or S3 location.

**Synopsis:**
```bash
aws iottwinmaker update-workspace \
    --workspace-id <value> \
    [--description <value>] \
    [--role <value>] \
    [--s3-location <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | Workspace ID |
| `--description` | No | string | None | Updated description |
| `--role` | No | string | None | Updated execution role ARN |
| `--s3-location` | No | string | None | Updated S3 bucket ARN |

**Output Schema:**
```json
{
    "updateDateTime": "timestamp"
}
```

---

### 1.5 `delete-workspace`

Deletes a workspace. All entities, component types, scenes, and sync jobs must be deleted first.

**Synopsis:**
```bash
aws iottwinmaker delete-workspace \
    --workspace-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | Workspace ID |

**Output Schema:**
```json
{
    "message": "string"
}
```
