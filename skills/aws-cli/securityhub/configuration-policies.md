# Configuration Policies

### 7.1 `create-configuration-policy`

Creates a configuration policy for centrally managing Security Hub across member accounts.

**Synopsis:**
```bash
aws securityhub create-configuration-policy \
    --name <value> \
    --configuration-policy <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Policy name |
| `--configuration-policy` | **Yes** | structure | -- | Policy configuration |
| `--description` | No | string | None | Policy description |
| `--tags` | No | map | None | Tags (max 50) |

**Configuration Policy Structure:**
```json
{
    "SecurityHub": {
        "ServiceEnabled": "boolean",
        "EnabledStandardIdentifiers": ["string"],
        "SecurityControlsConfiguration": {
            "EnabledSecurityControlIdentifiers": ["string"],
            "DisabledSecurityControlIdentifiers": ["string"],
            "SecurityControlCustomParameters": [
                {
                    "SecurityControlId": "string",
                    "Parameters": {
                        "string": {
                            "ValueType": "DEFAULT|CUSTOM",
                            "Value": {}
                        }
                    }
                }
            ]
        }
    }
}
```

**Output Schema:**
```json
{
    "Id": "string",
    "Arn": "string",
    "Name": "string",
    "Description": "string",
    "UpdatedAt": "timestamp",
    "CreatedAt": "timestamp",
    "ConfigurationPolicy": {}
}
```

---

### 7.2 `delete-configuration-policy`

Deletes a configuration policy.

**Synopsis:**
```bash
aws securityhub delete-configuration-policy \
    --identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Policy ARN or ID |

**Output:** None (HTTP 200 on success)

---

### 7.3 `get-configuration-policy`

Returns details about a configuration policy.

**Synopsis:**
```bash
aws securityhub get-configuration-policy \
    --identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Policy ARN or ID |

**Output Schema:**
```json
{
    "Id": "string",
    "Arn": "string",
    "Name": "string",
    "Description": "string",
    "UpdatedAt": "timestamp",
    "CreatedAt": "timestamp",
    "ConfigurationPolicy": {
        "SecurityHub": {
            "ServiceEnabled": "boolean",
            "EnabledStandardIdentifiers": ["string"],
            "SecurityControlsConfiguration": {}
        }
    }
}
```

---

### 7.4 `list-configuration-policies`

Lists configuration policies. **Paginated operation.**

**Synopsis:**
```bash
aws securityhub list-configuration-policies \
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
    "ConfigurationPolicySummaries": [
        {
            "Arn": "string",
            "Id": "string",
            "Name": "string",
            "Description": "string",
            "UpdatedAt": "timestamp",
            "ServiceEnabled": "boolean"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.5 `update-configuration-policy`

Updates a configuration policy.

**Synopsis:**
```bash
aws securityhub update-configuration-policy \
    --identifier <value> \
    [--name <value>] \
    [--description <value>] \
    [--configuration-policy <value>] \
    [--updated-reason <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Policy ARN or ID |
| `--name` | No | string | None | Updated policy name |
| `--description` | No | string | None | Updated description |
| `--configuration-policy` | No | structure | None | Updated policy configuration |
| `--updated-reason` | No | string | None | Reason for the update |

**Output Schema:**
```json
{
    "Id": "string",
    "Arn": "string",
    "Name": "string",
    "Description": "string",
    "UpdatedAt": "timestamp",
    "CreatedAt": "timestamp",
    "ConfigurationPolicy": {}
}
```

---

### 7.6 `get-configuration-policy-association`

Returns the association between a configuration policy and a target.

**Synopsis:**
```bash
aws securityhub get-configuration-policy-association \
    --target <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target` | **Yes** | structure | -- | Target to check association for |

**Target Structure:**
```json
{
    "AccountId": "string",
    "OrganizationalUnitId": "string",
    "RootId": "string"
}
```

**Output Schema:**
```json
{
    "ConfigurationPolicyId": "string",
    "TargetId": "string",
    "TargetType": "ACCOUNT|ORGANIZATIONAL_UNIT|ROOT",
    "AssociationType": "INHERITED|APPLIED",
    "UpdatedAt": "timestamp",
    "AssociationStatus": "PENDING|SUCCESS|FAILED",
    "AssociationStatusMessage": "string"
}
```

---

### 7.7 `list-configuration-policy-associations`

Lists associations between configuration policies and targets. **Paginated operation.**

**Synopsis:**
```bash
aws securityhub list-configuration-policy-associations \
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
| `--filters` | No | structure | None | Filters for associations |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ConfigurationPolicyAssociationSummaries": [
        {
            "ConfigurationPolicyId": "string",
            "TargetId": "string",
            "TargetType": "ACCOUNT|ORGANIZATIONAL_UNIT|ROOT",
            "AssociationType": "INHERITED|APPLIED",
            "UpdatedAt": "timestamp",
            "AssociationStatus": "PENDING|SUCCESS|FAILED",
            "AssociationStatusMessage": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.8 `batch-get-configuration-policy-associations`

Returns associations for a batch of targets.

**Synopsis:**
```bash
aws securityhub batch-get-configuration-policy-associations \
    --configuration-policy-association-identifiers <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-policy-association-identifiers` | **Yes** | list | -- | Targets to get associations for |

**Output Schema:**
```json
{
    "ConfigurationPolicyAssociations": [
        {
            "ConfigurationPolicyId": "string",
            "TargetId": "string",
            "TargetType": "ACCOUNT|ORGANIZATIONAL_UNIT|ROOT",
            "AssociationType": "INHERITED|APPLIED",
            "UpdatedAt": "timestamp",
            "AssociationStatus": "PENDING|SUCCESS|FAILED"
        }
    ],
    "UnprocessedConfigurationPolicyAssociations": [
        {
            "ConfigurationPolicyAssociationIdentifiers": {},
            "ErrorCode": "string",
            "ErrorReason": "string"
        }
    ]
}
```

---

### 7.9 `start-configuration-policy-association`

Associates a configuration policy with a target (account, OU, or root).

**Synopsis:**
```bash
aws securityhub start-configuration-policy-association \
    --configuration-policy-identifier <value> \
    --target <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-policy-identifier` | **Yes** | string | -- | Policy ARN or ID |
| `--target` | **Yes** | structure | -- | Target to associate with |

**Output Schema:**
```json
{
    "ConfigurationPolicyId": "string",
    "TargetId": "string",
    "TargetType": "ACCOUNT|ORGANIZATIONAL_UNIT|ROOT",
    "AssociationType": "INHERITED|APPLIED",
    "UpdatedAt": "timestamp",
    "AssociationStatus": "PENDING|SUCCESS|FAILED",
    "AssociationStatusMessage": "string"
}
```

---

### 7.10 `start-configuration-policy-disassociation`

Disassociates a configuration policy from a target.

**Synopsis:**
```bash
aws securityhub start-configuration-policy-disassociation \
    --configuration-policy-identifier <value> \
    --target <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-policy-identifier` | **Yes** | string | -- | Policy ARN or ID |
| `--target` | **Yes** | structure | -- | Target to disassociate from |

**Output:** None (HTTP 200 on success)
