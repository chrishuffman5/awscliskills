# Bot Locales

### 3.1 `create-bot-locale`

Creates a locale in a bot. A locale contains the intents and slot types for conversations in a specific language and region.

**Synopsis:**
```bash
aws lexv2-models create-bot-locale \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    --nlu-intent-confidence-threshold <value> \
    [--description <value>] \
    [--voice-settings <value>] \
    [--generative-ai-settings <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-version` | **Yes** | string | -- | Bot version (must be `DRAFT`) |
| `--locale-id` | **Yes** | string | -- | Locale identifier (e.g., `en_US`, `fr_FR`) |
| `--nlu-intent-confidence-threshold` | **Yes** | double | -- | Confidence threshold for fallback intent (0.0-1.0) |
| `--description` | No | string | None | Description (0-2000 chars) |
| `--voice-settings` | No | structure | None | Amazon Polly voice configuration |
| `--generative-ai-settings` | No | structure | None | Generative AI settings using Amazon Bedrock |

**VoiceSettings Structure:**
```json
{
    "engine": "standard|neural|long-form|generative",
    "voiceId": "string"
}
```

**Output Schema:**
```json
{
    "botId": "string",
    "botVersion": "string",
    "localeName": "string",
    "localeId": "string",
    "description": "string",
    "nluIntentConfidenceThreshold": "double",
    "voiceSettings": {
        "engine": "standard|neural|long-form|generative",
        "voiceId": "string"
    },
    "botLocaleStatus": "Creating|Building|Built|ReadyExpressTesting|Failed|Deleting|NotBuilt|Importing|Processing",
    "creationDateTime": "timestamp"
}
```

---

### 3.2 `delete-bot-locale`

Deletes a locale from a bot.

**Synopsis:**
```bash
aws lexv2-models delete-bot-locale \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-version` | **Yes** | string | -- | Bot version (must be `DRAFT`) |
| `--locale-id` | **Yes** | string | -- | Locale identifier |

**Output Schema:**
```json
{
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "botLocaleStatus": "string"
}
```

---

### 3.3 `describe-bot-locale`

Gets metadata for a bot locale.

**Synopsis:**
```bash
aws lexv2-models describe-bot-locale \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-version` | **Yes** | string | -- | Bot version |
| `--locale-id` | **Yes** | string | -- | Locale identifier |

**Output Schema:**
```json
{
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "localeName": "string",
    "description": "string",
    "nluIntentConfidenceThreshold": "double",
    "voiceSettings": {
        "engine": "string",
        "voiceId": "string"
    },
    "intentsCount": "integer",
    "slotTypesCount": "integer",
    "botLocaleStatus": "string",
    "failureReasons": ["string"],
    "creationDateTime": "timestamp",
    "lastUpdatedDateTime": "timestamp",
    "lastBuildSubmittedDateTime": "timestamp",
    "botLocaleHistoryEvents": [
        {
            "event": "string",
            "eventDate": "timestamp"
        }
    ],
    "recommendedActions": ["string"],
    "generativeAISettings": {}
}
```

---

### 3.4 `list-bot-locales`

Lists all locales for a bot version.

**Synopsis:**
```bash
aws lexv2-models list-bot-locales \
    --bot-id <value> \
    --bot-version <value> \
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
| `--sort-by` | No | structure | None | Sort field and order |
| `--filters` | No | list | None | Filter criteria |
| `--max-results` | No | integer | None | Maximum locales to return (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "botId": "string",
    "botVersion": "string",
    "botLocaleSummaries": [
        {
            "localeId": "string",
            "localeName": "string",
            "description": "string",
            "botLocaleStatus": "string",
            "lastUpdatedDateTime": "timestamp",
            "lastBuildSubmittedDateTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 3.5 `update-bot-locale`

Updates a bot locale configuration including NLU threshold, voice settings, and generative AI settings.

**Synopsis:**
```bash
aws lexv2-models update-bot-locale \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    --nlu-intent-confidence-threshold <value> \
    [--description <value>] \
    [--voice-settings <value>] \
    [--generative-ai-settings <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-version` | **Yes** | string | -- | Bot version (must be `DRAFT`) |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--nlu-intent-confidence-threshold` | **Yes** | double | -- | Updated confidence threshold (0.0-1.0) |
| `--description` | No | string | None | Updated description |
| `--voice-settings` | No | structure | None | Updated voice configuration |
| `--generative-ai-settings` | No | structure | None | Updated generative AI settings |

**Output Schema:**
```json
{
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "localeName": "string",
    "description": "string",
    "nluIntentConfidenceThreshold": "double",
    "voiceSettings": {},
    "botLocaleStatus": "string",
    "failureReasons": ["string"],
    "creationDateTime": "timestamp",
    "lastUpdatedDateTime": "timestamp",
    "recommendedActions": ["string"],
    "generativeAISettings": {}
}
```

---

### 3.6 `build-bot-locale`

Builds a bot locale. After building, the locale is ready for testing. You must build a locale before creating a bot version.

**Synopsis:**
```bash
aws lexv2-models build-bot-locale \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-version` | **Yes** | string | -- | Bot version (must be `DRAFT`) |
| `--locale-id` | **Yes** | string | -- | Locale identifier |

**Output Schema:**
```json
{
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "botLocaleStatus": "Creating|Building|Built|ReadyExpressTesting|Failed|Deleting|NotBuilt|Importing|Processing",
    "lastBuildSubmittedDateTime": "timestamp"
}
```
