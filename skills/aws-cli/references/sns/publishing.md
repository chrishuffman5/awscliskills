# Publishing

### 3.1 `publish`

Sends a message to a topic, phone number, or platform endpoint. Must specify exactly one of `--topic-arn`, `--target-arn`, or `--phone-number`.

**Synopsis:**
```bash
aws sns publish \
    [--topic-arn <value>] \
    [--target-arn <value>] \
    [--phone-number <value>] \
    --message <value> \
    [--subject <value>] \
    [--message-structure <value>] \
    [--message-attributes <value>] \
    [--message-deduplication-id <value>] \
    [--message-group-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--message` | **Yes** | string | -- | Message body. Max 256 KB. SMS: max 1,600 chars total. If `--message-structure json`, must have `"default"` key |
| `--topic-arn` | Conditional | string | -- | Topic ARN. Required if `--target-arn` and `--phone-number` not specified |
| `--target-arn` | Conditional | string | -- | Platform endpoint ARN for mobile push |
| `--phone-number` | Conditional | string | -- | Phone number in E.164 format for SMS |
| `--subject` | No | string | None | Subject line for email endpoints. UTF-8, max 100 chars |
| `--message-structure` | No | string | None | Set to `json` to send different messages per protocol |
| `--message-attributes` | No | map | None | Message attributes with `DataType` (String/Number/Binary), `StringValue`, `BinaryValue`. Max 256 KB total |
| `--message-deduplication-id` | No | string | None | FIFO topics only. Max 128 chars. Unique within 5-min dedup interval |
| `--message-group-id` | No | string | None | FIFO topics (required), standard topics (optional for SQS fair queuing). Max 128 chars |

**Output Schema:**
```json
{
    "MessageId": "string",
    "SequenceNumber": "string"
}
```

> `SequenceNumber` is only returned for FIFO topics.

---

### 3.2 `publish-batch`

Publishes up to 10 messages to a topic in a single request. Total payload max 256 KB.

**Synopsis:**
```bash
aws sns publish-batch \
    --topic-arn <value> \
    --publish-batch-request-entries <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--topic-arn` | **Yes** | string | -- | ARN of the topic |
| `--publish-batch-request-entries` | **Yes** | list | -- | List of batch entries (max 10). See entry structure below |

**Batch Entry Structure:**

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `Id` | **Yes** | string | Unique ID within the batch. Max 80 chars. Alphanumeric, hyphens, underscores |
| `Message` | **Yes** | string | Message body |
| `Subject` | No | string | Subject line for email |
| `MessageStructure` | No | string | Set to `json` for per-protocol messages |
| `MessageAttributes` | No | map | Message attributes |
| `MessageDeduplicationId` | No | string | FIFO only. Max 128 chars |
| `MessageGroupId` | No | string | FIFO (required). Max 128 chars |

**Output Schema:**
```json
{
    "Successful": [
        {
            "Id": "string",
            "MessageId": "string",
            "SequenceNumber": "string"
        }
    ],
    "Failed": [
        {
            "Id": "string",
            "Code": "string",
            "Message": "string",
            "SenderFault": true|false
        }
    ]
}
```

> Check `Failed` even on HTTP 200 -- a mix of successful and failed entries is possible.
