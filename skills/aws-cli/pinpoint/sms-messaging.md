# SMS v2 Messaging

All commands in this file use the `aws pinpoint-sms-voice-v2` namespace.

### 16.1 `send-text-message`

Sends an SMS text message.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 send-text-message \
    --destination-phone-number <value> \
    [--origination-identity <value>] \
    [--message-body <value>] \
    [--message-type <value>] \
    [--keyword <value>] \
    [--configuration-set-name <value>] \
    [--max-price <value>] \
    [--time-to-live <value>] \
    [--context <value>] \
    [--destination-country-parameters <value>] \
    [--dry-run | --no-dry-run] \
    [--protect-configuration-id <value>] \
    [--message-feedback-enabled | --no-message-feedback-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--destination-phone-number` | **Yes** | string | -- | Destination in E.164 format |
| `--origination-identity` | No | string | None | Origination identity (phone number, sender ID, pool) |
| `--message-body` | No | string | None | Message body (1-1600 chars) |
| `--message-type` | No | string | None | `TRANSACTIONAL` or `PROMOTIONAL` |
| `--keyword` | No | string | None | Keyword for US short codes |
| `--configuration-set-name` | No | string | None | Configuration set name or ARN |
| `--max-price` | No | string | None | Max price per SMS in USD |
| `--time-to-live` | No | integer | 259200 | Validity in seconds (5-259200) |
| `--context` | No | map | None | Custom data for event destinations (max 5 pairs) |
| `--destination-country-parameters` | No | map | None | Country params (e.g., `IN_ENTITY_ID`, `IN_TEMPLATE_ID` for India) |
| `--dry-run` | No | boolean | false | Validate without sending |
| `--protect-configuration-id` | No | string | None | Protect configuration ID |
| `--message-feedback-enabled` | No | boolean | None | Enable message feedback |

**Output Schema:**
```json
{
    "MessageId": "string"
}
```

---

### 16.2 `send-voice-message`

Sends a voice message.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 send-voice-message \
    --destination-phone-number <value> \
    --origination-identity <value> \
    [--message-body <value>] \
    [--message-body-text-type <value>] \
    [--voice-id <value>] \
    [--configuration-set-name <value>] \
    [--max-price-per-minute <value>] \
    [--time-to-live <value>] \
    [--context <value>] \
    [--dry-run | --no-dry-run] \
    [--protect-configuration-id <value>] \
    [--message-feedback-enabled | --no-message-feedback-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--destination-phone-number` | **Yes** | string | -- | Destination in E.164 format |
| `--origination-identity` | **Yes** | string | -- | Origination phone number |
| `--message-body` | No | string | None | Message body (SSML or text) |
| `--message-body-text-type` | No | string | None | `SSML` or `TEXT` |
| `--voice-id` | No | string | None | Amazon Polly voice ID |
| `--configuration-set-name` | No | string | None | Configuration set |
| `--max-price-per-minute` | No | string | None | Max price per minute in USD |
| `--time-to-live` | No | integer | 259200 | Validity in seconds |
| `--context` | No | map | None | Custom context data |
| `--dry-run` | No | boolean | false | Validate without sending |
| `--protect-configuration-id` | No | string | None | Protect configuration |
| `--message-feedback-enabled` | No | boolean | None | Enable message feedback |

**Output Schema:**
```json
{
    "MessageId": "string"
}
```

---

### 16.3 `send-media-message`

Sends an MMS media message.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 send-media-message \
    --destination-phone-number <value> \
    --origination-identity <value> \
    [--message-body <value>] \
    [--media-urls <value>] \
    [--configuration-set-name <value>] \
    [--max-price <value>] \
    [--time-to-live <value>] \
    [--context <value>] \
    [--dry-run | --no-dry-run] \
    [--protect-configuration-id <value>] \
    [--message-feedback-enabled | --no-message-feedback-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--destination-phone-number` | **Yes** | string | -- | Destination in E.164 format |
| `--origination-identity` | **Yes** | string | -- | Origination identity |
| `--message-body` | No | string | None | Message body text |
| `--media-urls` | No | list | None | Media file URLs (S3 URLs) |
| `--configuration-set-name` | No | string | None | Configuration set |
| `--max-price` | No | string | None | Max price per message in USD |
| `--time-to-live` | No | integer | 259200 | Validity in seconds |
| `--context` | No | map | None | Custom context data |
| `--dry-run` | No | boolean | false | Validate without sending |
| `--protect-configuration-id` | No | string | None | Protect configuration |
| `--message-feedback-enabled` | No | boolean | None | Enable message feedback |

**Output Schema:**
```json
{
    "MessageId": "string"
}
```

---

### 16.4 `put-message-feedback`

Provides feedback on a sent message for delivery optimization.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 put-message-feedback \
    --message-id <value> \
    --message-feedback-status <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--message-id` | **Yes** | string | -- | The message ID |
| `--message-feedback-status` | **Yes** | string | -- | `RECEIVED`, `FAILED` |

**Output Schema:**
```json
{
    "MessageId": "string",
    "MessageFeedbackStatus": "RECEIVED|FAILED"
}
```
