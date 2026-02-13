# Kinesis Streaming Destination

### 14.1 `enable-kinesis-streaming-destination`

Starts streaming table changes to a Kinesis data stream.

**Synopsis:**
```bash
aws dynamodb enable-kinesis-streaming-destination \
    --table-name <value> \
    --stream-arn <value> \
    [--enable-kinesis-streaming-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-name` | **Yes** | string | -- | Table name or ARN (1-1024 chars) |
| `--stream-arn` | **Yes** | string | -- | Kinesis data stream ARN (37-1024 chars) |
| `--enable-kinesis-streaming-configuration` | No | structure | -- | `ApproximateCreationDateTimePrecision=MILLISECOND\|MICROSECOND` |

**Output Schema:**
```json
{
    "TableName": "string",
    "StreamArn": "string",
    "DestinationStatus": "ENABLING|ACTIVE|DISABLING|DISABLED|ENABLE_FAILED|UPDATING",
    "EnableKinesisStreamingConfiguration": {
        "ApproximateCreationDateTimePrecision": "MILLISECOND|MICROSECOND"
    }
}
```

---

### 14.2 `disable-kinesis-streaming-destination`

Stops streaming table changes to a Kinesis data stream.

**Synopsis:**
```bash
aws dynamodb disable-kinesis-streaming-destination \
    --table-name <value> \
    --stream-arn <value> \
    [--enable-kinesis-streaming-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-name` | **Yes** | string | -- | Table name or ARN (1-1024 chars) |
| `--stream-arn` | **Yes** | string | -- | Kinesis data stream ARN (37-1024 chars) |
| `--enable-kinesis-streaming-configuration` | No | structure | -- | Streaming configuration |

**Output Schema:** Same as `enable-kinesis-streaming-destination`.

---

### 14.3 `describe-kinesis-streaming-destination`

Describes Kinesis streaming destination settings for a table.

**Synopsis:**
```bash
aws dynamodb describe-kinesis-streaming-destination \
    --table-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-name` | **Yes** | string | -- | Table name or ARN (1-1024 chars) |

**Output Schema:**
```json
{
    "TableName": "string",
    "KinesisDataStreamDestinations": [
        {
            "StreamArn": "string",
            "DestinationStatus": "ENABLING|ACTIVE|DISABLING|DISABLED|ENABLE_FAILED|UPDATING",
            "DestinationStatusDescription": "string",
            "ApproximateCreationDateTimePrecision": "MILLISECOND|MICROSECOND"
        }
    ]
}
```

---

### 14.4 `update-kinesis-streaming-destination`

Updates Kinesis streaming destination settings for a table.

**Synopsis:**
```bash
aws dynamodb update-kinesis-streaming-destination \
    --table-name <value> \
    --stream-arn <value> \
    [--update-kinesis-streaming-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-name` | **Yes** | string | -- | Table name or ARN (1-1024 chars) |
| `--stream-arn` | **Yes** | string | -- | Kinesis data stream ARN (37-1024 chars) |
| `--update-kinesis-streaming-configuration` | No | structure | -- | `ApproximateCreationDateTimePrecision=MILLISECOND\|MICROSECOND` |

**Output Schema:**
```json
{
    "TableName": "string",
    "StreamArn": "string",
    "DestinationStatus": "ENABLING|ACTIVE|DISABLING|DISABLED|ENABLE_FAILED|UPDATING",
    "UpdateKinesisStreamingConfiguration": {
        "ApproximateCreationDateTimePrecision": "MILLISECOND|MICROSECOND"
    }
}
```

---
