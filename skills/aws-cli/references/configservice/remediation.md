# Remediation

### 5.1 `put-remediation-configurations`

Creates or updates remediation configurations with automatic or manual remediation actions for noncompliant resources.

**Synopsis:**
```bash
aws configservice put-remediation-configurations \
    --remediation-configurations <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--remediation-configurations` | **Yes** | list | -- | List of remediation configurations |

**Remediation Configuration Structure:**
```json
{
    "ConfigRuleName": "string",
    "TargetType": "SSM_DOCUMENT",
    "TargetId": "string",
    "TargetVersion": "string",
    "Parameters": {
        "ParameterName": {
            "ResourceValue": {
                "Value": "RESOURCE_ID"
            },
            "StaticValue": {
                "Values": ["string"]
            }
        }
    },
    "ResourceType": "string",
    "Automatic": true|false,
    "ExecutionControls": {
        "SsmControls": {
            "ConcurrentExecutionRatePercentage": "integer",
            "ErrorPercentage": "integer"
        }
    },
    "MaximumAutomaticAttempts": "integer",
    "RetryAttemptSeconds": "integer",
    "Arn": "string",
    "CreatedByService": "string"
}
```

**Output Schema:**
```json
{
    "FailedBatches": [
        {
            "FailureMessage": "string",
            "FailedItems": []
        }
    ]
}
```

---

### 5.2 `delete-remediation-configuration`

Deletes the remediation configuration for a Config rule.

**Synopsis:**
```bash
aws configservice delete-remediation-configuration \
    --config-rule-name <value> \
    [--resource-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--config-rule-name` | **Yes** | string | -- | Name of the Config rule |
| `--resource-type` | No | string | None | Resource type for remediation (if scoped) |

**Output Schema:**
```json
{}
```

---

### 5.3 `describe-remediation-configurations`

Returns the details of one or more remediation configurations.

**Synopsis:**
```bash
aws configservice describe-remediation-configurations \
    --config-rule-names <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--config-rule-names` | **Yes** | list(string) | -- | Config rule names for which to get remediation configs |

**Output Schema:**
```json
{
    "RemediationConfigurations": [
        {
            "ConfigRuleName": "string",
            "TargetType": "SSM_DOCUMENT",
            "TargetId": "string",
            "TargetVersion": "string",
            "Parameters": {},
            "ResourceType": "string",
            "Automatic": true|false,
            "ExecutionControls": {
                "SsmControls": {
                    "ConcurrentExecutionRatePercentage": "integer",
                    "ErrorPercentage": "integer"
                }
            },
            "MaximumAutomaticAttempts": "integer",
            "RetryAttemptSeconds": "integer",
            "Arn": "string",
            "CreatedByService": "string"
        }
    ]
}
```

---

### 5.4 `put-remediation-exceptions`

Creates remediation exceptions for specific resources, exempting them from auto-remediation.

**Synopsis:**
```bash
aws configservice put-remediation-exceptions \
    --config-rule-name <value> \
    --resource-keys <value> \
    [--message <value>] \
    [--expiration-date <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--config-rule-name` | **Yes** | string | -- | Name of the Config rule |
| `--resource-keys` | **Yes** | list | -- | Resources to exempt. Shorthand: `ResourceType=string,ResourceId=string ...` |
| `--message` | No | string | None | Reason for the exception |
| `--expiration-date` | No | timestamp | None | When the exception expires |

**Output Schema:**
```json
{
    "FailedBatches": [
        {
            "FailureMessage": "string",
            "FailedItems": [
                {
                    "ConfigRuleName": "string",
                    "ResourceType": "string",
                    "ResourceId": "string",
                    "Message": "string",
                    "ExpirationDate": "timestamp"
                }
            ]
        }
    ]
}
```

---

### 5.5 `delete-remediation-exceptions`

Deletes one or more remediation exceptions for specific resources.

**Synopsis:**
```bash
aws configservice delete-remediation-exceptions \
    --config-rule-name <value> \
    --resource-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--config-rule-name` | **Yes** | string | -- | Name of the Config rule |
| `--resource-keys` | **Yes** | list | -- | Resources to remove exceptions for. Shorthand: `ResourceType=string,ResourceId=string ...` |

**Output Schema:**
```json
{
    "FailedBatches": [
        {
            "FailureMessage": "string",
            "FailedItems": []
        }
    ]
}
```

---

### 5.6 `describe-remediation-exceptions`

Returns the details of one or more remediation exceptions. **Paginated operation.**

**Synopsis:**
```bash
aws configservice describe-remediation-exceptions \
    --config-rule-name <value> \
    [--resource-keys <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--config-rule-name` | **Yes** | string | -- | Name of the Config rule |
| `--resource-keys` | No | list | None | Specific resources to query |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "RemediationExceptions": [
        {
            "ConfigRuleName": "string",
            "ResourceType": "string",
            "ResourceId": "string",
            "Message": "string",
            "ExpirationDate": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.7 `describe-remediation-execution-status`

Returns the status of remediation execution for a Config rule. **Paginated operation.**

**Synopsis:**
```bash
aws configservice describe-remediation-execution-status \
    --config-rule-name <value> \
    [--resource-keys <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--config-rule-name` | **Yes** | string | -- | Name of the Config rule |
| `--resource-keys` | No | list | None | Specific resources to query. Shorthand: `resourceType=string,resourceId=string ...` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "RemediationExecutionStatuses": [
        {
            "ResourceKey": {
                "resourceType": "string",
                "resourceId": "string"
            },
            "State": "QUEUED|IN_PROGRESS|SUCCEEDED|FAILED",
            "StepDetails": [
                {
                    "Name": "string",
                    "State": "SUCCEEDED|PENDING|FAILED",
                    "ErrorMessage": "string",
                    "StartTime": "timestamp",
                    "StopTime": "timestamp"
                }
            ],
            "InvocationTime": "timestamp",
            "LastUpdatedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.8 `start-remediation-execution`

Manually starts remediation execution for specified noncompliant resources.

**Synopsis:**
```bash
aws configservice start-remediation-execution \
    --config-rule-name <value> \
    --resource-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--config-rule-name` | **Yes** | string | -- | Name of the Config rule with remediation configured |
| `--resource-keys` | **Yes** | list | -- | Resources to remediate. Shorthand: `resourceType=string,resourceId=string ...` |

**Output Schema:**
```json
{
    "FailureMessage": "string",
    "FailedItems": [
        {
            "resourceType": "string",
            "resourceId": "string"
        }
    ]
}
```
