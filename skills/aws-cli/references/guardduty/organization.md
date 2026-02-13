# Organization

### 11.1 `enable-organization-admin-account`

Enables an AWS account as the delegated GuardDuty administrator account within an AWS organization.

**Synopsis:**
```bash
aws guardduty enable-organization-admin-account \
    --admin-account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--admin-account-id` | **Yes** | string | -- | AWS account ID to designate as admin |

**Output:** None (HTTP 200 on success)

---

### 11.2 `disable-organization-admin-account`

Disables the designated GuardDuty delegated administrator account within an AWS organization.

**Synopsis:**
```bash
aws guardduty disable-organization-admin-account \
    --admin-account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--admin-account-id` | **Yes** | string | -- | AWS account ID of the admin to disable |

**Output:** None (HTTP 200 on success)

---

### 11.3 `list-organization-admin-accounts`

Lists the accounts designated as GuardDuty delegated administrators. **Paginated operation.**

**Synopsis:**
```bash
aws guardduty list-organization-admin-accounts \
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
    "AdminAccounts": [
        {
            "AdminAccountId": "string",
            "AdminStatus": "ENABLED|DISABLE_IN_PROGRESS"
        }
    ],
    "NextToken": "string"
}
```

---

### 11.4 `describe-organization-configuration`

Returns information about the account selected as the delegated administrator for GuardDuty in the organization.

**Synopsis:**
```bash
aws guardduty describe-organization-configuration \
    --detector-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AutoEnable": "boolean",
    "MemberAccountLimitReached": "boolean",
    "DataSources": {
        "S3Logs": {
            "AutoEnable": "boolean"
        },
        "Kubernetes": {
            "AuditLogs": {
                "AutoEnable": "boolean"
            }
        },
        "MalwareProtection": {
            "ScanEc2InstanceWithFindings": {
                "EbsVolumes": {
                    "AutoEnable": "boolean"
                }
            }
        }
    },
    "Features": [
        {
            "Name": "string",
            "AutoEnable": "NEW|NONE|ALL",
            "AdditionalConfiguration": [
                {
                    "Name": "string",
                    "AutoEnable": "NEW|NONE|ALL"
                }
            ]
        }
    ],
    "NextToken": "string",
    "AutoEnableOrganizationMembers": "NEW|ALL|NONE"
}
```

---

### 11.5 `update-organization-configuration`

Configures the delegated administrator account with the provided values. Updates the auto-enable settings for member accounts.

**Synopsis:**
```bash
aws guardduty update-organization-configuration \
    --detector-id <value> \
    [--auto-enable | --no-auto-enable] \
    [--data-sources <value>] \
    [--features <value>] \
    [--auto-enable-organization-members <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--auto-enable` / `--no-auto-enable` | No | boolean | None | Auto-enable GuardDuty for new member accounts (deprecated) |
| `--data-sources` | No | structure | None | Data source configuration (deprecated) |
| `--features` | No | list | None | Features to configure for the organization |
| `--auto-enable-organization-members` | No | string | None | Auto-enable mode: `NEW`, `ALL`, `NONE` |

**Features Structure:**
```json
[
    {
        "Name": "S3_DATA_EVENTS|EKS_AUDIT_LOGS|EBS_MALWARE_PROTECTION|RDS_LOGIN_EVENTS|EKS_RUNTIME_MONITORING|LAMBDA_NETWORK_LOGS|RUNTIME_MONITORING",
        "AutoEnable": "NEW|NONE|ALL",
        "AdditionalConfiguration": [
            {
                "Name": "EKS_ADDON_MANAGEMENT|ECS_FARGATE_AGENT_MANAGEMENT|EC2_AGENT_MANAGEMENT",
                "AutoEnable": "NEW|NONE|ALL"
            }
        ]
    }
]
```

**Output:** None (HTTP 200 on success)

---

### 11.6 `get-organization-statistics`

Retrieves how many member accounts in the organization have GuardDuty enabled and the coverage statistics.

**Synopsis:**
```bash
aws guardduty get-organization-statistics \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "OrganizationDetails": {
        "UpdatedAt": "timestamp",
        "OrganizationStatistics": {
            "TotalAccountsCount": "integer",
            "MemberAccountsCount": "integer",
            "ActiveAccountsCount": "integer",
            "CountByFeature": [
                {
                    "Name": "string",
                    "EnabledAccountsCount": "integer",
                    "AdditionalConfiguration": [
                        {
                            "Name": "string",
                            "EnabledAccountsCount": "integer"
                        }
                    ]
                }
            ]
        }
    }
}
```
