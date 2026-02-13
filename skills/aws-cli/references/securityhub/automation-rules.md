# Automation Rules

### 6.1 `create-automation-rule`

Creates an automation rule that automatically updates or suppresses findings.

**Synopsis:**
```bash
aws securityhub create-automation-rule \
    --rule-name <value> \
    --rule-order <value> \
    --rule-status <value> \
    --criteria <value> \
    --actions <value> \
    [--description <value>] \
    [--is-terminal | --no-is-terminal] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rule-name` | **Yes** | string | -- | Name of the automation rule |
| `--rule-order` | **Yes** | integer | -- | Processing order (1-1000) |
| `--rule-status` | **Yes** | string | -- | Status: `ENABLED` or `DISABLED` |
| `--criteria` | **Yes** | structure | -- | Criteria for matching findings |
| `--actions` | **Yes** | list | -- | Actions to perform on matching findings |
| `--description` | No | string | None | Rule description |
| `--is-terminal` | No | boolean | None | Whether to stop processing further rules |
| `--tags` | No | map | None | Tags (max 50) |

**Actions Structure:**
```json
[
    {
        "Type": "FINDING_FIELDS_UPDATE",
        "FindingFieldsUpdate": {
            "Note": {
                "Text": "string",
                "UpdatedBy": "string"
            },
            "Severity": {
                "Normalized": "integer",
                "Product": "double",
                "Label": "INFORMATIONAL|LOW|MEDIUM|HIGH|CRITICAL"
            },
            "VerificationState": "UNKNOWN|TRUE_POSITIVE|FALSE_POSITIVE|BENIGN_POSITIVE",
            "Confidence": "integer",
            "Criticality": "integer",
            "Types": ["string"],
            "UserDefinedFields": {"string": "string"},
            "Workflow": {
                "Status": "NEW|NOTIFIED|RESOLVED|SUPPRESSED"
            },
            "RelatedFindings": [
                {
                    "ProductArn": "string",
                    "Id": "string"
                }
            ]
        }
    }
]
```

**Output Schema:**
```json
{
    "RuleArn": "string"
}
```

---

### 6.2 `list-automation-rules`

Lists automation rules and their metadata. **Paginated operation.**

**Synopsis:**
```bash
aws securityhub list-automation-rules \
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
    "AutomationRulesMetadata": [
        {
            "RuleArn": "string",
            "RuleStatus": "ENABLED|DISABLED",
            "RuleOrder": "integer",
            "RuleName": "string",
            "Description": "string",
            "IsTerminal": "boolean",
            "CreatedAt": "timestamp",
            "UpdatedAt": "timestamp",
            "CreatedBy": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.3 `batch-get-automation-rules`

Returns details about one or more automation rules.

**Synopsis:**
```bash
aws securityhub batch-get-automation-rules \
    --automation-rules-arns <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--automation-rules-arns` | **Yes** | list(string) | -- | ARNs of automation rules to retrieve |

**Output Schema:**
```json
{
    "Rules": [
        {
            "RuleArn": "string",
            "RuleStatus": "ENABLED|DISABLED",
            "RuleOrder": "integer",
            "RuleName": "string",
            "Description": "string",
            "IsTerminal": "boolean",
            "Criteria": {},
            "Actions": [],
            "CreatedAt": "timestamp",
            "UpdatedAt": "timestamp",
            "CreatedBy": "string"
        }
    ],
    "UnprocessedAutomationRules": [
        {
            "RuleArn": "string",
            "ErrorCode": "integer",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 6.4 `batch-update-automation-rules`

Updates one or more automation rules.

**Synopsis:**
```bash
aws securityhub batch-update-automation-rules \
    --update-automation-rules-request-items <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--update-automation-rules-request-items` | **Yes** | list | -- | Automation rule updates to apply |

**Update Structure:**
```json
[
    {
        "RuleArn": "string",
        "RuleStatus": "ENABLED|DISABLED",
        "RuleOrder": "integer",
        "Description": "string",
        "RuleName": "string",
        "IsTerminal": "boolean",
        "Criteria": {},
        "Actions": []
    }
]
```

**Output Schema:**
```json
{
    "ProcessedAutomationRules": ["string"],
    "UnprocessedAutomationRules": [
        {
            "RuleArn": "string",
            "ErrorCode": "integer",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 6.5 `batch-delete-automation-rules`

Deletes one or more automation rules.

**Synopsis:**
```bash
aws securityhub batch-delete-automation-rules \
    --automation-rules-arns <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--automation-rules-arns` | **Yes** | list(string) | -- | ARNs of automation rules to delete |

**Output Schema:**
```json
{
    "ProcessedAutomationRules": ["string"],
    "UnprocessedAutomationRules": [
        {
            "RuleArn": "string",
            "ErrorCode": "integer",
            "ErrorMessage": "string"
        }
    ]
}
```
