# Agent Runtime

### `create-invocation`

Creates an invocation to interact with an agent at runtime. The agent processes the input and returns a response.

**Synopsis:**
```bash
aws bedrock-agent-runtime create-invocation \
    --agent-id <value> \
    --agent-alias-id <value> \
    --session-id <value> \
    [--payload <value>] \
    [--invocation-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-id` | **Yes** | string | -- | Agent ID |
| `--agent-alias-id` | **Yes** | string | -- | Agent alias ID |
| `--session-id` | **Yes** | string | -- | Session ID for the conversation |
| `--payload` | No | structure | None | Invocation payload with input text |
| `--invocation-configuration` | No | structure | None | Configuration for the invocation |

**Output Schema:**
```json
{
    "invocationId": "string",
    "sessionId": "string"
}
```

---

### `list-invocations`

Lists invocations for a session. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock-agent-runtime list-invocations \
    --session-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--session-id` | **Yes** | string | -- | Session ID |

**Output Schema:**
```json
{
    "invocations": [
        {
            "invocationId": "string",
            "invocationInput": {...},
            "invocationOutput": {...},
            "createdAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### `get-invocation-step`

Gets a specific step within an invocation.

**Synopsis:**
```bash
aws bedrock-agent-runtime get-invocation-step \
    --invocation-identifier <value> \
    --invocation-step-id <value> \
    --session-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--invocation-identifier` | **Yes** | string | -- | Invocation ID |
| `--invocation-step-id` | **Yes** | string | -- | Step ID |
| `--session-identifier` | **Yes** | string | -- | Session ID |

**Output Schema:**
```json
{
    "invocationStep": {
        "invocationId": "string",
        "invocationStepId": "string",
        "invocationStepTime": "timestamp",
        "payload": {...}
    }
}
```

---

### `list-invocation-steps`

Lists steps within an invocation. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock-agent-runtime list-invocation-steps \
    --invocation-identifier <value> \
    --session-identifier <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

---

### `put-invocation-step`

Creates or updates an invocation step (used for return-of-control flows).

**Synopsis:**
```bash
aws bedrock-agent-runtime put-invocation-step \
    --invocation-identifier <value> \
    --invocation-step-id <value> \
    --session-identifier <value> \
    --payload <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--invocation-identifier` | **Yes** | string | -- | Invocation ID |
| `--invocation-step-id` | **Yes** | string | -- | Step ID |
| `--session-identifier` | **Yes** | string | -- | Session ID |
| `--payload` | **Yes** | structure | -- | Step payload |

**Output Schema:**
```json
{
    "invocationStepId": "string"
}
```

---

### `create-session`

Creates a session for agent interactions.

**Synopsis:**
```bash
aws bedrock-agent-runtime create-session \
    [--session-metadata <value>] \
    [--encryption-configuration <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--session-metadata` | No | map | None | Key-value metadata for the session |
| `--encryption-configuration` | No | structure | None | KMS key for session encryption |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "sessionId": "string",
    "createdAt": "timestamp"
}
```

---

### `get-session`

Gets session details.

**Synopsis:**
```bash
aws bedrock-agent-runtime get-session \
    --session-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--session-identifier` | **Yes** | string | -- | Session ID |

**Output Schema:**
```json
{
    "sessionId": "string",
    "sessionStatus": "ACTIVE|EXPIRED|ENDED",
    "sessionMetadata": {"string": "string"},
    "createdAt": "timestamp",
    "lastUpdatedAt": "timestamp"
}
```

---

### `list-sessions`

Lists sessions. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock-agent-runtime list-sessions \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "sessionSummaries": [
        {
            "sessionId": "string",
            "sessionStatus": "ACTIVE|EXPIRED|ENDED",
            "createdAt": "timestamp",
            "lastUpdatedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### `update-session`

Updates session metadata.

**Synopsis:**
```bash
aws bedrock-agent-runtime update-session \
    --session-identifier <value> \
    [--session-metadata <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

---

### `delete-session`

Deletes a session.

**Synopsis:**
```bash
aws bedrock-agent-runtime delete-session \
    --session-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

---

### `end-session`

Ends a session, making it inactive.

**Synopsis:**
```bash
aws bedrock-agent-runtime end-session \
    --session-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

---

### `delete-agent-memory`

Deletes memory from an agent session.

**Synopsis:**
```bash
aws bedrock-agent-runtime delete-agent-memory \
    --agent-id <value> \
    --agent-alias-id <value> \
    [--memory-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-id` | **Yes** | string | -- | Agent ID |
| `--agent-alias-id` | **Yes** | string | -- | Agent alias ID |
| `--memory-id` | No | string | None | Specific memory ID to delete |

**Output:** None (HTTP 200 on success)

---

### `get-agent-memory`

Retrieves agent memory contents.

**Synopsis:**
```bash
aws bedrock-agent-runtime get-agent-memory \
    --agent-id <value> \
    --agent-alias-id <value> \
    --memory-type <value> \
    --memory-id <value> \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-id` | **Yes** | string | -- | Agent ID |
| `--agent-alias-id` | **Yes** | string | -- | Agent alias ID |
| `--memory-type` | **Yes** | string | -- | Memory type: `SESSION_SUMMARY` |
| `--memory-id` | **Yes** | string | -- | Memory ID |

**Output Schema:**
```json
{
    "memoryContents": [
        {
            "sessionSummary": {
                "sessionId": "string",
                "summaryText": "string",
                "sessionStartTime": "timestamp",
                "sessionExpiryTime": "timestamp"
            }
        }
    ],
    "nextToken": "string"
}
```
