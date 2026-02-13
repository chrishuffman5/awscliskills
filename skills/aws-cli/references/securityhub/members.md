# Members

### 12.1 `create-members`

Creates member accounts in Security Hub.

**Synopsis:**
```bash
aws securityhub create-members \
    --account-details <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-details` | **Yes** | list | -- | Account details for members to add |

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
            "ProcessingResult": "string"
        }
    ]
}
```

---

### 12.2 `delete-members`

Deletes member accounts from Security Hub.

**Synopsis:**
```bash
aws securityhub delete-members \
    --account-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-ids` | **Yes** | list(string) | -- | Account IDs to delete |

**Output Schema:**
```json
{
    "UnprocessedAccounts": [
        {
            "AccountId": "string",
            "ProcessingResult": "string"
        }
    ]
}
```

---

### 12.3 `get-members`

Returns details about member accounts.

**Synopsis:**
```bash
aws securityhub get-members \
    --account-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-ids` | **Yes** | list(string) | -- | Account IDs to retrieve |

**Output Schema:**
```json
{
    "Members": [
        {
            "AccountId": "string",
            "Email": "string",
            "AdministratorId": "string",
            "MemberStatus": "CREATED|INVITED|DISABLED|ENABLED|REMOVED|RESIGNED|DELETED|ACCOUNT_SUSPENDED",
            "InvitedAt": "timestamp",
            "UpdatedAt": "timestamp"
        }
    ],
    "UnprocessedAccounts": [
        {
            "AccountId": "string",
            "ProcessingResult": "string"
        }
    ]
}
```

---

### 12.4 `invite-members`

Invites other AWS accounts to become member accounts.

**Synopsis:**
```bash
aws securityhub invite-members \
    --account-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-ids` | **Yes** | list(string) | -- | Account IDs to invite |

**Output Schema:**
```json
{
    "UnprocessedAccounts": [
        {
            "AccountId": "string",
            "ProcessingResult": "string"
        }
    ]
}
```

---

### 12.5 `list-members`

Lists member accounts. **Paginated operation.**

**Synopsis:**
```bash
aws securityhub list-members \
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
| `--only-associated` | No | boolean | true | Return only associated members |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Members": [
        {
            "AccountId": "string",
            "Email": "string",
            "AdministratorId": "string",
            "MemberStatus": "string",
            "InvitedAt": "timestamp",
            "UpdatedAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 12.6 `disassociate-members`

Disassociates member accounts from the administrator account.

**Synopsis:**
```bash
aws securityhub disassociate-members \
    --account-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-ids` | **Yes** | list(string) | -- | Account IDs to disassociate |

**Output:** None (HTTP 200 on success)

---

### 12.7 `accept-administrator-invitation`

Accepts an invitation to become a member account.

**Synopsis:**
```bash
aws securityhub accept-administrator-invitation \
    --administrator-id <value> \
    --invitation-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--administrator-id` | **Yes** | string | -- | Account ID of the administrator |
| `--invitation-id` | **Yes** | string | -- | Invitation ID |

**Output:** None (HTTP 200 on success)

---

### 12.8 `disassociate-from-administrator-account`

Disassociates the current member account from its administrator.

**Synopsis:**
```bash
aws securityhub disassociate-from-administrator-account \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output:** None (HTTP 200 on success)

---

### 12.9 `get-administrator-account`

Returns the administrator account for the current member account.

**Synopsis:**
```bash
aws securityhub get-administrator-account \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "Administrator": {
        "AccountId": "string",
        "InvitationId": "string",
        "InvitedAt": "timestamp",
        "MemberStatus": "string"
    }
}
```

---

### 12.10 `get-invitations-count`

Returns the count of pending invitations.

**Synopsis:**
```bash
aws securityhub get-invitations-count \
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

### 12.11 `list-invitations`

Lists pending invitations. **Paginated operation.**

**Synopsis:**
```bash
aws securityhub list-invitations \
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
            "InvitedAt": "timestamp",
            "MemberStatus": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 12.12 `decline-invitations`

Declines invitations to become a member account.

**Synopsis:**
```bash
aws securityhub decline-invitations \
    --account-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-ids` | **Yes** | list(string) | -- | Account IDs of invitations to decline |

**Output Schema:**
```json
{
    "UnprocessedAccounts": [
        {
            "AccountId": "string",
            "ProcessingResult": "string"
        }
    ]
}
```

---

### 12.13 `delete-invitations`

Deletes invitations to become a member account.

**Synopsis:**
```bash
aws securityhub delete-invitations \
    --account-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-ids` | **Yes** | list(string) | -- | Account IDs of invitations to delete |

**Output Schema:**
```json
{
    "UnprocessedAccounts": [
        {
            "AccountId": "string",
            "ProcessingResult": "string"
        }
    ]
}
```
