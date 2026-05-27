# Streams

### 3.1 `get-stream`

Gets details for the current live stream on a channel.

**Synopsis:**
```bash
aws ivs get-stream \
    --channel-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | ARN of the channel |

**Output Schema:**
```json
{
    "stream": {
        "channelArn": "string",
        "streamId": "string",
        "playbackUrl": "string",
        "startTime": "timestamp",
        "state": "LIVE|OFFLINE",
        "health": "HEALTHY|STARVING|UNKNOWN",
        "viewerCount": "long"
    }
}
```

---

### 3.2 `list-streams`

Lists all active streams. **Paginated operation.**

**Synopsis:**
```bash
aws ivs list-streams \
    [--filter-by <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter-by` | No | structure | None | Filter by `health`: `HEALTHY`, `STARVING`, `UNKNOWN` |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page |

**Output Schema:**
```json
{
    "streams": [
        {
            "channelArn": "string",
            "streamId": "string",
            "startTime": "timestamp",
            "state": "LIVE|OFFLINE",
            "health": "HEALTHY|STARVING|UNKNOWN",
            "viewerCount": "long"
        }
    ],
    "nextToken": "string"
}
```

---

### 3.3 `get-stream-session`

Gets metadata for a stream session (current or past).

**Synopsis:**
```bash
aws ivs get-stream-session \
    --channel-arn <value> \
    [--stream-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | ARN of the channel |
| `--stream-id` | No | string | Most recent | Specific stream session ID |

**Output Schema:**
```json
{
    "streamSession": {
        "streamId": "string",
        "startTime": "timestamp",
        "endTime": "timestamp",
        "channel": {},
        "ingestConfiguration": {
            "video": {"avcProfile": "string", "avcLevel": "string", "codec": "string", "encoder": "string", "targetBitrate": "long", "targetFramerate": "long", "videoHeight": "long", "videoWidth": "long"},
            "audio": {"channels": "long", "codec": "string", "sampleRate": "long", "targetBitrate": "long"}
        },
        "recordingConfiguration": {},
        "truncatedEvents": [
            {"name": "string", "type": "string", "eventTime": "timestamp"}
        ]
    }
}
```

---

### 3.4 `list-stream-sessions`

Lists stream sessions for a channel. **Paginated operation.**

**Synopsis:**
```bash
aws ivs list-stream-sessions \
    --channel-arn <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | ARN of the channel |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page |

**Output Schema:**
```json
{
    "streamSessions": [
        {
            "streamId": "string",
            "startTime": "timestamp",
            "endTime": "timestamp",
            "hasErrorEvent": "boolean"
        }
    ],
    "nextToken": "string"
}
```

---

### 3.5 `stop-stream`

Disconnects the incoming RTMP/SRT stream for a channel, stopping the live stream.

**Synopsis:**
```bash
aws ivs stop-stream \
    --channel-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | ARN of the channel |

**Output:** None

---

### 3.6 `put-metadata`

Inserts timed metadata into a live stream. Viewers receive the metadata via the player.

**Synopsis:**
```bash
aws ivs put-metadata \
    --channel-arn <value> \
    --metadata <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | ARN of the channel |
| `--metadata` | **Yes** | string | -- | Metadata string (1 KB max) |

**Output:** None
