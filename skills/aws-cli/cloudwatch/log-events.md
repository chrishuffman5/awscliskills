# Log Events

### 10.1 `put-log-events`

Uploads log events to a log stream. Max 10,000 events per call.

**Synopsis:**
```bash
aws logs put-log-events \
    --log-group-name <value> \
    --log-stream-name <value> \
    --log-events <value> \
    [--sequence-token <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-group-name` | **Yes** | string | -- | Log group name (1-512 chars) |
| `--log-stream-name` | **Yes** | string | -- | Log stream name (1-512 chars) |
| `--log-events` | **Yes** | list | -- | Log events (1-10,000). Each: `timestamp` (ms epoch, required), `message` (string, max 1 MB, required) |
| `--sequence-token` | No | string | -- | Sequence token (now ignored, kept for compatibility) |

**Output Schema:**
```json
{
    "nextSequenceToken": "string",
    "rejectedLogEventsInfo": {
        "tooNewLogEventStartIndex": integer,
        "tooOldLogEventEndIndex": integer,
        "expiredLogEventEndIndex": integer
    }
}
```

---

### 10.2 `get-log-events`

Retrieves log events from a specific log stream. **Paginated.**

**Synopsis:**
```bash
aws logs get-log-events \
    --log-stream-name <value> \
    [--log-group-name <value>] \
    [--log-group-identifier <value>] \
    [--start-time <value>] \
    [--end-time <value>] \
    [--start-from-head | --no-start-from-head] \
    [--unmask | --no-unmask] \
    [--limit <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-stream-name` | **Yes** | string | -- | Log stream name (1-512 chars) |
| `--log-group-name` | No | string | -- | Log group name (1-512 chars) |
| `--log-group-identifier` | No | string | -- | Log group name or ARN (1-2048 chars) |
| `--start-time` | No | long | -- | Start time in ms since epoch |
| `--end-time` | No | long | -- | End time in ms since epoch |
| `--start-from-head` | No | boolean | false | `true` = oldest first, `false` = newest first |
| `--unmask` | No | boolean | false | Show unmasked sensitive data |
| `--limit` | No | integer | -- | Max events to return (1-10000) |

**Output Schema:**
```json
{
    "events": [
        {
            "timestamp": long,
            "message": "string",
            "ingestionTime": long
        }
    ],
    "nextForwardToken": "string",
    "nextBackwardToken": "string"
}
```

---

### 10.3 `filter-log-events`

Searches log events across streams in a log group. **Paginated.**

**Synopsis:**
```bash
aws logs filter-log-events \
    [--log-group-name <value>] \
    [--log-group-identifier <value>] \
    [--log-stream-names <value>] \
    [--log-stream-name-prefix <value>] \
    [--start-time <value>] \
    [--end-time <value>] \
    [--filter-pattern <value>] \
    [--unmask | --no-unmask] \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-group-name` | No* | string | -- | Log group name (1-512 chars). *Must specify this or `--log-group-identifier` |
| `--log-group-identifier` | No* | string | -- | Log group name or ARN (1-2048 chars) |
| `--log-stream-names` | No | list | -- | Specific streams to search (max 100). Cannot combine with `--log-stream-name-prefix` |
| `--log-stream-name-prefix` | No | string | -- | Stream name prefix filter |
| `--start-time` | No | long | -- | Start time in ms since epoch |
| `--end-time` | No | long | -- | End time in ms since epoch |
| `--filter-pattern` | No | string | -- | Filter pattern (0-1024 chars). See Filter and Pattern Syntax |
| `--unmask` | No | boolean | false | Show unmasked sensitive data |
| `--max-items` | No | integer | -- | Total items to return |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |

**Output Schema:**
```json
{
    "events": [
        {
            "logStreamName": "string",
            "timestamp": long,
            "message": "string",
            "ingestionTime": long,
            "eventId": "string"
        }
    ],
    "searchedLogStreams": [],
    "nextToken": "string"
}
```

---

### 10.4 `tail`

Tails a log group's output in real time. This is a high-level CLI command, not a direct API call.

**Synopsis:**
```bash
aws logs tail <log-group-name> \
    [--since <value>] \
    [--follow] \
    [--format <value>] \
    [--filter-pattern <value>] \
    [--log-stream-names <value>] \
    [--log-stream-name-prefix <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `<log-group-name>` | **Yes** | string | -- | Log group name (positional argument) |
| `--since` | No | string | `10m` | How far back to start. Examples: `5m`, `1h`, `2024-01-01T00:00:00` |
| `--follow` | No | boolean | false | Continuously poll for new events |
| `--format` | No | string | `detailed` | `detailed` (timestamp + stream + message) or `short` (message only) |
| `--filter-pattern` | No | string | -- | Filter pattern for events |
| `--log-stream-names` | No | list | -- | Specific streams to tail |
| `--log-stream-name-prefix` | No | string | -- | Stream name prefix |

**Output:** Streams log events to stdout.

---

### 10.5 `get-log-record`

Retrieves all the fields and values of a single log event.

**Synopsis:**
```bash
aws logs get-log-record \
    --log-record-pointer <value> \
    [--unmask | --no-unmask]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-record-pointer` | **Yes** | string | -- | Log record pointer from `get-query-results` or `filter-log-events` |
| `--unmask` | No | boolean | false | Show unmasked sensitive data |

**Output Schema:**
```json
{
    "logRecord": {
        "string": "string"
    }
}
```

---

### 10.6 `start-live-tail`

Starts a live tail session to stream log events in real time.

**Synopsis:**
```bash
aws logs start-live-tail \
    --log-group-identifiers <value> \
    [--log-stream-names <value>] \
    [--log-stream-name-prefixes <value>] \
    [--log-event-filter-pattern <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-group-identifiers` | **Yes** | list | -- | Log group ARNs (1-10) |
| `--log-stream-names` | No | list | -- | Specific stream names (max 100) |
| `--log-stream-name-prefixes` | No | list | -- | Stream name prefixes (max 100) |
| `--log-event-filter-pattern` | No | string | -- | Filter pattern (0-2048 chars) |

**Output:** Streams live tail session events to stdout.

---
