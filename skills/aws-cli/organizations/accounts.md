# Accounts

### 2.1 `create-account`

Creates a new AWS account in the organization. The account is automatically a member of the organization.

**Synopsis:**
```bash
aws organizations create-account \
    --email <value> \
    --account-name <value> \
    [--role-name <value>] \
    [--iam-user-access-to-billing <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--email` | **Yes** | string | -- | Email address for the root user of the new account |
| `--account-name` | **Yes** | string | -- | Friendly name for the new account |
| `--role-name` | No | string | `OrganizationAccountAccessRole` | Name of the IAM role for cross-account access |
| `--iam-user-access-to-billing` | No | string | `ALLOW` | IAM user access to billing: `ALLOW` or `DENY` |
| `--tags` | No | list | None | Tags for the account. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "CreateAccountStatus": {
        "Id": "string",
        "AccountName": "string",
        "State": "IN_PROGRESS|SUCCEEDED|FAILED",
        "RequestedTimestamp": "timestamp",
        "CompletedTimestamp": "timestamp",
        "AccountId": "string",
        "GovCloudAccountId": "string",
        "FailureReason": "ACCOUNT_LIMIT_EXCEEDED|EMAIL_ALREADY_EXISTS|INVALID_ADDRESS|INVALID_EMAIL|CONCURRENT_ACCOUNT_MODIFICATION|INTERNAL_FAILURE|GOVCLOUD_ACCOUNT_ALREADY_EXISTS|MISSING_BUSINESS_VALIDATION|FAILED_BUSINESS_VALIDATION|PENDING_BUSINESS_VALIDATION|INVALID_IDENTITY_FOR_BUSINESS_VALIDATION|UNKNOWN_BUSINESS_VALIDATION|MISSING_PAYMENT_INSTRUMENT|INVALID_PAYMENT_INSTRUMENT|UPDATE_EXISTING_RESOURCE_POLICY_WITH_TAGS_NOT_SUPPORTED"
    }
}
```

---

### 2.2 `create-gov-cloud-account`

Creates an AWS GovCloud (US) account and a standard commercial account that is linked to it.

**Synopsis:**
```bash
aws organizations create-gov-cloud-account \
    --email <value> \
    --account-name <value> \
    [--role-name <value>] \
    [--iam-user-access-to-billing <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--email` | **Yes** | string | -- | Email address for the root user |
| `--account-name` | **Yes** | string | -- | Friendly name for the account |
| `--role-name` | No | string | `OrganizationAccountAccessRole` | IAM role name for cross-account access |
| `--iam-user-access-to-billing` | No | string | `ALLOW` | IAM user billing access: `ALLOW` or `DENY` |
| `--tags` | No | list | None | Tags for the account |

**Output Schema:**
```json
{
    "CreateAccountStatus": {
        "Id": "string",
        "AccountName": "string",
        "State": "IN_PROGRESS|SUCCEEDED|FAILED",
        "RequestedTimestamp": "timestamp",
        "CompletedTimestamp": "timestamp",
        "AccountId": "string",
        "GovCloudAccountId": "string",
        "FailureReason": "string"
    }
}
```

---

### 2.3 `close-account`

Closes a member account in the organization. The account transitions to SUSPENDED then CLOSED.

**Synopsis:**
```bash
aws organizations close-account \
    --account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | 12-digit account ID to close |

**Output Schema:**
```json
{}
```

---

### 2.4 `describe-account`

Retrieves information about an account in the organization.

**Synopsis:**
```bash
aws organizations describe-account \
    --account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | 12-digit account ID |

**Output Schema:**
```json
{
    "Account": {
        "Id": "string",
        "Arn": "string",
        "Email": "string",
        "Name": "string",
        "Status": "ACTIVE|SUSPENDED|PENDING_CLOSURE",
        "JoinedMethod": "INVITED|CREATED",
        "JoinedTimestamp": "timestamp"
    }
}
```

---

### 2.5 `describe-create-account-status`

Returns the current status of an asynchronous account creation request.

**Synopsis:**
```bash
aws organizations describe-create-account-status \
    --create-account-request-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--create-account-request-id` | **Yes** | string | -- | Request ID from `create-account` |

**Output Schema:**
```json
{
    "CreateAccountStatus": {
        "Id": "string",
        "AccountName": "string",
        "State": "IN_PROGRESS|SUCCEEDED|FAILED",
        "RequestedTimestamp": "timestamp",
        "CompletedTimestamp": "timestamp",
        "AccountId": "string",
        "GovCloudAccountId": "string",
        "FailureReason": "string"
    }
}
```

---

### 2.6 `list-accounts`

Lists all accounts in the organization. **Paginated operation.**

**Synopsis:**
```bash
aws organizations list-accounts \
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
    "Accounts": [
        {
            "Id": "string",
            "Arn": "string",
            "Email": "string",
            "Name": "string",
            "Status": "ACTIVE|SUSPENDED|PENDING_CLOSURE",
            "JoinedMethod": "INVITED|CREATED",
            "JoinedTimestamp": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.7 `list-accounts-for-parent`

Lists accounts that are direct children of a specified parent (root or OU). **Paginated operation.**

**Synopsis:**
```bash
aws organizations list-accounts-for-parent \
    --parent-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--parent-id` | **Yes** | string | -- | Root ID (`r-`) or OU ID (`ou-`) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Accounts": [
        {
            "Id": "string",
            "Arn": "string",
            "Email": "string",
            "Name": "string",
            "Status": "ACTIVE|SUSPENDED|PENDING_CLOSURE",
            "JoinedMethod": "INVITED|CREATED",
            "JoinedTimestamp": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.8 `list-create-account-status`

Lists the account creation requests. **Paginated operation.**

**Synopsis:**
```bash
aws organizations list-create-account-status \
    [--states <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--states` | No | list(string) | None | Filter: `IN_PROGRESS`, `SUCCEEDED`, `FAILED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CreateAccountStatuses": [
        {
            "Id": "string",
            "AccountName": "string",
            "State": "IN_PROGRESS|SUCCEEDED|FAILED",
            "RequestedTimestamp": "timestamp",
            "CompletedTimestamp": "timestamp",
            "AccountId": "string",
            "FailureReason": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.9 `move-account`

Moves an account from its current parent to a different parent (root or OU).

**Synopsis:**
```bash
aws organizations move-account \
    --account-id <value> \
    --source-parent-id <value> \
    --destination-parent-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | 12-digit account ID |
| `--source-parent-id` | **Yes** | string | -- | Current parent root or OU ID |
| `--destination-parent-id` | **Yes** | string | -- | Destination root or OU ID |

**Output Schema:**
```json
{}
```

---

### 2.10 `remove-account-from-organization`

Removes a member account from the organization. The account becomes a standalone account.

**Synopsis:**
```bash
aws organizations remove-account-from-organization \
    --account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | 12-digit account ID to remove |

**Output Schema:**
```json
{}
```

---

### 2.11 `invite-account-to-organization`

Sends an invitation to an existing AWS account to join the organization.

**Synopsis:**
```bash
aws organizations invite-account-to-organization \
    --target <value> \
    [--notes <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target` | **Yes** | structure | -- | Target account. Shorthand: `Id=string,Type=ACCOUNT\|ORGANIZATION\|EMAIL` |
| `--notes` | No | string | None | Message to include with the invitation |
| `--tags` | No | list | None | Tags for the account |

**Output Schema:**
```json
{
    "Handshake": {
        "Id": "string",
        "Arn": "string",
        "Parties": [
            {
                "Id": "string",
                "Type": "ACCOUNT|ORGANIZATION|EMAIL"
            }
        ],
        "State": "REQUESTED|OPEN|CANCELED|ACCEPTED|DECLINED|EXPIRED",
        "RequestedTimestamp": "timestamp",
        "ExpirationTimestamp": "timestamp",
        "Action": "INVITE",
        "Resources": []
    }
}
```
