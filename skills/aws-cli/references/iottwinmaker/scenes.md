# Scenes

### 4.1 `create-scene`

Creates a 3D scene in a workspace.

**Synopsis:**
```bash
aws iottwinmaker create-scene \
    --workspace-id <value> \
    --scene-id <value> \
    --content-location <value> \
    [--description <value>] \
    [--capabilities <value>] \
    [--scene-metadata <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | Workspace ID |
| `--scene-id` | **Yes** | string | -- | Scene ID (1-128 chars) |
| `--content-location` | **Yes** | string | -- | S3 URI for scene definition file |
| `--description` | No | string | None | Description (0-2048 chars) |
| `--capabilities` | No | list | None | Scene capabilities (max 50) |
| `--scene-metadata` | No | map | None | Scene metadata key-value pairs (max 50) |
| `--tags` | No | map | None | Tags (max 50) |

**Output Schema:**
```json
{
    "arn": "string",
    "creationDateTime": "timestamp"
}
```

---

### 4.2 `get-scene`

Gets details of a scene.

**Synopsis:**
```bash
aws iottwinmaker get-scene \
    --workspace-id <value> \
    --scene-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | Workspace ID |
| `--scene-id` | **Yes** | string | -- | Scene ID |

**Output Schema:**
```json
{
    "workspaceId": "string",
    "sceneId": "string",
    "contentLocation": "string",
    "arn": "string",
    "description": "string",
    "capabilities": ["string"],
    "sceneMetadata": {"key": "value"},
    "generatedSceneMetadata": {"key": "value"},
    "creationDateTime": "timestamp",
    "updateDateTime": "timestamp",
    "error": {"code": "string", "message": "string"}
}
```

---

### 4.3 `list-scenes`

Lists scenes in a workspace. **Paginated operation.**

**Synopsis:**
```bash
aws iottwinmaker list-scenes \
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
    "sceneSummaries": [
        {
            "sceneId": "string",
            "contentLocation": "string",
            "arn": "string",
            "creationDateTime": "timestamp",
            "updateDateTime": "timestamp",
            "description": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 4.4 `update-scene`

Updates a scene.

**Synopsis:**
```bash
aws iottwinmaker update-scene \
    --workspace-id <value> \
    --scene-id <value> \
    [--content-location <value>] \
    [--description <value>] \
    [--capabilities <value>] \
    [--scene-metadata <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | Workspace ID |
| `--scene-id` | **Yes** | string | -- | Scene ID |
| `--content-location` | No | string | None | Updated S3 URI |
| `--description` | No | string | None | Updated description |
| `--capabilities` | No | list | None | Updated capabilities |
| `--scene-metadata` | No | map | None | Updated metadata |

**Output Schema:**
```json
{
    "updateDateTime": "timestamp"
}
```

---

### 4.5 `delete-scene`

Deletes a scene.

**Synopsis:**
```bash
aws iottwinmaker delete-scene \
    --workspace-id <value> \
    --scene-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | Workspace ID |
| `--scene-id` | **Yes** | string | -- | Scene ID |

**Output:** None
