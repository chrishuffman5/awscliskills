# Standards

### 4.1 `describe-standards`

Returns a list of available security standards. **Paginated operation.**

**Synopsis:**
```bash
aws securityhub describe-standards \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Standards": [
        {
            "StandardsArn": "string",
            "Name": "string",
            "Description": "string",
            "EnabledByDefault": "boolean",
            "StandardsManagedBy": {
                "Company": "string",
                "Product": "string"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 4.2 `batch-enable-standards`

Enables the security standards specified by the standards ARNs.

**Synopsis:**
```bash
aws securityhub batch-enable-standards \
    --standards-subscription-requests <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--standards-subscription-requests` | **Yes** | list | -- | Standards to enable (max 25) |

**Request Structure:**
```json
[
    {
        "StandardsArn": "string",
        "StandardsInput": {
            "string": "string"
        }
    }
]
```

**Output Schema:**
```json
{
    "StandardsSubscriptions": [
        {
            "StandardsSubscriptionArn": "string",
            "StandardsArn": "string",
            "StandardsInput": {"string": "string"},
            "StandardsStatus": "PENDING|READY|INCOMPLETE|DELETING|FAILED",
            "StandardsStatusReason": {
                "StatusReasonCode": "NO_AVAILABLE_CONFIGURATION_RECORDER|INTERNAL_ERROR"
            }
        }
    ]
}
```

---

### 4.3 `batch-disable-standards`

Disables the security standards specified by the standards subscription ARNs.

**Synopsis:**
```bash
aws securityhub batch-disable-standards \
    --standards-subscription-arns <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--standards-subscription-arns` | **Yes** | list(string) | -- | Standards subscription ARNs to disable (max 25) |

**Output Schema:**
```json
{
    "StandardsSubscriptions": [
        {
            "StandardsSubscriptionArn": "string",
            "StandardsArn": "string",
            "StandardsInput": {"string": "string"},
            "StandardsStatus": "PENDING|READY|INCOMPLETE|DELETING|FAILED"
        }
    ]
}
```

---

### 4.4 `get-enabled-standards`

Returns a list of the standards currently enabled. **Paginated operation.**

**Synopsis:**
```bash
aws securityhub get-enabled-standards \
    [--standards-subscription-arns <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--standards-subscription-arns` | No | list(string) | None | Specific subscription ARNs (omit for all) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "StandardsSubscriptions": [
        {
            "StandardsSubscriptionArn": "string",
            "StandardsArn": "string",
            "StandardsInput": {"string": "string"},
            "StandardsStatus": "PENDING|READY|INCOMPLETE|DELETING|FAILED",
            "StandardsStatusReason": {
                "StatusReasonCode": "string"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 4.5 `describe-standards-controls`

Returns a list of security standards controls. **Paginated operation.**

**Synopsis:**
```bash
aws securityhub describe-standards-controls \
    --standards-subscription-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--standards-subscription-arn` | **Yes** | string | -- | ARN of the standards subscription |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Controls": [
        {
            "StandardsControlArn": "string",
            "ControlStatus": "ENABLED|DISABLED",
            "DisabledReason": "string",
            "ControlStatusUpdatedAt": "timestamp",
            "ControlId": "string",
            "Title": "string",
            "Description": "string",
            "RemediationUrl": "string",
            "SeverityRating": "LOW|MEDIUM|HIGH|CRITICAL",
            "RelatedRequirements": ["string"]
        }
    ],
    "NextToken": "string"
}
```

---

### 4.6 `update-standards-control`

Updates the status of a standards control (enable/disable).

**Synopsis:**
```bash
aws securityhub update-standards-control \
    --standards-control-arn <value> \
    [--control-status <value>] \
    [--disabled-reason <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--standards-control-arn` | **Yes** | string | -- | ARN of the standards control |
| `--control-status` | No | string | None | Status: `ENABLED` or `DISABLED` |
| `--disabled-reason` | No | string | None | Reason for disabling the control |

**Output:** None (HTTP 200 on success)

---

### 4.7 `batch-get-standards-control-associations`

Returns associations between security controls and standards.

**Synopsis:**
```bash
aws securityhub batch-get-standards-control-associations \
    --standards-control-association-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--standards-control-association-ids` | **Yes** | list | -- | Association identifiers to retrieve |

**Output Schema:**
```json
{
    "StandardsControlAssociationDetails": [
        {
            "StandardsArn": "string",
            "SecurityControlId": "string",
            "SecurityControlArn": "string",
            "AssociationStatus": "ENABLED|DISABLED",
            "RelatedRequirements": ["string"],
            "UpdatedAt": "timestamp",
            "UpdatedReason": "string",
            "StandardsControlTitle": "string",
            "StandardsControlDescription": "string",
            "StandardsControlArns": ["string"]
        }
    ],
    "UnprocessedAssociations": [
        {
            "StandardsControlAssociationId": {},
            "ErrorCode": "string",
            "ErrorReason": "string"
        }
    ]
}
```

---

### 4.8 `batch-update-standards-control-associations`

Updates the enablement status of security controls in a batch.

**Synopsis:**
```bash
aws securityhub batch-update-standards-control-associations \
    --standards-control-association-updates <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--standards-control-association-updates` | **Yes** | list | -- | Association updates to apply |

**Update Structure:**
```json
[
    {
        "StandardsArn": "string",
        "SecurityControlId": "string",
        "AssociationStatus": "ENABLED|DISABLED",
        "UpdatedReason": "string"
    }
]
```

**Output Schema:**
```json
{
    "UnprocessedAssociationUpdates": [
        {
            "StandardsControlAssociationUpdate": {},
            "ErrorCode": "string",
            "ErrorReason": "string"
        }
    ]
}
```

---

### 4.9 `list-standards-control-associations`

Lists the associations between security controls and standards. **Paginated operation.**

**Synopsis:**
```bash
aws securityhub list-standards-control-associations \
    --security-control-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--security-control-id` | **Yes** | string | -- | Security control ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "StandardsControlAssociationSummaries": [
        {
            "StandardsArn": "string",
            "SecurityControlId": "string",
            "SecurityControlArn": "string",
            "AssociationStatus": "ENABLED|DISABLED",
            "RelatedRequirements": ["string"],
            "UpdatedAt": "timestamp",
            "UpdatedReason": "string",
            "StandardsControlTitle": "string",
            "StandardsControlDescription": "string"
        }
    ],
    "NextToken": "string"
}
```
