# Enrollment

### 1.1 `get-enrollment-status`

Returns the enrollment (opt-in) status of an account to AWS Compute Optimizer.

**Synopsis:**
```bash
aws compute-optimizer get-enrollment-status \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| _(none)_ | -- | -- | -- | No parameters beyond global options |

**Output Schema:**
```json
{
    "status": "Active|Inactive|Pending|Failed",
    "statusReason": "string",
    "memberAccountsEnrolled": true|false,
    "lastUpdatedTimestamp": "timestamp",
    "numberOfMemberAccountsOptedIn": "integer"
}
```

---

### 1.2 `get-enrollment-statuses-for-organization`

Returns the enrollment statuses of member accounts in the organization. **Paginated operation.**

**Synopsis:**
```bash
aws compute-optimizer get-enrollment-statuses-for-organization \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | None | Filter by status. Shorthand: `name=Status,values=string,string ...` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "accountEnrollmentStatuses": [
        {
            "accountId": "string",
            "status": "Active|Inactive|Pending|Failed",
            "statusReason": "string",
            "lastUpdatedTimestamp": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.3 `update-enrollment-status`

Enrolls or unenrolls an account in AWS Compute Optimizer.

**Synopsis:**
```bash
aws compute-optimizer update-enrollment-status \
    --status <value> \
    [--include-member-accounts | --no-include-member-accounts] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--status` | **Yes** | string | -- | Enrollment status: `Active` or `Inactive` |
| `--include-member-accounts` | No | boolean | false | Also enroll all member accounts in the organization |

**Output Schema:**
```json
{
    "status": "Active|Inactive|Pending|Failed",
    "statusReason": "string"
}
```
