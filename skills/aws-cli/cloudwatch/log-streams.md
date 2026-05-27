# Log Streams

### 9.1 `create-log-stream`

Creates a log stream within a log group.

**Synopsis:**
```bash
aws logs create-log-stream \
    --log-group-name <value> \
    --log-stream-name <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-group-name` | **Yes** | string | -- | Log group name (1-512 chars) |
| `--log-stream-name` | **Yes** | string | -- | Log stream name (1-512 chars). Pattern: `[^:*]*` |

**Output:** None on success.

---

### 9.2 `delete-log-stream`

Deletes a log stream and all associated log events.

**Synopsis:**
```bash
aws logs delete-log-stream \
    --log-group-name <value> \
    --log-stream-name <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-group-name` | **Yes** | string | -- | Log group name (1-512 chars) |
| `--log-stream-name` | **Yes** | string | -- | Log stream name (1-512 chars) |

**Output:** None on success.

---

### 9.3 `describe-log-streams`

Lists log streams in a log group. **Paginated.**

**Synopsis:**
```bash
aws logs describe-log-streams \
    [--log-group-name <value>] \
    [--log-group-identifier <value>] \
    [--log-stream-name-prefix <value>] \
    [--order-by <value>] \
    [--descending | --no-descending] \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-group-name` | No | string | -- | Log group name (1-512 chars) |
| `--log-group-identifier` | No | string | -- | Log group name or ARN (1-2048 chars) |
| `--log-stream-name-prefix` | No | string | -- | Prefix filter for stream names (1-512 chars) |
| `--order-by` | No | string | `LogStreamName` | `LogStreamName` or `LastEventTime` |
| `--descending` | No | boolean | false | Sort in descending order |
| `--max-items` | No | integer | -- | Total items to return |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |

**Output Schema:**
```json
{
    "logStreams": [
        {
            "logStreamName": "string",
            "creationTime": long,
            "firstEventTimestamp": long,
            "lastEventTimestamp": long,
            "lastIngestionTime": long,
            "uploadSequenceToken": "string",
            "arn": "string",
            "storedBytes": long
        }
    ],
    "nextToken": "string"
}
```

---
