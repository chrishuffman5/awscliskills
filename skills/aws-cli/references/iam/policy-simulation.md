# Policy Simulation

### 20.1 `simulate-principal-policy`

Simulates the effect of all policies associated with a principal on specified API operations. **Paginated.**

**Synopsis:**
```bash
aws iam simulate-principal-policy \
    --policy-source-arn <value> \
    --action-names <value> \
    [--policy-input-list <value>] \
    [--permissions-boundary-policy-input-list <value>] \
    [--resource-arns <value>] \
    [--resource-policy <value>] \
    [--resource-owner <value>] \
    [--caller-arn <value>] \
    [--context-entries <value>] \
    [--resource-handling-option <value>] \
    [--starting-token <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-source-arn` | **Yes** | string | -- | ARN of user, group, or role whose policies to simulate |
| `--action-names` | **Yes** | list(string) | -- | API actions (e.g., `iam:CreateUser`, `s3:GetObject`) |
| `--policy-input-list` | No | list(string) | None | Additional policy documents to include |
| `--resource-arns` | No | list(string) | `*` | Resource ARNs for the simulation |
| `--resource-policy` | No | string | None | Resource-based policy JSON |
| `--caller-arn` | No | string | None | ARN of simulated caller |
| `--context-entries` | No | list | None | Context keys for conditions |

**Output Schema:**
```json
{
    "EvaluationResults": [
        {
            "EvalActionName": "string",
            "EvalResourceName": "string",
            "EvalDecision": "allowed|explicitDeny|implicitDeny",
            "MatchedStatements": [
                {
                    "SourcePolicyId": "string",
                    "SourcePolicyType": "user|group|role|aws-managed|user-managed|resource|none"
                }
            ],
            "MissingContextValues": ["string"],
            "EvalDecisionDetails": { "string": "allowed|explicitDeny|implicitDeny" },
            "ResourceSpecificResults": [
                {
                    "EvalResourceName": "string",
                    "EvalResourceDecision": "allowed|explicitDeny|implicitDeny",
                    "MatchedStatements": [],
                    "MissingContextValues": ["string"]
                }
            ]
        }
    ],
    "IsTruncated": true|false,
    "Marker": "string"
}
```

---

### 20.2 `simulate-custom-policy`

Simulates the effect of custom policy documents (not attached to any entity). **Paginated.**

**Synopsis:**
```bash
aws iam simulate-custom-policy \
    --policy-input-list <value> \
    --action-names <value> \
    [--permissions-boundary-policy-input-list <value>] \
    [--resource-arns <value>] \
    [--resource-policy <value>] \
    [--resource-owner <value>] \
    [--caller-arn <value>] \
    [--context-entries <value>] \
    [--resource-handling-option <value>] \
    [--starting-token <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-input-list` | **Yes** | list(string) | -- | Policy documents as JSON strings |
| `--action-names` | **Yes** | list(string) | -- | API actions to simulate |

**Output Schema:** Same as `simulate-principal-policy`.

---

### 20.3 `get-context-keys-for-principal-policy`

Gets context keys referenced in all policies attached to a principal.

**Synopsis:**
```bash
aws iam get-context-keys-for-principal-policy --policy-source-arn <value> [--policy-input-list <value>]
```

**Output Schema:**
```json
{
    "ContextKeyNames": ["string"]
}
```

---

### 20.4 `get-context-keys-for-custom-policy`

Gets context keys referenced in a set of custom policy documents.

**Synopsis:**
```bash
aws iam get-context-keys-for-custom-policy --policy-input-list <value>
```

**Output Schema:**
```json
{
    "ContextKeyNames": ["string"]
}
```

---
