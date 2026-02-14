# Chat Logging

### 12.1 `create-logging-configuration`

Creates a logging configuration for storing chat messages.

**Synopsis:**
```bash
aws ivschat create-logging-configuration \
    --destination-configuration <value> \
    [--name <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--destination-configuration` | **Yes** | structure | -- | Log destination (S3, CloudWatch Logs, or Firehose) |
| `--name` | No | string | None | Name (0-128 chars) |
| `--tags` | No | map | None | Key-value tag pairs |

**Destination — S3:**
```json
{
    "s3": {"bucketName": "my-chat-logs-bucket"}
}
```

**Destination — CloudWatch Logs:**
```json
{
    "cloudWatchLogs": {"logGroupName": "/aws/ivschat/my-room-logs"}
}
```

**Destination — Firehose:**
```json
{
    "firehose": {"deliveryStreamName": "my-chat-firehose"}
}
```

**Output Schema:**
```json
{
    "arn": "string",
    "id": "string",
    "name": "string",
    "createTime": "timestamp",
    "updateTime": "timestamp",
    "state": "ACTIVE",
    "destinationConfiguration": {
        "s3": {"bucketName": "string"},
        "cloudWatchLogs": {"logGroupName": "string"},
        "firehose": {"deliveryStreamName": "string"}
    },
    "tags": {"string": "string"}
}
```

---

### 12.2 `get-logging-configuration`

Gets details for a logging configuration.

**Synopsis:**
```bash
aws ivschat get-logging-configuration \
    --identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Logging config ARN or ID |

**Output Schema:** Same as `create-logging-configuration` output.

---

### 12.3 `list-logging-configurations`

Lists logging configurations. **Paginated operation.**

**Synopsis:**
```bash
aws ivschat list-logging-configurations \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page |

---

### 12.4 `update-logging-configuration`

Updates a logging configuration.

**Synopsis:**
```bash
aws ivschat update-logging-configuration \
    --identifier <value> \
    [--name <value>] \
    [--destination-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Logging config ARN or ID |
| `--name` | No | string | None | Updated name |
| `--destination-configuration` | No | structure | None | Updated destination |

---

### 12.5 `delete-logging-configuration`

Deletes a logging configuration.

**Synopsis:**
```bash
aws ivschat delete-logging-configuration \
    --identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Logging config ARN or ID to delete |

**Output:** None
