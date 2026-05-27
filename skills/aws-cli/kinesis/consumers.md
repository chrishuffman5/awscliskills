# Consumers

### 3.1 `register-stream-consumer`

Registers a stream consumer with a data stream for enhanced fan-out. Each consumer gets dedicated 2 MiB/sec read throughput per shard.

**Synopsis:**
```bash
aws kinesis register-stream-consumer \
    --stream-arn <value> \
    --consumer-name <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-arn` | **Yes** | string | -- | ARN of the stream to register the consumer with |
| `--consumer-name` | **Yes** | string | -- | Consumer name (1-128 chars, pattern: `[a-zA-Z0-9_.-]+`) |
| `--tags` | No | map | None | Key-value tags (max 50) |

**Output Schema:**
```json
{
    "Consumer": {
        "ConsumerName": "string",
        "ConsumerARN": "string",
        "ConsumerStatus": "CREATING|DELETING|ACTIVE",
        "ConsumerCreationTimestamp": "timestamp"
    }
}
```

---

### 3.2 `deregister-stream-consumer`

Deregisters a stream consumer. The consumer is deleted and can no longer be used.

**Synopsis:**
```bash
aws kinesis deregister-stream-consumer \
    [--stream-arn <value>] \
    [--consumer-name <value>] \
    [--consumer-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-arn` | No* | string | -- | ARN of the stream (use with `--consumer-name`) |
| `--consumer-name` | No* | string | -- | Name of the consumer (use with `--stream-arn`) |
| `--consumer-arn` | No* | string | -- | ARN of the consumer (alternative to name + stream ARN) |

*Provide either `--consumer-arn` alone, or both `--stream-arn` and `--consumer-name`.

**Output:** None

---

### 3.3 `describe-stream-consumer`

Describes a stream consumer, including its status and creation timestamp.

**Synopsis:**
```bash
aws kinesis describe-stream-consumer \
    [--stream-arn <value>] \
    [--consumer-name <value>] \
    [--consumer-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-arn` | No* | string | -- | ARN of the stream (use with `--consumer-name`) |
| `--consumer-name` | No* | string | -- | Name of the consumer (use with `--stream-arn`) |
| `--consumer-arn` | No* | string | -- | ARN of the consumer (alternative to name + stream ARN) |

*Provide either `--consumer-arn` alone, or both `--stream-arn` and `--consumer-name`.

**Output Schema:**
```json
{
    "ConsumerDescription": {
        "ConsumerName": "string",
        "ConsumerARN": "string",
        "ConsumerStatus": "CREATING|DELETING|ACTIVE",
        "ConsumerCreationTimestamp": "timestamp",
        "StreamARN": "string"
    }
}
```

---

### 3.4 `list-stream-consumers`

Lists the consumers registered to a data stream. **Paginated operation.**

**Synopsis:**
```bash
aws kinesis list-stream-consumers \
    --stream-arn <value> \
    [--stream-creation-timestamp <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-arn` | **Yes** | string | -- | ARN of the stream |
| `--stream-creation-timestamp` | No | timestamp | -- | Filter by stream creation time (for streams with same name) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Consumers": [
        {
            "ConsumerName": "string",
            "ConsumerARN": "string",
            "ConsumerStatus": "CREATING|DELETING|ACTIVE",
            "ConsumerCreationTimestamp": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
