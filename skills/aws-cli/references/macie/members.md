# Members

### 11.1 `create-member`

Associates an account with an Amazon Macie administrator account.

**Synopsis:**
```bash
aws macie2 create-member \
    --account <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account` | **Yes** | structure | -- | Account details |
| `--tags` | No | map | None | Tags to add |

**Account Structure:**
```json
{
    "accountId": "string",
    "email": "string"
}
```

**Output Schema:**
```json
{
    "arn": "string"
}
```

---

### 11.2 `delete-member`

Deletes the association between a Macie administrator and a member account.

**Synopsis:**
```bash
aws macie2 delete-member \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Account ID of the member to delete |

**Output:** None (HTTP 200 on success)

---

### 11.3 `get-member`

Retrieves information about a member account.

**Synopsis:**
```bash
aws macie2 get-member \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Account ID of the member |

**Output Schema:**
```json
{
    "accountId": "string",
    "administratorAccountId": "string",
    "arn": "string",
    "email": "string",
    "invitedAt": "timestamp",
    "relationshipStatus": "CREATED|INVITED|DISABLED|ENABLED|REMOVED|RESIGNED|EMAIL_VERIFICATION_IN_PROGRESS|EMAIL_VERIFICATION_FAILED|REGION_DISABLED|ACCOUNT_SUSPENDED|PAUSED",
    "tags": {"string": "string"},
    "updatedAt": "timestamp"
}
```

---

### 11.4 `list-members`

Lists member accounts. **Paginated operation.**

**Synopsis:**
```bash
aws macie2 list-members \
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
| `--only-associated` | No | string | None | Filter by association status |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "members": [
        {
            "accountId": "string",
            "administratorAccountId": "string",
            "arn": "string",
            "email": "string",
            "invitedAt": "timestamp",
            "relationshipStatus": "string",
            "tags": {"string": "string"},
            "updatedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 11.5 `disassociate-member`

Disassociates a member account from its Macie administrator account.

**Synopsis:**
```bash
aws macie2 disassociate-member \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Account ID of the member |

**Output:** None (HTTP 200 on success)

---

### 11.6 `create-invitations`

Sends invitations to one or more accounts.

**Synopsis:**
```bash
aws macie2 create-invitations \
    --account-ids <value> \
    [--disable-email-notification | --no-disable-email-notification] \
    [--message <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-ids` | **Yes** | list(string) | -- | Account IDs to invite |
| `--disable-email-notification` | No | boolean | false | Disable email notification |
| `--message` | No | string | None | Custom message |

**Output Schema:**
```json
{
    "unprocessedAccounts": [
        {
            "accountId": "string",
            "errorCode": "ClientError|InternalError",
            "errorMessage": "string"
        }
    ]
}
```

---

### 11.7 `accept-invitation`

Accepts a Macie membership invitation.

**Synopsis:**
```bash
aws macie2 accept-invitation \
    --invitation-id <value> \
    --administrator-account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--invitation-id` | **Yes** | string | -- | Invitation ID |
| `--administrator-account-id` | **Yes** | string | -- | Administrator account ID |

**Output:** None (HTTP 200 on success)

---

### 11.8 `decline-invitations`

Declines invitations.

**Synopsis:**
```bash
aws macie2 decline-invitations \
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
    "unprocessedAccounts": [
        {
            "accountId": "string",
            "errorCode": "ClientError|InternalError",
            "errorMessage": "string"
        }
    ]
}
```

---

### 11.9 `delete-invitations`

Deletes invitations.

**Synopsis:**
```bash
aws macie2 delete-invitations \
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
    "unprocessedAccounts": [
        {
            "accountId": "string",
            "errorCode": "ClientError|InternalError",
            "errorMessage": "string"
        }
    ]
}
```

---

### 11.10 `list-invitations`

Lists invitations. **Paginated operation.**

**Synopsis:**
```bash
aws macie2 list-invitations \
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
    "invitations": [
        {
            "accountId": "string",
            "invitationId": "string",
            "invitedAt": "timestamp",
            "relationshipStatus": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 11.11 `get-invitations-count`

Returns the number of pending invitations.

**Synopsis:**
```bash
aws macie2 get-invitations-count \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "invitationsCount": "long"
}
```

---

### 11.12 `disassociate-from-administrator-account`

Disassociates the current account from its Macie administrator.

**Synopsis:**
```bash
aws macie2 disassociate-from-administrator-account \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output:** None (HTTP 200 on success)

---

### 11.13 `get-administrator-account`

Returns the administrator account for the current account.

**Synopsis:**
```bash
aws macie2 get-administrator-account \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "administrator": {
        "accountId": "string",
        "invitationId": "string",
        "relationshipStatus": "string",
        "invitedAt": "timestamp"
    }
}
```

---

### 11.14 `update-member-session`

Enables or suspends Macie for a member account.

**Synopsis:**
```bash
aws macie2 update-member-session \
    --id <value> \
    --status <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Account ID of the member |
| `--status` | **Yes** | string | -- | Status: `ENABLED` or `PAUSED` |

**Output:** None (HTTP 200 on success)
