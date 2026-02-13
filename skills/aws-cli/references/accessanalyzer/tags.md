# Tags

### 6.1 `tag-resource`

Adds tags to the specified resource.

**Synopsis:**
```bash
aws accessanalyzer tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | The ARN of the resource to tag |
| `--tags` | **Yes** | map | -- | Key-value pairs to apply. Key: 1-128 chars (no `aws:` prefix), Value: 0-256 chars |

**Output:** None

---

### 6.2 `untag-resource`

Removes tags from the specified resource.

**Synopsis:**
```bash
aws accessanalyzer untag-resource \
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

### 6.3 `list-tags-for-resource`

Lists the tags applied to the specified resource.

**Synopsis:**
```bash
aws accessanalyzer list-tags-for-resource \
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
