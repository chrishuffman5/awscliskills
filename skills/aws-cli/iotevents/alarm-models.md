# Alarm Models

## 3.1 `create-alarm-model`

Creates an alarm model for threshold-based monitoring.

**Synopsis:**
```bash
aws iotevents create-alarm-model \
    --alarm-model-name <value> \
    --role-arn <value> \
    --alarm-rule <value> \
    [--alarm-model-description <value>] \
    [--tags <value>] \
    [--key <value>] \
    [--severity <value>] \
    [--alarm-notification <value>] \
    [--alarm-event-actions <value>] \
    [--alarm-capabilities <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alarm-model-name` | **Yes** | string | -- | Alarm model name (1-128 chars) |
| `--role-arn` | **Yes** | string | -- | IAM role ARN (1-2048 chars) |
| `--alarm-rule` | **Yes** | structure | -- | Rule defining when alarm triggers |
| `--alarm-model-description` | No | string | None | Description (max 1024 chars) |
| `--tags` | No | list | None | Tags (max 50) |
| `--key` | No | string | None | Input attribute for partitioning (1-128 chars) |
| `--severity` | No | integer | None | Severity level (0-2147483647) |
| `--alarm-notification` | No | structure | None | Notification actions (Lambda, SMS, Email) |
| `--alarm-event-actions` | No | structure | None | Actions on alarm state changes |
| `--alarm-capabilities` | No | structure | None | Initialization and acknowledge flow settings |

**AlarmRule:**
```json
{
    "simpleRule": {
        "inputProperty": "string",
        "comparisonOperator": "GREATER|GREATER_OR_EQUAL|LESS|LESS_OR_EQUAL|EQUAL|NOT_EQUAL",
        "threshold": "string"
    }
}
```

**AlarmCapabilities:**
```json
{
    "initializationConfiguration": {
        "disabledOnInitialization": "boolean"
    },
    "acknowledgeFlow": {
        "enabled": "boolean"
    }
}
```

**Output Schema:**
```json
{
    "creationTime": "timestamp",
    "alarmModelArn": "string",
    "alarmModelVersion": "string",
    "lastUpdateTime": "timestamp",
    "status": "ACTIVE|ACTIVATING|INACTIVE|FAILED"
}
```

---

## 3.2 `describe-alarm-model`

Describes an alarm model.

**Synopsis:**
```bash
aws iotevents describe-alarm-model \
    --alarm-model-name <value> \
    [--alarm-model-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alarm-model-name` | **Yes** | string | -- | Alarm model name |
| `--alarm-model-version` | No | string | None | Version (default: latest) |

**Output Schema:**
```json
{
    "creationTime": "timestamp",
    "alarmModelArn": "string",
    "alarmModelVersion": "string",
    "lastUpdateTime": "timestamp",
    "status": "ACTIVE|ACTIVATING|INACTIVE|FAILED",
    "statusMessage": "string",
    "alarmModelName": "string",
    "alarmModelDescription": "string",
    "roleArn": "string",
    "key": "string",
    "severity": "integer",
    "alarmRule": {},
    "alarmNotification": {},
    "alarmEventActions": {},
    "alarmCapabilities": {}
}
```

---

## 3.3 `list-alarm-models`

Lists alarm models. **Paginated operation.**

**Synopsis:**
```bash
aws iotevents list-alarm-models \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-250) |

**Output Schema:**
```json
{
    "alarmModelSummaries": [
        {
            "creationTime": "timestamp",
            "alarmModelDescription": "string",
            "alarmModelName": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 3.4 `update-alarm-model`

Updates an alarm model, creating a new version.

**Synopsis:**
```bash
aws iotevents update-alarm-model \
    --alarm-model-name <value> \
    --role-arn <value> \
    --alarm-rule <value> \
    [--alarm-model-description <value>] \
    [--severity <value>] \
    [--alarm-notification <value>] \
    [--alarm-event-actions <value>] \
    [--alarm-capabilities <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alarm-model-name` | **Yes** | string | -- | Alarm model name |
| `--role-arn` | **Yes** | string | -- | IAM role ARN |
| `--alarm-rule` | **Yes** | structure | -- | Updated alarm rule |
| `--alarm-model-description` | No | string | None | Updated description |
| `--severity` | No | integer | None | Updated severity |
| `--alarm-notification` | No | structure | None | Updated notifications |
| `--alarm-event-actions` | No | structure | None | Updated event actions |
| `--alarm-capabilities` | No | structure | None | Updated capabilities |

**Output Schema:**
```json
{
    "creationTime": "timestamp",
    "alarmModelArn": "string",
    "alarmModelVersion": "string",
    "lastUpdateTime": "timestamp",
    "status": "ACTIVE|ACTIVATING|INACTIVE|FAILED"
}
```

---

## 3.5 `delete-alarm-model`

Deletes an alarm model.

**Synopsis:**
```bash
aws iotevents delete-alarm-model \
    --alarm-model-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alarm-model-name` | **Yes** | string | -- | Alarm model name |

**Output:** None

---

## 3.6 `list-alarm-model-versions`

Lists alarm model versions. **Paginated operation.**

**Synopsis:**
```bash
aws iotevents list-alarm-model-versions \
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
    "alarmModelVersionSummaries": [
        {
            "alarmModelName": "string",
            "alarmModelArn": "string",
            "alarmModelVersion": "string",
            "roleArn": "string",
            "creationTime": "timestamp",
            "lastUpdateTime": "timestamp",
            "status": "ACTIVE|ACTIVATING|INACTIVE|FAILED",
            "statusMessage": "string"
        }
    ],
    "nextToken": "string"
}
```
