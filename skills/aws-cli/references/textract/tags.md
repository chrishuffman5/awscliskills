# Tags

### 4.1 `tag-resource`

Adds or overwrites tags for a Textract resource (adapters).

**Synopsis:**
```bash
aws textract tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag (1-1011 chars) |
| `--tags` | **Yes** | map | -- | Key-value tags (max 200). Key: 1-128 chars, Value: 0-256 chars |

**Tag Constraints:**
- Key pattern: `^(?!aws:)[\p{L}\p{Z}\p{N}_.:/=+\-@]*$`
- Value pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-@]*)$`
- Tags prefixed with `aws:` are reserved

**Output:** None

---

### 4.2 `untag-resource`

Removes tags from a Textract resource.

**Synopsis:**
```bash
aws textract untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to untag (1-1011 chars) |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove (max 200 keys, each 1-128 chars) |

**Output:** None

---

### 4.3 `list-tags-for-resource`

Lists all tags for a Textract resource.

**Synopsis:**
```bash
aws textract list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource (1-1011 chars) |

**Output Schema:**
```json
{
    "Tags": {
        "key": "value"
    }
}
```
