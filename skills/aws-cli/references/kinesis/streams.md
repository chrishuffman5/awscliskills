# Streams

### 1.1 `create-stream`

Creates a new Kinesis data stream. The operation is asynchronous — the stream status starts as `CREATING` and transitions to `ACTIVE`.

**Synopsis:**
```bash
aws kinesis create-stream \
    --stream-name <value> \
    [--shard-count <value>] \
    [--stream-mode-details <value>] \
    [--tags <value>] \
    [--warm-throughput-mi-bps <value>] \
    [--max-record-size-in-ki-b <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-name` | **Yes** | string | -- | Stream name (1-128 chars, pattern: `[a-zA-Z0-9_.-]+`) |
| `--shard-count` | No | integer | -- | Number of shards (required for `PROVISIONED` mode, min: 1) |
| `--stream-mode-details` | No | structure | `PROVISIONED` | Capacity mode. Shorthand: `StreamMode=PROVISIONED\|ON_DEMAND` |
| `--tags` | No | map | None | Key-value tags (max 50). Shorthand: `KeyName1=string,KeyName2=string` |
| `--warm-throughput-mi-bps` | No | integer | -- | Target warm throughput in MiB/s (on-demand streams, min: 0) |
| `--max-record-size-in-ki-b` | No | integer | -- | Max record size in KiB (1024-10240) |

**Output:** None

---

### 1.2 `delete-stream`

Deletes a data stream, including all shards and data. The operation is asynchronous.

**Synopsis:**
```bash
aws kinesis delete-stream \
    [--stream-name <value>] \
    [--stream-arn <value>] \
    [--enforce-consumer-deletion | --no-enforce-consumer-deletion] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-name` | No* | string | -- | Name of the stream to delete |
| `--stream-arn` | No* | string | -- | ARN of the stream to delete |
| `--enforce-consumer-deletion` | No | boolean | false | If true, deletes stream even if it has registered consumers |

*Either `--stream-name` or `--stream-arn` must be provided.

**Output:** None

---

### 1.3 `describe-stream`

Describes a data stream including shard list. **Paginated operation.** For summary without shard list, use `describe-stream-summary`.

**Synopsis:**
```bash
aws kinesis describe-stream \
    [--stream-name <value>] \
    [--stream-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-name` | No* | string | -- | Name of the stream |
| `--stream-arn` | No* | string | -- | ARN of the stream |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

*Either `--stream-name` or `--stream-arn` must be provided.

**Output Schema:**
```json
{
    "StreamDescription": {
        "StreamName": "string",
        "StreamARN": "string",
        "StreamStatus": "CREATING|DELETING|ACTIVE|UPDATING",
        "StreamModeDetails": {
            "StreamMode": "PROVISIONED|ON_DEMAND"
        },
        "Shards": [
            {
                "ShardId": "string",
                "ParentShardId": "string",
                "AdjacentParentShardId": "string",
                "HashKeyRange": {
                    "StartingHashKey": "string",
                    "EndingHashKey": "string"
                },
                "SequenceNumberRange": {
                    "StartingSequenceNumber": "string",
                    "EndingSequenceNumber": "string"
                }
            }
        ],
        "HasMoreShards": "boolean",
        "RetentionPeriodHours": "integer",
        "StreamCreationTimestamp": "timestamp",
        "EnhancedMonitoring": [
            {
                "ShardLevelMetrics": ["string"]
            }
        ],
        "EncryptionType": "NONE|KMS",
        "KeyId": "string"
    }
}
```

---

### 1.4 `describe-stream-summary`

Returns a summary of stream properties without the shard list. More efficient than `describe-stream` for large streams.

**Synopsis:**
```bash
aws kinesis describe-stream-summary \
    [--stream-name <value>] \
    [--stream-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-name` | No* | string | -- | Name of the stream |
| `--stream-arn` | No* | string | -- | ARN of the stream |

*Either `--stream-name` or `--stream-arn` must be provided.

**Output Schema:**
```json
{
    "StreamDescriptionSummary": {
        "StreamName": "string",
        "StreamARN": "string",
        "StreamStatus": "CREATING|DELETING|ACTIVE|UPDATING",
        "StreamModeDetails": {
            "StreamMode": "PROVISIONED|ON_DEMAND"
        },
        "RetentionPeriodHours": "integer",
        "StreamCreationTimestamp": "timestamp",
        "EnhancedMonitoring": [
            {
                "ShardLevelMetrics": ["string"]
            }
        ],
        "EncryptionType": "NONE|KMS",
        "KeyId": "string",
        "OpenShardCount": "integer",
        "ConsumerCount": "integer"
    }
}
```

---

### 1.5 `list-streams`

Lists data streams in the account. **Paginated operation.**

**Synopsis:**
```bash
aws kinesis list-streams \
    [--exclusive-start-stream-name <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--exclusive-start-stream-name` | No | string | -- | Name of stream to start listing after |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "StreamNames": ["string"],
    "HasMoreStreams": "boolean",
    "StreamSummaries": [
        {
            "StreamName": "string",
            "StreamARN": "string",
            "StreamStatus": "CREATING|DELETING|ACTIVE|UPDATING",
            "StreamModeDetails": {
                "StreamMode": "PROVISIONED|ON_DEMAND"
            },
            "StreamCreationTimestamp": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.6 `update-stream-mode`

Updates the capacity mode of a data stream. Switches between `PROVISIONED` and `ON_DEMAND`.

**Synopsis:**
```bash
aws kinesis update-stream-mode \
    --stream-arn <value> \
    --stream-mode-details <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-arn` | **Yes** | string | -- | ARN of the stream |
| `--stream-mode-details` | **Yes** | structure | -- | New stream mode. Shorthand: `StreamMode=PROVISIONED\|ON_DEMAND` |

**Output:** None

---

### 1.7 `increase-stream-retention-period`

Increases the data retention period of a stream. Maximum retention is 8760 hours (365 days).

**Synopsis:**
```bash
aws kinesis increase-stream-retention-period \
    [--stream-name <value>] \
    [--stream-arn <value>] \
    --retention-period-hours <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-name` | No* | string | -- | Name of the stream |
| `--stream-arn` | No* | string | -- | ARN of the stream |
| `--retention-period-hours` | **Yes** | integer | -- | New retention period in hours (max 8760) |

*Either `--stream-name` or `--stream-arn` must be provided.

**Output:** None

---

### 1.8 `decrease-stream-retention-period`

Decreases the data retention period of a stream. Minimum retention is 24 hours.

**Synopsis:**
```bash
aws kinesis decrease-stream-retention-period \
    [--stream-name <value>] \
    [--stream-arn <value>] \
    --retention-period-hours <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-name` | No* | string | -- | Name of the stream |
| `--stream-arn` | No* | string | -- | ARN of the stream |
| `--retention-period-hours` | **Yes** | integer | -- | New retention period in hours (min 24) |

*Either `--stream-name` or `--stream-arn` must be provided.

**Output:** None

---

### 1.9 `update-stream-warm-throughput`

Updates the warm throughput target for an on-demand data stream.

**Synopsis:**
```bash
aws kinesis update-stream-warm-throughput \
    [--stream-name <value>] \
    [--stream-arn <value>] \
    --warm-throughput-mi-bps <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-name` | No* | string | -- | Name of the stream |
| `--stream-arn` | No* | string | -- | ARN of the stream |
| `--warm-throughput-mi-bps` | **Yes** | integer | -- | Target warm throughput in MiB/s (min: 0) |

*Either `--stream-name` or `--stream-arn` must be provided.

**Output:** None

---

### 1.10 `update-max-record-size`

Updates the maximum record size for a data stream.

**Synopsis:**
```bash
aws kinesis update-max-record-size \
    [--stream-name <value>] \
    [--stream-arn <value>] \
    --max-record-size-in-ki-b <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-name` | No* | string | -- | Name of the stream |
| `--stream-arn` | No* | string | -- | ARN of the stream |
| `--max-record-size-in-ki-b` | **Yes** | integer | -- | Max record size in KiB (1024-10240) |

*Either `--stream-name` or `--stream-arn` must be provided.

**Output:** None
