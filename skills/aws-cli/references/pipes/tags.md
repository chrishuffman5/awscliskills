# Tags

### 2.1 `tag-resource`

Assigns tags to a pipe.

**Synopsis:**
```bash
aws pipes tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the pipe (1-1600 chars) |
| `--tags` | **Yes** | map | -- | Key-value tag pairs (max 50, key: 1-128 chars, value: 0-256 chars) |

**Output:** None

---

### 2.2 `untag-resource`

Removes tags from a pipe.

**Synopsis:**
```bash
aws pipes untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the pipe (1-1600 chars) |
| `--tag-keys` | **Yes** | list | -- | Tag keys to remove |

**Output:** None

---

### 2.3 `list-tags-for-resource`

Lists tags for a pipe.

**Synopsis:**
```bash
aws pipes list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the pipe (1-1600 chars) |

**Output Schema:**
```json
{
    "tags": {
        "string": "string"
    }
}
```
