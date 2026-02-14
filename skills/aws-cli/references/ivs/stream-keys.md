# Stream Keys

### 2.1 `create-stream-key`

Creates a stream key for a channel, used by the broadcaster to authenticate and start streaming.

**Synopsis:**
```bash
aws ivs create-stream-key \
    --channel-arn <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | ARN of the channel |
| `--tags` | No | map | None | Key-value tag pairs |

**Output Schema:**
```json
{
    "streamKey": {
        "arn": "string",
        "channelArn": "string",
        "value": "string",
        "tags": {"string": "string"}
    }
}
```

---

### 2.2 `get-stream-key`

Gets details for a stream key.

**Synopsis:**
```bash
aws ivs get-stream-key \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the stream key |

**Output Schema:** Same as `create-stream-key` output.

---

### 2.3 `batch-get-stream-key`

Gets details for multiple stream keys in a single call.

**Synopsis:**
```bash
aws ivs batch-get-stream-key \
    --arns <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arns` | **Yes** | list | -- | List of stream key ARNs (max 50) |

**Output Schema:**
```json
{
    "streamKeys": [{}],
    "errors": [{"arn": "string", "code": "string", "message": "string"}]
}
```

---

### 2.4 `list-stream-keys`

Lists stream keys for a channel. **Paginated operation.**

**Synopsis:**
```bash
aws ivs list-stream-keys \
    --channel-arn <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | ARN of the channel |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page |

**Output Schema:**
```json
{
    "streamKeys": [{"arn": "string", "channelArn": "string", "tags": {}}],
    "nextToken": "string"
}
```

---

### 2.5 `delete-stream-key`

Deletes a stream key.

**Synopsis:**
```bash
aws ivs delete-stream-key \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the stream key to delete |

**Output:** None
