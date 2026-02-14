# App Instance Admin & Bots

Commands from the `aws chime-sdk-identity` service.

### 3.1 `create-app-instance-admin`

Creates an admin for an AppInstance.

**Synopsis:**
```bash
aws chime-sdk-identity create-app-instance-admin \
    --app-instance-admin-arn <value> \
    --app-instance-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-admin-arn` | **Yes** | string | -- | ARN of the user to promote to admin |
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |

**Output Schema:**
```json
{
    "AppInstanceAdmin": {
        "Arn": "string",
        "Name": "string"
    },
    "AppInstanceArn": "string"
}
```

---

### 3.2 `describe-app-instance-admin`

Describes an AppInstance admin.

**Synopsis:**
```bash
aws chime-sdk-identity describe-app-instance-admin \
    --app-instance-admin-arn <value> \
    --app-instance-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-admin-arn` | **Yes** | string | -- | Admin user ARN |
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |

**Output Schema:**
```json
{
    "AppInstanceAdmin": {
        "Admin": {
            "Arn": "string",
            "Name": "string"
        },
        "AppInstanceArn": "string",
        "CreatedTimestamp": "timestamp"
    }
}
```

---

### 3.3 `list-app-instance-admins`

Lists admins for an AppInstance. **Paginated operation.**

**Synopsis:**
```bash
aws chime-sdk-identity list-app-instance-admins \
    --app-instance-arn <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |
| `--max-results` | No | integer | None | Max results per page (1-50) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "AppInstanceArn": "string",
    "AppInstanceAdmins": [
        {
            "Admin": {
                "Arn": "string",
                "Name": "string"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 3.4 `delete-app-instance-admin`

Removes an admin from an AppInstance.

**Synopsis:**
```bash
aws chime-sdk-identity delete-app-instance-admin \
    --app-instance-admin-arn <value> \
    --app-instance-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-admin-arn` | **Yes** | string | -- | Admin user ARN |
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |

**Output:** None

---

### 3.5 `create-app-instance-bot`

Creates a bot for an AppInstance (Lex V2 integration).

**Synopsis:**
```bash
aws chime-sdk-identity create-app-instance-bot \
    --app-instance-arn <value> \
    --configuration <value> \
    [--name <value>] \
    [--metadata <value>] \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |
| `--configuration` | **Yes** | structure | -- | Lex V2 bot configuration |
| `--name` | No | string | None | Bot name (max 256 chars) |
| `--metadata` | No | string | None | Metadata (max 1024 chars) |
| `--client-request-token` | No | string | Auto | Idempotency token (2-64 chars) |
| `--tags` | No | list | None | Tags (max 50) |

**Configuration:**
```json
{
    "Lex": {
        "LexBotAliasArn": "string (required)",
        "LocaleId": "string (required)",
        "InvokedBy": {
            "StandardMessages": "AUTO|ALL|MENTIONS|NONE (required)",
            "TargetedMessages": "ALL|NONE (required)"
        },
        "WelcomeIntent": "string (1-100 chars, optional)"
    }
}
```

**Output Schema:**
```json
{
    "AppInstanceBotArn": "string"
}
```

---

### 3.6 `describe-app-instance-bot`

Describes an AppInstance bot.

**Synopsis:**
```bash
aws chime-sdk-identity describe-app-instance-bot \
    --app-instance-bot-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-bot-arn` | **Yes** | string | -- | Bot ARN |

**Output Schema:**
```json
{
    "AppInstanceBot": {
        "AppInstanceBotArn": "string",
        "Name": "string",
        "Configuration": {
            "Lex": {
                "RespondsTo": "STANDARD_MESSAGES",
                "InvokedBy": {
                    "StandardMessages": "AUTO|ALL|MENTIONS|NONE",
                    "TargetedMessages": "ALL|NONE"
                },
                "LexBotAliasArn": "string",
                "LocaleId": "string",
                "WelcomeIntent": "string"
            }
        },
        "CreatedTimestamp": "timestamp",
        "LastUpdatedTimestamp": "timestamp",
        "Metadata": "string"
    }
}
```

---

### 3.7 `list-app-instance-bots`

Lists bots for an AppInstance. **Paginated operation.**

**Synopsis:**
```bash
aws chime-sdk-identity list-app-instance-bots \
    --app-instance-arn <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |
| `--max-results` | No | integer | None | Max results per page (1-50) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "AppInstanceArn": "string",
    "AppInstanceBots": [
        {
            "AppInstanceBotArn": "string",
            "Name": "string",
            "Metadata": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.8 `update-app-instance-bot`

Updates an AppInstance bot.

**Synopsis:**
```bash
aws chime-sdk-identity update-app-instance-bot \
    --app-instance-bot-arn <value> \
    --name <value> \
    --metadata <value> \
    [--configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-bot-arn` | **Yes** | string | -- | Bot ARN |
| `--name` | **Yes** | string | -- | Updated name (max 256 chars) |
| `--metadata` | **Yes** | string | -- | Updated metadata (max 1024 chars) |
| `--configuration` | No | structure | None | Updated Lex configuration |

**Output Schema:**
```json
{
    "AppInstanceBotArn": "string"
}
```

---

### 3.9 `delete-app-instance-bot`

Deletes an AppInstance bot.

**Synopsis:**
```bash
aws chime-sdk-identity delete-app-instance-bot \
    --app-instance-bot-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-bot-arn` | **Yes** | string | -- | Bot ARN |

**Output:** None
