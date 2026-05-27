# Enablement

### 1.1 `enable`

Enables Amazon Inspector scanning for specified resource types in one or more accounts.

**Synopsis:**
```bash
aws inspector2 enable \
    --resource-types <value> \
    [--account-ids <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-types` | **Yes** | list(string) | -- | Resource scan types to enable: `EC2`, `ECR`, `LAMBDA`, `LAMBDA_CODE`, `CODE_REPOSITORY` (max 5) |
| `--account-ids` | No | list(string) | None | Account IDs to enable scanning for (max 100, each 12 digits) |
| `--client-token` | No | string | None | Idempotency token (1-64 chars) |

**Output Schema:**
```json
{
    "accounts": [
        {
            "accountId": "string",
            "status": "ENABLING|ENABLED|DISABLING|DISABLED|SUSPENDING|SUSPENDED",
            "resourceStatus": {
                "ec2": "ENABLING|ENABLED|DISABLING|DISABLED|SUSPENDING|SUSPENDED",
                "ecr": "ENABLING|ENABLED|DISABLING|DISABLED|SUSPENDING|SUSPENDED",
                "lambda": "ENABLING|ENABLED|DISABLING|DISABLED|SUSPENDING|SUSPENDED",
                "lambdaCode": "ENABLING|ENABLED|DISABLING|DISABLED|SUSPENDING|SUSPENDED",
                "codeRepository": "ENABLING|ENABLED|DISABLING|DISABLED|SUSPENDING|SUSPENDED"
            }
        }
    ],
    "failedAccounts": [
        {
            "accountId": "string",
            "status": "string",
            "resourceStatus": {},
            "errorCode": "ALREADY_ENABLED|ENABLE_IN_PROGRESS|DISABLE_IN_PROGRESS|SUSPEND_IN_PROGRESS|RESOURCE_NOT_FOUND|ACCESS_DENIED|INTERNAL_ERROR|SSM_UNAVAILABLE|SSM_THROTTLED|EVENTBRIDGE_UNAVAILABLE|EVENTBRIDGE_THROTTLED|RESOURCE_SCAN_NOT_DISABLED|DISASSOCIATE_ALL_MEMBERS|ACCOUNT_IS_ISOLATED",
            "errorMessage": "string"
        }
    ]
}
```

---

### 1.2 `disable`

Disables Amazon Inspector scanning for specified resource types. Disabling all scan types disables the service entirely.

**Synopsis:**
```bash
aws inspector2 disable \
    [--account-ids <value>] \
    [--resource-types <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-ids` | No | list(string) | None | Account IDs to disable scanning for (max 100) |
| `--resource-types` | No | list(string) | None | Resource types to disable: `EC2`, `ECR`, `LAMBDA`, `LAMBDA_CODE`, `CODE_REPOSITORY` |

**Output Schema:**
```json
{
    "accounts": [
        {
            "accountId": "string",
            "status": "ENABLING|ENABLED|DISABLING|DISABLED|SUSPENDING|SUSPENDED",
            "resourceStatus": {
                "ec2": "string",
                "ecr": "string",
                "lambda": "string",
                "lambdaCode": "string",
                "codeRepository": "string"
            }
        }
    ],
    "failedAccounts": [
        {
            "accountId": "string",
            "status": "string",
            "resourceStatus": {},
            "errorCode": "string",
            "errorMessage": "string"
        }
    ]
}
```

---

### 1.3 `batch-get-account-status`

Retrieves the Amazon Inspector status of multiple AWS accounts.

**Synopsis:**
```bash
aws inspector2 batch-get-account-status \
    [--account-ids <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-ids` | No | list(string) | None | Account IDs to check (max 100, each 12 digits) |

**Output Schema:**
```json
{
    "accounts": [
        {
            "accountId": "string",
            "state": {
                "status": "ENABLING|ENABLED|DISABLING|DISABLED|SUSPENDING|SUSPENDED",
                "errorCode": "string",
                "errorMessage": "string"
            },
            "resourceState": {
                "ec2": {
                    "status": "ENABLING|ENABLED|DISABLING|DISABLED|SUSPENDING|SUSPENDED",
                    "errorCode": "string",
                    "errorMessage": "string"
                },
                "ecr": {
                    "status": "string",
                    "errorCode": "string",
                    "errorMessage": "string"
                },
                "lambda": {
                    "status": "string",
                    "errorCode": "string",
                    "errorMessage": "string"
                },
                "lambdaCode": {
                    "status": "string",
                    "errorCode": "string",
                    "errorMessage": "string"
                },
                "codeRepository": {
                    "status": "string",
                    "errorCode": "string",
                    "errorMessage": "string"
                }
            }
        }
    ],
    "failedAccounts": [
        {
            "accountId": "string",
            "status": "string",
            "resourceStatus": {},
            "errorCode": "string",
            "errorMessage": "string"
        }
    ]
}
```

---

### 1.4 `batch-get-free-trial-info`

Gets free trial status for specified accounts.

**Synopsis:**
```bash
aws inspector2 batch-get-free-trial-info \
    --account-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-ids` | **Yes** | list(string) | -- | Account IDs to get free trial info for (max 100) |

**Output Schema:**
```json
{
    "accounts": [
        {
            "accountId": "string",
            "freeTrialInfo": [
                {
                    "type": "EC2|ECR|LAMBDA|LAMBDA_CODE|CODE_REPOSITORY",
                    "start": "timestamp",
                    "end": "timestamp",
                    "status": "ACTIVE|INACTIVE"
                }
            ]
        }
    ],
    "failedAccounts": [
        {
            "accountId": "string",
            "code": "ACCESS_DENIED|INTERNAL_ERROR",
            "message": "string"
        }
    ]
}
```

---

### 1.5 `get-configuration`

Gets the Amazon Inspector configuration for ECR image scan duration.

**Synopsis:**
```bash
aws inspector2 get-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No command-specific parameters.

**Output Schema:**
```json
{
    "ecrConfiguration": {
        "rescanDuration": "LIFETIME|DAYS_30|DAYS_60|DAYS_90|DAYS_180|DAYS_14"
    },
    "ec2Configuration": {
        "scanMode": "EC2_SSM_AGENT_BASED|EC2_AGENTLESS"
    }
}
```

---

### 1.6 `update-configuration`

Updates the Amazon Inspector configuration.

**Synopsis:**
```bash
aws inspector2 update-configuration \
    [--ecr-configuration <value>] \
    [--ec2-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ecr-configuration` | No | structure | None | ECR configuration. Shorthand: `rescanDuration=LIFETIME\|DAYS_30\|DAYS_60\|DAYS_90\|DAYS_180\|DAYS_14` |
| `--ec2-configuration` | No | structure | None | EC2 scan mode. Shorthand: `scanMode=EC2_SSM_AGENT_BASED\|EC2_AGENTLESS` |

**Output Schema:** Empty on success.

---

### 1.7 `update-organization-configuration`

Updates the Amazon Inspector auto-enable settings for new member accounts in your organization.

**Synopsis:**
```bash
aws inspector2 update-organization-configuration \
    --auto-enable <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-enable` | **Yes** | structure | -- | Auto-enable settings. Shorthand: `ec2=boolean,ecr=boolean,lambda=boolean,lambdaCode=boolean` |

**Output Schema:**
```json
{
    "autoEnable": {
        "ec2": true|false,
        "ecr": true|false,
        "lambda": true|false,
        "lambdaCode": true|false
    }
}
```

---

### 1.8 `describe-organization-configuration`

Describes the organization auto-enable configuration for Inspector.

**Synopsis:**
```bash
aws inspector2 describe-organization-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No command-specific parameters.

**Output Schema:**
```json
{
    "autoEnable": {
        "ec2": true|false,
        "ecr": true|false,
        "lambda": true|false,
        "lambdaCode": true|false
    },
    "maxAccountLimitReached": true|false
}
```

---

### 1.9 `list-account-permissions`

Lists the permissions an account has to configure Amazon Inspector. **Paginated.**

**Synopsis:**
```bash
aws inspector2 list-account-permissions \
    [--service <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service` | No | string | None | Service to filter permissions: `EC2`, `ECR`, `LAMBDA` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "permissions": [
        {
            "service": "EC2|ECR|LAMBDA",
            "operation": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.10 `list-usage-totals`

Lists the total usage for all accounts in the organization. **Paginated.**

**Synopsis:**
```bash
aws inspector2 list-usage-totals \
    [--account-ids <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-ids` | No | list(string) | None | Account IDs to filter (max 25) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "totals": [
        {
            "accountId": "string",
            "usage": [
                {
                    "type": "EC2_AGENTLESS_INSTANCE_HOURS|EC2_INSTANCE_HOURS|ECR_INITIAL_SCAN|ECR_RESCAN|LAMBDA_FUNCTION_HOURS|LAMBDA_FUNCTION_CODE_HOURS|CODE_REPOSITORY_SAST",
                    "total": "double",
                    "estimatedMonthlyCost": "double",
                    "currency": "USD"
                }
            ]
        }
    ],
    "nextToken": "string"
}
```

---

### 1.11 `get-member`

Gets details about a member account.

**Synopsis:**
```bash
aws inspector2 get-member \
    --account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | The account ID of the member (12 digits) |

**Output Schema:**
```json
{
    "member": {
        "accountId": "string",
        "delegatedAdminAccountId": "string",
        "relationshipStatus": "CREATED|INVITED|DISABLED|ENABLED|REMOVED|RESIGNED|DELETED|EMAIL_VERIFICATION_IN_PROGRESS|EMAIL_VERIFICATION_FAILED|REGION_DISABLED|ACCOUNT_SUSPENDED|CANNOT_CREATE_DETECTOR_IN_ORG_MASTER",
        "updatedAt": "timestamp"
    }
}
```

---

### 1.12 `list-members`

Lists member accounts associated with the delegated administrator. **Paginated.**

**Synopsis:**
```bash
aws inspector2 list-members \
    [--only-associated | --no-only-associated] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--only-associated` | No | boolean | None | Only return associated member accounts |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "members": [
        {
            "accountId": "string",
            "delegatedAdminAccountId": "string",
            "relationshipStatus": "string",
            "updatedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.13 `associate-member`

Associates an AWS account with the delegated administrator account.

**Synopsis:**
```bash
aws inspector2 associate-member \
    --account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | The account ID to associate (12 digits) |

**Output Schema:**
```json
{
    "accountId": "string"
}
```

---

### 1.14 `disassociate-member`

Disassociates a member account from the delegated administrator.

**Synopsis:**
```bash
aws inspector2 disassociate-member \
    --account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | The account ID to disassociate (12 digits) |

**Output Schema:**
```json
{
    "accountId": "string"
}
```

---

### 1.15 `batch-get-member-ec2-deep-inspection-status`

Gets EC2 deep inspection status for member accounts.

**Synopsis:**
```bash
aws inspector2 batch-get-member-ec2-deep-inspection-status \
    [--account-ids <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-ids` | No | list(string) | None | Account IDs to check (max 100) |

**Output Schema:**
```json
{
    "accountIds": [
        {
            "accountId": "string",
            "status": "ACTIVATED|DEACTIVATED|PENDING|FAILED"
        }
    ],
    "failedAccountIds": [
        {
            "accountId": "string",
            "ec2ScanStatus": "string",
            "errorMessage": "string"
        }
    ]
}
```

---

### 1.16 `batch-update-member-ec2-deep-inspection-status`

Updates EC2 deep inspection status for member accounts.

**Synopsis:**
```bash
aws inspector2 batch-update-member-ec2-deep-inspection-status \
    --account-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-ids` | **Yes** | list | -- | Account IDs with activation status. Structure: `accountId=string,activateDeepInspection=boolean` |

**Output Schema:**
```json
{
    "accountIds": [
        {
            "accountId": "string",
            "status": "ACTIVATED|DEACTIVATED|PENDING|FAILED"
        }
    ],
    "failedAccountIds": [
        {
            "accountId": "string",
            "ec2ScanStatus": "string",
            "errorMessage": "string"
        }
    ]
}
```

---

### 1.17 `get-ec2-deep-inspection-configuration`

Gets the EC2 deep inspection configuration for the calling account.

**Synopsis:**
```bash
aws inspector2 get-ec2-deep-inspection-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No command-specific parameters.

**Output Schema:**
```json
{
    "packagePaths": ["string"],
    "orgPackagePaths": ["string"],
    "status": "ACTIVATED|DEACTIVATED|PENDING|FAILED",
    "errorMessage": "string"
}
```

---

### 1.18 `update-ec2-deep-inspection-configuration`

Updates EC2 deep inspection configuration for the calling account.

**Synopsis:**
```bash
aws inspector2 update-ec2-deep-inspection-configuration \
    [--activate-deep-inspection | --no-activate-deep-inspection] \
    [--package-paths <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--activate-deep-inspection` | No | boolean | None | Whether to activate deep inspection |
| `--package-paths` | No | list(string) | None | Custom paths to inspect for packages (max 5, each 1-256 chars) |

**Output Schema:**
```json
{
    "packagePaths": ["string"],
    "orgPackagePaths": ["string"],
    "status": "ACTIVATED|DEACTIVATED|PENDING|FAILED",
    "errorMessage": "string"
}
```

---

### 1.19 `update-org-ec2-deep-inspection-configuration`

Updates the organization-level EC2 deep inspection configuration.

**Synopsis:**
```bash
aws inspector2 update-org-ec2-deep-inspection-configuration \
    --org-package-paths <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--org-package-paths` | **Yes** | list(string) | -- | Organization-level package paths to inspect (max 5) |

**Output Schema:** Empty on success.
