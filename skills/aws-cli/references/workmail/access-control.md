# Access Control

### 8.1 `put-access-control-rule`

Creates or updates an access control rule for a WorkMail organization.

**Synopsis:**
```bash
aws workmail put-access-control-rule \
    --name <value> \
    --effect <value> \
    --description <value> \
    --organization-id <value> \
    [--ip-ranges <value>] \
    [--not-ip-ranges <value>] \
    [--actions <value>] \
    [--not-actions <value>] \
    [--user-ids <value>] \
    [--not-user-ids <value>] \
    [--impersonation-role-ids <value>] \
    [--not-impersonation-role-ids <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Rule name (1-64 chars) |
| `--effect` | **Yes** | string | -- | Rule effect: `ALLOW` or `DENY` |
| `--description` | **Yes** | string | -- | Rule description (0-255 chars) |
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--ip-ranges` | No | list | None | IPv4 CIDR ranges to include (max 1024) |
| `--not-ip-ranges` | No | list | None | IPv4 CIDR ranges to exclude (max 1024) |
| `--actions` | No | list | None | Protocol actions to include (max 10): `ActiveSync`, `AutoDiscover`, `EWS`, `IMAP`, `SMTP`, `WindowsOutlook`, `WebMail` |
| `--not-actions` | No | list | None | Protocol actions to exclude (max 10) |
| `--user-ids` | No | list | None | User IDs to include (max 10) |
| `--not-user-ids` | No | list | None | User IDs to exclude (max 10) |
| `--impersonation-role-ids` | No | list | None | Impersonation role IDs to include (max 10) |
| `--not-impersonation-role-ids` | No | list | None | Impersonation role IDs to exclude (max 10) |

**Output:** None

---

### 8.2 `list-access-control-rules`

Lists access control rules for an organization.

**Synopsis:**
```bash
aws workmail list-access-control-rules \
    --organization-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |

**Output Schema:**
```json
{
    "Rules": [
        {
            "Name": "string",
            "Effect": "ALLOW|DENY",
            "Description": "string",
            "IpRanges": ["string"],
            "NotIpRanges": ["string"],
            "Actions": ["string"],
            "NotActions": ["string"],
            "UserIds": ["string"],
            "NotUserIds": ["string"],
            "DateCreated": "timestamp",
            "DateModified": "timestamp",
            "ImpersonationRoleIds": ["string"],
            "NotImpersonationRoleIds": ["string"]
        }
    ]
}
```

---

### 8.3 `delete-access-control-rule`

Deletes an access control rule.

**Synopsis:**
```bash
aws workmail delete-access-control-rule \
    --organization-id <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--name` | **Yes** | string | -- | Rule name to delete |

**Output:** None

---

### 8.4 `get-access-control-effect`

Gets the access control effect for a given context (IP, action, user, impersonation role).

**Synopsis:**
```bash
aws workmail get-access-control-effect \
    --organization-id <value> \
    --ip-address <value> \
    --action <value> \
    [--user-id <value>] \
    [--impersonation-role-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--ip-address` | **Yes** | string | -- | IPv4 address to test |
| `--action` | **Yes** | string | -- | Protocol action to test |
| `--user-id` | No | string | None | User ID to test |
| `--impersonation-role-id` | No | string | None | Impersonation role ID to test |

**Output Schema:**
```json
{
    "Effect": "ALLOW|DENY",
    "MatchedRules": [
        {
            "Name": "string",
            "Effect": "ALLOW|DENY"
        }
    ]
}
```
