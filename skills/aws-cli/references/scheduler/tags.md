# Tags

### 3.1 `tag-resource`

Adds tags to a schedule group.

**Synopsis:**
```bash
aws scheduler tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Schedule group ARN |
| `--tags` | **Yes** | list | -- | Tags to add (Key/Value pairs, max 200) |

**Tags structure:**
```json
[
    {"Key": "string", "Value": "string"}
]
```

**Output:** None

---

### 3.2 `untag-resource`

Removes tags from a schedule group.

**Synopsis:**
```bash
aws scheduler untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Schedule group ARN |
| `--tag-keys` | **Yes** | list | -- | List of tag keys to remove |

**Output:** None

---

### 3.3 `list-tags-for-resource`

Lists tags for a schedule group.

**Synopsis:**
```bash
aws scheduler list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Schedule group ARN |

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
