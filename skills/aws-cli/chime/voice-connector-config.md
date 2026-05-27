# Voice Connector Configuration

CLI namespace: `aws chime-sdk-voice`

Each configuration type follows a get/put/delete pattern scoped to a voice connector ID.

### 12.1 Origination — `put-voice-connector-origination` / `get-voice-connector-origination` / `delete-voice-connector-origination`

Configures inbound calling routes.

**Synopsis:**
```bash
aws chime-sdk-voice put-voice-connector-origination \
    --voice-connector-id <value> \
    --origination <value>

aws chime-sdk-voice get-voice-connector-origination \
    --voice-connector-id <value>

aws chime-sdk-voice delete-voice-connector-origination \
    --voice-connector-id <value>
```

**Origination structure:**
```json
{
    "Routes": [
        {
            "Host": "string",
            "Port": 5060,
            "Protocol": "TCP|UDP",
            "Priority": 1,
            "Weight": 1
        }
    ],
    "Disabled": false
}
```

---

### 12.2 Termination — `put-voice-connector-termination` / `get-voice-connector-termination` / `delete-voice-connector-termination`

Configures outbound calling settings.

**Synopsis:**
```bash
aws chime-sdk-voice put-voice-connector-termination \
    --voice-connector-id <value> \
    --termination <value>

aws chime-sdk-voice get-voice-connector-termination \
    --voice-connector-id <value>

aws chime-sdk-voice delete-voice-connector-termination \
    --voice-connector-id <value>
```

**Termination structure:**
```json
{
    "CpsLimit": 1,
    "DefaultPhoneNumber": "string",
    "CallingRegions": ["US", "CA"],
    "CidrAllowedList": ["10.0.0.0/24"],
    "Disabled": false
}
```

---

### 12.3 `get-voice-connector-termination-health`

Gets termination health status.

```bash
aws chime-sdk-voice get-voice-connector-termination-health \
    --voice-connector-id <value>
```

**Output Schema:**
```json
{
    "TerminationHealth": {
        "Timestamp": "timestamp",
        "Source": "string"
    }
}
```

---

### 12.4 Termination Credentials — `put-voice-connector-termination-credentials` / `list-voice-connector-termination-credentials` / `delete-voice-connector-termination-credentials`

```bash
aws chime-sdk-voice put-voice-connector-termination-credentials \
    --voice-connector-id <value> \
    --credentials '[{"Username":"user","Password":"pass"}]'

aws chime-sdk-voice list-voice-connector-termination-credentials \
    --voice-connector-id <value>

aws chime-sdk-voice delete-voice-connector-termination-credentials \
    --voice-connector-id <value> --usernames user1 user2
```

---

### 12.5 Streaming — `put-voice-connector-streaming-configuration` / `get-voice-connector-streaming-configuration` / `delete-voice-connector-streaming-configuration`

Configures media streaming to Kinesis.

**StreamingConfiguration structure:**
```json
{
    "DataRetentionInHours": 24,
    "Disabled": false,
    "StreamingNotificationTargets": [{"NotificationTarget": "EventBridge|SNS|SQS"}],
    "MediaInsightsConfiguration": {
        "Disabled": false,
        "ConfigurationArn": "string"
    }
}
```

---

### 12.6 Logging — `put-voice-connector-logging-configuration` / `get-voice-connector-logging-configuration`

```bash
aws chime-sdk-voice put-voice-connector-logging-configuration \
    --voice-connector-id <value> \
    --logging-configuration '{"EnableSIPLogs":true,"EnableMediaMetricLogs":false}'
```

---

### 12.7 Proxy — `put-voice-connector-proxy` / `get-voice-connector-proxy` / `delete-voice-connector-proxy`

Configures proxy sessions for phone number masking.

```bash
aws chime-sdk-voice put-voice-connector-proxy \
    --voice-connector-id <value> \
    --default-session-expiry-minutes 60 \
    --phone-number-pool-countries US CA \
    [--fall-back-phone-number <value>] \
    [--disabled | --no-disabled]
```

---

### 12.8 Emergency Calling — `put-voice-connector-emergency-calling-configuration` / `get-voice-connector-emergency-calling-configuration` / `delete-voice-connector-emergency-calling-configuration`

Configures E911 emergency calling.

**EmergencyCallingConfiguration structure:**
```json
{
    "DNIS": [
        {
            "EmergencyPhoneNumber": "+15551234567",
            "TestPhoneNumber": "+15559876543",
            "CallingCountry": "US"
        }
    ]
}
```

---

### 12.9 External Systems — `put-voice-connector-external-systems-configuration` / `get-voice-connector-external-systems-configuration` / `delete-voice-connector-external-systems-configuration`

Configures external system integration (e.g., Amazon Connect).

```bash
aws chime-sdk-voice put-voice-connector-external-systems-configuration \
    --voice-connector-id <value> \
    --external-systems-configuration <value>
```
