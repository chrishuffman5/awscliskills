# Runtime

### 13.1 `recognize-text`

Sends user text input to a bot for processing. Returns the bot's response messages, session state, and intent interpretations.

**Synopsis:**
```bash
aws lexv2-runtime recognize-text \
    --bot-id <value> \
    --bot-alias-id <value> \
    --locale-id <value> \
    --session-id <value> \
    --text <value> \
    [--session-state <value>] \
    [--request-attributes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-alias-id` | **Yes** | string | -- | Bot alias identifier (10 chars) |
| `--locale-id` | **Yes** | string | -- | Locale identifier (e.g., `en_US`) |
| `--session-id` | **Yes** | string | -- | Session identifier (2-100 chars) |
| `--text` | **Yes** | string | -- | User text input (1-1024 chars) |
| `--session-state` | No | structure | None | Current dialog session state |
| `--request-attributes` | No | map | None | Request-specific key-value pairs |

**Output Schema:**
```json
{
    "messages": [
        {
            "content": "string",
            "contentType": "CustomPayload|ImageResponseCard|PlainText|SSML",
            "imageResponseCard": {
                "title": "string",
                "subtitle": "string",
                "imageUrl": "string",
                "buttons": [
                    {
                        "text": "string",
                        "value": "string"
                    }
                ]
            }
        }
    ],
    "sessionState": {
        "dialogAction": {
            "type": "Close|ConfirmIntent|Delegate|ElicitIntent|ElicitSlot|None",
            "slotToElicit": "string",
            "slotElicitationStyle": "Default|SpellByLetter|SpellByWord"
        },
        "intent": {
            "name": "string",
            "slots": {
                "string": {
                    "value": {
                        "originalValue": "string",
                        "interpretedValue": "string",
                        "resolvedValues": ["string"]
                    },
                    "shape": "Scalar|List|Composite",
                    "values": []
                }
            },
            "state": "Failed|Fulfilled|InProgress|ReadyForFulfillment|Waiting|FulfillmentInProgress",
            "confirmationState": "Confirmed|Denied|None"
        },
        "activeContexts": [
            {
                "name": "string",
                "timeToLive": {
                    "timeToLiveInSeconds": "integer",
                    "turnsToLive": "integer"
                },
                "contextAttributes": {"string": "string"}
            }
        ],
        "sessionAttributes": {"string": "string"},
        "originatingRequestId": "string",
        "runtimeHints": {}
    },
    "interpretations": [
        {
            "nluConfidence": {"score": "double"},
            "sentimentResponse": {
                "sentiment": "MIXED|NEGATIVE|NEUTRAL|POSITIVE",
                "sentimentScore": {
                    "positive": "double",
                    "negative": "double",
                    "neutral": "double",
                    "mixed": "double"
                }
            },
            "intent": {
                "name": "string",
                "slots": {},
                "state": "string",
                "confirmationState": "string"
            },
            "interpretationSource": "Bedrock|Lex"
        }
    ],
    "requestAttributes": {"string": "string"},
    "sessionId": "string",
    "recognizedBotMember": {
        "botId": "string",
        "botName": "string"
    }
}
```

---

### 13.2 `recognize-utterance`

Sends user audio or text input to a bot for processing. Accepts audio as a binary stream and returns audio/text responses.

**Synopsis:**
```bash
aws lexv2-runtime recognize-utterance \
    --bot-id <value> \
    --bot-alias-id <value> \
    --locale-id <value> \
    --session-id <value> \
    --request-content-type <value> \
    [--session-state <value>] \
    [--request-attributes <value>] \
    [--response-content-type <value>] \
    [--input-stream <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-alias-id` | **Yes** | string | -- | Bot alias identifier |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--session-id` | **Yes** | string | -- | Session identifier (2-100 chars) |
| `--request-content-type` | **Yes** | string | -- | Content type of input (e.g., `audio/l16; rate=16000`, `text/plain; charset=utf-8`) |
| `--session-state` | No | string | None | Base64-encoded JSON session state |
| `--request-attributes` | No | string | None | Base64-encoded JSON request attributes |
| `--response-content-type` | No | string | None | Desired response audio format |
| `--input-stream` | No | blob | None | Audio input stream (`fileb://audio.wav`) |

**Output:** Binary audio stream with HTTP headers containing base64-encoded JSON for messages, session state, interpretations, and request attributes.

---

### 13.3 `get-session`

Gets the current session state for a user session.

**Synopsis:**
```bash
aws lexv2-runtime get-session \
    --bot-id <value> \
    --bot-alias-id <value> \
    --locale-id <value> \
    --session-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-alias-id` | **Yes** | string | -- | Bot alias identifier |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--session-id` | **Yes** | string | -- | Session identifier (2-100 chars) |

**Output Schema:**
```json
{
    "sessionId": "string",
    "messages": [
        {
            "content": "string",
            "contentType": "CustomPayload|ImageResponseCard|PlainText|SSML",
            "imageResponseCard": {}
        }
    ],
    "interpretations": [],
    "sessionState": {
        "dialogAction": {},
        "intent": {},
        "activeContexts": [],
        "sessionAttributes": {},
        "originatingRequestId": "string",
        "runtimeHints": {}
    }
}
```

---

### 13.4 `put-session`

Creates or updates a session with a bot. Can be used to set the dialog state, session attributes, and slot values.

**Synopsis:**
```bash
aws lexv2-runtime put-session \
    --bot-id <value> \
    --bot-alias-id <value> \
    --locale-id <value> \
    --session-id <value> \
    --session-state <value> \
    [--messages <value>] \
    [--request-attributes <value>] \
    [--response-content-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-alias-id` | **Yes** | string | -- | Bot alias identifier |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--session-id` | **Yes** | string | -- | Session identifier (2-100 chars) |
| `--session-state` | **Yes** | structure | -- | Session state to set |
| `--messages` | No | list | None | Messages to include in the response |
| `--request-attributes` | No | map | None | Request-specific key-value pairs |
| `--response-content-type` | No | string | None | Desired response audio format |

**Output:** Binary audio stream with HTTP headers containing base64-encoded JSON for messages, session state, and request attributes.

---

### 13.5 `delete-session`

Deletes a session, removing all session attributes and the dialog state.

**Synopsis:**
```bash
aws lexv2-runtime delete-session \
    --bot-id <value> \
    --bot-alias-id <value> \
    --locale-id <value> \
    --session-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-alias-id` | **Yes** | string | -- | Bot alias identifier |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--session-id` | **Yes** | string | -- | Session identifier (2-100 chars) |

**Output Schema:**
```json
{
    "botId": "string",
    "botAliasId": "string",
    "localeId": "string",
    "sessionId": "string"
}
```
