# Data Operations

### 2.1 `put-record`

Writes a single data record into a delivery stream. Max record size: 1,000 KiB before base64 encoding.

**Synopsis:**
```bash
aws firehose put-record \
    --delivery-stream-name <value> \
    --record <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--delivery-stream-name` | **Yes** | string | -- | Name of the delivery stream (1-64 chars) |
| `--record` | **Yes** | structure | -- | Record to deliver. Shorthand: `Data=blob` |

**Record Structure:**
```json
{
    "Data": "blob"
}
```

**Output Schema:**
```json
{
    "RecordId": "string",
    "Encrypted": "boolean"
}
```

---

### 2.2 `put-record-batch`

Writes multiple data records into a delivery stream in a single call. Max 500 records, max 4 MiB total payload.

**Synopsis:**
```bash
aws firehose put-record-batch \
    --delivery-stream-name <value> \
    --records <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--delivery-stream-name` | **Yes** | string | -- | Name of the delivery stream (1-64 chars) |
| `--records` | **Yes** | list | -- | Records to deliver (1-500). Shorthand: `Data=blob ...` |

**Record Structure:**
```json
[
    {
        "Data": "blob"
    }
]
```

**Output Schema:**
```json
{
    "FailedPutCount": "integer",
    "Encrypted": "boolean",
    "RequestResponses": [
        {
            "RecordId": "string",
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

**Error Codes:**
| Code | Description |
|------|-------------|
| `ServiceUnavailableException` | Service temporarily unavailable |
| `InternalFailure` | Internal service error |

**Retry Pattern:**
When `FailedPutCount` is greater than 0, retry only the failed records. The `RequestResponses` array maintains the same order as the input records — entries with `ErrorCode` are the ones that need retry.
