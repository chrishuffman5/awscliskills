# Workspaces

### 23.1 `create-workspace`

Creates a workspace for the specified instance.

**Synopsis:**
```bash
aws connect create-workspace \
    --instance-id <value> \
    --name <value> \
    [--description <value>] \
    [--theme <value>] \
    [--title <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--name` | **Yes** | string | -- | Workspace name (1-127 chars, unique per instance) |
| `--description` | No | string | None | Description (max 250 chars) |
| `--theme` | No | structure | None | Theme config (Light/Dark modes with Palette, Images, Typography) |
| `--title` | No | string | None | Display title (0-127 chars) |
| `--tags` | No | map | None | Tags (max 50) |

**Output Schema:**
```json
{
    "WorkspaceId": "string",
    "WorkspaceArn": "string"
}
```

---

### 23.2 `describe-workspace`

Describes a workspace.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--workspace-id` | **Yes** | string | -- | Workspace ID |

**Output Schema:**
```json
{
    "Workspace": {
        "WorkspaceId": "string",
        "WorkspaceArn": "string",
        "Name": "string",
        "Description": "string",
        "Title": "string",
        "Theme": {},
        "Status": "string",
        "Visibility": "string",
        "Tags": { "key": "value" },
        "LastModifiedTime": "timestamp",
        "CreatedTime": "timestamp"
    }
}
```

---

### 23.3 `list-workspaces`

Lists workspaces. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results |

---

### 23.4-23.6 Workspace Update Commands

`update-workspace-metadata`, `update-workspace-visibility`, `update-workspace-theme` update workspace properties. All require `--instance-id` and `--workspace-id`.

**Output:** None

---

### 23.7 `delete-workspace`

Deletes a workspace.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--workspace-id` | **Yes** | string | -- | Workspace ID |

**Output:** None

---

### 23.8-23.10 Search & Association Commands

`search-workspaces`, `search-workspace-associations`, `associate-workspace`, `disassociate-workspace` manage workspace searching and associations. All require `--instance-id`.

---

### 23.11-23.14 Workspace Page Commands

`create-workspace-page`, `list-workspace-pages`, `update-workspace-page`, `delete-workspace-page` manage pages within workspaces. All require `--instance-id` and `--workspace-id`.

---

### 23.15-23.17 Workspace Media Commands

`import-workspace-media`, `list-workspace-media`, `delete-workspace-media` manage media assets in workspaces. All require `--instance-id` and `--workspace-id`.
