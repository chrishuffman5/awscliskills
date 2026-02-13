# Members

### 2.1 `create-members`

Sends invitations to the specified accounts. Each invited account becomes a member of the behavior graph.

**Synopsis:**
```bash
aws detective create-members \
    --graph-arn <value> \
    --accounts <value> \
    [--message <value>] \
    [--disable-email-notification | --no-disable-email-notification] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-arn` | **Yes** | string | -- | ARN of the behavior graph |
| `--accounts` | **Yes** | list | -- | Accounts to invite (max 50) |
| `--message` | No | string | None | Custom invitation message |
| `--disable-email-notification` | No | boolean | false | Disable email notification |

**Accounts Structure:**
```json
[
    {
        "AccountId": "string",
        "EmailAddress": "string"
    }
]
```

**Output Schema:**
```json
{
    "Members": [
        {
            "AccountId": "string",
            "EmailAddress": "string",
            "GraphArn": "string",
            "AdministratorId": "string",
            "Status": "INVITED|VERIFICATION_IN_PROGRESS|VERIFICATION_FAILED|ENABLED|ACCEPTED_BUT_DISABLED",
            "DisabledReason": "VOLUME_TOO_HIGH|VOLUME_UNKNOWN",
            "InvitedTime": "timestamp",
            "UpdatedTime": "timestamp",
            "VolumeUsageInBytes": "long",
            "VolumeUsageUpdatedTime": "timestamp",
            "PercentOfGraphUtilization": "double",
            "PercentOfGraphUtilizationUpdatedTime": "timestamp",
            "InvitationType": "INVITATION|ORGANIZATION",
            "VolumeUsageByDatasourcePackage": {},
            "DatasourcePackageIngestStates": {}
        }
    ],
    "UnprocessedAccounts": [
        {
            "AccountId": "string",
            "Reason": "string"
        }
    ]
}
```

---

### 2.2 `delete-members`

Removes the specified member accounts from the behavior graph.

**Synopsis:**
```bash
aws detective delete-members \
    --graph-arn <value> \
    --account-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-arn` | **Yes** | string | -- | ARN of the behavior graph |
| `--account-ids` | **Yes** | list(string) | -- | Account IDs to remove (max 50) |

**Output Schema:**
```json
{
    "AccountIds": ["string"],
    "UnprocessedAccounts": [
        {
            "AccountId": "string",
            "Reason": "string"
        }
    ]
}
```

---

### 2.3 `get-members`

Returns details about the member accounts in a behavior graph.

**Synopsis:**
```bash
aws detective get-members \
    --graph-arn <value> \
    --account-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-arn` | **Yes** | string | -- | ARN of the behavior graph |
| `--account-ids` | **Yes** | list(string) | -- | Account IDs to retrieve (max 50) |

**Output Schema:**
```json
{
    "MemberDetails": [
        {
            "AccountId": "string",
            "EmailAddress": "string",
            "GraphArn": "string",
            "AdministratorId": "string",
            "Status": "INVITED|VERIFICATION_IN_PROGRESS|VERIFICATION_FAILED|ENABLED|ACCEPTED_BUT_DISABLED",
            "DisabledReason": "VOLUME_TOO_HIGH|VOLUME_UNKNOWN",
            "InvitedTime": "timestamp",
            "UpdatedTime": "timestamp",
            "VolumeUsageInBytes": "long",
            "InvitationType": "INVITATION|ORGANIZATION",
            "DatasourcePackageIngestStates": {
                "string": "STARTED|STOPPED|DISABLED"
            }
        }
    ],
    "UnprocessedAccounts": [
        {
            "AccountId": "string",
            "Reason": "string"
        }
    ]
}
```

---

### 2.4 `list-members`

Lists member accounts in a behavior graph. **Paginated operation.**

**Synopsis:**
```bash
aws detective list-members \
    --graph-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-arn` | **Yes** | string | -- | ARN of the behavior graph |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "MemberDetails": [
        {
            "AccountId": "string",
            "EmailAddress": "string",
            "GraphArn": "string",
            "Status": "string",
            "InvitedTime": "timestamp",
            "UpdatedTime": "timestamp",
            "InvitationType": "INVITATION|ORGANIZATION"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.5 `accept-invitation`

Accepts an invitation to contribute data to a behavior graph.

**Synopsis:**
```bash
aws detective accept-invitation \
    --graph-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-arn` | **Yes** | string | -- | ARN of the behavior graph |

**Output:** None (HTTP 200 on success)

---

### 2.6 `reject-invitation`

Rejects an invitation to contribute data to a behavior graph.

**Synopsis:**
```bash
aws detective reject-invitation \
    --graph-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-arn` | **Yes** | string | -- | ARN of the behavior graph |

**Output:** None (HTTP 200 on success)

---

### 2.7 `disassociate-membership`

Removes the calling account from the specified behavior graph.

**Synopsis:**
```bash
aws detective disassociate-membership \
    --graph-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-arn` | **Yes** | string | -- | ARN of the behavior graph |

**Output:** None (HTTP 200 on success)

---

### 2.8 `list-invitations`

Lists the invitations sent to the current account. **Paginated operation.**

**Synopsis:**
```bash
aws detective list-invitations \
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
            "EmailAddress": "string",
            "GraphArn": "string",
            "AdministratorId": "string",
            "Status": "string",
            "InvitedTime": "timestamp",
            "UpdatedTime": "timestamp",
            "InvitationType": "INVITATION|ORGANIZATION"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.9 `start-monitoring-member`

Sends a request to enable data ingest for a member account that had data ingest stopped.

**Synopsis:**
```bash
aws detective start-monitoring-member \
    --graph-arn <value> \
    --account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-arn` | **Yes** | string | -- | ARN of the behavior graph |
| `--account-id` | **Yes** | string | -- | Account ID to start monitoring |

**Output:** None (HTTP 200 on success)
