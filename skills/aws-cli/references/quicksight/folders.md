# Folders

### 10.1 `create-folder`

Creates a folder to organize QuickSight resources.

**Synopsis:**
```bash
aws quicksight create-folder \
    --aws-account-id <value> \
    --folder-id <value> \
    --name <value> \
    [--folder-type <value>] \
    [--parent-folder-arn <value>] \
    [--permissions <value>] \
    [--tags <value>] \
    [--sharing-model <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--folder-id` | **Yes** | string | -- | Folder ID |
| `--name` | **Yes** | string | -- | Folder name (1-200 chars) |
| `--folder-type` | No | string | `SHARED` | `SHARED` or `RESTRICTED` |
| `--parent-folder-arn` | No | string | None | Parent folder ARN for nesting |
| `--permissions` | No | list | None | Resource permissions |
| `--tags` | No | list | None | Resource tags |
| `--sharing-model` | No | string | None | `ACCOUNT` or `NAMESPACE` |

**Output Schema:**
```json
{
    "Arn": "string",
    "FolderId": "string",
    "Status": "integer",
    "RequestId": "string"
}
```

---

### 10.2 `describe-folder`

Describes a folder.

**Synopsis:**
```bash
aws quicksight describe-folder \
    --aws-account-id <value> \
    --folder-id <value>
```

**Output Schema:**
```json
{
    "Folder": {
        "FolderId": "string",
        "Arn": "string",
        "Name": "string",
        "FolderType": "SHARED|RESTRICTED",
        "FolderPath": ["string"],
        "CreatedTime": "timestamp",
        "LastUpdatedTime": "timestamp",
        "SharingModel": "ACCOUNT|NAMESPACE"
    },
    "Status": "integer",
    "RequestId": "string"
}
```

---

### 10.3 `update-folder` / `delete-folder`

Update or delete a folder.

**Synopsis:**
```bash
aws quicksight update-folder --aws-account-id <value> --folder-id <value> --name <value>
aws quicksight delete-folder --aws-account-id <value> --folder-id <value>
```

---

### 10.4 `list-folders` / `search-folders`

List or search folders. **Paginated operations.**

**Synopsis:**
```bash
aws quicksight list-folders --aws-account-id <value>
aws quicksight search-folders --aws-account-id <value> --filters <value>
```

---

### 10.5 `create-folder-membership` / `delete-folder-membership`

Add or remove a resource from a folder.

**Synopsis:**
```bash
aws quicksight create-folder-membership \
    --aws-account-id <value> \
    --folder-id <value> \
    --member-id <value> \
    --member-type <value>

aws quicksight delete-folder-membership \
    --aws-account-id <value> \
    --folder-id <value> \
    --member-id <value> \
    --member-type <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--member-id` | **Yes** | string | -- | Resource ID to add/remove |
| `--member-type` | **Yes** | string | -- | `DASHBOARD`, `ANALYSIS`, `DATASET`, `DATASOURCE`, `TOPIC` |

---

### 10.6 `list-folder-members`

Lists members of a folder. **Paginated operation.**

**Synopsis:**
```bash
aws quicksight list-folder-members \
    --aws-account-id <value> \
    --folder-id <value>
```

---

### 10.7 `list-folders-for-resource`

Lists folders that contain a specific resource.

**Synopsis:**
```bash
aws quicksight list-folders-for-resource \
    --aws-account-id <value> \
    --resource-arn <value>
```

---

### 10.8 `describe-folder-permissions` / `describe-folder-resolved-permissions` / `update-folder-permissions`

Manage folder permissions.

**Synopsis:**
```bash
aws quicksight describe-folder-permissions --aws-account-id <value> --folder-id <value>
aws quicksight describe-folder-resolved-permissions --aws-account-id <value> --folder-id <value>
aws quicksight update-folder-permissions --aws-account-id <value> --folder-id <value> \
    [--grant-permissions <value>] [--revoke-permissions <value>]
```
