# Detector Models

## 1.1 `create-detector-model`

Creates a detector model (finite state machine) that evaluates incoming inputs.

**Synopsis:**
```bash
aws iotevents create-detector-model \
    --detector-model-name <value> \
    --detector-model-definition <value> \
    --role-arn <value> \
    [--detector-model-description <value>] \
    [--key <value>] \
    [--evaluation-method <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-model-name` | **Yes** | string | -- | Model name (1-128 chars, pattern `^[a-zA-Z0-9_-]+$`) |
| `--detector-model-definition` | **Yes** | structure | -- | State machine definition with states, events, transitions, actions |
| `--role-arn` | **Yes** | string | -- | IAM role ARN for performing actions |
| `--detector-model-description` | No | string | None | Description (max 1024 chars) |
| `--key` | No | string | None | Input attribute for partitioning detector instances |
| `--evaluation-method` | No | string | None | `BATCH` or `SERIAL` |
| `--tags` | No | list | None | Tags |

**DetectorModelDefinition (key structure):**
```json
{
    "states": [
        {
            "stateName": "string",
            "onInput": {
                "events": [{"eventName": "string", "condition": "string", "actions": []}],
                "transitionEvents": [{"eventName": "string", "condition": "string", "nextState": "string", "actions": []}]
            },
            "onEnter": {"events": []},
            "onExit": {"events": []}
        }
    ],
    "initialStateName": "string"
}
```

**Supported actions:** `setVariable`, `sns`, `iotTopicPublish`, `setTimer`, `clearTimer`, `resetTimer`, `lambda`, `iotEvents`, `sqs`, `firehose`, `dynamoDB`, `dynamoDBv2`, `iotSiteWise`

**Output Schema:**
```json
{
    "detectorModelConfiguration": {
        "detectorModelName": "string",
        "detectorModelVersion": "string",
        "detectorModelArn": "string",
        "roleArn": "string",
        "creationTime": "timestamp",
        "lastUpdateTime": "timestamp",
        "status": "ACTIVE|ACTIVATING|INACTIVE|DEPRECATED|DRAFT|PAUSED|FAILED",
        "key": "string",
        "evaluationMethod": "BATCH|SERIAL"
    }
}
```

---

## 1.2 `describe-detector-model`

Describes a detector model. Returns the latest or specified version.

**Synopsis:**
```bash
aws iotevents describe-detector-model \
    --detector-model-name <value> \
    [--detector-model-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-model-name` | **Yes** | string | -- | Model name |
| `--detector-model-version` | No | string | None | Version (default: latest) |

**Output Schema:**
```json
{
    "detectorModel": {
        "detectorModelDefinition": {},
        "detectorModelConfiguration": {
            "detectorModelName": "string",
            "detectorModelVersion": "string",
            "detectorModelDescription": "string",
            "detectorModelArn": "string",
            "roleArn": "string",
            "creationTime": "timestamp",
            "lastUpdateTime": "timestamp",
            "status": "string",
            "key": "string",
            "evaluationMethod": "string"
        }
    }
}
```

---

## 1.3 `list-detector-models`

Lists detector models. **Paginated operation.**

**Synopsis:**
```bash
aws iotevents list-detector-models \
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
    "detectorModelSummaries": [
        {
            "detectorModelName": "string",
            "detectorModelDescription": "string",
            "creationTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

## 1.4 `update-detector-model`

Updates a detector model, creating a new version.

**Synopsis:**
```bash
aws iotevents update-detector-model \
    --detector-model-name <value> \
    --detector-model-definition <value> \
    --role-arn <value> \
    [--detector-model-description <value>] \
    [--evaluation-method <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-model-name` | **Yes** | string | -- | Model name |
| `--detector-model-definition` | **Yes** | structure | -- | Updated definition |
| `--role-arn` | **Yes** | string | -- | IAM role ARN |
| `--detector-model-description` | No | string | None | Updated description |
| `--evaluation-method` | No | string | None | `BATCH` or `SERIAL` |

**Output Schema:**
```json
{
    "detectorModelConfiguration": {
        "detectorModelName": "string",
        "detectorModelVersion": "string",
        "detectorModelArn": "string",
        "roleArn": "string",
        "creationTime": "timestamp",
        "lastUpdateTime": "timestamp",
        "status": "string",
        "key": "string",
        "evaluationMethod": "string"
    }
}
```

---

## 1.5 `delete-detector-model`

Deletes a detector model and all versions.

**Synopsis:**
```bash
aws iotevents delete-detector-model \
    --detector-model-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-model-name` | **Yes** | string | -- | Model name |

**Output:** None

---

## 1.6 `list-detector-model-versions`

Lists detector model versions. **Paginated operation.**

**Synopsis:**
```bash
aws iotevents list-detector-model-versions \
    --detector-model-name <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-model-name` | **Yes** | string | -- | Model name |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-250) |

**Output Schema:**
```json
{
    "detectorModelVersionSummaries": [
        {
            "detectorModelName": "string",
            "detectorModelVersion": "string",
            "detectorModelArn": "string",
            "roleArn": "string",
            "creationTime": "timestamp",
            "lastUpdateTime": "timestamp",
            "status": "string",
            "evaluationMethod": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 1.7 `start-detector-model-analysis`

Starts analyzing a detector model definition for errors.

**Synopsis:**
```bash
aws iotevents start-detector-model-analysis \
    --detector-model-definition <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-model-definition` | **Yes** | structure | -- | Detector model definition to analyze |

**Output Schema:**
```json
{
    "analysisId": "string"
}
```

---

## 1.8 `describe-detector-model-analysis`

Describes the status of a detector model analysis.

**Synopsis:**
```bash
aws iotevents describe-detector-model-analysis \
    --analysis-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--analysis-id` | **Yes** | string | -- | Analysis ID |

**Output Schema:**
```json
{
    "status": "RUNNING|COMPLETE|FAILED"
}
```

---

## 1.9 `get-detector-model-analysis-results`

Gets the results of a detector model analysis.

**Synopsis:**
```bash
aws iotevents get-detector-model-analysis-results \
    --analysis-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--analysis-id` | **Yes** | string | -- | Analysis ID |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results |

**Output Schema:**
```json
{
    "analysisResults": [
        {
            "type": "string",
            "level": "INFO|WARNING|ERROR",
            "message": "string",
            "locations": [
                {"path": "string"}
            ]
        }
    ],
    "nextToken": "string"
}
```
