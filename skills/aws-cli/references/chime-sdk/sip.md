# SIP

Commands from the `aws chime-sdk-voice` service.

### 14.1 `create-sip-media-application`

Creates a SIP media application backed by a Lambda function.

**Synopsis:**
```bash
aws chime-sdk-voice create-sip-media-application \
    --aws-region <value> \
    --name <value> \
    --endpoints <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-region` | **Yes** | string | -- | AWS Region for the SIP media app |
| `--name` | **Yes** | string | -- | App name (1-256 chars) |
| `--endpoints` | **Yes** | list | -- | Lambda endpoint (exactly 1) |
| `--tags` | No | list | None | Tags (max 50) |

**Endpoints:**
```json
[
    {
        "LambdaArn": "string (required)"
    }
]
```

**Output Schema:**
```json
{
    "SipMediaApplication": {
        "SipMediaApplicationId": "string",
        "AwsRegion": "string",
        "Name": "string",
        "Endpoints": [
            { "LambdaArn": "string" }
        ],
        "CreatedTimestamp": "timestamp",
        "UpdatedTimestamp": "timestamp",
        "SipMediaApplicationArn": "string"
    }
}
```

---

### 14.2 `get-sip-media-application`

Gets SIP media application details.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sip-media-application-id` | **Yes** | string | -- | SIP media application ID |

**Output Schema:** Same as `create-sip-media-application` SipMediaApplication object.

---

### 14.3 `list-sip-media-applications`

Lists SIP media applications. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Max results (1-99) |
| `--next-token` | No | string | None | Pagination token |

---

### 14.4 `update-sip-media-application`

Updates a SIP media application.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sip-media-application-id` | **Yes** | string | -- | SIP media application ID |
| `--name` | No | string | None | Updated name |
| `--endpoints` | No | list | None | Updated endpoints |

---

### 14.5 `delete-sip-media-application`

Deletes a SIP media application.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sip-media-application-id` | **Yes** | string | -- | SIP media application ID |

**Output:** None

---

### 14.6 `get-sip-media-application-logging-configuration`

Gets logging configuration for a SIP media application.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sip-media-application-id` | **Yes** | string | -- | SIP media application ID |

**Output Schema:**
```json
{
    "SipMediaApplicationLoggingConfiguration": {
        "EnableSipMediaApplicationMessageLogs": "boolean"
    }
}
```

---

### 14.7 `put-sip-media-application-logging-configuration`

Sets logging configuration for a SIP media application.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sip-media-application-id` | **Yes** | string | -- | SIP media application ID |
| `--sip-media-application-logging-configuration` | No | structure | None | Logging config |

---

### 14.8 `create-sip-media-application-call`

Creates an outbound call from a SIP media application.

**Synopsis:**
```bash
aws chime-sdk-voice create-sip-media-application-call \
    --from-phone-number <value> \
    --to-phone-number <value> \
    --sip-media-application-id <value> \
    [--sip-headers <value>] \
    [--arguments-map <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--from-phone-number` | **Yes** | string | -- | Calling phone number (E.164) |
| `--to-phone-number` | **Yes** | string | -- | Called phone number (E.164) |
| `--sip-media-application-id` | **Yes** | string | -- | SIP media application ID |
| `--sip-headers` | No | map | None | SIP headers (max 20) |
| `--arguments-map` | No | map | None | Arguments passed to Lambda (max 20) |

**Output Schema:**
```json
{
    "SipMediaApplicationCall": {
        "TransactionId": "string"
    }
}
```

---

### 14.9 `update-sip-media-application-call`

Updates an in-progress SIP media application call.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sip-media-application-id` | **Yes** | string | -- | SIP media application ID |
| `--transaction-id` | **Yes** | string | -- | Transaction ID |
| `--arguments` | **Yes** | map | -- | Arguments passed to Lambda |

---

### 14.10 `create-sip-rule`

Creates a SIP rule for routing calls.

**Synopsis:**
```bash
aws chime-sdk-voice create-sip-rule \
    --name <value> \
    --trigger-type <value> \
    --trigger-value <value> \
    [--disabled | --no-disabled] \
    [--target-applications <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Rule name (1-256 chars) |
| `--trigger-type` | **Yes** | string | -- | `ToPhoneNumber` or `RequestUriHostname` |
| `--trigger-value` | **Yes** | string | -- | Trigger value (phone number or hostname) |
| `--disabled` | No | boolean | None | Disable the rule |
| `--target-applications` | No | list | None | Target SIP media applications |

**TargetApplications:**
```json
[
    {
        "SipMediaApplicationId": "string (required)",
        "Priority": "integer (1-25, required)",
        "AwsRegion": "string (required)"
    }
]
```

**Output Schema:**
```json
{
    "SipRule": {
        "SipRuleId": "string",
        "Name": "string",
        "Disabled": "boolean",
        "TriggerType": "ToPhoneNumber|RequestUriHostname",
        "TriggerValue": "string",
        "TargetApplications": [
            {
                "SipMediaApplicationId": "string",
                "Priority": "integer",
                "AwsRegion": "string"
            }
        ],
        "CreatedTimestamp": "timestamp",
        "UpdatedTimestamp": "timestamp"
    }
}
```

---

### 14.11 `get-sip-rule`

Gets SIP rule details.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sip-rule-id` | **Yes** | string | -- | SIP rule ID |

---

### 14.12 `list-sip-rules`

Lists SIP rules. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sip-media-application-id` | No | string | None | Filter by SIP media app |
| `--max-results` | No | integer | None | Max results (1-99) |
| `--next-token` | No | string | None | Pagination token |

---

### 14.13 `update-sip-rule`

Updates a SIP rule.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sip-rule-id` | **Yes** | string | -- | SIP rule ID |
| `--name` | **Yes** | string | -- | Updated name |
| `--disabled` | No | boolean | None | Enable/disable |
| `--target-applications` | No | list | None | Updated targets |

---

### 14.14 `delete-sip-rule`

Deletes a SIP rule.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sip-rule-id` | **Yes** | string | -- | SIP rule ID |

**Output:** None
