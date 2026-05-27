# SIP Media Applications & Rules

CLI namespace: `aws chime-sdk-voice`

### 14.1 `create-sip-media-application`

Creates a SIP media application that uses a Lambda function to handle SIP call flows.

**Synopsis:**
```bash
aws chime-sdk-voice create-sip-media-application \
    --aws-region <value> \
    --name <value> \
    --endpoints <value> \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-region` | **Yes** | string | -- | AWS region for the application |
| `--name` | **Yes** | string | -- | Application name (1-256 chars) |
| `--endpoints` | **Yes** | list | -- | Lambda endpoints (exactly 1) |
| `--tags` | No | list | None | Tags (1-50) |

**Endpoints structure:**
```json
[
    {
        "LambdaArn": "arn:aws:lambda:us-east-1:123456789012:function:my-sip-handler"
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
        "Endpoints": [{"LambdaArn": "string"}],
        "CreatedTimestamp": "timestamp",
        "UpdatedTimestamp": "timestamp",
        "SipMediaApplicationArn": "string"
    }
}
```

---

### 14.2 `get-sip-media-application` / `list-sip-media-applications` / `update-sip-media-application` / `delete-sip-media-application`

**Synopsis:**
```bash
aws chime-sdk-voice get-sip-media-application \
    --sip-media-application-id <value>

aws chime-sdk-voice list-sip-media-applications \
    [--max-results <value>] [--next-token <value>]

aws chime-sdk-voice update-sip-media-application \
    --sip-media-application-id <value> \
    [--name <value>] [--endpoints <value>]

aws chime-sdk-voice delete-sip-media-application \
    --sip-media-application-id <value>
```

---

### 14.3 `get-sip-media-application-logging-configuration` / `put-sip-media-application-logging-configuration`

```bash
aws chime-sdk-voice get-sip-media-application-logging-configuration \
    --sip-media-application-id <value>

aws chime-sdk-voice put-sip-media-application-logging-configuration \
    --sip-media-application-id <value> \
    --sip-media-application-logging-configuration '{\"EnableSipMediaApplicationMessageLogs\":true}'
```

**Output Schema:**
```json
{
    "SipMediaApplicationLoggingConfiguration": {
        "EnableSipMediaApplicationMessageLogs": "boolean"
    }
}
```

---

### 14.4 `get-sip-media-application-alexa-skill-configuration` / `put-sip-media-application-alexa-skill-configuration`

```bash
aws chime-sdk-voice get-sip-media-application-alexa-skill-configuration \
    --sip-media-application-id <value>

aws chime-sdk-voice put-sip-media-application-alexa-skill-configuration \
    --sip-media-application-id <value> \
    --sip-media-application-alexa-skill-configuration <value>
```

**AlexaSkillConfiguration structure:**
```json
{
    "AlexaSkillStatus": "ACTIVE|INACTIVE",
    "AlexaSkillIds": ["amzn1.ask.skill.xxxxx"]
}
```

---

### 14.5 `create-sip-rule`

Creates a SIP rule that routes calls to SIP media applications based on trigger conditions.

**Synopsis:**
```bash
aws chime-sdk-voice create-sip-rule \
    --name <value> \
    --trigger-type <value> \
    --trigger-value <value> \
    [--disabled | --no-disabled] \
    [--target-applications <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Rule name (1-256 chars) |
| `--trigger-type` | **Yes** | string | -- | `ToPhoneNumber` or `RequestUriHostname` |
| `--trigger-value` | **Yes** | string | -- | Phone number (E.164) or Voice Connector hostname |
| `--disabled` | No | boolean | false | Disable the rule |
| `--target-applications` | No | list | None | Target SIP media applications (1-25) |

**TargetApplications structure:**
```json
[
    {
        "SipMediaApplicationId": "string",
        "Priority": 1,
        "AwsRegion": "us-east-1"
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

### 14.6 `get-sip-rule` / `list-sip-rules` / `update-sip-rule` / `delete-sip-rule`

**Synopsis:**
```bash
aws chime-sdk-voice get-sip-rule --sip-rule-id <value>

aws chime-sdk-voice list-sip-rules \
    [--sip-media-application-id <value>] \
    [--max-results <value>] [--next-token <value>]

aws chime-sdk-voice update-sip-rule \
    --sip-rule-id <value> --name <value> \
    [--disabled | --no-disabled] [--target-applications <value>]

aws chime-sdk-voice delete-sip-rule --sip-rule-id <value>
```

> **Note:** SIP rules must be disabled before they can be deleted.
