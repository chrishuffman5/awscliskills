# Voice Connectors

Commands from the `aws chime-sdk-voice` service.

### 12.1 `create-voice-connector`

Creates a voice connector.

**Synopsis:**
```bash
aws chime-sdk-voice create-voice-connector \
    --name <value> \
    --require-encryption | --no-require-encryption \
    [--aws-region <value>] \
    [--tags <value>] \
    [--integration-type <value>] \
    [--network-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Connector name (1-256 chars) |
| `--require-encryption` | **Yes** | boolean | -- | Enable/disable encryption |
| `--aws-region` | No | string | us-east-1 | AWS Region for connector |
| `--tags` | No | list | None | Tags (max 50) |
| `--integration-type` | No | string | None | `CONNECT_CALL_TRANSFER_CONNECTOR` or `CONNECT_ANALYTICS_CONNECTOR` |
| `--network-type` | No | string | None | `IPV4_ONLY` or `DUAL_STACK` |

**Output Schema:**
```json
{
    "VoiceConnector": {
        "VoiceConnectorId": "string",
        "AwsRegion": "string",
        "Name": "string",
        "OutboundHostName": "string",
        "RequireEncryption": "boolean",
        "CreatedTimestamp": "timestamp",
        "UpdatedTimestamp": "timestamp",
        "VoiceConnectorArn": "string",
        "IntegrationType": "string",
        "NetworkType": "string"
    }
}
```

---

### 12.2 `get-voice-connector`

Gets voice connector details.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |

**Output Schema:** Same as `create-voice-connector` VoiceConnector object.

---

### 12.3 `list-voice-connectors`

Lists voice connectors. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-99) |

---

### 12.4 `update-voice-connector`

Updates a voice connector.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |
| `--name` | **Yes** | string | -- | Updated name |
| `--require-encryption` | **Yes** | boolean | -- | Updated encryption setting |

---

### 12.5 `delete-voice-connector`

Deletes a voice connector.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |

**Output:** None

---

### 12.6 `create-voice-connector-group`

Creates a voice connector group.

**Synopsis:**
```bash
aws chime-sdk-voice create-voice-connector-group \
    --name <value> \
    [--voice-connector-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Group name (1-256 chars) |
| `--voice-connector-items` | No | list | None | Voice connectors in the group |

**VoiceConnectorItems:**
```json
[
    {
        "VoiceConnectorId": "string (required)",
        "Priority": "integer (1-99, required)"
    }
]
```

**Output Schema:**
```json
{
    "VoiceConnectorGroup": {
        "VoiceConnectorGroupId": "string",
        "VoiceConnectorGroupArn": "string",
        "Name": "string",
        "VoiceConnectorItems": [
            { "VoiceConnectorId": "string", "Priority": "integer" }
        ],
        "CreatedTimestamp": "timestamp",
        "UpdatedTimestamp": "timestamp"
    }
}
```

---

### 12.7 `get-voice-connector-group`

Gets voice connector group details.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-group-id` | **Yes** | string | -- | Group ID |

---

### 12.8 `list-voice-connector-groups`

Lists voice connector groups. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-99) |

---

### 12.9 `update-voice-connector-group`

Updates a voice connector group.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-group-id` | **Yes** | string | -- | Group ID |
| `--name` | **Yes** | string | -- | Updated name |
| `--voice-connector-items` | **Yes** | list | -- | Updated connector items |

---

### 12.10 `delete-voice-connector-group`

Deletes a voice connector group.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-group-id` | **Yes** | string | -- | Group ID |

**Output:** None

---

### 12.11 `get-voice-connector-origination`

Gets origination settings for a voice connector.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |

**Output Schema:**
```json
{
    "Origination": {
        "Routes": [
            {
                "Host": "string",
                "Port": "integer",
                "Protocol": "TCP|UDP",
                "Priority": "integer",
                "Weight": "integer"
            }
        ],
        "Disabled": "boolean"
    }
}
```

---

### 12.12 `put-voice-connector-origination`

Sets origination settings.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |
| `--origination` | **Yes** | structure | -- | Origination settings |

---

### 12.13 `delete-voice-connector-origination`

Deletes origination settings.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |

**Output:** None

---

### 12.14 `get-voice-connector-termination`

Gets termination settings.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |

**Output Schema:**
```json
{
    "Termination": {
        "CpsLimit": "integer",
        "DefaultPhoneNumber": "string",
        "CallingRegions": ["string"],
        "CidrAllowedList": ["string"],
        "Disabled": "boolean"
    }
}
```

---

### 12.15 `put-voice-connector-termination`

Sets termination settings.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |
| `--termination` | **Yes** | structure | -- | Termination settings |

---

### 12.16 `delete-voice-connector-termination`

Deletes termination settings.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |

**Output:** None

---

### 12.17 `list-voice-connector-termination-credentials`

Lists termination SIP credentials.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |

**Output Schema:**
```json
{
    "Usernames": ["string"]
}
```

---

### 12.18 `put-voice-connector-termination-credentials`

Sets termination SIP credentials.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |
| `--credentials` | No | list | None | Credentials with `Username` and `Password` |

---

### 12.19 `delete-voice-connector-termination-credentials`

Deletes termination SIP credentials.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |
| `--usernames` | **Yes** | list | -- | Usernames to delete |

**Output:** None

---

### 12.20 `get-voice-connector-proxy`

Gets proxy configuration.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |

**Output Schema:**
```json
{
    "Proxy": {
        "DefaultSessionExpiryMinutes": "integer",
        "Disabled": "boolean",
        "FallBackPhoneNumber": "string",
        "PhoneNumberCountries": ["string"]
    }
}
```

---

### 12.21 `put-voice-connector-proxy`

Sets proxy configuration.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |
| `--default-session-expiry-minutes` | **Yes** | integer | -- | Default session expiry |
| `--phone-number-pool-countries` | **Yes** | list | -- | Country codes for phone pool |
| `--fall-back-phone-number` | No | string | None | Fallback phone number |
| `--disabled` | No | boolean | None | Disable proxy |

---

### 12.22 `delete-voice-connector-proxy`

Deletes proxy configuration.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |

**Output:** None

---

### 12.23 `get-voice-connector-streaming-configuration`

Gets streaming configuration.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |

**Output Schema:**
```json
{
    "StreamingConfiguration": {
        "DataRetentionInHours": "integer",
        "Disabled": "boolean",
        "StreamingNotificationTargets": [
            { "NotificationTarget": "EventBridge|SNS|SQS" }
        ],
        "MediaInsightsConfiguration": {
            "Disabled": "boolean",
            "ConfigurationArn": "string"
        }
    }
}
```

---

### 12.24 `put-voice-connector-streaming-configuration`

Sets streaming configuration.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |
| `--streaming-configuration` | **Yes** | structure | -- | Streaming config |

---

### 12.25 `delete-voice-connector-streaming-configuration`

Deletes streaming configuration.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |

**Output:** None

---

### 12.26 `get-voice-connector-logging-configuration`

Gets logging configuration.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |

**Output Schema:**
```json
{
    "LoggingConfiguration": {
        "EnableSIPLogs": "boolean",
        "EnableMediaMetricLogs": "boolean"
    }
}
```

---

### 12.27 `put-voice-connector-logging-configuration`

Sets logging configuration.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |
| `--logging-configuration` | **Yes** | structure | -- | Logging config |

---

### 12.28 `get-voice-connector-emergency-calling-configuration`

Gets E911 configuration.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |

**Output Schema:**
```json
{
    "EmergencyCallingConfiguration": {
        "DNIS": [
            {
                "EmergencyPhoneNumber": "string",
                "TestPhoneNumber": "string",
                "CallingCountry": "string"
            }
        ]
    }
}
```

---

### 12.29 `put-voice-connector-emergency-calling-configuration`

Sets E911 configuration.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |
| `--emergency-calling-configuration` | **Yes** | structure | -- | E911 config |

---

### 12.30 `delete-voice-connector-emergency-calling-configuration`

Deletes E911 configuration.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |

**Output:** None

---

### 12.31 `get-voice-connector-external-systems-configuration`

Gets external systems configuration.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |

---

### 12.32 `put-voice-connector-external-systems-configuration`

Sets external systems configuration.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |
| `--session-border-controller-types` | No | list | None | SBC types |
| `--contact-center-system-types` | No | list | None | Contact center types |

---

### 12.33 `delete-voice-connector-external-systems-configuration`

Deletes external systems configuration.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |

**Output:** None

---

### 12.34 `get-voice-connector-termination-health`

Gets termination health for a voice connector.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |

**Output Schema:**
```json
{
    "TerminationHealth": {
        "Timestamp": "timestamp",
        "Source": "string"
    }
}
```
