# Messages

### 2.1 `send-message`

Delivers a message to the specified queue. Maximum message size is 256 KB (262,144 bytes).

**Synopsis:**
```bash
aws sqs send-message \
    --queue-url <value> \
    --message-body <value> \
    [--delay-seconds <value>] \
    [--message-attributes <value>] \
    [--message-system-attributes <value>] \
    [--message-deduplication-id <value>] \
    [--message-group-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--queue-url` | **Yes** | string | -- | URL of the queue. Case-sensitive. |
| `--message-body` | **Yes** | string | -- | Message content (1 char to 256 KB). XML, JSON, or unformatted text. |
| `--delay-seconds` | No | integer | queue default | Per-message delay (0-900). Not available for FIFO queues. |
| `--message-attributes` | No | map | -- | Custom attributes. Each has `DataType` (String/Number/Binary), `StringValue` or `BinaryValue`. |
| `--message-system-attributes` | No | map | -- | System attributes. Currently only `AWSTraceHeader` supported. |
| `--message-deduplication-id` | No* | string | -- | Deduplication token (max 128 chars). *Required for FIFO queues without `ContentBasedDeduplication`. |
| `--message-group-id` | No* | string | -- | Message group tag (max 128 chars). *Required for FIFO queues. Optional for standard queues. |

**Message Attributes Structure:**
```json
{
    "AttributeName": {
        "DataType": "String|Number|Binary",
        "StringValue": "string",
        "BinaryValue": "blob"
    }
}
```

**Output Schema:**
```json
{
    "MD5OfMessageBody": "string",
    "MD5OfMessageAttributes": "string",
    "MD5OfMessageSystemAttributes": "string",
    "MessageId": "string",
    "SequenceNumber": "string"
}
```

| Field | Description |
|-------|-------------|
| `MD5OfMessageBody` | MD5 digest of the message body |
| `MD5OfMessageAttributes` | MD5 digest of message attributes |
| `MD5OfMessageSystemAttributes` | MD5 digest of system attributes |
| `MessageId` | Unique identifier of the sent message |
| `SequenceNumber` | FIFO only. 128-bit number assigned to the message. |

---

### 2.2 `send-message-batch`

Delivers up to 10 messages to the specified queue. Total batch payload max 256 KB.

**Synopsis:**
```bash
aws sqs send-message-batch \
    --queue-url <value> \
    --entries <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--queue-url` | **Yes** | string | -- | URL of the queue. Case-sensitive. |
| `--entries` | **Yes** | list | -- | List of up to 10 `SendMessageBatchRequestEntry` items |

**Entry Structure:**
```json
[
    {
        "Id": "string",
        "MessageBody": "string",
        "DelaySeconds": integer,
        "MessageAttributes": { ... },
        "MessageSystemAttributes": { ... },
        "MessageDeduplicationId": "string",
        "MessageGroupId": "string"
    }
]
```

| Entry Field | Required | Type | Description |
|-------------|----------|------|-------------|
| `Id` | **Yes** | string | Unique identifier (max 80 chars, alphanumeric/hyphens/underscores) |
| `MessageBody` | **Yes** | string | Message content (up to 256 KB) |
| `DelaySeconds` | No | integer | Per-message delay (0-900). Not for FIFO. |
| `MessageAttributes` | No | map | Custom message attributes |
| `MessageSystemAttributes` | No | map | System attributes (`AWSTraceHeader`) |
| `MessageDeduplicationId` | No* | string | FIFO deduplication token (max 128 chars) |
| `MessageGroupId` | No* | string | FIFO message group (max 128 chars) |

**Output Schema:**
```json
{
    "Successful": [
        {
            "Id": "string",
            "MessageId": "string",
            "MD5OfMessageBody": "string",
            "MD5OfMessageAttributes": "string",
            "MD5OfMessageSystemAttributes": "string",
            "SequenceNumber": "string"
        }
    ],
    "Failed": [
        {
            "Id": "string",
            "SenderFault": true|false,
            "Code": "string",
            "Message": "string"
        }
    ]
}
```

---

### 2.3 `receive-message`

Retrieves one or more messages (up to 10) from the specified queue. Short polling returns immediately; long polling waits for `WaitTimeSeconds`.

**Synopsis:**
```bash
aws sqs receive-message \
    --queue-url <value> \
    [--attribute-names <value>] \
    [--message-system-attribute-names <value>] \
    [--message-attribute-names <value>] \
    [--max-number-of-messages <value>] \
    [--visibility-timeout <value>] \
    [--wait-time-seconds <value>] \
    [--receive-request-attempt-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--queue-url` | **Yes** | string | -- | URL of the queue. Case-sensitive. |
| `--attribute-names` | No | list | -- | *Deprecated.* Use `--message-system-attribute-names`. |
| `--message-system-attribute-names` | No | list | -- | System attributes to return: `All`, `SenderId`, `SentTimestamp`, `ApproximateReceiveCount`, `ApproximateFirstReceiveTimestamp`, `SequenceNumber`, `MessageDeduplicationId`, `MessageGroupId`, `AWSTraceHeader`, `DeadLetterQueueSourceArn` |
| `--message-attribute-names` | No | list | -- | Custom attribute names to return. Supports `All`, `.*`, or prefix patterns (e.g. `bar.*`). |
| `--max-number-of-messages` | No | integer | `1` | Max messages to return (1-10) |
| `--visibility-timeout` | No | integer | queue default (30) | Override visibility timeout in seconds for returned messages |
| `--wait-time-seconds` | No | integer | queue default (0) | Long-poll wait time in seconds (0-20) |
| `--receive-request-attempt-id` | No | string | -- | Deduplication token for FIFO receive calls (max 128 chars) |

**Output Schema:**
```json
{
    "Messages": [
        {
            "MessageId": "string",
            "ReceiptHandle": "string",
            "MD5OfBody": "string",
            "Body": "string",
            "Attributes": {
                "SenderId": "string",
                "SentTimestamp": "string",
                "ApproximateReceiveCount": "string",
                "ApproximateFirstReceiveTimestamp": "string",
                "SequenceNumber": "string",
                "MessageDeduplicationId": "string",
                "MessageGroupId": "string",
                "AWSTraceHeader": "string",
                "DeadLetterQueueSourceArn": "string"
            },
            "MD5OfMessageAttributes": "string",
            "MessageAttributes": {
                "string": {
                    "StringValue": "string",
                    "BinaryValue": "blob",
                    "StringListValues": ["string"],
                    "BinaryListValues": ["blob"],
                    "DataType": "string"
                }
            }
        }
    ]
}
```

| Field | Description |
|-------|-------------|
| `MessageId` | Unique message identifier |
| `ReceiptHandle` | Handle used to delete or change visibility of the message |
| `MD5OfBody` | MD5 digest of the message body |
| `Body` | The message content |
| `Attributes` | Map of system attribute name-value pairs |
| `MessageAttributes` | Map of custom attribute name-value pairs |

---

### 2.4 `delete-message`

Deletes the specified message from the queue. Use the `ReceiptHandle` from `receive-message`, not the `MessageId`.

**Synopsis:**
```bash
aws sqs delete-message \
    --queue-url <value> \
    --receipt-handle <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--queue-url` | **Yes** | string | -- | URL of the queue. Case-sensitive. |
| `--receipt-handle` | **Yes** | string | -- | Receipt handle of the message to delete (from `receive-message`) |

**Output:** None

---

### 2.5 `delete-message-batch`

Deletes up to 10 messages from the specified queue. Always check `Failed` in the response even on HTTP 200.

**Synopsis:**
```bash
aws sqs delete-message-batch \
    --queue-url <value> \
    --entries <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--queue-url` | **Yes** | string | -- | URL of the queue. Case-sensitive. |
| `--entries` | **Yes** | list | -- | List of up to 10 delete entries |

**Entry Structure:**
```json
[
    {
        "Id": "string",
        "ReceiptHandle": "string"
    }
]
```

| Entry Field | Required | Type | Description |
|-------------|----------|------|-------------|
| `Id` | **Yes** | string | Unique identifier (max 80 chars) |
| `ReceiptHandle` | **Yes** | string | Receipt handle of the message |

**Output Schema:**
```json
{
    "Successful": [
        {
            "Id": "string"
        }
    ],
    "Failed": [
        {
            "Id": "string",
            "SenderFault": true|false,
            "Code": "string",
            "Message": "string"
        }
    ]
}
```

---

### 2.6 `change-message-visibility`

Changes the visibility timeout of a specified message. The timeout begins counting from the time of this call.

**Synopsis:**
```bash
aws sqs change-message-visibility \
    --queue-url <value> \
    --receipt-handle <value> \
    --visibility-timeout <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--queue-url` | **Yes** | string | -- | URL of the queue. Case-sensitive. |
| `--receipt-handle` | **Yes** | string | -- | Receipt handle of the message |
| `--visibility-timeout` | **Yes** | integer | -- | New visibility timeout in seconds (0-43,200) |

**Output:** None

---

### 2.7 `change-message-visibility-batch`

Changes the visibility timeout of up to 10 messages. Always check `Failed` in the response.

**Synopsis:**
```bash
aws sqs change-message-visibility-batch \
    --queue-url <value> \
    --entries <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--queue-url` | **Yes** | string | -- | URL of the queue. Case-sensitive. |
| `--entries` | **Yes** | list | -- | List of up to 10 visibility change entries |

**Entry Structure:**
```json
[
    {
        "Id": "string",
        "ReceiptHandle": "string",
        "VisibilityTimeout": integer
    }
]
```

| Entry Field | Required | Type | Description |
|-------------|----------|------|-------------|
| `Id` | **Yes** | string | Unique identifier (max 80 chars) |
| `ReceiptHandle` | **Yes** | string | Receipt handle of the message |
| `VisibilityTimeout` | No | integer | New visibility timeout in seconds (0-43,200) |

**Output Schema:**
```json
{
    "Successful": [
        {
            "Id": "string"
        }
    ],
    "Failed": [
        {
            "Id": "string",
            "SenderFault": true|false,
            "Code": "string",
            "Message": "string"
        }
    ]
}
```
