# Sending

### 5.1 `send-email`

Sends an email message. Supports simple (inline content), raw (MIME), and templated messages.

**Synopsis:**
```bash
aws sesv2 send-email \
    [--from-email-address <value>] \
    [--from-email-address-identity-arn <value>] \
    --destination <value> \
    [--reply-to-addresses <value>] \
    [--feedback-forwarding-email-address <value>] \
    [--feedback-forwarding-email-address-identity-arn <value>] \
    --content <value> \
    [--email-tags <value>] \
    [--configuration-set-name <value>] \
    [--list-management-options <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--from-email-address` | No | string | None | Sender email address (must be verified) |
| `--from-email-address-identity-arn` | No | string | None | ARN of the identity for cross-account sending |
| `--destination` | **Yes** | structure | -- | Recipient addresses |
| `--reply-to-addresses` | No | list(string) | None | Reply-to email addresses |
| `--feedback-forwarding-email-address` | No | string | None | Address for bounce/complaint feedback |
| `--feedback-forwarding-email-address-identity-arn` | No | string | None | ARN of feedback forwarding identity |
| `--content` | **Yes** | structure | -- | Email content (Simple, Raw, or Template) |
| `--email-tags` | No | list | None | Message tags. Shorthand: `Name=string,Value=string ...` |
| `--configuration-set-name` | No | string | None | Configuration set to use |
| `--list-management-options` | No | structure | None | Contact list management options |

**Destination Structure:**
```json
{
    "ToAddresses": ["string"],
    "CcAddresses": ["string"],
    "BccAddresses": ["string"]
}
```

**Content Structure (Simple):**
```json
{
    "Simple": {
        "Subject": {
            "Data": "string",
            "Charset": "string"
        },
        "Body": {
            "Text": {
                "Data": "string",
                "Charset": "string"
            },
            "Html": {
                "Data": "string",
                "Charset": "string"
            }
        },
        "Headers": [
            {
                "Name": "string",
                "Value": "string"
            }
        ]
    }
}
```

**Content Structure (Raw):**
```json
{
    "Raw": {
        "Data": "blob"
    }
}
```

**Content Structure (Template):**
```json
{
    "Template": {
        "TemplateName": "string",
        "TemplateArn": "string",
        "TemplateData": "string",
        "Headers": [
            {
                "Name": "string",
                "Value": "string"
            }
        ]
    }
}
```

**List Management Options Structure:**
```json
{
    "ContactListName": "string",
    "TopicName": "string"
}
```

**Output Schema:**
```json
{
    "MessageId": "string"
}
```

---

### 5.2 `send-bulk-email`

Sends bulk templated emails to multiple recipients. Each recipient can receive a personalized version of the template.

**Synopsis:**
```bash
aws sesv2 send-bulk-email \
    [--from-email-address <value>] \
    [--from-email-address-identity-arn <value>] \
    [--reply-to-addresses <value>] \
    [--feedback-forwarding-email-address <value>] \
    [--feedback-forwarding-email-address-identity-arn <value>] \
    --default-content <value> \
    [--default-email-tags <value>] \
    [--configuration-set-name <value>] \
    --bulk-email-entries <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--from-email-address` | No | string | None | Sender email address |
| `--from-email-address-identity-arn` | No | string | None | ARN of the sending identity |
| `--reply-to-addresses` | No | list(string) | None | Reply-to addresses |
| `--feedback-forwarding-email-address` | No | string | None | Feedback forwarding address |
| `--default-content` | **Yes** | structure | -- | Default template content |
| `--default-email-tags` | No | list | None | Default message tags |
| `--configuration-set-name` | No | string | None | Configuration set to use |
| `--bulk-email-entries` | **Yes** | list | -- | List of bulk email entries (max 50) |

**Default Content Structure:**
```json
{
    "Template": {
        "TemplateName": "string",
        "TemplateArn": "string",
        "TemplateData": "string",
        "Headers": []
    }
}
```

**Bulk Email Entry Structure:**
```json
[
    {
        "Destination": {
            "ToAddresses": ["string"],
            "CcAddresses": ["string"],
            "BccAddresses": ["string"]
        },
        "ReplacementTags": [
            {
                "Name": "string",
                "Value": "string"
            }
        ],
        "ReplacementEmailContent": {
            "ReplacementTemplate": {
                "ReplacementTemplateData": "string"
            }
        }
    }
]
```

**Output Schema:**
```json
{
    "BulkEmailEntryResults": [
        {
            "Status": "SUCCESS|MESSAGE_REJECTED|MAIL_FROM_DOMAIN_NOT_VERIFIED|CONFIGURATION_SET_NOT_FOUND|TEMPLATE_NOT_FOUND|ACCOUNT_SUSPENDED|ACCOUNT_THROTTLED|ACCOUNT_DAILY_QUOTA_EXCEEDED|INVALID_SENDING_POOL_NAME|ACCOUNT_SENDING_PAUSED|CONFIGURATION_SET_SENDING_PAUSED|INVALID_PARAMETER|TRANSIENT_FAILURE|FAILED",
            "Error": "string",
            "MessageId": "string"
        }
    ]
}
```

---

### 5.3 `create-email-identity-policy`

Creates a sending authorization policy for an email identity. Policies allow other AWS accounts to send emails using the identity.

**Synopsis:**
```bash
aws sesv2 create-email-identity-policy \
    --email-identity <value> \
    --policy-name <value> \
    --policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--email-identity` | **Yes** | string | -- | Email identity to create the policy for |
| `--policy-name` | **Yes** | string | -- | Name for the authorization policy |
| `--policy` | **Yes** | string | -- | JSON policy document |

**Output Schema:**
```json
{}
```

---

### 5.4 `delete-email-identity-policy`

Deletes a sending authorization policy from an email identity.

**Synopsis:**
```bash
aws sesv2 delete-email-identity-policy \
    --email-identity <value> \
    --policy-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--email-identity` | **Yes** | string | -- | Email identity |
| `--policy-name` | **Yes** | string | -- | Policy name to delete |

**Output Schema:**
```json
{}
```

---

### 5.5 `get-email-identity-policies`

Returns the sending authorization policies for an email identity.

**Synopsis:**
```bash
aws sesv2 get-email-identity-policies \
    --email-identity <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--email-identity` | **Yes** | string | -- | Email identity |

**Output Schema:**
```json
{
    "Policies": {
        "PolicyName": "string"
    }
}
```
