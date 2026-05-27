# Policies

### 2.1 `put-policy`

Creates or updates a Firewall Manager policy.

**Synopsis:**
```bash
aws fms put-policy \
    --policy <value> \
    [--tag-list <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy` | **Yes** | structure | -- | Policy details (JSON). See Policy Structure below |
| `--tag-list` | No | list | None | Tags for the policy (max 200) |

**Policy Structure:**
```json
{
    "PolicyId": "string",
    "PolicyName": "string",
    "PolicyUpdateToken": "string",
    "SecurityServicePolicyData": {
        "Type": "WAF|WAFV2|SHIELD_ADVANCED|SECURITY_GROUPS_COMMON|SECURITY_GROUPS_CONTENT_AUDIT|SECURITY_GROUPS_USAGE_AUDIT|NETWORK_FIREWALL|DNS_FIREWALL|THIRD_PARTY_FIREWALL|IMPORT_NETWORK_FIREWALL|NETWORK_ACL_COMMON",
        "ManagedServiceData": "string",
        "PolicyOption": {}
    },
    "ResourceType": "string",
    "ResourceTypeList": ["string"],
    "ResourceTags": [{"Key": "string", "Value": "string"}],
    "ExcludeResourceTags": true|false,
    "RemediationEnabled": true|false,
    "DeleteUnusedFMManagedResources": true|false,
    "IncludeMap": {"ACCOUNT": ["string"], "ORG_UNIT": ["string"]},
    "ExcludeMap": {"ACCOUNT": ["string"], "ORG_UNIT": ["string"]},
    "ResourceSetIds": ["string"],
    "PolicyDescription": "string",
    "PolicyStatus": "ACTIVE|OUT_OF_ADMIN_SCOPE",
    "ResourceTagLogicalOperator": "AND|OR"
}
```

Required fields in policy: `PolicyName`, `SecurityServicePolicyData`, `ResourceType`, `ExcludeResourceTags`, `RemediationEnabled`

**Output Schema:**
```json
{
    "Policy": {
        "PolicyId": "string",
        "PolicyName": "string",
        "PolicyUpdateToken": "string",
        "SecurityServicePolicyData": {},
        "ResourceType": "string",
        "ResourceTypeList": ["string"],
        "ResourceTags": [],
        "ExcludeResourceTags": true|false,
        "RemediationEnabled": true|false,
        "DeleteUnusedFMManagedResources": true|false,
        "IncludeMap": {},
        "ExcludeMap": {},
        "ResourceSetIds": ["string"],
        "PolicyDescription": "string",
        "PolicyStatus": "string",
        "ResourceTagLogicalOperator": "string"
    },
    "PolicyArn": "string"
}
```

---

### 2.2 `get-policy`

Returns information about the specified Firewall Manager policy.

**Synopsis:**
```bash
aws fms get-policy \
    --policy-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-id` | **Yes** | string | -- | Policy ID (36 chars, UUID format) |

**Output Schema:**
```json
{
    "Policy": {
        "PolicyId": "string",
        "PolicyName": "string",
        "PolicyUpdateToken": "string",
        "SecurityServicePolicyData": {
            "Type": "string",
            "ManagedServiceData": "string",
            "PolicyOption": {}
        },
        "ResourceType": "string",
        "ResourceTypeList": ["string"],
        "ResourceTags": [{"Key": "string", "Value": "string"}],
        "ExcludeResourceTags": true|false,
        "RemediationEnabled": true|false,
        "DeleteUnusedFMManagedResources": true|false,
        "IncludeMap": {},
        "ExcludeMap": {},
        "ResourceSetIds": ["string"],
        "PolicyDescription": "string",
        "PolicyStatus": "string",
        "ResourceTagLogicalOperator": "string"
    },
    "PolicyArn": "string"
}
```

---

### 2.3 `delete-policy`

Permanently deletes a Firewall Manager policy.

**Synopsis:**
```bash
aws fms delete-policy \
    --policy-id <value> \
    [--delete-all-policy-resources | --no-delete-all-policy-resources] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-id` | **Yes** | string | -- | Policy ID to delete |
| `--delete-all-policy-resources` | No | boolean | false | Also delete all resources created by the policy |

**Output Schema:** Empty on success.

---

### 2.4 `list-policies`

Returns a list of all Firewall Manager policies. **Paginated.**

**Synopsis:**
```bash
aws fms list-policies \
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
    "PolicyList": [
        {
            "PolicyArn": "string",
            "PolicyId": "string",
            "PolicyName": "string",
            "ResourceType": "string",
            "SecurityServiceType": "WAF|WAFV2|SHIELD_ADVANCED|SECURITY_GROUPS_COMMON|SECURITY_GROUPS_CONTENT_AUDIT|SECURITY_GROUPS_USAGE_AUDIT|NETWORK_FIREWALL|DNS_FIREWALL|THIRD_PARTY_FIREWALL|IMPORT_NETWORK_FIREWALL|NETWORK_ACL_COMMON",
            "RemediationEnabled": true|false,
            "DeleteUnusedFMManagedResources": true|false,
            "PolicyStatus": "ACTIVE|OUT_OF_ADMIN_SCOPE"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.5 `get-compliance-detail`

Returns detailed compliance information about the specified member account.

**Synopsis:**
```bash
aws fms get-compliance-detail \
    --policy-id <value> \
    --member-account <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-id` | **Yes** | string | -- | Policy ID (36 chars) |
| `--member-account` | **Yes** | string | -- | Member account ID |

**Output Schema:**
```json
{
    "PolicyComplianceDetail": {
        "PolicyOwner": "string",
        "PolicyId": "string",
        "MemberAccount": "string",
        "Violators": [
            {
                "ResourceId": "string",
                "ViolationReason": "WEB_ACL_MISSING_RULE_GROUP|RESOURCE_MISSING_WEB_ACL|RESOURCE_MISSING_SHIELD_PROTECTION|RESOURCE_MISSING_SECURITY_GROUP|SECURITY_GROUP_UNUSED|MISSING_FIREWALL|MISSING_EXPECTED_ROUTE_TABLE|FMS_CREATED_SECURITY_GROUP_EDITED|...",
                "ResourceType": "string",
                "Metadata": {"key": "value"}
            }
        ],
        "EvaluationLimitExceeded": true|false,
        "ExpiredAt": "timestamp",
        "IssueInfoMap": {"key": "value"}
    }
}
```

---

### 2.6 `list-compliance-status`

Returns a list of compliance status for all member accounts for a policy. **Paginated.**

**Synopsis:**
```bash
aws fms list-compliance-status \
    --policy-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-id` | **Yes** | string | -- | Policy ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "PolicyComplianceStatusList": [
        {
            "PolicyOwner": "string",
            "PolicyId": "string",
            "PolicyName": "string",
            "MemberAccount": "string",
            "EvaluationResults": [
                {
                    "ComplianceStatus": "COMPLIANT|NON_COMPLIANT",
                    "ViolatorCount": "long",
                    "EvaluationLimitExceeded": true|false
                }
            ],
            "LastUpdated": "timestamp",
            "IssueInfoMap": {"key": "value"}
        }
    ],
    "NextToken": "string"
}
```

---

### 2.7 `get-violation-details`

Returns violation details for a specific resource and policy.

**Synopsis:**
```bash
aws fms get-violation-details \
    --policy-id <value> \
    --member-account <value> \
    --resource-id <value> \
    --resource-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-id` | **Yes** | string | -- | Policy ID |
| `--member-account` | **Yes** | string | -- | Member account ID |
| `--resource-id` | **Yes** | string | -- | Resource ID |
| `--resource-type` | **Yes** | string | -- | Resource type (e.g., `AWS::EC2::Instance`) |

**Output Schema:**
```json
{
    "ViolationDetail": {
        "PolicyId": "string",
        "MemberAccount": "string",
        "ResourceId": "string",
        "ResourceType": "string",
        "ResourceViolations": [
            {
                "AwsVPCSecurityGroupViolation": {},
                "AwsEc2NetworkInterfaceViolation": {},
                "AwsEc2InstanceViolation": {},
                "NetworkFirewallMissingFirewallViolation": {},
                "NetworkFirewallMissingSubnetViolation": {},
                "NetworkFirewallMissingExpectedRTViolation": {},
                "NetworkFirewallPolicyModifiedViolation": {},
                "DnsRuleGroupPriorityConflictViolation": {},
                "DnsDuplicateRuleGroupViolation": {},
                "DnsRuleGroupLimitExceededViolation": {},
                "ThirdPartyFirewallMissingFirewallViolation": {},
                "ThirdPartyFirewallMissingSubnetViolation": {},
                "ThirdPartyFirewallMissingExpectedRouteTableViolation": {},
                "FirewallSubnetMissingVPCEndpointViolation": {},
                "InvalidNetworkAclEntriesViolation": {},
                "WebACLHasOutOfScopeResourcesViolation": {},
                "WebACLHasIncompatibleConfigurationViolation": {}
            }
        ],
        "ResourceTags": [{"Key": "string", "Value": "string"}],
        "ResourceDescription": "string"
    }
}
```

---

### 2.8 `get-protection-status`

Gets attack event information for Shield Advanced-protected resources.

**Synopsis:**
```bash
aws fms get-protection-status \
    --policy-id <value> \
    [--member-account-id <value>] \
    [--start-time <value>] \
    [--end-time <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-id` | **Yes** | string | -- | Policy ID |
| `--member-account-id` | No | string | None | Member account to filter |
| `--start-time` | No | timestamp | None | Start time for attack events |
| `--end-time` | No | timestamp | None | End time for attack events |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AdminAccountId": "string",
    "ServiceType": "WAF|WAFV2|SHIELD_ADVANCED|SECURITY_GROUPS_COMMON|SECURITY_GROUPS_CONTENT_AUDIT|SECURITY_GROUPS_USAGE_AUDIT|NETWORK_FIREWALL|DNS_FIREWALL|THIRD_PARTY_FIREWALL|NETWORK_ACL_COMMON",
    "Data": "string",
    "NextToken": "string"
}
```

---

### 2.9 `list-member-accounts`

Returns a list of all member accounts in the organization. **Paginated.**

**Synopsis:**
```bash
aws fms list-member-accounts \
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
    "MemberAccounts": ["string"],
    "NextToken": "string"
}
```

---

### 2.10 `list-discovered-resources`

Returns a list of resources discovered by Firewall Manager for a policy. **Paginated.**

**Synopsis:**
```bash
aws fms list-discovered-resources \
    --member-account-ids <value> \
    --resource-type <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--member-account-ids` | **Yes** | list(string) | -- | Member account IDs |
| `--resource-type` | **Yes** | string | -- | Resource type (e.g., `AWS::EC2::Instance`) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Items": [
        {
            "URI": "string",
            "AccountId": "string",
            "Type": "string",
            "Name": "string"
        }
    ],
    "NextToken": "string"
}
```
