# Events

### 11.1 `put-events`

Records user interaction events in real time. Events are added to the Interactions dataset and used for model training and real-time personalization.

**Synopsis:**
```bash
aws personalize-events put-events \
    --tracking-id <value> \
    --session-id <value> \
    --event-list <value> \
    [--user-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tracking-id` | **Yes** | string | -- | Tracking ID from `create-event-tracker` (1-256 chars) |
| `--session-id` | **Yes** | string | -- | Session identifier (1-256 chars) |
| `--event-list` | **Yes** | list | -- | List of events (1-10 per call) |
| `--user-id` | No | string | None | User associated with the events (1-256 chars) |

**Event Structure:**
```json
[
    {
        "eventType": "string",
        "sentAt": "timestamp",
        "eventId": "string",
        "eventValue": "float",
        "itemId": "string",
        "properties": "{\"key\": \"value\"}",
        "recommendationId": "string",
        "impression": ["string"],
        "metricAttribution": {
            "eventAttributionSource": "string"
        }
    }
]
```

**Output:** None

---

### 11.2 `put-items`

Adds or updates item data in real time. Items are added to the Items dataset.

**Synopsis:**
```bash
aws personalize-events put-items \
    --dataset-arn <value> \
    --items <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-arn` | **Yes** | string | -- | ARN of the Items dataset |
| `--items` | **Yes** | list | -- | List of items to add/update (1-10 per call) |

**Item Structure:**
```json
[
    {
        "itemId": "string",
        "properties": "{\"GENRE\": \"Comedy\"}"
    }
]
```

**Output:** None

---

### 11.3 `put-users`

Adds or updates user data in real time. Users are added to the Users dataset.

**Synopsis:**
```bash
aws personalize-events put-users \
    --dataset-arn <value> \
    --users <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-arn` | **Yes** | string | -- | ARN of the Users dataset |
| `--users` | **Yes** | list | -- | List of users to add/update (1-10 per call) |

**User Structure:**
```json
[
    {
        "userId": "string",
        "properties": "{\"AGE\": \"25\"}"
    }
]
```

**Output:** None

---

### 11.4 `put-actions`

Adds or updates action data in real time. Actions are added to the Actions dataset.

**Synopsis:**
```bash
aws personalize-events put-actions \
    --dataset-arn <value> \
    --actions <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-arn` | **Yes** | string | -- | ARN of the Actions dataset |
| `--actions` | **Yes** | list | -- | List of actions to add/update (1-10 per call) |

**Action Structure:**
```json
[
    {
        "actionId": "string",
        "properties": "{\"ACTION_TYPE\": \"discount\"}"
    }
]
```

**Output:** None

---

### 11.5 `put-action-interactions`

Records action interaction events in real time. Events are added to the Action_Interactions dataset.

**Synopsis:**
```bash
aws personalize-events put-action-interactions \
    --tracking-id <value> \
    --action-interactions <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tracking-id` | **Yes** | string | -- | Tracking ID from `create-event-tracker` |
| `--action-interactions` | **Yes** | list | -- | List of action interactions (1-10 per call) |

**ActionInteraction Structure:**
```json
[
    {
        "actionId": "string",
        "userId": "string",
        "sessionId": "string",
        "timestamp": "timestamp",
        "eventType": "string",
        "eventId": "string",
        "recommendationId": "string",
        "impression": ["string"],
        "properties": "{\"key\": \"value\"}"
    }
]
```

**Output:** None
