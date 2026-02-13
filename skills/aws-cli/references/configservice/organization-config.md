# Organization Config

### 9.1 `put-organization-config-rule`

Creates or updates an organization Config rule across all member accounts.

**Synopsis:**
```bash
aws configservice put-organization-config-rule \
    --organization-config-rule-name <value> \
    [--organization-managed-rule-metadata <value>] \
    [--organization-custom-rule-metadata <value>] \
    [--excluded-accounts <value>] \
    [--organization-custom-policy-rule-metadata <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-config-rule-name` | **Yes** | string | -- | Name of the organization Config rule |
| `--organization-managed-rule-metadata` | No | structure | None | Metadata for AWS managed rules |
| `--organization-custom-rule-metadata` | No | structure | None | Metadata for custom Lambda rules |
| `--excluded-accounts` | No | list(string) | None | Account IDs to exclude |
| `--organization-custom-policy-rule-metadata` | No | structure | None | Metadata for custom policy rules (Guard) |

**Organization Managed Rule Metadata:**
```json
{
    "Description": "string",
    "RuleIdentifier": "string",
    "InputParameters": "string",
    "MaximumExecutionFrequency": "One_Hour|Three_Hours|Six_Hours|Twelve_Hours|TwentyFour_Hours",
    "ResourceTypesScope": ["string"],
    "ResourceIdScope": "string",
    "TagKeyScope": "string",
    "TagValueScope": "string"
}
```

**Output Schema:**
```json
{
    "OrganizationConfigRuleArn": "string"
}
```

---

### 9.2 `delete-organization-config-rule`

Deletes an organization Config rule and all associated member account rules.

**Synopsis:**
```bash
aws configservice delete-organization-config-rule \
    --organization-config-rule-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-config-rule-name` | **Yes** | string | -- | Name of the organization Config rule to delete |

**Output Schema:**
```json
{}
```

---

### 9.3 `describe-organization-config-rules`

Returns details about organization Config rules. **Paginated operation.**

**Synopsis:**
```bash
aws configservice describe-organization-config-rules \
    [--organization-config-rule-names <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-config-rule-names` | No | list(string) | None | Specific rule names |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "OrganizationConfigRules": [
        {
            "OrganizationConfigRuleName": "string",
            "OrganizationConfigRuleArn": "string",
            "OrganizationManagedRuleMetadata": {},
            "OrganizationCustomRuleMetadata": {},
            "ExcludedAccounts": ["string"],
            "LastUpdateTime": "timestamp",
            "OrganizationCustomPolicyRuleMetadata": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 9.4 `describe-organization-config-rule-statuses`

Returns deployment status for organization Config rules. **Paginated operation.**

**Synopsis:**
```bash
aws configservice describe-organization-config-rule-statuses \
    [--organization-config-rule-names <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-config-rule-names` | No | list(string) | None | Specific rule names |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "OrganizationConfigRuleStatuses": [
        {
            "OrganizationConfigRuleName": "string",
            "OrganizationRuleStatus": "CREATE_SUCCESSFUL|CREATE_IN_PROGRESS|CREATE_FAILED|DELETE_SUCCESSFUL|DELETE_FAILED|DELETE_IN_PROGRESS|UPDATE_SUCCESSFUL|UPDATE_IN_PROGRESS|UPDATE_FAILED",
            "ErrorCode": "string",
            "ErrorMessage": "string",
            "LastUpdateTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.5 `get-organization-config-rule-detailed-status`

Returns detailed status for each member account for an organization Config rule. **Paginated operation.**

**Synopsis:**
```bash
aws configservice get-organization-config-rule-detailed-status \
    --organization-config-rule-name <value> \
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
| `--organization-config-rule-name` | **Yes** | string | -- | Name of the organization Config rule |
| `--filters` | No | structure | None | Filter by account or status |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "OrganizationConfigRuleDetailedStatus": [
        {
            "AccountId": "string",
            "ConfigRuleName": "string",
            "MemberAccountRuleStatus": "CREATE_SUCCESSFUL|CREATE_IN_PROGRESS|CREATE_FAILED|DELETE_SUCCESSFUL|DELETE_FAILED|DELETE_IN_PROGRESS|UPDATE_SUCCESSFUL|UPDATE_IN_PROGRESS|UPDATE_FAILED",
            "ErrorCode": "string",
            "ErrorMessage": "string",
            "LastUpdateTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.6 `put-organization-conformance-pack`

Creates or updates an organization conformance pack across all member accounts.

**Synopsis:**
```bash
aws configservice put-organization-conformance-pack \
    --organization-conformance-pack-name <value> \
    [--template-s3-uri <value>] \
    [--template-body <value>] \
    [--delivery-s3-bucket <value>] \
    [--delivery-s3-key-prefix <value>] \
    [--conformance-pack-input-parameters <value>] \
    [--excluded-accounts <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-conformance-pack-name` | **Yes** | string | -- | Name of the organization conformance pack |
| `--template-s3-uri` | No | string | None | S3 URI of the template |
| `--template-body` | No | string | None | Inline template body |
| `--delivery-s3-bucket` | No | string | None | S3 bucket for delivery |
| `--delivery-s3-key-prefix` | No | string | None | S3 key prefix |
| `--conformance-pack-input-parameters` | No | list | None | Input parameters |
| `--excluded-accounts` | No | list(string) | None | Account IDs to exclude |

**Output Schema:**
```json
{
    "OrganizationConformancePackArn": "string"
}
```

---

### 9.7 `delete-organization-conformance-pack`

Deletes an organization conformance pack.

**Synopsis:**
```bash
aws configservice delete-organization-conformance-pack \
    --organization-conformance-pack-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-conformance-pack-name` | **Yes** | string | -- | Name of the organization conformance pack to delete |

**Output Schema:**
```json
{}
```

---

### 9.8 `describe-organization-conformance-packs`

Returns details about organization conformance packs. **Paginated operation.**

**Synopsis:**
```bash
aws configservice describe-organization-conformance-packs \
    [--organization-conformance-pack-names <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-conformance-pack-names` | No | list(string) | None | Specific pack names |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "OrganizationConformancePacks": [
        {
            "OrganizationConformancePackName": "string",
            "OrganizationConformancePackArn": "string",
            "DeliveryS3Bucket": "string",
            "DeliveryS3KeyPrefix": "string",
            "ConformancePackInputParameters": [],
            "ExcludedAccounts": ["string"],
            "LastUpdateTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.9 `describe-organization-conformance-pack-statuses`

Returns deployment status for organization conformance packs. **Paginated operation.**

**Synopsis:**
```bash
aws configservice describe-organization-conformance-pack-statuses \
    [--organization-conformance-pack-names <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-conformance-pack-names` | No | list(string) | None | Specific pack names |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "OrganizationConformancePackStatuses": [
        {
            "OrganizationConformancePackName": "string",
            "Status": "CREATE_SUCCESSFUL|CREATE_IN_PROGRESS|CREATE_FAILED|DELETE_SUCCESSFUL|DELETE_FAILED|DELETE_IN_PROGRESS|UPDATE_SUCCESSFUL|UPDATE_IN_PROGRESS|UPDATE_FAILED",
            "ErrorCode": "string",
            "ErrorMessage": "string",
            "LastUpdateTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.10 `get-organization-conformance-pack-detailed-status`

Returns detailed per-member-account status for an organization conformance pack. **Paginated operation.**

**Synopsis:**
```bash
aws configservice get-organization-conformance-pack-detailed-status \
    --organization-conformance-pack-name <value> \
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
| `--organization-conformance-pack-name` | **Yes** | string | -- | Name of the organization conformance pack |
| `--filters` | No | structure | None | Filter by account or status |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "OrganizationConformancePackDetailedStatuses": [
        {
            "AccountId": "string",
            "ConformancePackName": "string",
            "Status": "CREATE_SUCCESSFUL|CREATE_IN_PROGRESS|CREATE_FAILED|DELETE_SUCCESSFUL|DELETE_FAILED|DELETE_IN_PROGRESS|UPDATE_SUCCESSFUL|UPDATE_IN_PROGRESS|UPDATE_FAILED",
            "ErrorCode": "string",
            "ErrorMessage": "string",
            "LastUpdateTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.11 `get-organization-custom-rule-policy`

Returns the Guard policy definition for an organization custom policy Config rule.

**Synopsis:**
```bash
aws configservice get-organization-custom-rule-policy \
    --organization-config-rule-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-config-rule-name` | **Yes** | string | -- | Name of the organization Config rule |

**Output Schema:**
```json
{
    "PolicyText": "string"
}
```
