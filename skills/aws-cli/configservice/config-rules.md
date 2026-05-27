# Config Rules

### 1.1 `put-config-rule`

Creates or updates an AWS Config rule for evaluating resource compliance.

**Synopsis:**
```bash
aws configservice put-config-rule \
    --config-rule <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--config-rule` | **Yes** | structure | -- | Config rule definition (JSON or shorthand) |
| `--tags` | No | list | None | Tags to apply to the rule |

**Config Rule Structure:**
```json
{
    "ConfigRuleName": "string",
    "Description": "string",
    "Scope": {
        "ComplianceResourceTypes": ["string"],
        "TagKey": "string",
        "TagValue": "string",
        "ComplianceResourceId": "string"
    },
    "Source": {
        "Owner": "AWS|CUSTOM_LAMBDA|CUSTOM_POLICY",
        "SourceIdentifier": "string",
        "SourceDetails": [
            {
                "EventSource": "aws.config",
                "MessageType": "ConfigurationItemChangeNotification|ConfigurationSnapshotDeliveryCompleted|ScheduledNotification|OversizedConfigurationItemChangeNotification",
                "MaximumExecutionFrequency": "One_Hour|Three_Hours|Six_Hours|Twelve_Hours|TwentyFour_Hours"
            }
        ],
        "CustomPolicyDetails": {
            "PolicyRuntime": "guard-2.x.x",
            "PolicyText": "string",
            "EnableDebugLogDelivery": true|false
        }
    },
    "InputParameters": "string",
    "MaximumExecutionFrequency": "One_Hour|Three_Hours|Six_Hours|Twelve_Hours|TwentyFour_Hours",
    "ConfigRuleState": "ACTIVE|DELETING|DELETING_RESULTS|EVALUATING",
    "EvaluationModes": [
        {
            "Mode": "DETECTIVE|PROACTIVE"
        }
    ]
}
```

**Output Schema:**
```json
{}
```

> Returns empty on success.

---

### 1.2 `delete-config-rule`

Deletes the specified Config rule and all of its evaluation results.

**Synopsis:**
```bash
aws configservice delete-config-rule \
    --config-rule-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--config-rule-name` | **Yes** | string | -- | Name of the Config rule to delete |

**Output Schema:**
```json
{}
```

---

### 1.3 `describe-config-rules`

Returns details about your Config rules. **Paginated operation.**

**Synopsis:**
```bash
aws configservice describe-config-rules \
    [--config-rule-names <value>] \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--config-rule-names` | No | list(string) | None | Specific rule names to describe |
| `--filters` | No | structure | None | Filter by evaluation mode or rule state |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ConfigRules": [
        {
            "ConfigRuleName": "string",
            "ConfigRuleArn": "string",
            "ConfigRuleId": "string",
            "Description": "string",
            "Scope": {
                "ComplianceResourceTypes": ["string"],
                "TagKey": "string",
                "TagValue": "string",
                "ComplianceResourceId": "string"
            },
            "Source": {
                "Owner": "AWS|CUSTOM_LAMBDA|CUSTOM_POLICY",
                "SourceIdentifier": "string",
                "SourceDetails": [],
                "CustomPolicyDetails": {}
            },
            "InputParameters": "string",
            "MaximumExecutionFrequency": "string",
            "ConfigRuleState": "ACTIVE|DELETING|DELETING_RESULTS|EVALUATING",
            "CreatedBy": "string",
            "EvaluationModes": []
        }
    ],
    "NextToken": "string"
}
```

---

### 1.4 `describe-compliance-by-config-rule`

Indicates whether each Config rule is compliant. **Paginated operation.**

**Synopsis:**
```bash
aws configservice describe-compliance-by-config-rule \
    [--config-rule-names <value>] \
    [--compliance-types <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--config-rule-names` | No | list(string) | None | Specific rule names |
| `--compliance-types` | No | list(string) | None | Filter: `COMPLIANT`, `NON_COMPLIANT`, `NOT_APPLICABLE`, `INSUFFICIENT_DATA` |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ComplianceByConfigRules": [
        {
            "ConfigRuleName": "string",
            "Compliance": {
                "ComplianceType": "COMPLIANT|NON_COMPLIANT|NOT_APPLICABLE|INSUFFICIENT_DATA",
                "ComplianceContributorCount": {
                    "CappedCount": "integer",
                    "CapExceeded": true|false
                }
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `describe-compliance-by-resource`

Indicates whether a resource is compliant with the Config rules that evaluate it. **Paginated operation.**

**Synopsis:**
```bash
aws configservice describe-compliance-by-resource \
    [--resource-type <value>] \
    [--resource-id <value>] \
    [--compliance-types <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-type` | No | string | None | AWS resource type (e.g., `AWS::EC2::Instance`) |
| `--resource-id` | No | string | None | ID of the resource |
| `--compliance-types` | No | list(string) | None | Filter: `COMPLIANT`, `NON_COMPLIANT`, `NOT_APPLICABLE`, `INSUFFICIENT_DATA` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ComplianceByResources": [
        {
            "ResourceType": "string",
            "ResourceId": "string",
            "Compliance": {
                "ComplianceType": "COMPLIANT|NON_COMPLIANT|NOT_APPLICABLE|INSUFFICIENT_DATA",
                "ComplianceContributorCount": {
                    "CappedCount": "integer",
                    "CapExceeded": true|false
                }
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 1.6 `get-compliance-details-by-config-rule`

Returns evaluation results for a specific Config rule. **Paginated operation.**

**Synopsis:**
```bash
aws configservice get-compliance-details-by-config-rule \
    --config-rule-name <value> \
    [--compliance-types <value>] \
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
| `--compliance-types` | No | list(string) | None | Filter by compliance type |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "EvaluationResults": [
        {
            "EvaluationResultIdentifier": {
                "EvaluationResultQualifier": {
                    "ConfigRuleName": "string",
                    "ResourceType": "string",
                    "ResourceId": "string",
                    "EvaluationMode": "DETECTIVE|PROACTIVE"
                },
                "OrderingTimestamp": "timestamp",
                "ResourceEvaluationId": "string"
            },
            "ComplianceType": "COMPLIANT|NON_COMPLIANT|NOT_APPLICABLE|INSUFFICIENT_DATA",
            "ResultRecordedTime": "timestamp",
            "ConfigRuleInvokedTime": "timestamp",
            "Annotation": "string",
            "ResultToken": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.7 `get-compliance-details-by-resource`

Returns evaluation results for a specific resource. **Paginated operation.**

**Synopsis:**
```bash
aws configservice get-compliance-details-by-resource \
    [--resource-type <value>] \
    [--resource-id <value>] \
    [--compliance-types <value>] \
    [--resource-evaluation-id <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-type` | No | string | None | AWS resource type |
| `--resource-id` | No | string | None | ID of the resource |
| `--compliance-types` | No | list(string) | None | Filter by compliance type |
| `--resource-evaluation-id` | No | string | None | Resource evaluation ID |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "EvaluationResults": [
        {
            "EvaluationResultIdentifier": {
                "EvaluationResultQualifier": {
                    "ConfigRuleName": "string",
                    "ResourceType": "string",
                    "ResourceId": "string",
                    "EvaluationMode": "DETECTIVE|PROACTIVE"
                },
                "OrderingTimestamp": "timestamp",
                "ResourceEvaluationId": "string"
            },
            "ComplianceType": "COMPLIANT|NON_COMPLIANT|NOT_APPLICABLE|INSUFFICIENT_DATA",
            "ResultRecordedTime": "timestamp",
            "ConfigRuleInvokedTime": "timestamp",
            "Annotation": "string",
            "ResultToken": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.8 `get-compliance-summary-by-config-rule`

Returns the number of Config rules that are compliant and noncompliant.

**Synopsis:**
```bash
aws configservice get-compliance-summary-by-config-rule \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| _(none)_ | -- | -- | -- | No parameters beyond global options |

**Output Schema:**
```json
{
    "ComplianceSummary": {
        "CompliantResourceCount": {
            "CappedCount": "integer",
            "CapExceeded": true|false
        },
        "NonCompliantResourceCount": {
            "CappedCount": "integer",
            "CapExceeded": true|false
        },
        "ComplianceSummaryTimestamp": "timestamp"
    }
}
```

---

### 1.9 `get-compliance-summary-by-resource-type`

Returns the number of resources that are compliant and noncompliant, grouped by resource type.

**Synopsis:**
```bash
aws configservice get-compliance-summary-by-resource-type \
    [--resource-types <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-types` | No | list(string) | None | Resource types to include (e.g., `AWS::EC2::Instance`) |

**Output Schema:**
```json
{
    "ComplianceSummariesByResourceType": [
        {
            "ResourceType": "string",
            "ComplianceSummary": {
                "CompliantResourceCount": {
                    "CappedCount": "integer",
                    "CapExceeded": true|false
                },
                "NonCompliantResourceCount": {
                    "CappedCount": "integer",
                    "CapExceeded": true|false
                },
                "ComplianceSummaryTimestamp": "timestamp"
            }
        }
    ]
}
```

---

### 1.10 `describe-config-rule-evaluation-status`

Returns status information for each Config rule including last evaluation time, last success/failure, and number of resources evaluated. **Paginated operation.**

**Synopsis:**
```bash
aws configservice describe-config-rule-evaluation-status \
    [--config-rule-names <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--config-rule-names` | No | list(string) | None | Specific rule names |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ConfigRulesEvaluationStatus": [
        {
            "ConfigRuleName": "string",
            "ConfigRuleArn": "string",
            "ConfigRuleId": "string",
            "LastSuccessfulInvocationTime": "timestamp",
            "LastFailedInvocationTime": "timestamp",
            "LastSuccessfulEvaluationTime": "timestamp",
            "LastFailedEvaluationTime": "timestamp",
            "FirstActivatedTime": "timestamp",
            "LastDeactivatedTime": "timestamp",
            "LastErrorCode": "string",
            "LastErrorMessage": "string",
            "FirstEvaluationStarted": true|false
        }
    ],
    "NextToken": "string"
}
```

---

### 1.11 `start-config-rules-evaluation`

Runs an on-demand evaluation for the specified Config rules against the last known configuration state.

**Synopsis:**
```bash
aws configservice start-config-rules-evaluation \
    --config-rule-names <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--config-rule-names` | **Yes** | list(string) | -- | Config rule names to evaluate (up to 25) |

**Output Schema:**
```json
{}
```

---

### 1.12 `delete-evaluation-results`

Deletes the evaluation results for the specified Config rule. Use this to force a re-evaluation.

**Synopsis:**
```bash
aws configservice delete-evaluation-results \
    --config-rule-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--config-rule-name` | **Yes** | string | -- | Name of the Config rule |

**Output Schema:**
```json
{}
```

---

### 1.13 `get-custom-rule-policy`

Returns the policy definition for a custom Config rule that uses Guard policy language.

**Synopsis:**
```bash
aws configservice get-custom-rule-policy \
    [--config-rule-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--config-rule-name` | No | string | None | Name of the custom policy Config rule |

**Output Schema:**
```json
{
    "PolicyText": "string"
}
```
