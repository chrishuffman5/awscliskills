# Analytics

### 9.1 `list-aggregated-utterances`

Lists aggregated utterance data for a bot. Provides information about how often utterances are recognized or missed.

**Synopsis:**
```bash
aws lexv2-models list-aggregated-utterances \
    --bot-id <value> \
    --locale-id <value> \
    --aggregation-duration <value> \
    [--bot-alias-id <value>] \
    [--bot-version <value>] \
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
| `--locale-id` | **Yes** | string | -- | Locale identifier |
| `--aggregation-duration` | **Yes** | structure | -- | Time period for aggregation |
| `--bot-alias-id` | No | string | None | Alias identifier (use either alias or version) |
| `--bot-version` | No | string | None | Bot version |
| `--sort-by` | No | structure | None | Sort field and order |
| `--filters` | No | list | None | Filter criteria |
| `--max-results` | No | integer | None | Maximum results (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**AggregationDuration Structure:**
```json
{
    "relativeAggregationDuration": {
        "timeDimension": "Hours|Days|Weeks",
        "timeValue": "integer"
    }
}
```

**Output Schema:**
```json
{
    "botId": "string",
    "botAliasId": "string",
    "botVersion": "string",
    "localeId": "string",
    "aggregationDuration": {},
    "aggregationWindowStartTime": "timestamp",
    "aggregationWindowEndTime": "timestamp",
    "aggregationLastRefreshedDateTime": "timestamp",
    "aggregatedUtterancesSummaries": [
        {
            "utterance": "string",
            "hitCount": "integer",
            "missedCount": "integer",
            "utteranceFirstRecordedInAggregationDuration": "timestamp",
            "utteranceLastRecordedInAggregationDuration": "timestamp",
            "containsDataFromDeletedResources": true|false
        }
    ],
    "nextToken": "string"
}
```

---

### 9.2 `list-intent-metrics`

Lists intent-level metrics for a bot.

**Synopsis:**
```bash
aws lexv2-models list-intent-metrics \
    --bot-id <value> \
    --start-date-time <value> \
    --end-date-time <value> \
    --metrics <value> \
    [--bin-by <value>] \
    [--group-by <value>] \
    [--filters <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier |
| `--start-date-time` | **Yes** | timestamp | -- | Start of the time range |
| `--end-date-time` | **Yes** | timestamp | -- | End of the time range |
| `--metrics` | **Yes** | list | -- | Metrics to retrieve |
| `--bin-by` | No | list | None | Time bin specifications |
| `--group-by` | No | list | None | Grouping fields |
| `--filters` | No | list | None | Filter criteria |
| `--max-results` | No | integer | None | Maximum results (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "botId": "string",
    "results": [
        {
            "binKeys": [
                {
                    "name": "string",
                    "value": "integer"
                }
            ],
            "groupByKeys": [
                {
                    "name": "string",
                    "value": "string"
                }
            ],
            "metricsResults": [
                {
                    "name": "string",
                    "statistic": "Sum|Avg|Max",
                    "value": "double"
                }
            ]
        }
    ],
    "nextToken": "string"
}
```

---

### 9.3 `list-intent-paths`

Lists intent paths showing how users navigate through intents.

**Synopsis:**
```bash
aws lexv2-models list-intent-paths \
    --bot-id <value> \
    --start-date-time <value> \
    --end-date-time <value> \
    --intent-path <value> \
    [--filters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier |
| `--start-date-time` | **Yes** | timestamp | -- | Start of the time range |
| `--end-date-time` | **Yes** | timestamp | -- | End of the time range |
| `--intent-path` | **Yes** | string | -- | Intent path to analyze |
| `--filters` | No | list | None | Filter criteria |

**Output Schema:**
```json
{
    "nodeSummaries": [
        {
            "intentName": "string",
            "intentPath": "string",
            "intentCount": "integer",
            "intentLevel": "integer",
            "nodeType": "Inner|Exit"
        }
    ]
}
```

---

### 9.4 `list-intent-stage-metrics`

Lists intent stage metrics for a bot.

**Synopsis:**
```bash
aws lexv2-models list-intent-stage-metrics \
    --bot-id <value> \
    --start-date-time <value> \
    --end-date-time <value> \
    --metrics <value> \
    [--bin-by <value>] \
    [--group-by <value>] \
    [--filters <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier |
| `--start-date-time` | **Yes** | timestamp | -- | Start of the time range |
| `--end-date-time` | **Yes** | timestamp | -- | End of the time range |
| `--metrics` | **Yes** | list | -- | Metrics to retrieve |
| `--bin-by` | No | list | None | Time bin specifications |
| `--group-by` | No | list | None | Grouping fields |
| `--filters` | No | list | None | Filter criteria |
| `--max-results` | No | integer | None | Maximum results (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "botId": "string",
    "results": [],
    "nextToken": "string"
}
```

---

### 9.5 `list-session-analytics-data`

Lists detailed session analytics data.

**Synopsis:**
```bash
aws lexv2-models list-session-analytics-data \
    --bot-id <value> \
    --start-date-time <value> \
    --end-date-time <value> \
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
| `--bot-id` | **Yes** | string | -- | Bot identifier |
| `--start-date-time` | **Yes** | timestamp | -- | Start of the time range |
| `--end-date-time` | **Yes** | timestamp | -- | End of the time range |
| `--sort-by` | No | structure | None | Sort field and order |
| `--filters` | No | list | None | Filter criteria |
| `--max-results` | No | integer | None | Maximum results (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "botId": "string",
    "sessions": [
        {
            "botAliasId": "string",
            "botVersion": "string",
            "localeId": "string",
            "channel": "string",
            "sessionId": "string",
            "conversationStartTime": "timestamp",
            "conversationEndTime": "timestamp",
            "conversationDurationSeconds": "long",
            "conversationEndState": "Success|Failure|Dropped",
            "mode": "Speech|Text|DTMF|MultiMode",
            "numberOfTurns": "long",
            "invokedIntentSamples": [
                {
                    "intentName": "string"
                }
            ],
            "originatingRequestId": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 9.6 `list-session-metrics`

Lists session-level metrics for a bot.

**Synopsis:**
```bash
aws lexv2-models list-session-metrics \
    --bot-id <value> \
    --start-date-time <value> \
    --end-date-time <value> \
    --metrics <value> \
    [--bin-by <value>] \
    [--group-by <value>] \
    [--filters <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier |
| `--start-date-time` | **Yes** | timestamp | -- | Start of the time range |
| `--end-date-time` | **Yes** | timestamp | -- | End of the time range |
| `--metrics` | **Yes** | list | -- | Metrics to retrieve |
| `--bin-by` | No | list | None | Time bin specifications |
| `--group-by` | No | list | None | Grouping fields |
| `--filters` | No | list | None | Filter criteria |
| `--max-results` | No | integer | None | Maximum results (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "botId": "string",
    "results": [],
    "nextToken": "string"
}
```

---

### 9.7 `list-utterance-analytics-data`

Lists detailed utterance analytics data.

**Synopsis:**
```bash
aws lexv2-models list-utterance-analytics-data \
    --bot-id <value> \
    --start-date-time <value> \
    --end-date-time <value> \
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
| `--bot-id` | **Yes** | string | -- | Bot identifier |
| `--start-date-time` | **Yes** | timestamp | -- | Start of the time range |
| `--end-date-time` | **Yes** | timestamp | -- | End of the time range |
| `--sort-by` | No | structure | None | Sort field and order |
| `--filters` | No | list | None | Filter criteria |
| `--max-results` | No | integer | None | Maximum results (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "botId": "string",
    "utterances": [
        {
            "botAliasId": "string",
            "botVersion": "string",
            "localeId": "string",
            "sessionId": "string",
            "channel": "string",
            "mode": "Speech|Text|DTMF|MultiMode",
            "conversationStartTime": "timestamp",
            "conversationEndTime": "timestamp",
            "utterance": "string",
            "utteranceTimestamp": "timestamp",
            "audioVoiceDurationMillis": "long",
            "utteranceUnderstood": true|false,
            "inputType": "string",
            "outputType": "string",
            "associatedIntentName": "string",
            "associatedSlotName": "string",
            "intentState": "string",
            "dialogActionType": "string",
            "botResponseAudioVoiceId": "string",
            "slotsFilledInSession": "string",
            "utteranceRequestId": "string",
            "botResponses": [
                {
                    "content": "string",
                    "contentType": "PlainText|CustomPayload|SSML|ImageResponseCard"
                }
            ]
        }
    ],
    "nextToken": "string"
}
```

---

### 9.8 `list-utterance-metrics`

Lists utterance-level metrics for a bot.

**Synopsis:**
```bash
aws lexv2-models list-utterance-metrics \
    --bot-id <value> \
    --start-date-time <value> \
    --end-date-time <value> \
    --metrics <value> \
    [--bin-by <value>] \
    [--group-by <value>] \
    [--filters <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier |
| `--start-date-time` | **Yes** | timestamp | -- | Start of the time range |
| `--end-date-time` | **Yes** | timestamp | -- | End of the time range |
| `--metrics` | **Yes** | list | -- | Metrics to retrieve |
| `--bin-by` | No | list | None | Time bin specifications |
| `--group-by` | No | list | None | Grouping fields |
| `--filters` | No | list | None | Filter criteria |
| `--max-results` | No | integer | None | Maximum results (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "botId": "string",
    "results": [],
    "nextToken": "string"
}
```

---

### 9.9 `delete-utterances`

Deletes stored utterance data for a bot.

**Synopsis:**
```bash
aws lexv2-models delete-utterances \
    --bot-id <value> \
    [--locale-id <value>] \
    [--session-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--locale-id` | No | string | None | Locale identifier (deletes for specific locale) |
| `--session-id` | No | string | None | Session identifier (deletes for specific session) |

**Output:** None
