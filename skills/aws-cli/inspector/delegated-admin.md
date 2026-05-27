# Delegated Admin

### 9.1 `enable-delegated-admin-account`

Enables the Amazon Inspector delegated administrator for your AWS Organizations organization.

**Synopsis:**
```bash
aws inspector2 enable-delegated-admin-account \
    --delegated-admin-account-id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--delegated-admin-account-id` | **Yes** | string | -- | Account ID to designate as delegated admin (12 digits) |
| `--client-token` | No | string | None | Idempotency token (1-64 chars) |

**Output Schema:**
```json
{
    "delegatedAdminAccountId": "string"
}
```

---

### 9.2 `disable-delegated-admin-account`

Disables the Amazon Inspector delegated administrator for your organization.

**Synopsis:**
```bash
aws inspector2 disable-delegated-admin-account \
    --delegated-admin-account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--delegated-admin-account-id` | **Yes** | string | -- | Account ID to remove as delegated admin (12 digits) |

**Output Schema:**
```json
{
    "delegatedAdminAccountId": "string"
}
```

---

### 9.3 `get-delegated-admin-account`

Gets the delegated administrator account for your organization.

**Synopsis:**
```bash
aws inspector2 get-delegated-admin-account \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No command-specific parameters.

**Output Schema:**
```json
{
    "delegatedAdmin": {
        "accountId": "string",
        "relationshipStatus": "CREATED|INVITED|DISABLED|ENABLED|REMOVED|RESIGNED|DELETED|EMAIL_VERIFICATION_IN_PROGRESS|EMAIL_VERIFICATION_FAILED|REGION_DISABLED|ACCOUNT_SUSPENDED|CANNOT_CREATE_DETECTOR_IN_ORG_MASTER"
    }
}
```

---

### 9.4 `list-delegated-admin-accounts`

Lists the delegated admin accounts for your organization. **Paginated.**

**Synopsis:**
```bash
aws inspector2 list-delegated-admin-accounts \
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
    "delegatedAdminAccounts": [
        {
            "accountId": "string",
            "status": "ENABLED|DISABLE_IN_PROGRESS"
        }
    ],
    "nextToken": "string"
}
```
