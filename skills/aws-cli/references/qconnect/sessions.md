# Sessions

### 9.1 `create-session`

Creates a session for generating recommendations.

**Synopsis:**
```bash
aws qconnect create-session \
    --assistant-id <value> \
    --name <value> \
    [--description <value>] \
    [--tags <value>] \
    [--tag-filter <value>] \
    [--ai-agent-configuration <value>] \
    [--contact-arn <value>] \
    [--client-token <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assistant-id` | **Yes** | string | -- | Assistant ID or ARN |
| `--name` | **Yes** | string | -- | Session name (1-255 chars) |
| `--description` | No | string | None | Description (1-255 chars) |
| `--tags` | No | map | None | Tags |
| `--tag-filter` | No | structure | None | Content tag filter |
| `--ai-agent-configuration` | No | map | None | AI agent config by type |
| `--contact-arn` | No | string | None | Amazon Connect contact ARN |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "session": {
        "sessionArn": "string",
        "sessionId": "string",
        "name": "string",
        "description": "string",
        "tags": {},
        "tagFilter": {},
        "aiAgentConfiguration": {},
        "origin": "SYSTEM|CUSTOMER"
    }
}
```

---

### 9.2 `get-session`

Gets session details.

**Synopsis:**
```bash
aws qconnect get-session \
    --assistant-id <value> \
    --session-id <value>
```

---

### 9.3 `update-session`

Updates a session configuration.

**Synopsis:**
```bash
aws qconnect update-session \
    --assistant-id <value> \
    --session-id <value> \
    [--description <value>] \
    [--tag-filter <value>] \
    [--ai-agent-configuration <value>]
```

---

### 9.4 `update-session-data`

Updates session data.

**Synopsis:**
```bash
aws qconnect update-session-data \
    --assistant-id <value> \
    --session-id <value> \
    --data <value> \
    [--namespace <value>]
```

---

### 9.5 `search-sessions`

Searches sessions. **Paginated operation.**

**Synopsis:**
```bash
aws qconnect search-sessions \
    --assistant-id <value> \
    --search-expression <value> \
    [--next-token <value>] \
    [--max-results <value>]
```

---

### 9.6 `send-message`

Sends a message to an AI agent in a session.

**Synopsis:**
```bash
aws qconnect send-message \
    --assistant-id <value> \
    --session-id <value> \
    --type <value> \
    --message <value> \
    [--ai-agent-id <value>] \
    [--conversation-context <value>] \
    [--configuration <value>] \
    [--client-token <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assistant-id` | **Yes** | string | -- | Assistant ID or ARN |
| `--session-id` | **Yes** | string | -- | Session ID or ARN |
| `--type` | **Yes** | string | -- | Must be `TEXT` |
| `--message` | **Yes** | structure | -- | Message data (see below) |
| `--ai-agent-id` | No | string | None | AI agent to use |
| `--conversation-context` | No | structure | None | Prior conversation history (max 10 items) |
| `--configuration` | No | structure | None | `generateFillerMessage=boolean,generateChunkedMessage=boolean` |
| `--client-token` | No | string | None | Idempotency token |

**Message Structure:**
```json
{
    "value": {
        "text": {
            "value": "string (0-25000 chars)"
        }
    }
}
```

**Output Schema:**
```json
{
    "requestMessageId": "string",
    "nextMessageToken": "string",
    "configuration": {}
}
```

---

### 9.7 `get-next-message`

Gets the next AI response message after `send-message`.

**Synopsis:**
```bash
aws qconnect get-next-message \
    --assistant-id <value> \
    --session-id <value> \
    --next-message-token <value>
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assistant-id` | **Yes** | string | -- | Assistant ID or ARN |
| `--session-id` | **Yes** | string | -- | Session ID or ARN |
| `--next-message-token` | **Yes** | string | -- | Token from `send-message` |

---

### 9.8 `list-messages`

Lists messages in a session. **Paginated operation.**

**Synopsis:**
```bash
aws qconnect list-messages \
    --assistant-id <value> \
    --session-id <value> \
    [--next-token <value>] \
    [--max-results <value>]
```

---

### 9.9 `retrieve`

Retrieves content from a knowledge base for a session.

**Synopsis:**
```bash
aws qconnect retrieve \
    --assistant-id <value> \
    --session-id <value> \
    --knowledge-base-id <value> \
    --query-text <value> \
    [--next-token <value>] \
    [--max-results <value>]
```
