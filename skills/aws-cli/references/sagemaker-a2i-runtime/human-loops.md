# Human Loops

### 1.1 `start-human-loop`

Starts a human loop for a custom task type. Routes data to human workers for review when ML models cannot evaluate with high confidence.

**Synopsis:**
```bash
aws sagemaker-a2i-runtime start-human-loop \
    --human-loop-name <value> \
    --flow-definition-arn <value> \
    --human-loop-input <value> \
    [--data-attributes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--human-loop-name` | **Yes** | string | -- | Human loop name (1-63 chars, pattern: `^[a-z0-9](-*[a-z0-9])*$`) |
| `--flow-definition-arn` | **Yes** | string | -- | ARN of the flow definition (max 1024 chars) |
| `--human-loop-input` | **Yes** | structure | -- | Input data. Shorthand: `InputContent=string` (max 3,145,728 chars) |
| `--data-attributes` | No | structure | -- | Content classifiers. Shorthand: `ContentClassifiers=FreeOfPersonallyIdentifiableInformation,FreeOfAdultContent` |

**Human Loop Input Structure:**
```json
{
    "InputContent": "string"
}
```

**Data Attributes Structure:**
```json
{
    "ContentClassifiers": [
        "FreeOfPersonallyIdentifiableInformation",
        "FreeOfAdultContent"
    ]
}
```

**Output Schema:**
```json
{
    "HumanLoopArn": "string"
}
```

---

### 1.2 `describe-human-loop`

Gets details about a human loop, including its status and output.

**Synopsis:**
```bash
aws sagemaker-a2i-runtime describe-human-loop \
    --human-loop-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--human-loop-name` | **Yes** | string | -- | Name of the human loop (1-63 chars) |

**Output Schema:**
```json
{
    "CreationTime": "timestamp",
    "FailureReason": "string",
    "FailureCode": "ValidationError|Expired|InternalError",
    "HumanLoopStatus": "InProgress|Failed|Completed|Stopped|Stopping",
    "HumanLoopName": "string",
    "HumanLoopArn": "string",
    "FlowDefinitionArn": "string",
    "HumanLoopOutput": {
        "OutputS3Uri": "string"
    }
}
```

---

### 1.3 `list-human-loops`

Lists human loops for a flow definition. **Paginated operation.**

**Synopsis:**
```bash
aws sagemaker-a2i-runtime list-human-loops \
    --flow-definition-arn <value> \
    [--creation-time-after <value>] \
    [--creation-time-before <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-definition-arn` | **Yes** | string | -- | ARN of the flow definition (max 1024 chars) |
| `--creation-time-after` | No | timestamp | -- | Filter loops created after this time (ISO 8601) |
| `--creation-time-before` | No | timestamp | -- | Filter loops created before this time (ISO 8601) |
| `--sort-order` | No | string | -- | Sort order: `Ascending` or `Descending` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "HumanLoopSummaries": [
        {
            "HumanLoopName": "string",
            "HumanLoopStatus": "InProgress|Failed|Completed|Stopped|Stopping",
            "CreationTime": "timestamp",
            "FailureReason": "string",
            "FlowDefinitionArn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.4 `stop-human-loop`

Stops an in-progress human loop.

**Synopsis:**
```bash
aws sagemaker-a2i-runtime stop-human-loop \
    --human-loop-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--human-loop-name` | **Yes** | string | -- | Name of the human loop to stop (1-63 chars) |

**Output:** None (HTTP 200 on success)

---

### 1.5 `delete-human-loop`

Deletes a human loop. The loop must be in `Completed`, `Failed`, or `Stopped` status.

**Synopsis:**
```bash
aws sagemaker-a2i-runtime delete-human-loop \
    --human-loop-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--human-loop-name` | **Yes** | string | -- | Name of the human loop to delete (1-63 chars) |

**Output:** None (HTTP 200 on success)
