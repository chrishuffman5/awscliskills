# Tags

### 4.1 `tag-resource`

Adds tags to a Control Tower resource.

**Synopsis:**
```bash
aws controltower tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | The ARN of the resource to tag |
| `--tags` | **Yes** | map | -- | Key-value pairs to apply (max 200). Key: 1-128 chars, Value: 0-256 chars |

**Output:** None

---

### 4.2 `untag-resource`

Removes tags from a Control Tower resource.

**Synopsis:**
```bash
aws controltower untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | The ARN of the resource to untag |
| `--tag-keys` | **Yes** | list(string) | -- | List of tag keys to remove |

**Output:** None

---

### 4.3 `list-tags-for-resource`

Lists tags for a Control Tower resource.

**Synopsis:**
```bash
aws controltower list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | The ARN of the resource |

**Output Schema:**
```json
{
    "tags": {
        "string": "string"
    }
}
```
