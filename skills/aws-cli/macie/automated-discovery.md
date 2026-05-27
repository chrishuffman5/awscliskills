# Automated Discovery

### 8.1 `get-automated-discovery-configuration`

Retrieves the configuration settings and status of automated sensitive data discovery.

**Synopsis:**
```bash
aws macie2 get-automated-discovery-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "autoEnableOrganizationMembers": "ALL|NEW|NONE",
    "classificationScopeId": "string",
    "disabledAt": "timestamp",
    "firstEnabledAt": "timestamp",
    "lastUpdatedAt": "timestamp",
    "sensitivityInspectionTemplateId": "string",
    "status": "ENABLED|DISABLED"
}
```

---

### 8.2 `update-automated-discovery-configuration`

Enables or disables automated sensitive data discovery and updates configuration settings.

**Synopsis:**
```bash
aws macie2 update-automated-discovery-configuration \
    --status <value> \
    [--auto-enable-organization-members <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--status` | **Yes** | string | -- | Status: `ENABLED` or `DISABLED` |
| `--auto-enable-organization-members` | No | string | None | Auto-enable for org members: `ALL`, `NEW`, `NONE` |

**Output:** None (HTTP 200 on success)

---

### 8.3 `list-automated-discovery-accounts`

Lists the status of automated discovery for member accounts. **Paginated operation.**

**Synopsis:**
```bash
aws macie2 list-automated-discovery-accounts \
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
| `--account-ids` | No | list(string) | None | Account IDs to query |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "items": [
        {
            "accountId": "string",
            "status": "ENABLED|DISABLED"
        }
    ],
    "nextToken": "string"
}
```

---

### 8.4 `batch-update-automated-discovery-accounts`

Changes the status of automated discovery for member accounts.

**Synopsis:**
```bash
aws macie2 batch-update-automated-discovery-accounts \
    --accounts <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--accounts` | **Yes** | list | -- | Account updates |

**Accounts Structure:**
```json
[
    {
        "accountId": "string",
        "status": "ENABLED|DISABLED"
    }
]
```

**Output Schema:**
```json
{
    "errors": [
        {
            "accountId": "string",
            "errorCode": "string"
        }
    ]
}
```
