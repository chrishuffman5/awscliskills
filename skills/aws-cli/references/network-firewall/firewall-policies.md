# Firewall Policies

### 2.1 `create-firewall-policy`

Creates a firewall policy defining stateless and stateful rule groups and default actions.

**Synopsis:**
```bash
aws network-firewall create-firewall-policy \
    --firewall-policy-name <value> \
    --firewall-policy <value> \
    [--description <value>] \
    [--tags <value>] \
    [--dry-run | --no-dry-run] \
    [--encryption-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-policy-name` | **Yes** | string | -- | Policy name (1-128 chars, alphanumeric and hyphens) |
| `--firewall-policy` | **Yes** | structure | -- | Policy definition with rule groups and actions |
| `--description` | No | string | None | Description (max 512 chars) |
| `--tags` | No | list | None | Tags (max 200) |
| `--dry-run` | No | boolean | false | Validate without creating |
| `--encryption-configuration` | No | structure | None | KMS encryption config |

**Firewall Policy Structure:**
```json
{
    "StatelessRuleGroupReferences": [
        {
            "ResourceArn": "string",
            "Priority": "integer (1-65535)"
        }
    ],
    "StatelessDefaultActions": ["aws:pass|aws:drop|aws:forward_to_sfe"],
    "StatelessFragmentDefaultActions": ["aws:pass|aws:drop|aws:forward_to_sfe"],
    "StatelessCustomActions": [
        {
            "ActionName": "string",
            "ActionDefinition": {
                "PublishMetricAction": {
                    "Dimensions": [{"Value": "string"}]
                }
            }
        }
    ],
    "StatefulRuleGroupReferences": [
        {
            "ResourceArn": "string",
            "Priority": "integer (1-65535)",
            "Override": {
                "Action": "DROP_TO_ALERT"
            }
        }
    ],
    "StatefulDefaultActions": ["aws:drop_strict|aws:drop_established|aws:alert_strict|aws:alert_established"],
    "StatefulEngineOptions": {
        "RuleOrder": "DEFAULT_ACTION_ORDER|STRICT_ORDER",
        "StreamExceptionPolicy": "DROP|CONTINUE|REJECT",
        "FlowTimeouts": {
            "TcpIdleTimeoutSeconds": "integer (60-6000)"
        }
    },
    "TLSInspectionConfigurationArn": "string",
    "PolicyVariables": {
        "RuleVariables": {
            "key": {
                "Definition": ["string"]
            }
        }
    }
}
```

**Output Schema:**
```json
{
    "UpdateToken": "string",
    "FirewallPolicyResponse": {
        "FirewallPolicyName": "string",
        "FirewallPolicyArn": "string",
        "FirewallPolicyId": "string",
        "Description": "string",
        "FirewallPolicyStatus": "ACTIVE|DELETING|ERROR",
        "Tags": [],
        "ConsumedStatelessRuleCapacity": "integer",
        "ConsumedStatefulRuleCapacity": "integer",
        "NumberOfAssociations": "integer",
        "EncryptionConfiguration": {},
        "LastModifiedTime": "timestamp"
    }
}
```

---

### 2.2 `delete-firewall-policy`

Deletes the specified firewall policy. Must not be associated with any firewalls.

**Synopsis:**
```bash
aws network-firewall delete-firewall-policy \
    [--firewall-policy-name <value>] \
    [--firewall-policy-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-policy-name` | No* | string | None | Policy name |
| `--firewall-policy-arn` | No* | string | None | Policy ARN |

*Must specify either name or ARN.

**Output Schema:**
```json
{
    "FirewallPolicyResponse": {
        "FirewallPolicyName": "string",
        "FirewallPolicyArn": "string",
        "FirewallPolicyId": "string",
        "FirewallPolicyStatus": "DELETING"
    }
}
```

---

### 2.3 `describe-firewall-policy`

Returns the full details of the specified firewall policy.

**Synopsis:**
```bash
aws network-firewall describe-firewall-policy \
    [--firewall-policy-name <value>] \
    [--firewall-policy-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-policy-name` | No* | string | None | Policy name |
| `--firewall-policy-arn` | No* | string | None | Policy ARN |

**Output Schema:**
```json
{
    "UpdateToken": "string",
    "FirewallPolicyResponse": {
        "FirewallPolicyName": "string",
        "FirewallPolicyArn": "string",
        "FirewallPolicyId": "string",
        "Description": "string",
        "FirewallPolicyStatus": "ACTIVE|DELETING|ERROR",
        "Tags": [],
        "ConsumedStatelessRuleCapacity": "integer",
        "ConsumedStatefulRuleCapacity": "integer",
        "NumberOfAssociations": "integer",
        "EncryptionConfiguration": {},
        "LastModifiedTime": "timestamp"
    },
    "FirewallPolicy": {
        "StatelessRuleGroupReferences": [],
        "StatelessDefaultActions": [],
        "StatelessFragmentDefaultActions": [],
        "StatelessCustomActions": [],
        "StatefulRuleGroupReferences": [],
        "StatefulDefaultActions": [],
        "StatefulEngineOptions": {},
        "TLSInspectionConfigurationArn": "string",
        "PolicyVariables": {}
    }
}
```

---

### 2.4 `list-firewall-policies`

Lists all firewall policies in the account. **Paginated operation.**

**Synopsis:**
```bash
aws network-firewall list-firewall-policies \
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
    "FirewallPolicies": [
        {
            "Name": "string",
            "Arn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.5 `update-firewall-policy`

Updates the specified firewall policy. Requires the update token from describe for optimistic locking.

**Synopsis:**
```bash
aws network-firewall update-firewall-policy \
    --update-token <value> \
    [--firewall-policy-name <value>] \
    [--firewall-policy-arn <value>] \
    --firewall-policy <value> \
    [--description <value>] \
    [--dry-run | --no-dry-run] \
    [--encryption-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--update-token` | **Yes** | string | -- | Token from describe for optimistic locking |
| `--firewall-policy-name` | No* | string | None | Policy name |
| `--firewall-policy-arn` | No* | string | None | Policy ARN |
| `--firewall-policy` | **Yes** | structure | -- | Updated policy definition |
| `--description` | No | string | None | Updated description |
| `--dry-run` | No | boolean | false | Validate without updating |
| `--encryption-configuration` | No | structure | None | KMS encryption config |

**Output Schema:**
```json
{
    "UpdateToken": "string",
    "FirewallPolicyResponse": {
        "FirewallPolicyName": "string",
        "FirewallPolicyArn": "string",
        "FirewallPolicyId": "string",
        "Description": "string",
        "FirewallPolicyStatus": "ACTIVE|DELETING|ERROR",
        "LastModifiedTime": "timestamp"
    }
}
```
