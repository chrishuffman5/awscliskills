# Organization

### 13.1 `enable-organization-admin-account`

Designates the Security Hub administrator account for an organization.

**Synopsis:**
```bash
aws securityhub enable-organization-admin-account \
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

### 13.2 `disable-organization-admin-account`

Disables a Security Hub administrator account.

**Synopsis:**
```bash
aws securityhub disable-organization-admin-account \
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

### 13.3 `list-organization-admin-accounts`

Lists Security Hub administrator accounts. **Paginated operation.**

**Synopsis:**
```bash
aws securityhub list-organization-admin-accounts \
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
            "AccountId": "string",
            "Status": "ENABLED|DISABLE_IN_PROGRESS"
        }
    ],
    "NextToken": "string"
}
```

---

### 13.4 `describe-organization-configuration`

Returns information about the Organizations configuration for Security Hub.

**Synopsis:**
```bash
aws securityhub describe-organization-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "AutoEnable": "boolean",
    "MemberAccountLimitReached": "boolean",
    "AutoEnableStandards": "NONE|DEFAULT",
    "OrganizationConfiguration": {
        "ConfigurationType": "CENTRAL|LOCAL",
        "Status": "PENDING|ENABLED|FAILED",
        "StatusMessage": "string"
    }
}
```

---

### 13.5 `update-organization-configuration`

Updates the Organizations configuration for Security Hub.

**Synopsis:**
```bash
aws securityhub update-organization-configuration \
    --auto-enable | --no-auto-enable \
    [--auto-enable-standards <value>] \
    [--organization-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-enable` / `--no-auto-enable` | **Yes** | boolean | -- | Auto-enable Security Hub for new member accounts |
| `--auto-enable-standards` | No | string | None | Auto-enable standards: `NONE` or `DEFAULT` |
| `--organization-configuration` | No | structure | None | Organization configuration type |

**Organization Configuration Structure:**
```json
{
    "ConfigurationType": "CENTRAL|LOCAL"
}
```

**Output:** None (HTTP 200 on success)
