# Tags

### 14.1 `tag-resource`

Adds tags to a WorkMail organization resource.

**Synopsis:**
```bash
aws workmail tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN to tag |
| `--tags` | **Yes** | list | -- | Tags to add (Key/Value pairs) |

**Tags structure:**
```json
[
    {
        "Key": "string",
        "Value": "string"
    }
]
```

**Output:** None

---

### 14.2 `untag-resource`

Removes tags from a WorkMail organization resource.

**Synopsis:**
```bash
aws workmail untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN to untag |
| `--tag-keys` | **Yes** | list | -- | List of tag keys to remove |

**Output:** None

---

### 14.3 `list-tags-for-resource`

Lists tags for a WorkMail organization resource.

**Synopsis:**
```bash
aws workmail list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |

**Output Schema:**
```json
{
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```
