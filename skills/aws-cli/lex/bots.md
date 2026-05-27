# Bots

### 1.1 `create-bot`

Creates a new Amazon Lex V2 bot.

**Synopsis:**
```bash
aws lexv2-models create-bot \
    --bot-name <value> \
    --role-arn <value> \
    --data-privacy <value> \
    --idle-session-ttl-in-seconds <value> \
    [--description <value>] \
    [--bot-tags <value>] \
    [--test-bot-alias-tags <value>] \
    [--bot-type <value>] \
    [--bot-members <value>] \
    [--error-log-settings <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-name` | **Yes** | string | -- | Bot name (1-100 chars, pattern: `^([0-9a-zA-Z][_-]?){1,100}$`) |
| `--role-arn` | **Yes** | string | -- | IAM role ARN with bot access permissions |
| `--data-privacy` | **Yes** | structure | -- | COPPA compliance. Shorthand: `childDirected=true\|false` |
| `--idle-session-ttl-in-seconds` | **Yes** | integer | -- | Session timeout (60-86400 seconds) |
| `--description` | No | string | None | Bot description (0-2000 chars) |
| `--bot-tags` | No | map | None | Tags for the bot (max 200) |
| `--test-bot-alias-tags` | No | map | None | Tags for the test bot alias (max 200) |
| `--bot-type` | No | string | `Bot` | Bot type: `Bot` or `BotNetwork` |
| `--bot-members` | No | list | None | Bot members for a bot network (max 10) |
| `--error-log-settings` | No | structure | None | Error logging. Shorthand: `enabled=true\|false` |

**Output Schema:**
```json
{
    "botId": "string",
    "botName": "string",
    "description": "string",
    "roleArn": "string",
    "dataPrivacy": {
        "childDirected": true|false
    },
    "idleSessionTTLInSeconds": "integer",
    "botStatus": "Creating|Available|Inactive|Deleting|Failed|Versioning|Importing|Updating",
    "creationDateTime": "timestamp",
    "botTags": {"string": "string"},
    "testBotAliasTags": {"string": "string"},
    "botType": "Bot|BotNetwork",
    "botMembers": [
        {
            "botMemberId": "string",
            "botMemberName": "string",
            "botMemberAliasId": "string",
            "botMemberAliasName": "string",
            "botMemberVersion": "string"
        }
    ],
    "errorLogSettings": {
        "enabled": true|false
    }
}
```

---

### 1.2 `delete-bot`

Deletes all versions, aliases, and locales of a bot.

**Synopsis:**
```bash
aws lexv2-models delete-bot \
    --bot-id <value> \
    [--skip-resource-in-use-check | --no-skip-resource-in-use-check] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 alphanumeric chars) |
| `--skip-resource-in-use-check` | No | boolean | false | Skip checking if bot is in use |

**Output Schema:**
```json
{
    "botId": "string",
    "botStatus": "Creating|Available|Inactive|Deleting|Failed|Versioning|Importing|Updating"
}
```

---

### 1.3 `describe-bot`

Gets metadata information about a bot.

**Synopsis:**
```bash
aws lexv2-models describe-bot \
    --bot-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 alphanumeric chars) |

**Output Schema:**
```json
{
    "botId": "string",
    "botName": "string",
    "description": "string",
    "roleArn": "string",
    "dataPrivacy": {
        "childDirected": true|false
    },
    "idleSessionTTLInSeconds": "integer",
    "botStatus": "Creating|Available|Inactive|Deleting|Failed|Versioning|Importing|Updating",
    "creationDateTime": "timestamp",
    "lastUpdatedDateTime": "timestamp",
    "botType": "Bot|BotNetwork",
    "botMembers": [
        {
            "botMemberId": "string",
            "botMemberName": "string",
            "botMemberAliasId": "string",
            "botMemberAliasName": "string",
            "botMemberVersion": "string"
        }
    ],
    "failureReasons": ["string"],
    "errorLogSettings": {
        "enabled": true|false
    }
}
```

---

### 1.4 `list-bots`

Lists all bots in the account.

**Synopsis:**
```bash
aws lexv2-models list-bots \
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
| `--sort-by` | No | structure | None | Sort field and order. Shorthand: `attribute=BotName,order=Ascending\|Descending` |
| `--filters` | No | list | None | Filter criteria for bots |
| `--max-results` | No | integer | None | Maximum bots to return (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "botSummaries": [
        {
            "botId": "string",
            "botName": "string",
            "description": "string",
            "botStatus": "string",
            "latestBotVersion": "string",
            "lastUpdatedDateTime": "timestamp",
            "botType": "Bot|BotNetwork"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.5 `update-bot`

Updates an existing bot configuration.

**Synopsis:**
```bash
aws lexv2-models update-bot \
    --bot-id <value> \
    --bot-name <value> \
    --role-arn <value> \
    --data-privacy <value> \
    --idle-session-ttl-in-seconds <value> \
    [--description <value>] \
    [--bot-type <value>] \
    [--bot-members <value>] \
    [--error-log-settings <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-name` | **Yes** | string | -- | New bot name (1-100 chars) |
| `--role-arn` | **Yes** | string | -- | IAM role ARN |
| `--data-privacy` | **Yes** | structure | -- | COPPA compliance settings |
| `--idle-session-ttl-in-seconds` | **Yes** | integer | -- | Session timeout (60-86400) |
| `--description` | No | string | None | Updated description (0-2000 chars) |
| `--bot-type` | No | string | None | `Bot` or `BotNetwork` |
| `--bot-members` | No | list | None | Bot members for network |
| `--error-log-settings` | No | structure | None | Error logging settings |

**Output Schema:**
```json
{
    "botId": "string",
    "botName": "string",
    "description": "string",
    "roleArn": "string",
    "dataPrivacy": {"childDirected": true|false},
    "idleSessionTTLInSeconds": "integer",
    "botStatus": "string",
    "creationDateTime": "timestamp",
    "lastUpdatedDateTime": "timestamp",
    "botType": "Bot|BotNetwork",
    "botMembers": [],
    "errorLogSettings": {"enabled": true|false}
}
```

---

### 1.6 `create-bot-version`

Creates an immutable snapshot of a bot.

**Synopsis:**
```bash
aws lexv2-models create-bot-version \
    --bot-id <value> \
    --bot-version-locale-specification <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-version-locale-specification` | **Yes** | map | -- | Map of locale IDs to source versions |
| `--description` | No | string | None | Version description (0-2000 chars) |

**Output Schema:**
```json
{
    "botId": "string",
    "description": "string",
    "botVersion": "string",
    "botVersionLocaleSpecification": {
        "string": {
            "sourceBotVersion": "string"
        }
    },
    "botStatus": "string",
    "creationDateTime": "timestamp"
}
```

---

### 1.7 `delete-bot-version`

Deletes a specific version of a bot.

**Synopsis:**
```bash
aws lexv2-models delete-bot-version \
    --bot-id <value> \
    --bot-version <value> \
    [--skip-resource-in-use-check | --no-skip-resource-in-use-check] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-version` | **Yes** | string | -- | Version number to delete (1-5 digits) |
| `--skip-resource-in-use-check` | No | boolean | false | Skip in-use check |

**Output Schema:**
```json
{
    "botId": "string",
    "botVersion": "string",
    "botStatus": "string"
}
```

---

### 1.8 `describe-bot-version`

Gets metadata for a specific bot version.

**Synopsis:**
```bash
aws lexv2-models describe-bot-version \
    --bot-id <value> \
    --bot-version <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-version` | **Yes** | string | -- | Version number (1-5 digits) |

**Output Schema:**
```json
{
    "botId": "string",
    "botName": "string",
    "botVersion": "string",
    "description": "string",
    "roleArn": "string",
    "dataPrivacy": {"childDirected": true|false},
    "idleSessionTTLInSeconds": "integer",
    "botStatus": "string",
    "failureReasons": ["string"],
    "creationDateTime": "timestamp",
    "parentBotNetworks": [
        {
            "botId": "string",
            "botVersion": "string"
        }
    ],
    "botType": "Bot|BotNetwork",
    "botMembers": []
}
```

---

### 1.9 `list-bot-versions`

Lists all versions of a bot.

**Synopsis:**
```bash
aws lexv2-models list-bot-versions \
    --bot-id <value> \
    [--sort-by <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--sort-by` | No | structure | None | Sort field and order |
| `--max-results` | No | integer | None | Maximum versions to return (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "botId": "string",
    "botVersionSummaries": [
        {
            "botName": "string",
            "botVersion": "string",
            "description": "string",
            "botStatus": "string",
            "creationDateTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```
