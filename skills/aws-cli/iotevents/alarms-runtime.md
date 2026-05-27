# Alarms Runtime

Commands from the `aws iotevents-data` service for managing alarm instances at runtime.

## 5.1 `describe-alarm`

Describes an alarm instance.

**Synopsis:**
```bash
aws iotevents-data describe-alarm \
    --alarm-model-name <value> \
    [--key-value <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alarm-model-name` | **Yes** | string | -- | Alarm model name (1-128 chars) |
| `--key-value` | No | string | None | Key value for the alarm instance (1-128 chars) |

**Output Schema:**
```json
{
    "alarm": {
        "alarmModelName": "string",
        "alarmModelVersion": "string",
        "keyValue": "string",
        "alarmState": {
            "stateName": "DISABLED|NORMAL|ACTIVE|ACKNOWLEDGED|SNOOZE_DISABLED|LATCHED",
            "ruleEvaluation": {
                "simpleRuleEvaluation": {
                    "inputPropertyValue": "string",
                    "operator": "GREATER|GREATER_OR_EQUAL|LESS|LESS_OR_EQUAL|EQUAL|NOT_EQUAL",
                    "thresholdValue": "string"
                }
            },
            "customerAction": {
                "actionName": "SNOOZE|ENABLE|DISABLE|ACKNOWLEDGE|RESET",
                "snoozeActionConfiguration": {"snoozeDuration": "integer", "note": "string"},
                "enableActionConfiguration": {"note": "string"},
                "disableActionConfiguration": {"note": "string"},
                "acknowledgeActionConfiguration": {"note": "string"},
                "resetActionConfiguration": {"note": "string"}
            },
            "systemEvent": {
                "eventType": "STATE_CHANGE",
                "stateChangeConfiguration": {"triggerType": "SNOOZE_TIMEOUT"}
            }
        },
        "severity": "integer",
        "creationTime": "timestamp",
        "lastUpdateTime": "timestamp"
    }
}
```

---

## 5.2 `list-alarms`

Lists alarm instances for an alarm model. **Paginated operation.**

**Synopsis:**
```bash
aws iotevents-data list-alarms \
    --alarm-model-name <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alarm-model-name` | **Yes** | string | -- | Alarm model name |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-250) |

**Output Schema:**
```json
{
    "alarmSummaries": [
        {
            "alarmModelName": "string",
            "alarmModelVersion": "string",
            "keyValue": "string",
            "stateName": "DISABLED|NORMAL|ACTIVE|ACKNOWLEDGED|SNOOZE_DISABLED|LATCHED",
            "creationTime": "timestamp",
            "lastUpdateTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

## 5.3 `batch-acknowledge-alarm`

Acknowledges one or more alarms.

**Synopsis:**
```bash
aws iotevents-data batch-acknowledge-alarm \
    --acknowledge-action-requests <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--acknowledge-action-requests` | **Yes** | list | -- | Acknowledge requests (min 1) |

**Request structure:**
```json
[
    {
        "requestId": "string",
        "alarmModelName": "string",
        "keyValue": "string",
        "note": "string"
    }
]
```

**Output Schema:**
```json
{
    "errorEntries": [
        {
            "requestId": "string",
            "errorCode": "ResourceNotFoundException|InvalidRequestException|InternalFailureException|ServiceUnavailableException|ThrottlingException",
            "errorMessage": "string"
        }
    ]
}
```

---

## 5.4 `batch-disable-alarm`

Disables one or more alarms.

**Synopsis:**
```bash
aws iotevents-data batch-disable-alarm \
    --disable-action-requests <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--disable-action-requests` | **Yes** | list | -- | Disable requests (min 1) |

**Request structure:**
```json
[
    {
        "requestId": "string",
        "alarmModelName": "string",
        "keyValue": "string",
        "note": "string"
    }
]
```

**Output Schema:**
```json
{
    "errorEntries": [
        {"requestId": "string", "errorCode": "string", "errorMessage": "string"}
    ]
}
```

---

## 5.5 `batch-enable-alarm`

Enables one or more alarms.

**Synopsis:**
```bash
aws iotevents-data batch-enable-alarm \
    --enable-action-requests <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--enable-action-requests` | **Yes** | list | -- | Enable requests (min 1) |

**Request structure:**
```json
[
    {
        "requestId": "string",
        "alarmModelName": "string",
        "keyValue": "string",
        "note": "string"
    }
]
```

**Output Schema:**
```json
{
    "errorEntries": [
        {"requestId": "string", "errorCode": "string", "errorMessage": "string"}
    ]
}
```

---

## 5.6 `batch-reset-alarm`

Resets one or more alarms to NORMAL state.

**Synopsis:**
```bash
aws iotevents-data batch-reset-alarm \
    --reset-action-requests <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--reset-action-requests` | **Yes** | list | -- | Reset requests (min 1) |

**Request structure:**
```json
[
    {
        "requestId": "string",
        "alarmModelName": "string",
        "keyValue": "string",
        "note": "string"
    }
]
```

**Output Schema:**
```json
{
    "errorEntries": [
        {"requestId": "string", "errorCode": "string", "errorMessage": "string"}
    ]
}
```

---

## 5.7 `batch-snooze-alarm`

Snoozes one or more alarms for a specified duration.

**Synopsis:**
```bash
aws iotevents-data batch-snooze-alarm \
    --snooze-action-requests <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--snooze-action-requests` | **Yes** | list | -- | Snooze requests (min 1) |

**Request structure:**
```json
[
    {
        "requestId": "string",
        "alarmModelName": "string",
        "keyValue": "string",
        "note": "string",
        "snoozeDuration": "integer"
    }
]
```

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `requestId` | **Yes** | string | Unique request ID |
| `alarmModelName` | **Yes** | string | Alarm model name |
| `keyValue` | No | string | Key value |
| `note` | No | string | Note (max 256 chars) |
| `snoozeDuration` | **Yes** | integer | Snooze duration in seconds |

**Output Schema:**
```json
{
    "errorEntries": [
        {"requestId": "string", "errorCode": "string", "errorMessage": "string"}
    ]
}
```
