# Tags

### 3.1 `tag-delivery-stream`

Adds or updates tags for a delivery stream. Max 50 tags per stream. Tags added during `create-delivery-stream` count toward this limit.

**Synopsis:**
```bash
aws firehose tag-delivery-stream \
    --delivery-stream-name <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--delivery-stream-name` | **Yes** | string | -- | Name of the delivery stream (1-64 chars) |
| `--tags` | **Yes** | list | -- | Tags to add. Shorthand: `Key=string,Value=string ...` |

**Tag Constraints:**
- Key: 1-128 Unicode characters
- Value: 0-256 Unicode characters
- Max 50 tags per stream
- Keys must be unique; duplicate keys overwrite existing values

**Output:** None

---

### 3.2 `untag-delivery-stream`

Removes tags from a delivery stream. Specify one or more tag keys to remove.

**Synopsis:**
```bash
aws firehose untag-delivery-stream \
    --delivery-stream-name <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--delivery-stream-name` | **Yes** | string | -- | Name of the delivery stream (1-64 chars) |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove (1-50 keys) |

**Output:** None

---

### 3.3 `list-tags-for-delivery-stream`

Lists tags for a delivery stream.

**Synopsis:**
```bash
aws firehose list-tags-for-delivery-stream \
    --delivery-stream-name <value> \
    [--exclusive-start-tag-key <value>] \
    [--limit <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--delivery-stream-name` | **Yes** | string | -- | Name of the delivery stream (1-64 chars) |
| `--exclusive-start-tag-key` | No | string | -- | Tag key to start listing after |
| `--limit` | No | integer | -- | Max tags to return |

**Output Schema:**
```json
{
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ],
    "HasMoreTags": "boolean"
}
```
