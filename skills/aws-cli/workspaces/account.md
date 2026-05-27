# Account

### 7.1 `describe-account`

Describes the account-level settings for Amazon WorkSpaces, including Bring Your Own License (BYOL) status.

**Synopsis:**
```bash
aws workspaces describe-account \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| -- | -- | -- | -- | No required parameters |

**Output Schema:**
```json
{
    "DedicatedTenancySupport": "ENABLED|DISABLED",
    "DedicatedTenancyManagementCidrRange": "string",
    "DedicatedTenancyAccountType": "SOURCE_ACCOUNT|TARGET_ACCOUNT"
}
```

---

### 7.2 `describe-account-modifications`

Describes modifications to the account-level settings. **Paginated operation.**

**Synopsis:**
```bash
aws workspaces describe-account-modifications \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AccountModifications": [
        {
            "ModificationState": "PENDING|COMPLETED|FAILED",
            "DedicatedTenancySupport": "ENABLED|DISABLED",
            "DedicatedTenancyManagementCidrRange": "string",
            "StartTime": "timestamp",
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.3 `modify-account`

Modifies the account-level settings for Amazon WorkSpaces. Currently supports configuring dedicated tenancy and BYOL.

**Synopsis:**
```bash
aws workspaces modify-account \
    [--dedicated-tenancy-support <value>] \
    [--dedicated-tenancy-management-cidr-range <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dedicated-tenancy-support` | No | string | None | Dedicated tenancy support: `ENABLED` |
| `--dedicated-tenancy-management-cidr-range` | No | string | None | Management CIDR range for dedicated tenancy (e.g., `10.0.0.0/16`) |

**Output Schema:**
```json
{}
```

---

### 7.4 `create-tags`

Creates or updates the specified tags for the specified WorkSpaces resource.

**Synopsis:**
```bash
aws workspaces create-tags \
    --resource-id <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | The resource ID (WorkSpace ID, directory ID, bundle ID, image ID, IP group ID, or connection alias ID) |
| `--tags` | **Yes** | list | -- | Tags to create or update. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{}
```

---

### 7.5 `delete-tags`

Deletes the specified tags from a WorkSpaces resource.

**Synopsis:**
```bash
aws workspaces delete-tags \
    --resource-id <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | The resource ID |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to delete |

**Output Schema:**
```json
{}
```

---

### 7.6 `describe-tags`

Describes the specified tags for the specified WorkSpaces resource.

**Synopsis:**
```bash
aws workspaces describe-tags \
    --resource-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | The resource ID |

**Output Schema:**
```json
{
    "TagList": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```
