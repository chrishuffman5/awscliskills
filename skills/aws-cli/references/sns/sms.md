# SMS

### 7.1 `get-sms-attributes`

Returns the default settings for sending SMS messages from your account.

**Synopsis:**
```bash
aws sns get-sms-attributes \
    [--attributes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attributes` | No | list(string) | all | Specific attribute names to retrieve. If omitted, returns all |

**Output Schema:**
```json
{
    "attributes": {
        "MonthlySpendLimit": "string",
        "DeliveryStatusIAMRole": "string",
        "DeliveryStatusSuccessSamplingRate": "string",
        "DefaultSenderID": "string",
        "DefaultSMSType": "Promotional|Transactional",
        "UsageReportS3Bucket": "string"
    }
}
```

---

### 7.2 `set-sms-attributes`

Sets default settings for sending SMS messages and receiving daily usage reports.

**Synopsis:**
```bash
aws sns set-sms-attributes \
    --attributes <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attributes` | **Yes** | map | -- | SMS attribute key-value pairs (see supported list below) |

**Supported Attributes:**

| Attribute | Description |
|-----------|-------------|
| `MonthlySpendLimit` | Max monthly USD spend for SMS. SNS stops sending within minutes of exceeding |
| `DeliveryStatusIAMRole` | IAM role ARN for CloudWatch Logs delivery logging |
| `DeliveryStatusSuccessSamplingRate` | 0-100 percentage of successful deliveries to log |
| `DefaultSenderID` | Sender name (1-11 alphanumeric chars, at least one letter) |
| `DefaultSMSType` | `Promotional` (default, lowest cost) or `Transactional` (highest reliability) |
| `UsageReportS3Bucket` | S3 bucket for daily SMS usage reports (CSV) |

**Output Schema:** None

---

### 7.3 `check-if-phone-number-is-opted-out`

Checks whether a phone number has opted out of receiving SMS messages.

**Synopsis:**
```bash
aws sns check-if-phone-number-is-opted-out \
    --phone-number <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--phone-number` | **Yes** | string | -- | Phone number in E.164 format |

**Output Schema:**
```json
{
    "isOptedOut": true|false
}
```

---

### 7.4 `list-phone-numbers-opted-out`

Returns a list of phone numbers that have opted out of SMS. **Paginated operation** (max 100 per page).

**Synopsis:**
```bash
aws sns list-phone-numbers-opted-out \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--no-paginate] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--max-items` | No | integer | None | Maximum total items to return |

**Output Schema:**
```json
{
    "phoneNumbers": [
        "string"
    ],
    "nextToken": "string"
}
```

---

### 7.5 `opt-in-phone-number`

Opts in a phone number that was previously opted out. A phone number can only be opted in once every 30 days.

**Synopsis:**
```bash
aws sns opt-in-phone-number \
    --phone-number <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--phone-number` | **Yes** | string | -- | Phone number in E.164 format |

**Output Schema:** None
