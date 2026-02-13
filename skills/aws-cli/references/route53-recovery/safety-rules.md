# Safety Rules

Commands for managing Route 53 ARC safety rules via `aws route53-recovery-control-config`. Safety rules prevent dangerous routing control state changes that could cause fail-open scenarios.

### 4.1 `create-safety-rule`

Creates a safety rule. Provide either an assertion rule or a gating rule (mutually exclusive).

**Synopsis:**
```bash
aws route53-recovery-control-config create-safety-rule \
    [--assertion-rule <value>] \
    [--gating-rule <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assertion-rule` | No* | structure | None | Assertion rule configuration (see below) |
| `--gating-rule` | No* | structure | None | Gating rule configuration (see below) |
| `--client-token` | No | string | None | Idempotency token (1-64 chars) |
| `--tags` | No | map | None | Tags as key-value pairs |

*Either `--assertion-rule` or `--gating-rule` must be provided.

**Assertion Rule Structure (JSON):**
```json
{
    "AssertedControls": ["routing-control-arn", "..."],
    "ControlPanelArn": "string",
    "Name": "string",
    "RuleConfig": {
        "Type": "ATLEAST|AND|OR",
        "Threshold": "integer",
        "Inverted": true|false
    },
    "WaitPeriodMs": "integer"
}
```

**Gating Rule Structure (JSON):**
```json
{
    "ControlPanelArn": "string",
    "GatingControls": ["routing-control-arn", "..."],
    "TargetControls": ["routing-control-arn", "..."],
    "Name": "string",
    "RuleConfig": {
        "Type": "ATLEAST|AND|OR",
        "Threshold": "integer",
        "Inverted": true|false
    },
    "WaitPeriodMs": "integer"
}
```

**RuleConfig Fields:**

| Field | Type | Description |
|-------|------|-------------|
| `Type` | string | Rule type: `ATLEAST` (at least N), `AND` (all), `OR` (at least one) |
| `Threshold` | integer | Number of controls that must match (used with ATLEAST) |
| `Inverted` | boolean | If true, logically negates the rule evaluation |

**Output Schema:**
```json
{
    "AssertionRule": {
        "AssertedControls": ["string"],
        "ControlPanelArn": "string",
        "Name": "string",
        "RuleConfig": {
            "Type": "ATLEAST|AND|OR",
            "Threshold": "integer",
            "Inverted": "boolean"
        },
        "SafetyRuleArn": "string",
        "Status": "PENDING|DEPLOYED|PENDING_DELETION",
        "WaitPeriodMs": "integer",
        "Owner": "string"
    },
    "GatingRule": {
        "ControlPanelArn": "string",
        "GatingControls": ["string"],
        "TargetControls": ["string"],
        "Name": "string",
        "RuleConfig": {
            "Type": "ATLEAST|AND|OR",
            "Threshold": "integer",
            "Inverted": "boolean"
        },
        "SafetyRuleArn": "string",
        "Status": "PENDING|DEPLOYED|PENDING_DELETION",
        "WaitPeriodMs": "integer",
        "Owner": "string"
    }
}
```

Response contains either `AssertionRule` or `GatingRule` depending on which was created.

---

### 4.2 `delete-safety-rule`

Deletes a safety rule.

**Synopsis:**
```bash
aws route53-recovery-control-config delete-safety-rule \
    --safety-rule-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--safety-rule-arn` | **Yes** | string | -- | ARN of the safety rule to delete |

**Output:** None on success.

---

### 4.3 `describe-safety-rule`

Gets details about a safety rule.

**Synopsis:**
```bash
aws route53-recovery-control-config describe-safety-rule \
    --safety-rule-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--safety-rule-arn` | **Yes** | string | -- | ARN of the safety rule |

**Output Schema:**
```json
{
    "AssertionRule": {
        "AssertedControls": ["string"],
        "ControlPanelArn": "string",
        "Name": "string",
        "RuleConfig": {
            "Type": "ATLEAST|AND|OR",
            "Threshold": "integer",
            "Inverted": "boolean"
        },
        "SafetyRuleArn": "string",
        "Status": "PENDING|DEPLOYED|PENDING_DELETION",
        "WaitPeriodMs": "integer",
        "Owner": "string"
    },
    "GatingRule": {
        "ControlPanelArn": "string",
        "GatingControls": ["string"],
        "TargetControls": ["string"],
        "Name": "string",
        "RuleConfig": {
            "Type": "ATLEAST|AND|OR",
            "Threshold": "integer",
            "Inverted": "boolean"
        },
        "SafetyRuleArn": "string",
        "Status": "PENDING|DEPLOYED|PENDING_DELETION",
        "WaitPeriodMs": "integer",
        "Owner": "string"
    }
}
```

Response contains either `AssertionRule` or `GatingRule` depending on the rule type.

---

### 4.4 `update-safety-rule`

Updates a safety rule. Only the name and wait period can be updated. To change other fields, delete and recreate the rule.

**Synopsis:**
```bash
aws route53-recovery-control-config update-safety-rule \
    [--assertion-rule-update <value>] \
    [--gating-rule-update <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assertion-rule-update` | No* | structure | None | Assertion rule update |
| `--gating-rule-update` | No* | structure | None | Gating rule update |

*Provide one of the two.

**Assertion Rule Update Structure:**
```json
{
    "Name": "string",
    "SafetyRuleArn": "string",
    "WaitPeriodMs": "integer"
}
```

**Gating Rule Update Structure:**
```json
{
    "Name": "string",
    "SafetyRuleArn": "string",
    "WaitPeriodMs": "integer"
}
```

**Output Schema:** Same as `describe-safety-rule`.

---

### 4.5 `list-safety-rules`

Lists safety rules for a control panel. **Paginated operation.**

**Synopsis:**
```bash
aws route53-recovery-control-config list-safety-rules \
    --control-panel-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--control-panel-arn` | **Yes** | string | -- | ARN of the control panel |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "SafetyRules": [
        {
            "ASSERTION": {
                "AssertedControls": ["string"],
                "ControlPanelArn": "string",
                "Name": "string",
                "RuleConfig": {
                    "Type": "ATLEAST|AND|OR",
                    "Threshold": "integer",
                    "Inverted": "boolean"
                },
                "SafetyRuleArn": "string",
                "Status": "PENDING|DEPLOYED|PENDING_DELETION",
                "WaitPeriodMs": "integer",
                "Owner": "string"
            },
            "GATING": {
                "ControlPanelArn": "string",
                "GatingControls": ["string"],
                "TargetControls": ["string"],
                "Name": "string",
                "RuleConfig": {
                    "Type": "ATLEAST|AND|OR",
                    "Threshold": "integer",
                    "Inverted": "boolean"
                },
                "SafetyRuleArn": "string",
                "Status": "PENDING|DEPLOYED|PENDING_DELETION",
                "WaitPeriodMs": "integer",
                "Owner": "string"
            }
        }
    ],
    "NextToken": "string"
}
```

Each entry in `SafetyRules` contains either an `ASSERTION` or `GATING` key.
