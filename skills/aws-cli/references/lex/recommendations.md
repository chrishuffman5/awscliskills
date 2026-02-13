# Recommendations

### 11.1 `start-bot-recommendation`

Starts a bot recommendation process that analyzes transcripts to suggest intents and slot types.

**Synopsis:**
```bash
aws lexv2-models start-bot-recommendation \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    --transcript-source-setting <value> \
    [--encryption-setting <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-version` | **Yes** | string | -- | Bot version (must be `DRAFT`) |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--transcript-source-setting` | **Yes** | structure | -- | Source of transcripts for analysis |
| `--encryption-setting` | No | structure | None | KMS encryption settings |

**Output Schema:**
```json
{
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "botRecommendationStatus": "Processing|Updating|Available|Deleting|Failed|Stopping|Stopped|Downloading",
    "botRecommendationId": "string",
    "creationDateTime": "timestamp",
    "transcriptSourceSetting": {},
    "encryptionSetting": {}
}
```

---

### 11.2 `describe-bot-recommendation`

Gets metadata for a bot recommendation.

**Synopsis:**
```bash
aws lexv2-models describe-bot-recommendation \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    --bot-recommendation-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier |
| `--bot-version` | **Yes** | string | -- | Bot version |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--bot-recommendation-id` | **Yes** | string | -- | Recommendation identifier (10 chars) |

**Output Schema:**
```json
{
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "botRecommendationStatus": "string",
    "botRecommendationId": "string",
    "failureReasons": ["string"],
    "creationDateTime": "timestamp",
    "lastUpdatedDateTime": "timestamp",
    "transcriptSourceSetting": {},
    "encryptionSetting": {},
    "botRecommendationResults": {
        "botLocaleExportUrl": "string",
        "associatedTranscriptsUrl": "string",
        "statistics": {
            "intents": {
                "discoveredIntentCount": "integer"
            },
            "slotTypes": {
                "discoveredSlotTypeCount": "integer"
            }
        }
    }
}
```

---

### 11.3 `list-bot-recommendations`

Lists bot recommendations for a bot locale.

**Synopsis:**
```bash
aws lexv2-models list-bot-recommendations \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier |
| `--bot-version` | **Yes** | string | -- | Bot version |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--max-results` | No | integer | None | Maximum results (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "botRecommendationSummaries": [
        {
            "botRecommendationStatus": "string",
            "botRecommendationId": "string",
            "creationDateTime": "timestamp",
            "lastUpdatedDateTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 11.4 `update-bot-recommendation`

Updates a bot recommendation.

**Synopsis:**
```bash
aws lexv2-models update-bot-recommendation \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    --bot-recommendation-id <value> \
    --encryption-setting <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier |
| `--bot-version` | **Yes** | string | -- | Bot version |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--bot-recommendation-id` | **Yes** | string | -- | Recommendation identifier |
| `--encryption-setting` | **Yes** | structure | -- | Updated encryption settings |

**Output Schema:**
```json
{
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "botRecommendationStatus": "string",
    "botRecommendationId": "string",
    "creationDateTime": "timestamp",
    "lastUpdatedDateTime": "timestamp",
    "transcriptSourceSetting": {},
    "encryptionSetting": {}
}
```

---

### 11.5 `stop-bot-recommendation`

Stops a running bot recommendation.

**Synopsis:**
```bash
aws lexv2-models stop-bot-recommendation \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    --bot-recommendation-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier |
| `--bot-version` | **Yes** | string | -- | Bot version |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--bot-recommendation-id` | **Yes** | string | -- | Recommendation identifier |

**Output Schema:**
```json
{
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "botRecommendationStatus": "string",
    "botRecommendationId": "string"
}
```

---

### 11.6 `start-bot-resource-generation`

Starts generating bot resources (intents, slot types) from a natural language description.

**Synopsis:**
```bash
aws lexv2-models start-bot-resource-generation \
    --generation-input-prompt <value> \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--generation-input-prompt` | **Yes** | string | -- | Natural language description of the bot resources to generate (1-2000 chars) |
| `--bot-id` | **Yes** | string | -- | Bot identifier |
| `--bot-version` | **Yes** | string | -- | Bot version (must be `DRAFT`) |
| `--locale-id` | **Yes** | string | -- | Locale identifier |

**Output Schema:**
```json
{
    "generationInputPrompt": "string",
    "generationId": "string",
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "generationStatus": "Failed|Complete|InProgress",
    "creationDateTime": "timestamp"
}
```

---

### 11.7 `describe-bot-resource-generation`

Gets details about a bot resource generation.

**Synopsis:**
```bash
aws lexv2-models describe-bot-resource-generation \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    --generation-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier |
| `--bot-version` | **Yes** | string | -- | Bot version |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--generation-id` | **Yes** | string | -- | Generation identifier (10 chars) |

**Output Schema:**
```json
{
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "generationId": "string",
    "failureReasons": ["string"],
    "generationStatus": "Failed|Complete|InProgress",
    "generationInputPrompt": "string",
    "generatedBotLocaleUrl": "string",
    "creationDateTime": "timestamp",
    "modelArn": "string",
    "lastUpdatedDateTime": "timestamp"
}
```

---

### 11.8 `list-bot-resource-generations`

Lists bot resource generations.

**Synopsis:**
```bash
aws lexv2-models list-bot-resource-generations \
    --bot-id <value> \
    --bot-version <value> \
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
| `--bot-id` | **Yes** | string | -- | Bot identifier |
| `--bot-version` | **Yes** | string | -- | Bot version |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--sort-by` | No | structure | None | Sort field and order |
| `--max-results` | No | integer | None | Maximum results (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "generationSummaries": [
        {
            "generationId": "string",
            "generationStatus": "Failed|Complete|InProgress",
            "creationDateTime": "timestamp",
            "lastUpdatedDateTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 11.9 `generate-bot-element`

Generates a bot element such as an intent or slot type using generative AI.

**Synopsis:**
```bash
aws lexv2-models generate-bot-element \
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
| `--intent-id` | **Yes** | string | -- | Intent identifier |
| `--bot-id` | **Yes** | string | -- | Bot identifier |
| `--bot-version` | **Yes** | string | -- | Bot version |
| `--locale-id` | **Yes** | string | -- | Locale identifier |

**Output Schema:**
```json
{
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "intentId": "string",
    "sampleUtterances": [{"utterance": "string"}]
}
```

---

### 11.10 `search-associated-transcripts`

Searches transcripts associated with a bot recommendation.

**Synopsis:**
```bash
aws lexv2-models search-associated-transcripts \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    --bot-recommendation-id <value> \
    --search-order <value> \
    --filters <value> \
    [--max-results <value>] \
    [--next-index <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier |
| `--bot-version` | **Yes** | string | -- | Bot version |
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--bot-recommendation-id` | **Yes** | string | -- | Recommendation identifier |
| `--search-order` | **Yes** | string | -- | Sort order: `Ascending` or `Descending` |
| `--filters` | **Yes** | list | -- | Filter criteria |
| `--max-results` | No | integer | None | Maximum results (1-1000) |
| `--next-index` | No | integer | None | Index for pagination |

**Output Schema:**
```json
{
    "botId": "string",
    "botVersion": "string",
    "localeId": "string",
    "botRecommendationId": "string",
    "nextIndex": "integer",
    "associatedTranscripts": [
        {
            "transcript": "string"
        }
    ],
    "totalResults": "integer"
}
```
