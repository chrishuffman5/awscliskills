# Streams

### 3.1 `stream-journal-to-kinesis`

Creates a journal stream for a given QLDB ledger. The stream captures every document revision committed to the journal and delivers the data to a specified Amazon Kinesis Data Streams resource.

**Synopsis:**
```bash
aws qldb stream-journal-to-kinesis \
    --ledger-name <value> \
    --role-arn <value> \
    --inclusive-start-time <value> \
    --kinesis-configuration <value> \
    --stream-name <value> \
    [--tags <value>] \
    [--exclusive-end-time <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ledger-name` | **Yes** | string | -- | Name of the ledger |
| `--role-arn` | **Yes** | string | -- | IAM role ARN with permissions to write to the Kinesis stream |
| `--inclusive-start-time` | **Yes** | timestamp | -- | Start of the time range (inclusive), ISO 8601 format |
| `--kinesis-configuration` | **Yes** | structure | -- | Kinesis Data Streams configuration. Shorthand: `StreamArn=string,AggregationEnabled=boolean` |
| `--stream-name` | **Yes** | string | -- | Name to assign to the QLDB journal stream (unique per ledger) |
| `--tags` | No | map | None | Key-value tag pairs. Shorthand: `KeyName1=string,KeyName2=string` |
| `--exclusive-end-time` | No | timestamp | None | End of the time range (exclusive); if omitted, the stream runs indefinitely |

**Kinesis Configuration Structure:**
```json
{
    "StreamArn": "string",
    "AggregationEnabled": true|false
}
```

**Output Schema:**
```json
{
    "StreamId": "string"
}
```

---

### 3.2 `describe-journal-kinesis-stream`

Returns detailed information about a given QLDB journal stream, including its ARN, stream name, current status, creation time, and original stream creation parameters.

**Synopsis:**
```bash
aws qldb describe-journal-kinesis-stream \
    --ledger-name <value> \
    --stream-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ledger-name` | **Yes** | string | -- | Name of the ledger |
| `--stream-id` | **Yes** | string | -- | Unique ID of the QLDB journal stream |

**Output Schema:**
```json
{
    "Stream": {
        "LedgerName": "string",
        "CreationTime": "timestamp",
        "InclusiveStartTime": "timestamp",
        "ExclusiveEndTime": "timestamp",
        "RoleArn": "string",
        "StreamId": "string",
        "Arn": "string",
        "Status": "ACTIVE|COMPLETED|CANCELED|FAILED|IMPAIRED",
        "KinesisConfiguration": {
            "StreamArn": "string",
            "AggregationEnabled": true|false
        },
        "ErrorCause": "KINESIS_STREAM_NOT_FOUND|IAM_PERMISSION_REVOKED",
        "StreamName": "string"
    }
}
```

---

### 3.3 `list-journal-kinesis-streams-for-ledger`

Returns all QLDB journal streams for a given ledger. Does not return expired journal streams. **Paginated operation.**

**Synopsis:**
```bash
aws qldb list-journal-kinesis-streams-for-ledger \
    --ledger-name <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ledger-name` | **Yes** | string | -- | Name of the ledger |
| `--max-results` | No | integer | None | Maximum number of results per page (1-100) |
| `--next-token` | No | string | None | Pagination token from previous response |

**Output Schema:**
```json
{
    "Streams": [
        {
            "LedgerName": "string",
            "CreationTime": "timestamp",
            "InclusiveStartTime": "timestamp",
            "ExclusiveEndTime": "timestamp",
            "RoleArn": "string",
            "StreamId": "string",
            "Arn": "string",
            "Status": "ACTIVE|COMPLETED|CANCELED|FAILED|IMPAIRED",
            "KinesisConfiguration": {
                "StreamArn": "string",
                "AggregationEnabled": true|false
            },
            "ErrorCause": "KINESIS_STREAM_NOT_FOUND|IAM_PERMISSION_REVOKED",
            "StreamName": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.4 `cancel-journal-kinesis-stream`

Ends a given QLDB journal stream. Before a stream can be canceled, its current status must be `ACTIVE`.

**Synopsis:**
```bash
aws qldb cancel-journal-kinesis-stream \
    --ledger-name <value> \
    --stream-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ledger-name` | **Yes** | string | -- | Name of the ledger |
| `--stream-id` | **Yes** | string | -- | Unique ID of the QLDB journal stream to cancel |

**Output Schema:**
```json
{
    "StreamId": "string"
}
```
