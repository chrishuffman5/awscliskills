# SMS v2 Sender IDs

All commands in this section use `aws pinpoint-sms-voice-v2`.

### 15.1 `request-sender-id`

Requests a sender ID for sending SMS messages to a specific country.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 request-sender-id \
    --sender-id <value> \
    --iso-country-code <value> \
    [--message-types <value>] \
    [--deletion-protection-enabled | --no-deletion-protection-enabled] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sender-id` | **Yes** | string | -- | Sender ID string (1-11 alphanumeric characters) |
| `--iso-country-code` | **Yes** | string | -- | Two-character ISO 3166-1 alpha-2 country code |
| `--message-types` | No | list | None | `TRANSACTIONAL`, `PROMOTIONAL` (max 2) |
| `--deletion-protection-enabled` | No | boolean | false | Prevent deletion |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "SenderIdArn": "string",
    "SenderId": "string",
    "IsoCountryCode": "string",
    "MessageTypes": ["TRANSACTIONAL|PROMOTIONAL"],
    "MonthlyLeasingPrice": "string",
    "DeletionProtectionEnabled": "boolean",
    "Registered": "boolean",
    "Tags": [{"Key": "string", "Value": "string"}]
}
```

---

### 15.2 `describe-sender-ids`

Describes sender IDs in your account.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 describe-sender-ids \
    [--sender-ids <value>] \
    [--filters <value>] \
    [--owner <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sender-ids` | No | list | None | Array of `SenderId=string,IsoCountryCode=string` (max 5) |
| `--filters` | No | list | None | Filters: `sender-id`, `iso-country-code`, `message-type`, `deletion-protection-enabled`, `registered` |
| `--owner` | No | string | None | `SELF` or `SHARED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "SenderIds": [
        {
            "SenderIdArn": "string",
            "SenderId": "string",
            "IsoCountryCode": "string",
            "MessageTypes": ["TRANSACTIONAL|PROMOTIONAL"],
            "MonthlyLeasingPrice": "string",
            "DeletionProtectionEnabled": "boolean",
            "Registered": "boolean",
            "RegistrationId": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 15.3 `update-sender-id`

Updates sender ID settings (currently only deletion protection).

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 update-sender-id \
    --sender-id <value> \
    --iso-country-code <value> \
    [--deletion-protection-enabled | --no-deletion-protection-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sender-id` | **Yes** | string | -- | Sender ID to update |
| `--iso-country-code` | **Yes** | string | -- | Two-character ISO 3166-1 alpha-2 country code |
| `--deletion-protection-enabled` | No | boolean | -- | Enable/disable deletion protection |

**Output Schema:**
```json
{
    "SenderIdArn": "string",
    "SenderId": "string",
    "IsoCountryCode": "string",
    "MessageTypes": ["TRANSACTIONAL|PROMOTIONAL"],
    "MonthlyLeasingPrice": "string",
    "DeletionProtectionEnabled": "boolean",
    "Registered": "boolean",
    "RegistrationId": "string"
}
```

---

### 15.4 `release-sender-id`

Releases a sender ID from your account.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 release-sender-id \
    --sender-id <value> \
    --iso-country-code <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sender-id` | **Yes** | string | -- | Sender ID to release |
| `--iso-country-code` | **Yes** | string | -- | Two-character ISO 3166-1 alpha-2 country code |

**Output Schema:**
```json
{
    "SenderIdArn": "string",
    "SenderId": "string",
    "IsoCountryCode": "string",
    "MessageTypes": ["TRANSACTIONAL|PROMOTIONAL"],
    "MonthlyLeasingPrice": "string",
    "DeletionProtectionEnabled": "boolean",
    "Registered": "boolean",
    "RegistrationId": "string"
}
```
