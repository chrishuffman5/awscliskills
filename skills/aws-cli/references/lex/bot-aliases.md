# Bot Aliases

### 2.1 `create-bot-alias`

Creates an alias for a bot. An alias points to a specific version of a bot and can be used for routing traffic between versions.

**Synopsis:**
```bash
aws lexv2-models create-bot-alias \
    --bot-alias-name <value> \
    --bot-id <value> \
    [--description <value>] \
    [--bot-version <value>] \
    [--bot-alias-locale-settings <value>] \
    [--conversation-log-settings <value>] \
    [--sentiment-analysis-settings <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-alias-name` | **Yes** | string | -- | Alias name (1-100 chars, pattern: `^([0-9a-zA-Z][_-]?){1,100}$`) |
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--description` | No | string | None | Description (0-2000 chars) |
| `--bot-version` | No | string | None | Bot version this alias points to (1-5 digits) |
| `--bot-alias-locale-settings` | No | map | None | Per-locale Lambda and settings configuration |
| `--conversation-log-settings` | No | structure | None | Text and audio logging configuration |
| `--sentiment-analysis-settings` | No | structure | None | Sentiment detection. Shorthand: `detectSentiment=true\|false` |
| `--tags` | No | map | None | Tags (max 200) |

**ConversationLogSettings Structure:**
```json
{
    "textLogSettings": [
        {
            "enabled": true|false,
            "destination": {
                "cloudWatch": {
                    "cloudWatchLogGroupArn": "string",
                    "logPrefix": "string"
                }
            },
            "selectiveLoggingEnabled": true|false
        }
    ],
    "audioLogSettings": [
        {
            "enabled": true|false,
            "destination": {
                "s3Bucket": {
                    "kmsKeyArn": "string",
                    "s3BucketArn": "string",
                    "logPrefix": "string"
                }
            },
            "selectiveLoggingEnabled": true|false
        }
    ]
}
```

**BotAliasLocaleSettings Structure:**
```json
{
    "en_US": {
        "enabled": true|false,
        "codeHookSpecification": {
            "lambdaCodeHook": {
                "lambdaARN": "string",
                "codeHookInterfaceVersion": "1.0"
            }
        }
    }
}
```

**Output Schema:**
```json
{
    "botAliasId": "string",
    "botAliasName": "string",
    "description": "string",
    "botVersion": "string",
    "botAliasLocaleSettings": {},
    "conversationLogSettings": {},
    "sentimentAnalysisSettings": {"detectSentiment": true|false},
    "botAliasStatus": "Creating|Available|Deleting|Failed",
    "botId": "string",
    "creationDateTime": "timestamp",
    "tags": {"string": "string"}
}
```

---

### 2.2 `delete-bot-alias`

Deletes a bot alias.

**Synopsis:**
```bash
aws lexv2-models delete-bot-alias \
    --bot-alias-id <value> \
    --bot-id <value> \
    [--skip-resource-in-use-check | --no-skip-resource-in-use-check] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-alias-id` | **Yes** | string | -- | Alias identifier (10 chars) |
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--skip-resource-in-use-check` | No | boolean | false | Skip in-use check |

**Output Schema:**
```json
{
    "botAliasId": "string",
    "botId": "string",
    "botAliasStatus": "Creating|Available|Deleting|Failed"
}
```

---

### 2.3 `describe-bot-alias`

Gets metadata for a bot alias.

**Synopsis:**
```bash
aws lexv2-models describe-bot-alias \
    --bot-alias-id <value> \
    --bot-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-alias-id` | **Yes** | string | -- | Alias identifier (10 chars) |
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |

**Output Schema:**
```json
{
    "botAliasId": "string",
    "botAliasName": "string",
    "description": "string",
    "botVersion": "string",
    "botAliasLocaleSettings": {},
    "conversationLogSettings": {},
    "sentimentAnalysisSettings": {"detectSentiment": true|false},
    "botAliasHistoryEvents": [
        {
            "botVersion": "string",
            "startDate": "timestamp",
            "endDate": "timestamp"
        }
    ],
    "botAliasStatus": "Creating|Available|Deleting|Failed",
    "botId": "string",
    "creationDateTime": "timestamp",
    "lastUpdatedDateTime": "timestamp",
    "parentBotNetworks": [
        {
            "botId": "string",
            "botVersion": "string"
        }
    ]
}
```

---

### 2.4 `list-bot-aliases`

Lists all aliases for a bot.

**Synopsis:**
```bash
aws lexv2-models list-bot-aliases \
    --bot-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--max-results` | No | integer | None | Maximum aliases to return (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "botAliasSummaries": [
        {
            "botAliasId": "string",
            "botAliasName": "string",
            "description": "string",
            "botVersion": "string",
            "botAliasStatus": "string",
            "creationDateTime": "timestamp",
            "lastUpdatedDateTime": "timestamp"
        }
    ],
    "nextToken": "string",
    "botId": "string"
}
```

---

### 2.5 `update-bot-alias`

Updates an existing bot alias configuration.

**Synopsis:**
```bash
aws lexv2-models update-bot-alias \
    --bot-alias-id <value> \
    --bot-alias-name <value> \
    --bot-id <value> \
    [--description <value>] \
    [--bot-version <value>] \
    [--bot-alias-locale-settings <value>] \
    [--conversation-log-settings <value>] \
    [--sentiment-analysis-settings <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-alias-id` | **Yes** | string | -- | Alias identifier (10 chars) |
| `--bot-alias-name` | **Yes** | string | -- | Updated alias name (1-100 chars) |
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--description` | No | string | None | Updated description (0-2000 chars) |
| `--bot-version` | No | string | None | Bot version to point to |
| `--bot-alias-locale-settings` | No | map | None | Per-locale Lambda and settings |
| `--conversation-log-settings` | No | structure | None | Logging configuration |
| `--sentiment-analysis-settings` | No | structure | None | Sentiment detection settings |

**Output Schema:**
```json
{
    "botAliasId": "string",
    "botAliasName": "string",
    "description": "string",
    "botVersion": "string",
    "botAliasLocaleSettings": {},
    "conversationLogSettings": {},
    "sentimentAnalysisSettings": {"detectSentiment": true|false},
    "botAliasStatus": "string",
    "botId": "string",
    "creationDateTime": "timestamp",
    "lastUpdatedDateTime": "timestamp"
}
```
