# Tags

### 4.1 `create-tags`

Adds tags to an Amazon MQ resource.

**Synopsis:**
```bash
aws mq create-tags \
    --resource-arn <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tags` | No | map | None | Tags to add (key-value pairs) |

**Output:** None

---

### 4.2 `list-tags`

Lists tags for an Amazon MQ resource.

**Synopsis:**
```bash
aws mq list-tags \
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
    "Tags": {
        "string": "string"
    }
}
```

---

### 4.3 `delete-tags`

Removes tags from an Amazon MQ resource.

**Synopsis:**
```bash
aws mq delete-tags \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tag-keys` | **Yes** | list | -- | List of tag keys to remove |

**Output:** None
