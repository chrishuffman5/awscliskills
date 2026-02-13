# Monitoring

### 4.1 `enable-enhanced-monitoring`

Enables enhanced shard-level CloudWatch metrics for a data stream.

**Synopsis:**
```bash
aws kinesis enable-enhanced-monitoring \
    [--stream-name <value>] \
    [--stream-arn <value>] \
    --shard-level-metrics <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-name` | No* | string | -- | Name of the stream |
| `--stream-arn` | No* | string | -- | ARN of the stream |
| `--shard-level-metrics` | **Yes** | list(string) | -- | Metrics to enable: `IncomingBytes`, `IncomingRecords`, `OutgoingBytes`, `OutgoingRecords`, `WriteProvisionedThroughputExceeded`, `ReadProvisionedThroughputExceeded`, `IteratorAgeMilliseconds`, `ALL` |

*Either `--stream-name` or `--stream-arn` must be provided.

**Output Schema:**
```json
{
    "StreamName": "string",
    "CurrentShardLevelMetrics": ["string"],
    "DesiredShardLevelMetrics": ["string"],
    "StreamARN": "string"
}
```

---

### 4.2 `disable-enhanced-monitoring`

Disables enhanced shard-level CloudWatch metrics for a data stream.

**Synopsis:**
```bash
aws kinesis disable-enhanced-monitoring \
    [--stream-name <value>] \
    [--stream-arn <value>] \
    --shard-level-metrics <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-name` | No* | string | -- | Name of the stream |
| `--stream-arn` | No* | string | -- | ARN of the stream |
| `--shard-level-metrics` | **Yes** | list(string) | -- | Metrics to disable: `IncomingBytes`, `IncomingRecords`, `OutgoingBytes`, `OutgoingRecords`, `WriteProvisionedThroughputExceeded`, `ReadProvisionedThroughputExceeded`, `IteratorAgeMilliseconds`, `ALL` |

*Either `--stream-name` or `--stream-arn` must be provided.

**Output Schema:**
```json
{
    "StreamName": "string",
    "CurrentShardLevelMetrics": ["string"],
    "DesiredShardLevelMetrics": ["string"],
    "StreamARN": "string"
}
```

---

### 4.3 `start-stream-encryption`

Enables server-side encryption using an AWS KMS key for a data stream. Asynchronous operation.

**Synopsis:**
```bash
aws kinesis start-stream-encryption \
    [--stream-name <value>] \
    [--stream-arn <value>] \
    --encryption-type <value> \
    --key-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-name` | No* | string | -- | Name of the stream |
| `--stream-arn` | No* | string | -- | ARN of the stream |
| `--encryption-type` | **Yes** | string | -- | Encryption type: `KMS` |
| `--key-id` | **Yes** | string | -- | KMS key ID, ARN, alias ARN, or `alias/aws/kinesis` |

*Either `--stream-name` or `--stream-arn` must be provided.

**Output:** None

---

### 4.4 `stop-stream-encryption`

Disables server-side encryption for a data stream. Asynchronous operation.

**Synopsis:**
```bash
aws kinesis stop-stream-encryption \
    [--stream-name <value>] \
    [--stream-arn <value>] \
    --encryption-type <value> \
    --key-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-name` | No* | string | -- | Name of the stream |
| `--stream-arn` | No* | string | -- | ARN of the stream |
| `--encryption-type` | **Yes** | string | -- | Encryption type: `KMS` |
| `--key-id` | **Yes** | string | -- | KMS key ID, ARN, alias ARN, or `alias/aws/kinesis` |

*Either `--stream-name` or `--stream-arn` must be provided.

**Output:** None
