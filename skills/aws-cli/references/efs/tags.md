# Tags

### 5.1 `tag-resource`

Creates a tag for an EFS resource (file system or access point).

**Synopsis:**
```bash
aws efs tag-resource \
    --resource-id <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | ID of the resource to tag (file system ID or access point ID) |
| `--tags` | **Yes** | list | -- | Tags to add (max 50 per resource). Shorthand: `Key=string,Value=string ...` |

**Output:** None on success.

---

### 5.2 `untag-resource`

Removes tags from an EFS resource.

**Synopsis:**
```bash
aws efs untag-resource \
    --resource-id <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | ID of the resource to untag |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output:** None on success.

---

### 5.3 `list-tags-for-resource`

Lists all tags for an EFS resource. **Paginated operation.**

**Synopsis:**
```bash
aws efs list-tags-for-resource \
    --resource-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | ID of the resource |
| `--max-results` | No | integer | None | Maximum number of results (1-100) |
| `--next-token` | No | string | None | Pagination token from previous response |

**Output Schema:**
```json
{
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.4 `create-tags` (Legacy)

> **Deprecated:** Use `tag-resource` instead. This API only works with file system IDs.

Creates or overwrites tags associated with a file system.

**Synopsis:**
```bash
aws efs create-tags \
    --file-system-id <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-id` | **Yes** | string | -- | ID of the file system |
| `--tags` | **Yes** | list | -- | Tags to create. Shorthand: `Key=string,Value=string ...` |

**Output:** None on success.

---

### 5.5 `delete-tags` (Legacy)

> **Deprecated:** Use `untag-resource` instead. This API only works with file system IDs.

Deletes the specified tags from a file system.

**Synopsis:**
```bash
aws efs delete-tags \
    --file-system-id <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-id` | **Yes** | string | -- | ID of the file system |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to delete |

**Output:** None on success.
