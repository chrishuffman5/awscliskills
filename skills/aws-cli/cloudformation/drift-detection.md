# Drift Detection

### 4.1 `detect-stack-drift`

Detects whether a stack's actual configuration differs (has drifted) from its expected configuration as defined in the stack template. Returns a detection ID to poll for results.

**Synopsis:**
```bash
aws cloudformation detect-stack-drift \
    --stack-name <value> \
    [--logical-resource-ids <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Stack name or ID |
| `--logical-resource-ids` | No | list(string) | None | Specific resources to check for drift. Omit to check all supported resources |

**Output Schema:**
```json
{
    "StackDriftDetectionId": "string"
}
```

---

### 4.2 `detect-stack-resource-drift`

Returns information about whether a resource's actual configuration differs from its expected configuration.

**Synopsis:**
```bash
aws cloudformation detect-stack-resource-drift \
    --stack-name <value> \
    --logical-resource-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Stack name or ID |
| `--logical-resource-id` | **Yes** | string | -- | Logical resource ID |

**Output Schema:**
```json
{
    "StackResourceDrift": {
        "StackId": "string",
        "LogicalResourceId": "string",
        "PhysicalResourceId": "string",
        "PhysicalResourceIdContext": [
            {
                "Key": "string",
                "Value": "string"
            }
        ],
        "ResourceType": "string",
        "ExpectedProperties": "string",
        "ActualProperties": "string",
        "PropertyDifferences": [
            {
                "PropertyPath": "string",
                "ExpectedValue": "string",
                "ActualValue": "string",
                "DifferenceType": "ADD|REMOVE|NOT_EQUAL"
            }
        ],
        "StackResourceDriftStatus": "IN_SYNC|MODIFIED|DELETED|NOT_CHECKED",
        "Timestamp": "timestamp",
        "ModuleInfo": {
            "TypeHierarchy": "string",
            "LogicalIdHierarchy": "string"
        }
    }
}
```

---

### 4.3 `detect-stack-set-drift`

Detect drift on a stack set. CloudFormation compares the current stack instance configurations with the expected configurations defined in the stack set template.

**Synopsis:**
```bash
aws cloudformation detect-stack-set-drift \
    --stack-set-name <value> \
    [--operation-preferences <value>] \
    [--operation-id <value>] \
    [--call-as <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-set-name` | **Yes** | string | -- | Stack set name or ID |
| `--operation-preferences` | No | structure | None | Operation preferences for drift detection |
| `--operation-id` | No | string | None | Custom operation ID |
| `--call-as` | No | string | `SELF` | `SELF` or `DELEGATED_ADMIN` |

**Output Schema:**
```json
{
    "OperationId": "string"
}
```

---

### 4.4 `describe-stack-drift-detection-status`

Returns information about a stack drift detection operation.

**Synopsis:**
```bash
aws cloudformation describe-stack-drift-detection-status \
    --stack-drift-detection-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-drift-detection-id` | **Yes** | string | -- | Drift detection ID from `detect-stack-drift` |

**Output Schema:**
```json
{
    "StackId": "string",
    "StackDriftDetectionId": "string",
    "StackDriftStatus": "DRIFTED|IN_SYNC|UNKNOWN|NOT_CHECKED",
    "DetectionStatus": "DETECTION_IN_PROGRESS|DETECTION_FAILED|DETECTION_COMPLETE",
    "DetectionStatusReason": "string",
    "DriftedStackResourceCount": "integer",
    "Timestamp": "timestamp"
}
```

---

### 4.5 `describe-stack-resource-drifts`

Returns drift information for resources in a stack. **Paginated operation.**

**Synopsis:**
```bash
aws cloudformation describe-stack-resource-drifts \
    --stack-name <value> \
    [--stack-resource-drift-status-filters <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Stack name or ID |
| `--stack-resource-drift-status-filters` | No | list(string) | None | Filter by drift status: `IN_SYNC`, `MODIFIED`, `DELETED`, `NOT_CHECKED` |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "StackResourceDrifts": [
        {
            "StackId": "string",
            "LogicalResourceId": "string",
            "PhysicalResourceId": "string",
            "PhysicalResourceIdContext": [
                {
                    "Key": "string",
                    "Value": "string"
                }
            ],
            "ResourceType": "string",
            "ExpectedProperties": "string",
            "ActualProperties": "string",
            "PropertyDifferences": [
                {
                    "PropertyPath": "string",
                    "ExpectedValue": "string",
                    "ActualValue": "string",
                    "DifferenceType": "ADD|REMOVE|NOT_EQUAL"
                }
            ],
            "StackResourceDriftStatus": "IN_SYNC|MODIFIED|DELETED|NOT_CHECKED",
            "Timestamp": "timestamp",
            "ModuleInfo": {
                "TypeHierarchy": "string",
                "LogicalIdHierarchy": "string"
            }
        }
    ],
    "NextToken": "string"
}
```
