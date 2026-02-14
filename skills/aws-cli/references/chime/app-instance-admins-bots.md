# App Instance Admins & Bots

CLI namespace: `aws chime-sdk-identity`

### 3.1 `create-app-instance-admin`

Promotes an AppInstanceUser to an admin.

**Synopsis:**
```bash
aws chime-sdk-identity create-app-instance-admin \
    --app-instance-admin-arn <value> \
    --app-instance-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-admin-arn` | **Yes** | string | -- | ARN of the user to promote |
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

Describes an app instance admin.

**Synopsis:**
```bash
aws chime-sdk-identity describe-app-instance-admin \
    --app-instance-admin-arn <value> \
    --app-instance-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-admin-arn` | **Yes** | string | -- | Admin ARN |
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |

**Output Schema:**
```json
{
    "AppInstanceAdmin": {
        "Admin": {"Arn": "string", "Name": "string"},
        "AppInstanceArn": "string",
        "CreatedTimestamp": "timestamp"
    }
}
```

---

### 3.3 `list-app-instance-admins`

Lists app instance admins. **Paginated operation.**

**Synopsis:**
```bash
aws chime-sdk-identity list-app-instance-admins \
    --app-instance-arn <value> \
    [--max-results <value>] \
    [--next-token <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |
| `--max-results` | No | integer | None | Max results (1-50) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "AppInstanceArn": "string",
    "AppInstanceAdmins": [
        {
            "Admin": {"Arn": "string", "Name": "string"}
        }
    ],
    "NextToken": "string"
}
```

---

### 3.4 `delete-app-instance-admin`

Removes an app instance admin.

**Synopsis:**
```bash
aws chime-sdk-identity delete-app-instance-admin \
    --app-instance-admin-arn <value> \
    --app-instance-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-admin-arn` | **Yes** | string | -- | Admin ARN |
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |

**Output:** None

---

### 3.5 `create-app-instance-bot`

Creates a bot for an AppInstance. Bots can be used with channel flows to process messages.

**Synopsis:**
```bash
aws chime-sdk-identity create-app-instance-bot \
    --app-instance-arn <value> \
    [--name <value>] \
    [--metadata <value>] \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--configuration <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |
| `--name` | No | string | None | Bot name (0-256 chars) |
| `--metadata` | No | string | None | Metadata (0-1024 chars) |
| `--client-request-token` | No | string | Auto | Idempotency token |
| `--tags` | No | list | None | Tags (1-50) |
| `--configuration` | No | structure | None | Bot configuration with Lex settings |

**Output Schema:**
```json
{
    "AppInstanceBotArn": "string"
}
```

---

### 3.6 `describe-app-instance-bot`

Describes an app instance bot.

**Synopsis:**
```bash
aws chime-sdk-identity describe-app-instance-bot \
    --app-instance-bot-arn <value>
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
        "Metadata": "string",
        "Configuration": {},
        "CreatedTimestamp": "timestamp",
        "LastUpdatedTimestamp": "timestamp"
    }
}
```

---

### 3.7 `list-app-instance-bots`

Lists bots for an app instance. **Paginated operation.**

**Synopsis:**
```bash
aws chime-sdk-identity list-app-instance-bots \
    --app-instance-arn <value> \
    [--max-results <value>] \
    [--next-token <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |
| `--max-results` | No | integer | None | Max results (1-50) |
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

Updates an app instance bot name and metadata.

**Synopsis:**
```bash
aws chime-sdk-identity update-app-instance-bot \
    --app-instance-bot-arn <value> \
    --name <value> \
    --metadata <value> \
    [--configuration <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-bot-arn` | **Yes** | string | -- | Bot ARN |
| `--name` | **Yes** | string | -- | Updated name (0-256 chars) |
| `--metadata` | **Yes** | string | -- | Updated metadata (0-1024 chars) |
| `--configuration` | No | structure | None | Updated bot configuration |

**Output Schema:**
```json
{
    "AppInstanceBotArn": "string"
}
```

---

### 3.9 `delete-app-instance-bot`

Deletes an app instance bot.

**Synopsis:**
```bash
aws chime-sdk-identity delete-app-instance-bot \
    --app-instance-bot-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-bot-arn` | **Yes** | string | -- | Bot ARN |

**Output:** None
