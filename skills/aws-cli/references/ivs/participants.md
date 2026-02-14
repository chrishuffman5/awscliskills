# Participants (Real-Time)

### 7.1 `create-participant-token`

Creates a token for a participant to join a real-time stage.

**Synopsis:**
```bash
aws ivs-realtime create-participant-token \
    --stage-arn <value> \
    [--duration <value>] \
    [--user-id <value>] \
    [--attributes <value>] \
    [--capabilities <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stage-arn` | **Yes** | string | -- | ARN of the stage |
| `--duration` | No | integer | 720 | Token duration in minutes (1-20160) |
| `--user-id` | No | string | None | User identifier (max 128 chars) |
| `--attributes` | No | map | None | Custom attributes (max 1 KB total) |
| `--capabilities` | No | list | None | `PUBLISH`, `SUBSCRIBE` (max 2) |

**Output Schema:**
```json
{
    "participantToken": {
        "participantId": "string",
        "token": "string",
        "userId": "string",
        "attributes": {"string": "string"},
        "duration": "integer",
        "capabilities": ["PUBLISH|SUBSCRIBE"],
        "expirationTime": "timestamp"
    }
}
```

---

### 7.2 `get-participant`

Gets details for a participant in a stage session.

**Synopsis:**
```bash
aws ivs-realtime get-participant \
    --stage-arn <value> \
    --session-id <value> \
    --participant-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stage-arn` | **Yes** | string | -- | ARN of the stage |
| `--session-id` | **Yes** | string | -- | Session ID |
| `--participant-id` | **Yes** | string | -- | Participant ID |

**Output Schema:**
```json
{
    "participant": {
        "participantId": "string",
        "userId": "string",
        "state": "CONNECTED|DISCONNECTED",
        "firstJoinTime": "timestamp",
        "attributes": {"string": "string"},
        "published": "boolean",
        "ispName": "string",
        "osName": "string",
        "osVersion": "string",
        "browserName": "string",
        "browserVersion": "string",
        "sdkVersion": "string",
        "protocol": "UNKNOWN|WHIP|RTMP|RTMPS"
    }
}
```

---

### 7.3 `list-participants`

Lists participants in a stage session. **Paginated operation.**

**Synopsis:**
```bash
aws ivs-realtime list-participants \
    --stage-arn <value> \
    --session-id <value> \
    [--filter-by-user-id <value>] \
    [--filter-by-published | --no-filter-by-published] \
    [--filter-by-state <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stage-arn` | **Yes** | string | -- | ARN of the stage |
| `--session-id` | **Yes** | string | -- | Session ID |
| `--filter-by-user-id` | No | string | None | Filter by user ID |
| `--filter-by-published` | No | boolean | None | Filter by publishing status |
| `--filter-by-state` | No | string | None | Filter: `CONNECTED` or `DISCONNECTED` |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page |

---

### 7.4 `list-participant-events`

Lists events for a participant. **Paginated operation.**

**Synopsis:**
```bash
aws ivs-realtime list-participant-events \
    --stage-arn <value> \
    --session-id <value> \
    --participant-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stage-arn` | **Yes** | string | -- | ARN of the stage |
| `--session-id` | **Yes** | string | -- | Session ID |
| `--participant-id` | **Yes** | string | -- | Participant ID |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page |

---

### 7.5 `disconnect-participant`

Disconnects a participant from a stage.

**Synopsis:**
```bash
aws ivs-realtime disconnect-participant \
    --stage-arn <value> \
    --participant-id <value> \
    [--reason <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stage-arn` | **Yes** | string | -- | ARN of the stage |
| `--participant-id` | **Yes** | string | -- | Participant ID to disconnect |
| `--reason` | No | string | None | Reason for disconnection |

**Output:** None

---

### 7.6 `start-participant-replication`

Starts replicating a participant's media to another stage.

**Synopsis:**
```bash
aws ivs-realtime start-participant-replication \
    --stage-arn <value> \
    --participant-id <value> \
    --destination-stage-arns <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stage-arn` | **Yes** | string | -- | Source stage ARN |
| `--participant-id` | **Yes** | string | -- | Participant ID to replicate |
| `--destination-stage-arns` | **Yes** | list | -- | Destination stage ARNs |

---

### 7.7 `stop-participant-replication`

Stops replicating a participant's media.

**Synopsis:**
```bash
aws ivs-realtime stop-participant-replication \
    --stage-arn <value> \
    --participant-id <value> \
    --destination-stage-arns <value>
```

---

### 7.8 `list-participant-replicas`

Lists replicas for a participant. **Paginated operation.**

**Synopsis:**
```bash
aws ivs-realtime list-participant-replicas \
    --stage-arn <value> \
    --participant-id <value> \
    [--next-token <value>] \
    [--max-results <value>]
```
