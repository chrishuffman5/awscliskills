# Impersonation

### 9.1 `create-impersonation-role`

Creates an impersonation role for accessing user mailboxes programmatically.

**Synopsis:**
```bash
aws workmail create-impersonation-role \
    --organization-id <value> \
    --name <value> \
    --type <value> \
    --rules <value> \
    [--client-token <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--name` | **Yes** | string | -- | Role name (1-64 chars) |
| `--type` | **Yes** | string | -- | Role type: `FULL_ACCESS` or `READ_ONLY` |
| `--rules` | **Yes** | list | -- | Impersonation rules (0-10 rules) |
| `--client-token` | No | string | Auto | Idempotency token |
| `--description` | No | string | None | Role description (1-256 chars) |

**Rules structure:**
```json
[
    {
        "ImpersonationRuleId": "string",
        "Effect": "ALLOW|DENY",
        "Name": "string",
        "Description": "string",
        "TargetUsers": ["string"],
        "NotTargetUsers": ["string"]
    }
]
```

**Output Schema:**
```json
{
    "ImpersonationRoleId": "string"
}
```

---

### 9.2 `get-impersonation-role`

Gets details about an impersonation role.

**Synopsis:**
```bash
aws workmail get-impersonation-role \
    --organization-id <value> \
    --impersonation-role-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--impersonation-role-id` | **Yes** | string | -- | Impersonation role ID |

**Output Schema:**
```json
{
    "ImpersonationRoleId": "string",
    "Name": "string",
    "Type": "FULL_ACCESS|READ_ONLY",
    "Description": "string",
    "Rules": [
        {
            "ImpersonationRuleId": "string",
            "Name": "string",
            "Description": "string",
            "Effect": "ALLOW|DENY",
            "TargetUsers": ["string"],
            "NotTargetUsers": ["string"]
        }
    ],
    "DateCreated": "timestamp",
    "DateModified": "timestamp"
}
```

---

### 9.3 `list-impersonation-roles`

Lists impersonation roles for an organization. **Paginated operation.**

**Synopsis:**
```bash
aws workmail list-impersonation-roles \
    --organization-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "Roles": [
        {
            "ImpersonationRoleId": "string",
            "Name": "string",
            "Type": "FULL_ACCESS|READ_ONLY",
            "DateCreated": "timestamp",
            "DateModified": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.4 `update-impersonation-role`

Updates an impersonation role's name, description, type, or rules.

**Synopsis:**
```bash
aws workmail update-impersonation-role \
    --organization-id <value> \
    --impersonation-role-id <value> \
    --name <value> \
    --type <value> \
    --rules <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--impersonation-role-id` | **Yes** | string | -- | Impersonation role ID |
| `--name` | **Yes** | string | -- | Updated role name |
| `--type` | **Yes** | string | -- | Updated type: `FULL_ACCESS` or `READ_ONLY` |
| `--rules` | **Yes** | list | -- | Updated rules (0-10) |
| `--description` | No | string | None | Updated description |

**Output:** None

---

### 9.5 `delete-impersonation-role`

Deletes an impersonation role.

**Synopsis:**
```bash
aws workmail delete-impersonation-role \
    --organization-id <value> \
    --impersonation-role-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--impersonation-role-id` | **Yes** | string | -- | Impersonation role ID to delete |

**Output:** None

---

### 9.6 `assume-impersonation-role`

Assumes an impersonation role and returns a token for EWS access.

**Synopsis:**
```bash
aws workmail assume-impersonation-role \
    --organization-id <value> \
    --impersonation-role-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--impersonation-role-id` | **Yes** | string | -- | Impersonation role ID to assume |

**Output Schema:**
```json
{
    "Token": "string",
    "ExpiresIn": "long"
}
```

---

### 9.7 `get-impersonation-role-effect`

Tests the effect of an impersonation role on a specific user.

**Synopsis:**
```bash
aws workmail get-impersonation-role-effect \
    --organization-id <value> \
    --impersonation-role-id <value> \
    --target-user <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--impersonation-role-id` | **Yes** | string | -- | Impersonation role ID |
| `--target-user` | **Yes** | string | -- | Target user ID to test |

**Output Schema:**
```json
{
    "Type": "FULL_ACCESS|READ_ONLY",
    "Effect": "ALLOW|DENY",
    "MatchedRules": [
        {
            "ImpersonationRuleId": "string",
            "Name": "string"
        }
    ]
}
```
