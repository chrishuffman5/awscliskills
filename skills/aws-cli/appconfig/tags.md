# Tags

### 9.1 `tag-resource`

Assigns metadata tags to an AppConfig resource.

**Synopsis:**
```bash
aws appconfig tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag (20-2048 chars) |
| `--tags` | **Yes** | map | -- | Key-value tag pairs (max 50, key: 1-128 chars, value: 0-256 chars) |

**Output:** None

---

### 9.2 `untag-resource`

Removes metadata tags from an AppConfig resource.

**Synopsis:**
```bash
aws appconfig untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource (20-2048 chars) |
| `--tag-keys` | **Yes** | list | -- | Tag keys to remove |

**Output:** None

---

### 9.3 `list-tags-for-resource`

Lists tags for an AppConfig resource.

**Synopsis:**
```bash
aws appconfig list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource (20-2048 chars) |

**Output Schema:**
```json
{
    "Tags": {
        "string": "string"
    }
}
```
