# Intents

### 4.1 `create-intent`

Creates an intent in a bot locale. An intent represents an action the user wants to perform.

**Synopsis:**
```bash
aws lexv2-models create-intent \
    --intent-name <value> \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    [--description <value>] \
    [--parent-intent-signature <value>] \
    [--sample-utterances <value>] \
    [--dialog-code-hook <value>] \
    [--fulfillment-code-hook <value>] \
    [--intent-confirmation-setting <value>] \
    [--intent-closing-setting <value>] \
    [--input-contexts <value>] \
    [--output-contexts <value>] \
    [--kendra-configuration <value>] \
    [--initial-response-setting <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--intent-name` | **Yes** | string | -- | Intent name (1-100 chars, pattern: `^([0-9a-zA-Z][_-]?){1,100}$`) |
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-version` | **Yes** | string | -- | Bot version (must be `DRAFT`) |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--description` | No | string | None | Intent description (0-2000 chars) |
| `--parent-intent-signature` | No | string | None | Built-in intent to base this on |
| `--sample-utterances` | No | list | None | User utterances that trigger the intent |
| `--dialog-code-hook` | No | structure | None | Lambda invocation per user input. Shorthand: `enabled=true\|false` |
| `--fulfillment-code-hook` | No | structure | None | Lambda invocation for fulfillment. Shorthand: `enabled=true\|false` |
| `--intent-confirmation-setting` | No | structure | None | Confirmation prompt before fulfillment |
| `--intent-closing-setting` | No | structure | None | Closing statement after fulfillment |
| `--input-contexts` | No | list | None | Contexts required for this intent |
| `--output-contexts` | No | list | None | Contexts set when intent is fulfilled |
| `--kendra-configuration` | No | structure | None | Amazon Kendra search configuration |
| `--initial-response-setting` | No | structure | None | Initial response configuration |

**Sample Utterances Structure:**
```json
[
    {"utterance": "I want to order a pizza"},
    {"utterance": "Can I get a pizza"}
]
```

**Output Schema:**
```json
{
    "intentId": "string",
    "intentName": "string",
    "description": "string",
    "parentIntentSignature": "string",
    "sampleUtterances": [{"utterance": "string"}],
    "dialogCodeHook": {"enabled": true|false},
    "fulfillmentCodeHook": {"enabled": true|false},
    "intentConfirmationSetting": {},
    "intentClosingSetting": {},
    "inputContexts": [{"name": "string"}],
    "outputContexts": [{"name": "string", "timeToLiveInSeconds": "integer", "turnsToLive": "integer"}],
    "kendraConfiguration": {},
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "creationDateTime": "timestamp",
    "initialResponseSetting": {}
}
```

---

### 4.2 `delete-intent`

Deletes an intent and all of its slots.

**Synopsis:**
```bash
aws lexv2-models delete-intent \
    --intent-id <value> \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--intent-id` | **Yes** | string | -- | Intent identifier (10 chars) |
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-version` | **Yes** | string | -- | Bot version (must be `DRAFT`) |
| `--locale-id` | **Yes** | string | -- | Locale identifier |

**Output:** None

---

### 4.3 `describe-intent`

Gets metadata for an intent.

**Synopsis:**
```bash
aws lexv2-models describe-intent \
    --intent-id <value> \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--intent-id` | **Yes** | string | -- | Intent identifier (10 chars) |
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-version` | **Yes** | string | -- | Bot version |
| `--locale-id` | **Yes** | string | -- | Locale identifier |

**Output Schema:**
```json
{
    "intentId": "string",
    "intentName": "string",
    "description": "string",
    "parentIntentSignature": "string",
    "sampleUtterances": [{"utterance": "string"}],
    "dialogCodeHook": {"enabled": true|false},
    "fulfillmentCodeHook": {},
    "slotPriorities": [
        {
            "priority": "integer",
            "slotId": "string"
        }
    ],
    "intentConfirmationSetting": {},
    "intentClosingSetting": {},
    "inputContexts": [{"name": "string"}],
    "outputContexts": [],
    "kendraConfiguration": {},
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "creationDateTime": "timestamp",
    "lastUpdatedDateTime": "timestamp",
    "initialResponseSetting": {},
    "qnaIntentConfiguration": {},
    "qInConnectIntentConfiguration": {}
}
```

---

### 4.4 `list-intents`

Lists all intents in a bot locale.

**Synopsis:**
```bash
aws lexv2-models list-intents \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    [--sort-by <value>] \
    [--filters <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-version` | **Yes** | string | -- | Bot version |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--sort-by` | No | structure | None | Sort field and order |
| `--filters` | No | list | None | Filter criteria |
| `--max-results` | No | integer | None | Maximum intents to return (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "intentSummaries": [
        {
            "intentId": "string",
            "intentName": "string",
            "description": "string",
            "parentIntentSignature": "string",
            "inputContexts": [{"name": "string"}],
            "outputContexts": [],
            "lastUpdatedDateTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 4.5 `update-intent`

Updates an existing intent.

**Synopsis:**
```bash
aws lexv2-models update-intent \
    --intent-id <value> \
    --intent-name <value> \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    [--description <value>] \
    [--parent-intent-signature <value>] \
    [--sample-utterances <value>] \
    [--dialog-code-hook <value>] \
    [--fulfillment-code-hook <value>] \
    [--slot-priorities <value>] \
    [--intent-confirmation-setting <value>] \
    [--intent-closing-setting <value>] \
    [--input-contexts <value>] \
    [--output-contexts <value>] \
    [--kendra-configuration <value>] \
    [--initial-response-setting <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--intent-id` | **Yes** | string | -- | Intent identifier (10 chars) |
| `--intent-name` | **Yes** | string | -- | Updated intent name (1-100 chars) |
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-version` | **Yes** | string | -- | Bot version (must be `DRAFT`) |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--description` | No | string | None | Updated description |
| `--sample-utterances` | No | list | None | Updated sample utterances |
| `--dialog-code-hook` | No | structure | None | Dialog code hook settings |
| `--fulfillment-code-hook` | No | structure | None | Fulfillment code hook settings |
| `--slot-priorities` | No | list | None | Priority order for slots |
| `--intent-confirmation-setting` | No | structure | None | Confirmation prompt settings |
| `--intent-closing-setting` | No | structure | None | Closing settings |
| `--input-contexts` | No | list | None | Input contexts |
| `--output-contexts` | No | list | None | Output contexts |
| `--kendra-configuration` | No | structure | None | Kendra search config |
| `--initial-response-setting` | No | structure | None | Initial response config |

**Output Schema:**
```json
{
    "intentId": "string",
    "intentName": "string",
    "description": "string",
    "parentIntentSignature": "string",
    "sampleUtterances": [],
    "dialogCodeHook": {},
    "fulfillmentCodeHook": {},
    "slotPriorities": [],
    "intentConfirmationSetting": {},
    "intentClosingSetting": {},
    "inputContexts": [],
    "outputContexts": [],
    "kendraConfiguration": {},
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "creationDateTime": "timestamp",
    "lastUpdatedDateTime": "timestamp",
    "initialResponseSetting": {}
}
```

---

### 4.6 `list-built-in-intents`

Lists the built-in intents available for a locale.

**Synopsis:**
```bash
aws lexv2-models list-built-in-intents \
    --locale-id <value> \
    [--sort-by <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--sort-by` | No | structure | None | Sort field and order |
| `--max-results` | No | integer | None | Maximum results (1-20) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "builtInIntentSummaries": [
        {
            "intentSignature": "string",
            "description": "string"
        }
    ],
    "nextToken": "string",
    "localeId": "string"
}
```

---

### 4.7 `list-recommended-intents`

Lists recommended intents from a bot recommendation.

**Synopsis:**
```bash
aws lexv2-models list-recommended-intents \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    --bot-recommendation-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-version` | **Yes** | string | -- | Bot version |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--bot-recommendation-id` | **Yes** | string | -- | Recommendation identifier (10 chars) |
| `--max-results` | No | integer | None | Maximum results (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "botRecommendationId": "string",
    "summaryList": [
        {
            "intentId": "string",
            "intentName": "string",
            "sampleUtterancesCount": "integer"
        }
    ],
    "nextToken": "string"
}
```
