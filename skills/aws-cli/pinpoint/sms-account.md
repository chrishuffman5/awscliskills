# SMS v2 Account, Tags & Verified Numbers

All commands in this section use `aws pinpoint-sms-voice-v2`.

## Account

### 20.1 `describe-account-attributes`

Describes account attributes including account tier (sandbox vs. production).

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 describe-account-attributes \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Pagination only (no required parameters).

**Output Schema:**
```json
{
    "AccountAttributes": [
        {
            "Name": "ACCOUNT_TIER|DEFAULT_PROTECT_CONFIGURATION_ID",
            "Value": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 20.2 `describe-account-limits`

Describes account resource limits (phone numbers, pools, configuration sets, etc.).

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 describe-account-limits \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Pagination only (no required parameters).

**Output Schema:**
```json
{
    "AccountLimits": [
        {
            "Name": "PHONE_NUMBERS|POOLS|CONFIGURATION_SETS|OPT_OUT_LISTS|SENDER_IDS|REGISTRATIONS|REGISTRATION_ATTACHMENTS|VERIFIED_DESTINATION_NUMBERS",
            "Used": "long",
            "Max": "long"
        }
    ],
    "NextToken": "string"
}
```

---

### 20.3 `describe-spend-limits`

Describes monthly spend limits for text, voice, and media messages.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 describe-spend-limits \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Pagination only (no required parameters).

**Output Schema:**
```json
{
    "SpendLimits": [
        {
            "Name": "TEXT_MESSAGE_MONTHLY_SPEND_LIMIT|VOICE_MESSAGE_MONTHLY_SPEND_LIMIT|MEDIA_MESSAGE_MONTHLY_SPEND_LIMIT",
            "EnforcedLimit": "long",
            "MaxLimit": "long",
            "Overridden": "boolean"
        }
    ],
    "NextToken": "string"
}
```

---

### 20.4 `set-text-message-spend-limit-override`

Sets a monthly spending limit override for text messages.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 set-text-message-spend-limit-override \
    --monthly-limit <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monthly-limit` | **Yes** | long | -- | Monthly limit in USD (0-1000000000) |

**Output Schema:**
```json
{
    "MonthlyLimit": "long"
}
```

---

### 20.5 `delete-text-message-spend-limit-override`

Removes the text message spending limit override, resetting to AWS default.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 delete-text-message-spend-limit-override \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No required parameters.

**Output Schema:**
```json
{
    "MonthlyLimit": "long"
}
```

---

### 20.6 `set-voice-message-spend-limit-override`

Sets a monthly spending limit override for voice messages.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 set-voice-message-spend-limit-override \
    --monthly-limit <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monthly-limit` | **Yes** | long | -- | Monthly limit in USD (0-1000000000) |

**Output Schema:**
```json
{
    "MonthlyLimit": "long"
}
```

---

### 20.7 `delete-voice-message-spend-limit-override`

Removes the voice message spending limit override.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 delete-voice-message-spend-limit-override \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No required parameters.

**Output Schema:**
```json
{
    "MonthlyLimit": "long"
}
```

---

### 20.8 `set-media-message-spend-limit-override`

Sets a monthly spending limit override for MMS messages.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 set-media-message-spend-limit-override \
    --monthly-limit <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monthly-limit` | **Yes** | long | -- | Monthly limit in USD (0-1000000000) |

**Output Schema:**
```json
{
    "MonthlyLimit": "long"
}
```

---

### 20.9 `delete-media-message-spend-limit-override`

Removes the MMS message spending limit override.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 delete-media-message-spend-limit-override \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No required parameters.

**Output Schema:**
```json
{
    "MonthlyLimit": "long"
}
```

---

## Configuration Set Defaults

### 20.10 `set-default-message-type`

Sets the default message type for a configuration set.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 set-default-message-type \
    --configuration-set-name <value> \
    --message-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-set-name` | **Yes** | string | -- | Configuration set name or ARN |
| `--message-type` | **Yes** | string | -- | `TRANSACTIONAL` or `PROMOTIONAL` |

**Output Schema:**
```json
{
    "ConfigurationSetArn": "string",
    "ConfigurationSetName": "string",
    "MessageType": "TRANSACTIONAL|PROMOTIONAL"
}
```

---

### 20.11 `set-default-sender-id`

Sets the default sender ID for a configuration set.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 set-default-sender-id \
    --configuration-set-name <value> \
    --sender-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-set-name` | **Yes** | string | -- | Configuration set name or ARN |
| `--sender-id` | **Yes** | string | -- | Sender ID (1-11 alphanumeric chars) |

**Output Schema:**
```json
{
    "ConfigurationSetArn": "string",
    "ConfigurationSetName": "string",
    "SenderId": "string"
}
```

---

## Tags

### 20.12 `tag-resource`

Adds tags to a resource.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tags` | **Yes** | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |

**Output:** None

---

### 20.13 `untag-resource`

Removes tags from a resource.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tag-keys` | **Yes** | list | -- | Tag keys to remove |

**Output:** None

---

### 20.14 `list-tags-for-resource`

Lists tags for a resource.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |

**Output Schema:**
```json
{
    "ResourceArn": "string",
    "Tags": [{"Key": "string", "Value": "string"}]
}
```

---

## Verified Destination Numbers

### 20.15 `create-verified-destination-number`

Creates a verified destination phone number (for sandbox testing).

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 create-verified-destination-number \
    --destination-phone-number <value> \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--destination-phone-number` | **Yes** | string | -- | Phone number in E.164 format |
| `--tags` | No | list | None | Tags |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "VerifiedDestinationNumberArn": "string",
    "VerifiedDestinationNumberId": "string",
    "DestinationPhoneNumber": "string",
    "Status": "PENDING|VERIFIED",
    "Tags": [{"Key": "string", "Value": "string"}],
    "CreatedTimestamp": "timestamp"
}
```

---

### 20.16 `describe-verified-destination-numbers`

Describes verified destination numbers.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 describe-verified-destination-numbers \
    [--verified-destination-number-ids <value>] \
    [--destination-phone-numbers <value>] \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--verified-destination-number-ids` | No | list | None | IDs to describe (max 5) |
| `--destination-phone-numbers` | No | list | None | Phone numbers in E.164 (max 5) |
| `--filters` | No | list | None | Filter: `status` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "VerifiedDestinationNumbers": [
        {
            "VerifiedDestinationNumberArn": "string",
            "VerifiedDestinationNumberId": "string",
            "DestinationPhoneNumber": "string",
            "Status": "PENDING|VERIFIED",
            "CreatedTimestamp": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 20.17 `verify-destination-number`

Verifies a destination phone number using a verification code.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 verify-destination-number \
    --verified-destination-number-id <value> \
    --verification-code <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--verified-destination-number-id` | **Yes** | string | -- | Verified destination number ID |
| `--verification-code` | **Yes** | string | -- | Verification code received |

**Output Schema:**
```json
{
    "VerifiedDestinationNumberArn": "string",
    "VerifiedDestinationNumberId": "string",
    "DestinationPhoneNumber": "string",
    "Status": "PENDING|VERIFIED",
    "CreatedTimestamp": "timestamp"
}
```

---

### 20.18 `delete-verified-destination-number`

Deletes a verified destination number.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 delete-verified-destination-number \
    --verified-destination-number-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--verified-destination-number-id` | **Yes** | string | -- | Verified destination number ID |

**Output Schema:** Same as `verify-destination-number`.
