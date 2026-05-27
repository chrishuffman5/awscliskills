# Replays

### 5.1 `start-replay`

Starts replaying events from an archive to the specified event bus. Events are replayed within a specified time range.

**Synopsis:**
```bash
aws events start-replay \
    --replay-name <value> \
    --event-source-arn <value> \
    --event-start-time <value> \
    --event-end-time <value> \
    --destination <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replay-name` | **Yes** | string | -- | Name for the replay |
| `--event-source-arn` | **Yes** | string | -- | ARN of the archive to replay from |
| `--event-start-time` | **Yes** | timestamp | -- | Start of the time range to replay (ISO 8601) |
| `--event-end-time` | **Yes** | timestamp | -- | End of the time range to replay (ISO 8601) |
| `--destination` | **Yes** | structure | -- | Destination event bus. Shorthand: `Arn=string,FilterArns=string,string` |
| `--description` | No | string | None | Description of the replay |

**Destination Structure:**
```json
{
    "Arn": "string",
    "FilterArns": ["string"]
}
```

**Output Schema:**
```json
{
    "ReplayArn": "string",
    "State": "STARTING|RUNNING|CANCELLING|COMPLETED|CANCELLED|FAILED",
    "StateReason": "string",
    "ReplayStartTime": "timestamp"
}
```

---

### 5.2 `cancel-replay`

Cancels a running replay.

**Synopsis:**
```bash
aws events cancel-replay \
    --replay-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replay-name` | **Yes** | string | -- | Name of the replay to cancel |

**Output Schema:**
```json
{
    "ReplayArn": "string",
    "State": "CANCELLING|CANCELLED",
    "StateReason": "string"
}
```

---

### 5.3 `describe-replay`

Retrieves details about a replay.

**Synopsis:**
```bash
aws events describe-replay \
    --replay-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replay-name` | **Yes** | string | -- | Name of the replay |

**Output Schema:**
```json
{
    "ReplayName": "string",
    "ReplayArn": "string",
    "Description": "string",
    "State": "STARTING|RUNNING|CANCELLING|COMPLETED|CANCELLED|FAILED",
    "StateReason": "string",
    "EventSourceArn": "string",
    "Destination": {
        "Arn": "string",
        "FilterArns": ["string"]
    },
    "EventStartTime": "timestamp",
    "EventEndTime": "timestamp",
    "EventLastReplayedTime": "timestamp",
    "ReplayStartTime": "timestamp",
    "ReplayEndTime": "timestamp"
}
```

---

### 5.4 `list-replays`

Lists all replays. Supports filtering by name prefix, state, or event source. **Paginated operation.**

**Synopsis:**
```bash
aws events list-replays \
    [--name-prefix <value>] \
    [--state <value>] \
    [--event-source-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name-prefix` | No | string | None | Filter by replay name prefix |
| `--state` | No | string | None | Filter by state: `STARTING`, `RUNNING`, `CANCELLING`, `COMPLETED`, `CANCELLED`, `FAILED` |
| `--event-source-arn` | No | string | None | Filter by event source ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Replays": [
        {
            "ReplayName": "string",
            "EventSourceArn": "string",
            "State": "STARTING|RUNNING|CANCELLING|COMPLETED|CANCELLED|FAILED",
            "StateReason": "string",
            "EventStartTime": "timestamp",
            "EventEndTime": "timestamp",
            "EventLastReplayedTime": "timestamp",
            "ReplayStartTime": "timestamp",
            "ReplayEndTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
