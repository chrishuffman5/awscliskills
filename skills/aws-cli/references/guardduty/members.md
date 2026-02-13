# Members

### 10.1 `create-members`

Creates member accounts of the current AWS account by specifying a list of AWS account IDs.

**Synopsis:**
```bash
aws guardduty create-members \
    --detector-id <value> \
    --account-details <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--account-details` | **Yes** | list | -- | Account details for members to add (max 50) |

**Account Details Structure:**
```json
[
    {
        "AccountId": "string",
        "Email": "string"
    }
]
```

**Output Schema:**
```json
{
    "UnprocessedAccounts": [
        {
            "AccountId": "string",
            "Result": "string"
        }
    ]
}
```

---

### 10.2 `delete-members`

Deletes GuardDuty member accounts specified by the account IDs.

**Synopsis:**
```bash
aws guardduty delete-members \
    --detector-id <value> \
    --account-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--account-ids` | **Yes** | list(string) | -- | Account IDs to delete (max 50) |

**Output Schema:**
```json
{
    "UnprocessedAccounts": [
        {
            "AccountId": "string",
            "Result": "string"
        }
    ]
}
```

---

### 10.3 `get-members`

Retrieves GuardDuty member accounts specified by the account IDs.

**Synopsis:**
```bash
aws guardduty get-members \
    --detector-id <value> \
    --account-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--account-ids` | **Yes** | list(string) | -- | Account IDs to retrieve (max 50) |

**Output Schema:**
```json
{
    "Members": [
        {
            "AccountId": "string",
            "DetectorId": "string",
            "MasterId": "string",
            "AdministratorId": "string",
            "Email": "string",
            "RelationshipStatus": "CREATED|INVITED|DISABLED|ENABLED|REMOVED|RESIGNED|EMAILVERIFICATIONINPROGRESS|EMAILVERIFICATIONFAILED",
            "InvitedAt": "string",
            "UpdatedAt": "string"
        }
    ],
    "UnprocessedAccounts": [
        {
            "AccountId": "string",
            "Result": "string"
        }
    ]
}
```

---

### 10.4 `invite-members`

Invites other AWS accounts to enable GuardDuty and become member accounts.

**Synopsis:**
```bash
aws guardduty invite-members \
    --detector-id <value> \
    --account-ids <value> \
    [--disable-email-notification | --no-disable-email-notification] \
    [--message <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--account-ids` | **Yes** | list(string) | -- | Account IDs to invite (max 50) |
| `--disable-email-notification` | No | boolean | false | Whether to disable email notification |
| `--message` | No | string | None | Invitation message |

**Output Schema:**
```json
{
    "UnprocessedAccounts": [
        {
            "AccountId": "string",
            "Result": "string"
        }
    ]
}
```

---

### 10.5 `list-members`

Lists all GuardDuty member accounts for the specified detector. **Paginated operation.**

**Synopsis:**
```bash
aws guardduty list-members \
    --detector-id <value> \
    [--only-associated <value>] \
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
| `--only-associated` | No | string | `true` | Whether to list only associated members |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (1-50) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Members": [
        {
            "AccountId": "string",
            "DetectorId": "string",
            "AdministratorId": "string",
            "Email": "string",
            "RelationshipStatus": "string",
            "InvitedAt": "string",
            "UpdatedAt": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 10.6 `disassociate-members`

Disassociates GuardDuty member accounts from the administrator account.

**Synopsis:**
```bash
aws guardduty disassociate-members \
    --detector-id <value> \
    --account-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--account-ids` | **Yes** | list(string) | -- | Account IDs to disassociate (max 50) |

**Output Schema:**
```json
{
    "UnprocessedAccounts": [
        {
            "AccountId": "string",
            "Result": "string"
        }
    ]
}
```

---

### 10.7 `start-monitoring-members`

Re-enables GuardDuty monitoring for member accounts that have been stopped.

**Synopsis:**
```bash
aws guardduty start-monitoring-members \
    --detector-id <value> \
    --account-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--account-ids` | **Yes** | list(string) | -- | Account IDs to start monitoring (max 50) |

**Output Schema:**
```json
{
    "UnprocessedAccounts": [
        {
            "AccountId": "string",
            "Result": "string"
        }
    ]
}
```

---

### 10.8 `stop-monitoring-members`

Stops GuardDuty monitoring for the specified member accounts.

**Synopsis:**
```bash
aws guardduty stop-monitoring-members \
    --detector-id <value> \
    --account-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--account-ids` | **Yes** | list(string) | -- | Account IDs to stop monitoring (max 50) |

**Output Schema:**
```json
{
    "UnprocessedAccounts": [
        {
            "AccountId": "string",
            "Result": "string"
        }
    ]
}
```

---

### 10.9 `accept-administrator-invitation`

Accepts the invitation from the administrator account to become a member.

**Synopsis:**
```bash
aws guardduty accept-administrator-invitation \
    --detector-id <value> \
    --administrator-id <value> \
    --invitation-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--administrator-id` | **Yes** | string | -- | Account ID of the administrator |
| `--invitation-id` | **Yes** | string | -- | The invitation ID |

**Output:** None (HTTP 200 on success)

---

### 10.10 `disassociate-from-administrator-account`

Disassociates the current member account from its administrator account.

**Synopsis:**
```bash
aws guardduty disassociate-from-administrator-account \
    --detector-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |

**Output:** None (HTTP 200 on success)

---

### 10.11 `get-administrator-account`

Provides the details for the GuardDuty administrator account associated with the current account.

**Synopsis:**
```bash
aws guardduty get-administrator-account \
    --detector-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |

**Output Schema:**
```json
{
    "Administrator": {
        "AccountId": "string",
        "InvitationId": "string",
        "RelationshipStatus": "string",
        "InvitedAt": "string"
    }
}
```

---

### 10.12 `get-invitations-count`

Returns the count of all GuardDuty membership invitations that were sent to the current member account.

**Synopsis:**
```bash
aws guardduty get-invitations-count \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "InvitationsCount": "integer"
}
```

---

### 10.13 `list-invitations`

Lists all GuardDuty membership invitations sent to the current account. **Paginated operation.**

**Synopsis:**
```bash
aws guardduty list-invitations \
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
    "Invitations": [
        {
            "AccountId": "string",
            "InvitationId": "string",
            "RelationshipStatus": "string",
            "InvitedAt": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 10.14 `decline-invitations`

Declines invitations sent to the current member account.

**Synopsis:**
```bash
aws guardduty decline-invitations \
    --account-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-ids` | **Yes** | list(string) | -- | Account IDs of the invitations to decline |

**Output Schema:**
```json
{
    "UnprocessedAccounts": [
        {
            "AccountId": "string",
            "Result": "string"
        }
    ]
}
```

---

### 10.15 `delete-invitations`

Deletes invitations sent to the current member account.

**Synopsis:**
```bash
aws guardduty delete-invitations \
    --account-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-ids` | **Yes** | list(string) | -- | Account IDs of the invitations to delete |

**Output Schema:**
```json
{
    "UnprocessedAccounts": [
        {
            "AccountId": "string",
            "Result": "string"
        }
    ]
}
```

---

### 10.16 `get-member-detectors`

Describes which data sources and features are enabled for member account detectors.

**Synopsis:**
```bash
aws guardduty get-member-detectors \
    --detector-id <value> \
    --account-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--account-ids` | **Yes** | list(string) | -- | Account IDs to get detector info for (max 50) |

**Output Schema:**
```json
{
    "MemberDataSourceConfigurations": [
        {
            "AccountId": "string",
            "DataSources": {
                "CloudTrail": {"Status": "ENABLED|DISABLED"},
                "DNSLogs": {"Status": "ENABLED|DISABLED"},
                "FlowLogs": {"Status": "ENABLED|DISABLED"},
                "S3Logs": {"Status": "ENABLED|DISABLED"},
                "Kubernetes": {"AuditLogs": {"Status": "ENABLED|DISABLED"}},
                "MalwareProtection": {}
            },
            "Features": [
                {
                    "Name": "string",
                    "Status": "ENABLED|DISABLED",
                    "UpdatedAt": "timestamp",
                    "AdditionalConfiguration": []
                }
            ]
        }
    ],
    "UnprocessedAccounts": [
        {
            "AccountId": "string",
            "Result": "string"
        }
    ]
}
```

---

### 10.17 `update-member-detectors`

Contains information on member accounts to be updated. Supports updating member accounts with features.

**Synopsis:**
```bash
aws guardduty update-member-detectors \
    --detector-id <value> \
    --account-ids <value> \
    [--data-sources <value>] \
    [--features <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--account-ids` | **Yes** | list(string) | -- | Account IDs to update (max 50) |
| `--data-sources` | No | structure | None | Data sources to configure (deprecated) |
| `--features` | No | list | None | Features to configure |

**Output Schema:**
```json
{
    "UnprocessedAccounts": [
        {
            "AccountId": "string",
            "Result": "string"
        }
    ]
}
```

---

### 10.18 `get-remaining-free-trial-days`

Returns the remaining free trial period for the specified accounts.

**Synopsis:**
```bash
aws guardduty get-remaining-free-trial-days \
    --detector-id <value> \
    [--account-ids <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--account-ids` | No | list(string) | None | Account IDs to query (max 50) |

**Output Schema:**
```json
{
    "Accounts": [
        {
            "AccountId": "string",
            "DataSources": {
                "CloudTrail": {"FreeTrialDaysRemaining": "integer"},
                "DnsLogs": {"FreeTrialDaysRemaining": "integer"},
                "FlowLogs": {"FreeTrialDaysRemaining": "integer"},
                "S3Logs": {"FreeTrialDaysRemaining": "integer"},
                "Kubernetes": {"AuditLogs": {"FreeTrialDaysRemaining": "integer"}},
                "MalwareProtection": {"ScanEc2InstanceWithFindings": {"FreeTrialDaysRemaining": "integer"}}
            },
            "Features": [
                {
                    "Name": "string",
                    "FreeTrialDaysRemaining": "integer"
                }
            ]
        }
    ],
    "UnprocessedAccounts": [
        {
            "AccountId": "string",
            "Result": "string"
        }
    ]
}
```
