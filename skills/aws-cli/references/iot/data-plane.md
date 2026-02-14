# Data Plane

Commands from `aws iot-data` and `aws iot-jobs-data` for device-side operations.

## 16.1 `publish` (iot-data)

Publishes a message to an MQTT topic over HTTP.

**Synopsis:**
```bash
aws iot-data publish \
    --topic <value> \
    [--qos <value>] \
    [--retain | --no-retain] \
    [--payload <value>] \
    [--user-properties <value>] \
    [--payload-format-indicator <value>] \
    [--content-type <value>] \
    [--response-topic <value>] \
    [--correlation-data <value>] \
    [--message-expiry <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--topic` | **Yes** | string | -- | MQTT topic name |
| `--qos` | No | integer | 0 | Quality of Service (0 or 1) |
| `--retain` | No | boolean | false | Set RETAIN flag |
| `--payload` | No | blob | None | Message body |
| `--user-properties` | No | JSON | None | MQTT5 user properties (base64 for HTTP) |
| `--payload-format-indicator` | No | string | None | `UNSPECIFIED_BYTES` or `UTF8_DATA` |
| `--content-type` | No | string | None | Content type description |
| `--response-topic` | No | string | None | Response topic for request-response |
| `--correlation-data` | No | string | None | Correlation data (base64) |
| `--message-expiry` | No | long | None | Message expiry in seconds |

**Output:** None

---

## 16.2 `get-retained-message` (iot-data)

Gets a retained message for a topic.

**Synopsis:**
```bash
aws iot-data get-retained-message \
    --topic <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--topic` | **Yes** | string | -- | Topic name |

**Output Schema:**
```json
{
    "topic": "string",
    "payload": "blob",
    "qos": "integer",
    "lastModifiedTime": "long",
    "userProperties": "blob"
}
```

---

## 16.3 `list-retained-messages` (iot-data)

Lists retained messages. **Paginated operation.**

**Synopsis:**
```bash
aws iot-data list-retained-messages \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-200) |

**Output Schema:**
```json
{
    "retainedTopics": [
        {
            "topic": "string",
            "payloadSize": "long",
            "qos": "integer",
            "lastModifiedTime": "long"
        }
    ],
    "nextToken": "string"
}
```

---

## 16.4 `delete-connection` (iot-data)

Deletes a persistent MQTT connection.

**Synopsis:**
```bash
aws iot-data delete-connection \
    --connection-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-id` | **Yes** | string | -- | Connection ID (client ID) |

**Output Schema:**
```json
{
    "isConnectionPersistent": "boolean"
}
```

---

## 16.5 `describe-job-execution` (iot-jobs-data)

Describes a job execution from the device side. Requires the IoT Jobs data endpoint.

**Synopsis:**
```bash
aws iot-jobs-data describe-job-execution \
    --job-id <value> \
    --thing-name <value> \
    [--include-job-document | --no-include-job-document] \
    [--execution-number <value>] \
    --endpoint-url <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID (or `$next` for next pending) |
| `--thing-name` | **Yes** | string | -- | Thing name (1-128 chars) |
| `--include-job-document` | No | boolean | true | Include job document in response |
| `--execution-number` | No | long | None | Specific execution number |
| `--endpoint-url` | **Yes** | string | -- | IoT Jobs data endpoint URL |

**Output Schema:**
```json
{
    "execution": {
        "jobId": "string",
        "thingName": "string",
        "status": "QUEUED|IN_PROGRESS|SUCCEEDED|FAILED|TIMED_OUT|REJECTED|REMOVED|CANCELED",
        "statusDetails": {"string": "string"},
        "queuedAt": "long",
        "startedAt": "long",
        "lastUpdatedAt": "long",
        "approximateSecondsBeforeTimedOut": "long",
        "versionNumber": "long",
        "executionNumber": "long",
        "jobDocument": "string"
    }
}
```

---

## 16.6 `get-pending-job-executions` (iot-jobs-data)

Gets pending job executions for a thing.

**Synopsis:**
```bash
aws iot-jobs-data get-pending-job-executions \
    --thing-name <value> \
    --endpoint-url <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-name` | **Yes** | string | -- | Thing name |
| `--endpoint-url` | **Yes** | string | -- | IoT Jobs data endpoint URL |

**Output Schema:**
```json
{
    "inProgressJobs": [
        {
            "jobId": "string",
            "queuedAt": "long",
            "startedAt": "long",
            "lastUpdatedAt": "long",
            "versionNumber": "long",
            "executionNumber": "long"
        }
    ],
    "queuedJobs": [
        {
            "jobId": "string",
            "queuedAt": "long",
            "lastUpdatedAt": "long",
            "versionNumber": "long",
            "executionNumber": "long"
        }
    ]
}
```

---

## 16.7 `start-next-pending-job-execution` (iot-jobs-data)

Starts the next pending job execution for a thing.

**Synopsis:**
```bash
aws iot-jobs-data start-next-pending-job-execution \
    --thing-name <value> \
    [--status-details <value>] \
    [--step-timeout-in-minutes <value>] \
    --endpoint-url <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-name` | **Yes** | string | -- | Thing name |
| `--status-details` | No | map | None | Status details |
| `--step-timeout-in-minutes` | No | long | None | Step timeout (1-10080 minutes) |
| `--endpoint-url` | **Yes** | string | -- | IoT Jobs data endpoint URL |

**Output Schema:**
```json
{
    "execution": {
        "jobId": "string",
        "thingName": "string",
        "status": "string",
        "statusDetails": {},
        "queuedAt": "long",
        "startedAt": "long",
        "lastUpdatedAt": "long",
        "versionNumber": "long",
        "executionNumber": "long",
        "jobDocument": "string"
    }
}
```

---

## 16.8 `update-job-execution` (iot-jobs-data)

Updates a job execution status from the device side.

**Synopsis:**
```bash
aws iot-jobs-data update-job-execution \
    --job-id <value> \
    --thing-name <value> \
    --status <value> \
    [--status-details <value>] \
    [--step-timeout-in-minutes <value>] \
    [--expected-version <value>] \
    [--include-job-execution-state | --no-include-job-execution-state] \
    [--include-job-document | --no-include-job-document] \
    [--execution-number <value>] \
    --endpoint-url <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID |
| `--thing-name` | **Yes** | string | -- | Thing name |
| `--status` | **Yes** | string | -- | `QUEUED`, `IN_PROGRESS`, `SUCCEEDED`, `FAILED`, `TIMED_OUT`, `REJECTED`, `REMOVED`, `CANCELED` |
| `--status-details` | No | map | None | Status details (max 1024 chars per value) |
| `--step-timeout-in-minutes` | No | long | None | Step timeout (1-10080, or -1 to cancel) |
| `--expected-version` | No | long | None | Expected version for optimistic locking |
| `--include-job-execution-state` | No | boolean | false | Include execution state in response |
| `--include-job-document` | No | boolean | false | Include job document in response |
| `--execution-number` | No | long | None | Execution number |
| `--endpoint-url` | **Yes** | string | -- | IoT Jobs data endpoint URL |

**Output Schema:**
```json
{
    "executionState": {
        "status": "string",
        "statusDetails": {},
        "versionNumber": "long"
    },
    "jobDocument": "string"
}
```
