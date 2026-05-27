# Organization

### 12.1 `enable-organization-admin-account`

Designates an account as the delegated Amazon Macie administrator for the organization.

**Synopsis:**
```bash
aws macie2 enable-organization-admin-account \
    --admin-account-id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--admin-account-id` | **Yes** | string | -- | Account ID to designate as admin |
| `--client-token` | No | string | None | Idempotency token |

**Output:** None (HTTP 200 on success)

---

### 12.2 `disable-organization-admin-account`

Disables an account as the delegated Macie administrator.

**Synopsis:**
```bash
aws macie2 disable-organization-admin-account \
    --admin-account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--admin-account-id` | **Yes** | string | -- | Admin account ID to disable |

**Output:** None (HTTP 200 on success)

---

### 12.3 `list-organization-admin-accounts`

Lists the Macie administrator accounts for the organization. **Paginated operation.**

**Synopsis:**
```bash
aws macie2 list-organization-admin-accounts \
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
    "adminAccounts": [
        {
            "accountId": "string",
            "status": "ENABLED|DISABLING_IN_PROGRESS"
        }
    ],
    "nextToken": "string"
}
```

---

### 12.4 `describe-organization-configuration`

Returns the Macie configuration settings for the organization.

**Synopsis:**
```bash
aws macie2 describe-organization-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "autoEnable": "boolean",
    "maxAccountLimitReached": "boolean"
}
```

---

### 12.5 `update-organization-configuration`

Updates the Macie configuration settings for the organization.

**Synopsis:**
```bash
aws macie2 update-organization-configuration \
    --auto-enable | --no-auto-enable \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-enable` / `--no-auto-enable` | **Yes** | boolean | -- | Auto-enable Macie for new member accounts |

**Output:** None (HTTP 200 on success)
