# Tags

### 9.1 `tag-resource`

Adds or edits tags on a KMS key.

**Synopsis:**
```bash
aws kms tag-resource \
    --key-id <value> \
    --tags <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Key ID or key ARN (1-2048 chars) |
| `--tags` | **Yes** | list | -- | Tags to add. Shorthand: `TagKey=string,TagValue=string ...`. Max 50 tags per key |

**Output:** None

---

### 9.2 `untag-resource`

Removes tags from a KMS key.

**Synopsis:**
```bash
aws kms untag-resource \
    --key-id <value> \
    --tag-keys <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Key ID or key ARN (1-2048 chars) |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output:** None

---

### 9.3 `list-resource-tags`

Lists tags on a KMS key. **Paginated.**

**Synopsis:**
```bash
aws kms list-resource-tags \
    --key-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Key ID or key ARN (1-2048 chars) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Tags": [
        {
            "TagKey": "string",
            "TagValue": "string"
        }
    ],
    "NextMarker": "string",
    "Truncated": true|false
}
```

---
