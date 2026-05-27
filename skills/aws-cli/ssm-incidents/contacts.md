# Contacts

### 8.1 `create-contact`

Contacts are either the contacts that Incident Manager engages during an incident or the escalation plans that Incident Manager uses to engage contacts in phases during an incident.

**Synopsis:**
```bash
aws ssm-contacts create-contact \
    --alias <value> \
    --type <value> \
    --plan <value> \
    [--display-name <value>] \
    [--tags <value>] \
    [--idempotency-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alias` | **Yes** | string | -- | Unique alias for the contact (1-255 chars) |
| `--type` | **Yes** | string | -- | Contact type: `PERSONAL`, `ESCALATION`, `ONCALL_SCHEDULE` |
| `--plan` | **Yes** | structure | -- | Engagement plan with stages |
| `--display-name` | No | string | None | Display name |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--idempotency-token` | No | string | None | Idempotency token |

**Plan Structure:**
```json
{
    "Stages": [
        {
            "DurationInMinutes": "integer",
            "Targets": [
                {
                    "ChannelTargetInfo": {
                        "ContactChannelId": "string",
                        "RetryIntervalInMinutes": "integer"
                    },
                    "ContactTargetInfo": {
                        "ContactId": "string",
                        "IsEssential": true|false
                    }
                }
            ]
        }
    ],
    "RotationIds": ["string"]
}
```

**Output Schema:**
```json
{
    "ContactArn": "string"
}
```

---

### 8.2 `delete-contact`

To remove a contact from Incident Manager, you can delete the contact.

**Synopsis:**
```bash
aws ssm-contacts delete-contact \
    --contact-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--contact-id` | **Yes** | string | -- | Contact ARN |

**Output Schema:**
```json
{}
```

---

### 8.3 `get-contact`

Retrieves information about the specified contact or escalation plan.

**Synopsis:**
```bash
aws ssm-contacts get-contact \
    --contact-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--contact-id` | **Yes** | string | -- | Contact ARN |

**Output Schema:**
```json
{
    "ContactArn": "string",
    "Alias": "string",
    "DisplayName": "string",
    "Type": "PERSONAL|ESCALATION|ONCALL_SCHEDULE",
    "Plan": {
        "Stages": [
            {
                "DurationInMinutes": "integer",
                "Targets": [
                    {
                        "ChannelTargetInfo": {
                            "ContactChannelId": "string",
                            "RetryIntervalInMinutes": "integer"
                        },
                        "ContactTargetInfo": {
                            "ContactId": "string",
                            "IsEssential": "boolean"
                        }
                    }
                ]
            }
        ],
        "RotationIds": ["string"]
    }
}
```

---

### 8.4 `list-contacts`

Lists all contacts and escalation plans in Incident Manager. **Paginated operation.**

**Synopsis:**
```bash
aws ssm-contacts list-contacts \
    [--alias-prefix <value>] \
    [--type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alias-prefix` | No | string | None | Filter by alias prefix |
| `--type` | No | string | None | Filter by type: `PERSONAL`, `ESCALATION`, `ONCALL_SCHEDULE` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "Contacts": [
        {
            "ContactArn": "string",
            "Alias": "string",
            "DisplayName": "string",
            "Type": "PERSONAL|ESCALATION|ONCALL_SCHEDULE"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.5 `update-contact`

Updates the contact or escalation plan.

**Synopsis:**
```bash
aws ssm-contacts update-contact \
    --contact-id <value> \
    [--display-name <value>] \
    [--plan <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--contact-id` | **Yes** | string | -- | Contact ARN |
| `--display-name` | No | string | None | Updated display name |
| `--plan` | No | structure | None | Updated engagement plan |

**Output Schema:**
```json
{}
```

---

### 8.6 `get-contact-policy`

Retrieves the resource policy attached to the specified contact or escalation plan.

**Synopsis:**
```bash
aws ssm-contacts get-contact-policy \
    --contact-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--contact-arn` | **Yes** | string | -- | Contact ARN |

**Output Schema:**
```json
{
    "ContactArn": "string",
    "Policy": "string"
}
```

---

### 8.7 `put-contact-policy`

Adds a resource policy to the specified contact or escalation plan. Used for cross-account access.

**Synopsis:**
```bash
aws ssm-contacts put-contact-policy \
    --contact-arn <value> \
    --policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--contact-arn` | **Yes** | string | -- | Contact ARN |
| `--policy` | **Yes** | string | -- | JSON resource policy document |

**Output Schema:**
```json
{}
```
