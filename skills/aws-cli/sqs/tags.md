# Tags

### 5.1 `tag-queue`

Adds cost allocation tags to the specified queue. Max 50 tags per queue. Tags with existing keys overwrite previous values.

**Synopsis:**
```bash
aws sqs tag-queue \
    --queue-url <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--queue-url` | **Yes** | string | -- | URL of the queue |
| `--tags` | **Yes** | map | -- | Key-value pairs. Shorthand: `Key1=Value1,Key2=Value2` |

**Output:** None

---

### 5.2 `untag-queue`

Removes cost allocation tags from the specified queue.

**Synopsis:**
```bash
aws sqs untag-queue \
    --queue-url <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--queue-url` | **Yes** | string | -- | URL of the queue |
| `--tag-keys` | **Yes** | list | -- | List of tag keys to remove |

**Output:** None

---

### 5.3 `list-queue-tags`

Lists all cost allocation tags for the specified queue.

**Synopsis:**
```bash
aws sqs list-queue-tags \
    --queue-url <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--queue-url` | **Yes** | string | -- | URL of the queue |

**Output Schema:**
```json
{
    "Tags": {
        "string": "string"
    }
}
```
