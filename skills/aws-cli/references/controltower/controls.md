# Controls

### 2.1 `enable-control`

Enables a control (guardrail) on an organizational unit. Only strongly recommended and elective controls are permitted (except Region deny control). This is an asynchronous operation.

**Synopsis:**
```bash
aws controltower enable-control \
    --control-identifier <value> \
    --target-identifier <value> \
    [--tags <value>] \
    [--parameters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--control-identifier` | **Yes** | string | -- | The ARN of the control to enable |
| `--target-identifier` | **Yes** | string | -- | The ARN of the organizational unit |
| `--tags` | No | map | None | Key-value pairs for tagging (max 200) |
| `--parameters` | No | list | None | Input parameters to configure the control |

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

### 2.2 `disable-control`

Disables a control on an organizational unit. This is an asynchronous operation.

**Synopsis:**
```bash
aws controltower disable-control \
    [--control-identifier <value>] \
    [--target-identifier <value>] \
    [--enabled-control-identifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--control-identifier` | No | string | None | The ARN of the control to disable |
| `--target-identifier` | No | string | None | The ARN of the organizational unit |
| `--enabled-control-identifier` | No | string | None | The ARN of the enabled control resource to disable |

> At least one identifier parameter is required. Use either `--control-identifier` + `--target-identifier` or `--enabled-control-identifier`.

**Output Schema:**
```json
{
    "operationIdentifier": "string"
}
```

---

### 2.3 `get-enabled-control`

Returns details about an enabled control.

**Synopsis:**
```bash
aws controltower get-enabled-control \
    --enabled-control-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--enabled-control-identifier` | **Yes** | string | -- | The ARN of the enabled control |

**Output Schema:**
```json
{
    "enabledControlDetails": {
        "arn": "string",
        "controlIdentifier": "string",
        "targetIdentifier": "string",
        "statusSummary": {
            "status": "SUCCEEDED|FAILED|UNDER_CHANGE",
            "lastOperationIdentifier": "string"
        },
        "driftStatusSummary": {
            "driftStatus": "DRIFTED|IN_SYNC|NOT_CHECKING|UNKNOWN",
            "types": {
                "inheritance": {
                    "status": "DRIFTED|IN_SYNC|NOT_CHECKING|UNKNOWN"
                },
                "resource": {
                    "status": "DRIFTED|IN_SYNC|NOT_CHECKING|UNKNOWN"
                }
            }
        },
        "parentIdentifier": "string",
        "targetRegions": [
            {
                "name": "string"
            }
        ],
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

### 2.4 `list-enabled-controls`

Lists enabled controls on an organizational unit. **Paginated operation.**

**Synopsis:**
```bash
aws controltower list-enabled-controls \
    [--target-identifier <value>] \
    [--filter <value>] \
    [--include-children | --no-include-children] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-identifier` | No | string | None | The ARN of the organizational unit |
| `--filter` | No | structure | None | Filter by statuses, drift statuses, control identifiers |
| `--include-children` | No | boolean | false | Include controls from child OUs |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Structure:**
```json
{
    "controlIdentifiers": ["string"],
    "statuses": ["SUCCEEDED|FAILED|UNDER_CHANGE"],
    "driftStatuses": ["DRIFTED|IN_SYNC|NOT_CHECKING|UNKNOWN"],
    "parentIdentifiers": ["string"],
    "inheritanceDriftStatuses": ["DRIFTED|IN_SYNC|NOT_CHECKING|UNKNOWN"],
    "resourceDriftStatuses": ["DRIFTED|IN_SYNC|NOT_CHECKING|UNKNOWN"]
}
```

**Output Schema:**
```json
{
    "enabledControls": [
        {
            "arn": "string",
            "controlIdentifier": "string",
            "targetIdentifier": "string",
            "statusSummary": {
                "status": "SUCCEEDED|FAILED|UNDER_CHANGE",
                "lastOperationIdentifier": "string"
            },
            "driftStatusSummary": {
                "driftStatus": "DRIFTED|IN_SYNC|NOT_CHECKING|UNKNOWN",
                "types": {
                    "inheritance": {"status": "string"},
                    "resource": {"status": "string"}
                }
            },
            "parentIdentifier": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.5 `reset-enabled-control`

Resets an enabled control. This is an asynchronous operation.

**Synopsis:**
```bash
aws controltower reset-enabled-control \
    --enabled-control-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--enabled-control-identifier` | **Yes** | string | -- | The ARN of the enabled control to reset |

**Output Schema:**
```json
{
    "operationIdentifier": "string"
}
```

---

### 2.6 `get-control-operation`

Returns the status of a control operation.

**Synopsis:**
```bash
aws controltower get-control-operation \
    --operation-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--operation-identifier` | **Yes** | string | -- | The operation UUID (36 chars, valid for 90 days) |

**Output Schema:**
```json
{
    "controlOperation": {
        "operationType": "ENABLE_CONTROL|DISABLE_CONTROL|UPDATE_ENABLED_CONTROL|RESET_ENABLED_CONTROL",
        "startTime": "timestamp",
        "endTime": "timestamp",
        "status": "SUCCEEDED|FAILED|IN_PROGRESS",
        "statusMessage": "string",
        "operationIdentifier": "string",
        "controlIdentifier": "string",
        "targetIdentifier": "string",
        "enabledControlIdentifier": "string"
    }
}
```

---

### 2.7 `list-control-operations`

Lists control operations. **Paginated operation.**

**Synopsis:**
```bash
aws controltower list-control-operations \
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
| `--filter` | No | structure | None | Filter by operation types, statuses, control/target identifiers |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Structure:**
```json
{
    "controlOperationTypes": ["ENABLE_CONTROL|DISABLE_CONTROL|UPDATE_ENABLED_CONTROL|RESET_ENABLED_CONTROL"],
    "statuses": ["SUCCEEDED|FAILED|IN_PROGRESS"],
    "controlIdentifiers": ["string"],
    "targetIdentifiers": ["string"],
    "enabledControlIdentifiers": ["string"]
}
```

**Output Schema:**
```json
{
    "controlOperations": [
        {
            "operationType": "string",
            "startTime": "timestamp",
            "endTime": "timestamp",
            "status": "SUCCEEDED|FAILED|IN_PROGRESS",
            "statusMessage": "string",
            "operationIdentifier": "string",
            "controlIdentifier": "string",
            "targetIdentifier": "string",
            "enabledControlIdentifier": "string"
        }
    ],
    "nextToken": "string"
}
```
