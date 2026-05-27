# Tags

### 12.1 `tag-resource`

Adds tags to a Q Connect resource.

**Synopsis:**
```bash
aws qconnect tag-resource \
    --resource-arn <value> \
    --tags <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tags` | **Yes** | map | -- | Tags (key: 1-128 chars, value: 1-256 chars) |

**Output:** None

---

### 12.2 `untag-resource`

Removes tags from a Q Connect resource.

**Synopsis:**
```bash
aws qconnect untag-resource \
    --resource-arn <value> \
    --tag-keys <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tag-keys` | **Yes** | list | -- | Tag keys to remove |

**Output:** None

---

### 12.3 `list-tags-for-resource`

Lists tags for a Q Connect resource.

**Synopsis:**
```bash
aws qconnect list-tags-for-resource \
    --resource-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |

**Output Schema:**
```json
{
    "tags": {
        "string": "string"
    }
}
```
