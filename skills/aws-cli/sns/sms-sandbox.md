# SMS Sandbox

### 8.1 `get-sms-sandbox-account-status`

Checks whether the calling AWS account is in the SMS sandbox for the target region.

**Synopsis:**
```bash
aws sns get-sms-sandbox-account-status \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "IsInSandbox": true|false
}
```

---

### 8.2 `create-sms-sandbox-phone-number`

Adds a destination phone number to the SMS sandbox and sends a one-time password (OTP) for verification.

**Synopsis:**
```bash
aws sns create-sms-sandbox-phone-number \
    --phone-number <value> \
    [--language-code <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--phone-number` | **Yes** | string | -- | Phone number. Max 20 chars. Pattern: `^(\+[0-9]{8,}\|[0-9]{0,9})$` |
| `--language-code` | No | string | `en-US` | Language for OTP message. Values: `en-US`, `en-GB`, `es-419`, `es-ES`, `de-DE`, `fr-CA`, `fr-FR`, `it-IT`, `ja-JP`, `pt-BR`, `kr-KR`, `zh-CN`, `zh-TW` |

**Output Schema:** None

---

### 8.3 `verify-sms-sandbox-phone-number`

Verifies a phone number using the OTP sent by `create-sms-sandbox-phone-number`.

**Synopsis:**
```bash
aws sns verify-sms-sandbox-phone-number \
    --phone-number <value> \
    --one-time-password <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--phone-number` | **Yes** | string | -- | Phone number. Max 20 chars |
| `--one-time-password` | **Yes** | string | -- | OTP code (5-8 digits). Pattern: `^[0-9]+$` |

**Output Schema:** None

---

### 8.4 `delete-sms-sandbox-phone-number`

Removes a verified or pending phone number from the SMS sandbox.

**Synopsis:**
```bash
aws sns delete-sms-sandbox-phone-number \
    --phone-number <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--phone-number` | **Yes** | string | -- | Phone number. Max 20 chars. Pattern: `^(\+[0-9]{8,}\|[0-9]{0,9})$` |

**Output Schema:** None

---

### 8.5 `list-sms-sandbox-phone-numbers`

Lists verified and pending destination phone numbers in the SMS sandbox. **Paginated operation.**

**Synopsis:**
```bash
aws sns list-sms-sandbox-phone-numbers \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--no-paginate] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Maximum total items to return |

**Output Schema:**
```json
{
    "PhoneNumbers": [
        {
            "PhoneNumber": "string",
            "Status": "Pending|Verified"
        }
    ],
    "NextToken": "string"
}
```
