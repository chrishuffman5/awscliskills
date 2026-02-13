# Rule Groups

### 3.1 `create-rule-group`

Creates a rule group for use in a firewall policy. Provide rules either as structured `--rule-group` JSON or as `--rules` in Suricata flat format.

**Synopsis:**
```bash
aws network-firewall create-rule-group \
    --rule-group-name <value> \
    --type <value> \
    --capacity <value> \
    [--rule-group <value>] \
    [--rules <value>] \
    [--description <value>] \
    [--tags <value>] \
    [--dry-run | --no-dry-run] \
    [--encryption-configuration <value>] \
    [--source-metadata <value>] \
    [--analyze-rule-group | --no-analyze-rule-group] \
    [--summary-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rule-group-name` | **Yes** | string | -- | Rule group name (1-128 chars, alphanumeric and hyphens) |
| `--type` | **Yes** | string | -- | Type: `STATELESS` or `STATEFUL` |
| `--capacity` | **Yes** | integer | -- | Maximum rule capacity (fixed at creation) |
| `--rule-group` | No | structure | None | Structured rule definitions (mutually exclusive with `--rules`) |
| `--rules` | No | string | None | Rules in Suricata flat format (mutually exclusive with `--rule-group`) |
| `--description` | No | string | None | Description (max 512 chars) |
| `--tags` | No | list | None | Tags (max 200) |
| `--dry-run` | No | boolean | false | Validate without creating |
| `--encryption-configuration` | No | structure | None | KMS encryption config |
| `--source-metadata` | No | structure | None | Source rule group metadata for copying |
| `--analyze-rule-group` | No | boolean | false | Analyze stateless rules for issues |
| `--summary-configuration` | No | structure | None | Rule options to show in summaries |

**Output Schema:**
```json
{
    "UpdateToken": "string",
    "RuleGroupResponse": {
        "RuleGroupArn": "string",
        "RuleGroupName": "string",
        "RuleGroupId": "string",
        "Description": "string",
        "Type": "STATELESS|STATEFUL",
        "Capacity": "integer",
        "RuleGroupStatus": "ACTIVE|DELETING|ERROR",
        "Tags": [],
        "ConsumedCapacity": "integer",
        "NumberOfAssociations": "integer",
        "EncryptionConfiguration": {},
        "SourceMetadata": {},
        "SnsTopic": "string",
        "LastModifiedTime": "timestamp",
        "AnalysisResults": [
            {
                "IdentifiedRuleIds": ["string"],
                "IdentifiedType": "string",
                "AnalysisDetail": "string"
            }
        ]
    }
}
```

---

### 3.2 `delete-rule-group`

Deletes the specified rule group. Must not be referenced by any firewall policies.

**Synopsis:**
```bash
aws network-firewall delete-rule-group \
    [--rule-group-name <value>] \
    [--rule-group-arn <value>] \
    [--type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rule-group-name` | No* | string | None | Rule group name |
| `--rule-group-arn` | No* | string | None | Rule group ARN |
| `--type` | No | string | None | Type: `STATELESS` or `STATEFUL` (required when using name) |

*Must specify either name or ARN.

**Output Schema:**
```json
{
    "RuleGroupResponse": {
        "RuleGroupArn": "string",
        "RuleGroupName": "string",
        "RuleGroupId": "string",
        "RuleGroupStatus": "DELETING"
    }
}
```

---

### 3.3 `describe-rule-group`

Returns the full details of the specified rule group including all rules.

**Synopsis:**
```bash
aws network-firewall describe-rule-group \
    [--rule-group-name <value>] \
    [--rule-group-arn <value>] \
    [--type <value>] \
    [--analyze-rule-group | --no-analyze-rule-group] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rule-group-name` | No* | string | None | Rule group name |
| `--rule-group-arn` | No* | string | None | Rule group ARN |
| `--type` | No | string | None | Type (required when using name) |
| `--analyze-rule-group` | No | boolean | false | Analyze rules |

**Output Schema:**
```json
{
    "UpdateToken": "string",
    "RuleGroup": {
        "RuleVariables": {
            "IPSets": {},
            "PortSets": {}
        },
        "ReferenceSets": {
            "IPSetReferences": {}
        },
        "RulesSource": {
            "RulesString": "string",
            "RulesSourceList": {
                "Targets": ["string"],
                "TargetTypes": ["TLS_SNI|HTTP_HOST"],
                "GeneratedRulesType": "ALLOWLIST|DENYLIST"
            },
            "StatefulRules": [],
            "StatelessRulesAndCustomActions": {}
        },
        "StatefulRuleOptions": {
            "RuleOrder": "DEFAULT_ACTION_ORDER|STRICT_ORDER"
        }
    },
    "RuleGroupResponse": {
        "RuleGroupArn": "string",
        "RuleGroupName": "string",
        "RuleGroupId": "string",
        "Type": "STATELESS|STATEFUL",
        "Capacity": "integer",
        "RuleGroupStatus": "ACTIVE|DELETING|ERROR",
        "ConsumedCapacity": "integer",
        "NumberOfAssociations": "integer",
        "LastModifiedTime": "timestamp"
    }
}
```

---

### 3.4 `describe-rule-group-metadata`

Returns metadata about a rule group without the full rule definitions.

**Synopsis:**
```bash
aws network-firewall describe-rule-group-metadata \
    [--rule-group-name <value>] \
    [--rule-group-arn <value>] \
    [--type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rule-group-name` | No* | string | None | Rule group name |
| `--rule-group-arn` | No* | string | None | Rule group ARN |
| `--type` | No | string | None | Type (required when using name) |

**Output Schema:**
```json
{
    "RuleGroupArn": "string",
    "RuleGroupName": "string",
    "Description": "string",
    "Type": "STATELESS|STATEFUL",
    "Capacity": "integer",
    "StatefulRuleOptions": {
        "RuleOrder": "DEFAULT_ACTION_ORDER|STRICT_ORDER"
    },
    "LastModifiedTime": "timestamp"
}
```

---

### 3.5 `list-rule-groups`

Lists all rule groups in the account. **Paginated operation.**

**Synopsis:**
```bash
aws network-firewall list-rule-groups \
    [--scope <value>] \
    [--managed-type <value>] \
    [--type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scope` | No | string | None | Filter: `MANAGED` or `ACCOUNT` |
| `--managed-type` | No | string | None | Filter managed rules: `AWS_MANAGED_THREAT_SIGNATURES` or `AWS_MANAGED_DOMAIN_LISTS` |
| `--type` | No | string | None | Filter by type: `STATELESS` or `STATEFUL` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "RuleGroups": [
        {
            "Name": "string",
            "Arn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.6 `update-rule-group`

Updates the specified rule group. Requires the update token for optimistic locking.

**Synopsis:**
```bash
aws network-firewall update-rule-group \
    --update-token <value> \
    [--rule-group-name <value>] \
    [--rule-group-arn <value>] \
    [--rule-group <value>] \
    [--rules <value>] \
    [--type <value>] \
    [--description <value>] \
    [--dry-run | --no-dry-run] \
    [--encryption-configuration <value>] \
    [--source-metadata <value>] \
    [--analyze-rule-group | --no-analyze-rule-group] \
    [--summary-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--update-token` | **Yes** | string | -- | Token from describe for optimistic locking |
| `--rule-group-name` | No* | string | None | Rule group name |
| `--rule-group-arn` | No* | string | None | Rule group ARN |
| `--rule-group` | No | structure | None | Updated structured rules |
| `--rules` | No | string | None | Updated Suricata format rules |
| `--type` | No | string | None | Type (required when using name) |
| `--description` | No | string | None | Updated description |
| `--dry-run` | No | boolean | false | Validate without updating |
| `--encryption-configuration` | No | structure | None | KMS encryption config |
| `--source-metadata` | No | structure | None | Source metadata |
| `--analyze-rule-group` | No | boolean | false | Analyze rules |
| `--summary-configuration` | No | structure | None | Summary config |

**Output Schema:**
```json
{
    "UpdateToken": "string",
    "RuleGroupResponse": {
        "RuleGroupArn": "string",
        "RuleGroupName": "string",
        "RuleGroupId": "string",
        "Type": "STATELESS|STATEFUL",
        "Capacity": "integer",
        "RuleGroupStatus": "ACTIVE|DELETING|ERROR",
        "ConsumedCapacity": "integer",
        "LastModifiedTime": "timestamp"
    }
}
```
