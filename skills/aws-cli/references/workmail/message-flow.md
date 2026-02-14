# Message Flow

Commands in this group use `aws workmailmessageflow` (not `aws workmail`). The WorkMail Message Flow API provides access to email messages as they are being sent and received, allowing Lambda-based email processing rules to modify message content.

### 15.1 `get-raw-message-content`

Retrieves the raw content of an in-transit email message in MIME format.

**Synopsis:**
```bash
aws workmailmessageflow get-raw-message-content \
    --message-id <value> \
    <outfile>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--message-id` | **Yes** | string | -- | Email message ID (1-120 chars) |
| `outfile` | **Yes** | string | -- | Local file path to save the MIME content |

**Output:**

The raw email content is saved to the specified `outfile` in MIME format. No JSON output is returned.

---

### 15.2 `put-raw-message-content`

Updates the raw content of an in-transit email message with content from S3.

**Synopsis:**
```bash
aws workmailmessageflow put-raw-message-content \
    --message-id <value> \
    --content <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--message-id` | **Yes** | string | -- | Email message ID (1-120 chars) |
| `--content` | **Yes** | structure | -- | S3 reference for the updated message content |

**Content structure:**
```json
{
    "s3Reference": {
        "bucket": "string",
        "key": "string",
        "objectVersion": "string"
    }
}
```

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `bucket` | **Yes** | string | S3 bucket name (3-63 chars) |
| `key` | **Yes** | string | S3 object key (1-1024 chars) |
| `objectVersion` | No | string | Object version (if versioning enabled) |

**Output:** None
