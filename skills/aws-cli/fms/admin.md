# Admin

### 1.1 `associate-admin-account`

Sets the AWS Firewall Manager default administrator account. Must be called from the Organizations management account.

**Synopsis:**
```bash
aws fms associate-admin-account \
    --admin-account <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--admin-account` | **Yes** | string | -- | AWS account ID to designate as administrator |

**Output Schema:** Empty on success.

---

### 1.2 `disassociate-admin-account`

Disassociates the default Firewall Manager administrator account. Must be called from the Organizations management account.

**Synopsis:**
```bash
aws fms disassociate-admin-account \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No command-specific parameters.

**Output Schema:** Empty on success.

---

### 1.3 `get-admin-account`

Returns the default Firewall Manager administrator account ID.

**Synopsis:**
```bash
aws fms get-admin-account \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No command-specific parameters.

**Output Schema:**
```json
{
    "AdminAccount": "string",
    "RoleStatus": "READY|CREATING|PENDING_DELETION|DELETING|DELETED"
}
```

---

### 1.4 `get-admin-scope`

Returns information about the specified Firewall Manager administrator's scope.

**Synopsis:**
```bash
aws fms get-admin-scope \
    --admin-account <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--admin-account` | **Yes** | string | -- | Administrator account ID |

**Output Schema:**
```json
{
    "AdminScope": {
        "AccountScope": {
            "Accounts": ["string"],
            "AllAccountsEnabled": true|false,
            "ExcludeSpecifiedAccounts": true|false
        },
        "OrganizationalUnitScope": {
            "OrganizationalUnits": ["string"],
            "AllOrganizationalUnitsEnabled": true|false,
            "ExcludeSpecifiedOrganizationalUnits": true|false
        },
        "RegionScope": {
            "Regions": ["string"],
            "AllRegionsEnabled": true|false
        },
        "PolicyTypeScope": {
            "PolicyTypes": ["WAF|WAFV2|SHIELD_ADVANCED|SECURITY_GROUPS_COMMON|SECURITY_GROUPS_CONTENT_AUDIT|SECURITY_GROUPS_USAGE_AUDIT|NETWORK_FIREWALL|DNS_FIREWALL|THIRD_PARTY_FIREWALL|NETWORK_ACL_COMMON"],
            "AllPolicyTypesEnabled": true|false
        }
    },
    "Status": "ONBOARDING|ONBOARDING_COMPLETE|OFFBOARDING|OFFBOARDING_COMPLETE"
}
```

---

### 1.5 `put-admin-account`

Creates or updates a Firewall Manager administrator account with an admin scope.

**Synopsis:**
```bash
aws fms put-admin-account \
    --admin-account <value> \
    [--admin-scope <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--admin-account` | **Yes** | string | -- | Account ID to set as administrator |
| `--admin-scope` | No | structure | None | Admin scope definition (JSON). See `get-admin-scope` output for structure |

**Output Schema:** Empty on success.

---

### 1.6 `list-admin-accounts-for-organization`

Lists all Firewall Manager administrator accounts in the organization. **Paginated.**

**Synopsis:**
```bash
aws fms list-admin-accounts-for-organization \
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
            "AdminAccount": "string",
            "DefaultAdmin": true|false,
            "Status": "ONBOARDING|ONBOARDING_COMPLETE|OFFBOARDING|OFFBOARDING_COMPLETE"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.7 `list-admins-managing-account`

Lists the Firewall Manager administrators that manage a specific account. **Paginated.**

**Synopsis:**
```bash
aws fms list-admins-managing-account \
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
    "AdminAccounts": ["string"],
    "NextToken": "string"
}
```
