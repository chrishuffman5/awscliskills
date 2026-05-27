# Tags

### 8.1 `tag-resource`

Adds tags to an SWF resource (domain).

**Synopsis:**
```bash
aws swf tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag (1-1600 chars) |
| `--tags` | **Yes** | list | -- | Tags to add. Shorthand: `key=string,value=string ...` |

**Tag Constraints:**
- Key: 1-128 chars, unicode letters, digits, whitespace, `_ . : / = + - @`
- Value: max 256 chars, same character set

**Output:** None

---

### 8.2 `untag-resource`

Removes tags from an SWF resource.

**Synopsis:**
```bash
aws swf untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource (1-1600 chars) |
| `--tag-keys` | **Yes** | list | -- | List of tag keys to remove. Space-separated |

**Output:** None

---

### 8.3 `list-tags-for-resource`

Lists tags for an SWF resource.

**Synopsis:**
```bash
aws swf list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource (1-1600 chars) |

**Output Schema:**
```json
{
    "tags": [
        {
            "key": "string",
            "value": "string"
        }
    ]
}
```
