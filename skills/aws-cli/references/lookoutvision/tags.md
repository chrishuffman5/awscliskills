# Tags

### 5.1 `tag-resource`

Adds one or more key-value tags to an Amazon Lookout for Vision model.

**Synopsis:**
```bash
aws lookoutvision tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the model to tag |
| `--tags` | **Yes** | list | -- | Tags to add |

**Tag Structure:**
```json
[
    {
        "Key": "string",
        "Value": "string"
    }
]
```

**Output:** None (returns empty object on success)

---

### 5.2 `untag-resource`

Removes one or more tags from an Amazon Lookout for Vision model.

**Synopsis:**
```bash
aws lookoutvision untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the model to untag |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output:** None (returns empty object on success)

---

### 5.3 `list-tags-for-resource`

Lists tags attached to an Amazon Lookout for Vision model.

**Synopsis:**
```bash
aws lookoutvision list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the model |

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
