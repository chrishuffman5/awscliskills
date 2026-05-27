# Tags

### 5.1 `tag-resource`

Adds tags to a MediaStore container.

**Synopsis:**
```bash
aws mediastore tag-resource \
    --resource <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource` | **Yes** | string | -- | ARN of the container |
| `--tags` | **Yes** | list | -- | Tags as Key/Value structures (max 50 per container) |

**Tags Structure:**
```
Key=environment,Value=production Key=team,Value=media
```

**Output:** None

---

### 5.2 `untag-resource`

Removes tags from a MediaStore container.

**Synopsis:**
```bash
aws mediastore untag-resource \
    --resource <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource` | **Yes** | string | -- | ARN of the container |
| `--tag-keys` | **Yes** | list | -- | List of tag keys to remove |

**Output:** None

---

### 5.3 `list-tags-for-resource`

Lists all tags for a MediaStore container.

**Synopsis:**
```bash
aws mediastore list-tags-for-resource \
    --resource <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource` | **Yes** | string | -- | ARN of the container |

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
