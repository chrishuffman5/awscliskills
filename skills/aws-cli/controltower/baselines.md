# Baselines

### 3.1 `enable-baseline`

Enables a baseline on an organizational unit. This is an asynchronous operation.

**Synopsis:**
```bash
aws controltower enable-baseline \
    --baseline-identifier <value> \
    --baseline-version <value> \
    --target-identifier <value> \
    [--parameters <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--baseline-identifier` | **Yes** | string | -- | The ARN of the baseline to enable |
| `--baseline-version` | **Yes** | string | -- | Version to enable (pattern: `\d+(?:\.\d+){0,2}`) |
| `--target-identifier` | **Yes** | string | -- | The ARN of the target OU |
| `--parameters` | No | list | None | Key-value input parameters for enablement |
| `--tags` | No | map | None | Key-value pairs for tagging (max 200) |

**Parameters Structure:**
```json
[
    {
        "key": "string",
        "value": "document"
    }
]
```

**Output Schema:**
```json
{
    "operationIdentifier": "string",
    "arn": "string"
}
```

---

### 3.2 `disable-baseline`

Disables a baseline on an organizational unit. This is an asynchronous operation.

**Synopsis:**
```bash
aws controltower disable-baseline \
    --enabled-baseline-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--enabled-baseline-identifier` | **Yes** | string | -- | The ARN of the enabled baseline to disable |

**Output Schema:**
```json
{
    "operationIdentifier": "string"
}
```

---

### 3.3 `get-baseline`

Returns details about a baseline.

**Synopsis:**
```bash
aws controltower get-baseline \
    --baseline-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--baseline-identifier` | **Yes** | string | -- | The ARN of the baseline |

**Output Schema:**
```json
{
    "arn": "string",
    "name": "string",
    "description": "string"
}
```

---

### 3.4 `get-enabled-baseline`

Returns details about an enabled baseline.

**Synopsis:**
```bash
aws controltower get-enabled-baseline \
    --enabled-baseline-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--enabled-baseline-identifier` | **Yes** | string | -- | The ARN of the enabled baseline |

**Output Schema:**
```json
{
    "enabledBaselineDetails": {
        "arn": "string",
        "baselineIdentifier": "string",
        "baselineVersion": "string",
        "targetIdentifier": "string",
        "statusSummary": {
            "status": "SUCCEEDED|FAILED|UNDER_CHANGE",
            "lastOperationIdentifier": "string"
        },
        "parameters": [
            {
                "key": "string",
                "value": "document"
            }
        ]
    }
}
```

---

### 3.5 `list-baselines`

Lists all available baselines. **Paginated operation.**

**Synopsis:**
```bash
aws controltower list-baselines \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "baselines": [
        {
            "arn": "string",
            "name": "string",
            "description": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 3.6 `list-enabled-baselines`

Lists all enabled baselines. **Paginated operation.**

**Synopsis:**
```bash
aws controltower list-enabled-baselines \
    [--filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter` | No | structure | None | Filter by baseline identifiers and target identifiers |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Structure:**
```json
{
    "baselineIdentifiers": ["string"],
    "targetIdentifiers": ["string"],
    "parentIdentifiers": ["string"]
}
```

**Output Schema:**
```json
{
    "enabledBaselines": [
        {
            "arn": "string",
            "baselineIdentifier": "string",
            "baselineVersion": "string",
            "targetIdentifier": "string",
            "statusSummary": {
                "status": "SUCCEEDED|FAILED|UNDER_CHANGE",
                "lastOperationIdentifier": "string"
            },
            "parentIdentifier": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 3.7 `update-enabled-baseline`

Updates an enabled baseline. This is an asynchronous operation.

**Synopsis:**
```bash
aws controltower update-enabled-baseline \
    --enabled-baseline-identifier <value> \
    --baseline-version <value> \
    [--parameters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--enabled-baseline-identifier` | **Yes** | string | -- | The ARN of the enabled baseline to update |
| `--baseline-version` | **Yes** | string | -- | Target baseline version |
| `--parameters` | No | list | None | Updated key-value input parameters |

**Output Schema:**
```json
{
    "operationIdentifier": "string"
}
```

---

### 3.8 `reset-enabled-baseline`

Resets an enabled baseline. This is an asynchronous operation.

**Synopsis:**
```bash
aws controltower reset-enabled-baseline \
    --enabled-baseline-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--enabled-baseline-identifier` | **Yes** | string | -- | The ARN of the enabled baseline to reset |

**Output Schema:**
```json
{
    "operationIdentifier": "string"
}
```

---

### 3.9 `get-baseline-operation`

Returns details of a baseline operation.

**Synopsis:**
```bash
aws controltower get-baseline-operation \
    --operation-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--operation-identifier` | **Yes** | string | -- | The operation UUID (36 chars) |

**Output Schema:**
```json
{
    "baselineOperation": {
        "operationType": "ENABLE_BASELINE|DISABLE_BASELINE|UPDATE_ENABLED_BASELINE|RESET_ENABLED_BASELINE",
        "startTime": "timestamp",
        "endTime": "timestamp",
        "status": "SUCCEEDED|FAILED|IN_PROGRESS",
        "statusMessage": "string",
        "operationIdentifier": "string"
    }
}
```
