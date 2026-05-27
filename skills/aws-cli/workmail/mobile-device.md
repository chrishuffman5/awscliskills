# Mobile Device Access

### 10.1 `create-mobile-device-access-rule`

Creates a mobile device access rule for an organization.

**Synopsis:**
```bash
aws workmail create-mobile-device-access-rule \
    --organization-id <value> \
    --name <value> \
    --effect <value> \
    [--client-token <value>] \
    [--description <value>] \
    [--device-types <value>] \
    [--not-device-types <value>] \
    [--device-models <value>] \
    [--not-device-models <value>] \
    [--device-operating-systems <value>] \
    [--not-device-operating-systems <value>] \
    [--device-user-agents <value>] \
    [--not-device-user-agents <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--name` | **Yes** | string | -- | Rule name (1-64 chars) |
| `--effect` | **Yes** | string | -- | Effect: `ALLOW` or `DENY` |
| `--client-token` | No | string | Auto | Idempotency token |
| `--description` | No | string | None | Rule description (1-256 chars) |
| `--device-types` | No | list | None | Device types to match (max 10) |
| `--not-device-types` | No | list | None | Device types to exclude (max 10) |
| `--device-models` | No | list | None | Device models to match (max 10) |
| `--not-device-models` | No | list | None | Device models to exclude (max 10) |
| `--device-operating-systems` | No | list | None | OS patterns to match (max 10) |
| `--not-device-operating-systems` | No | list | None | OS patterns to exclude (max 10) |
| `--device-user-agents` | No | list | None | User agents to match (max 10) |
| `--not-device-user-agents` | No | list | None | User agents to exclude (max 10) |

**Output Schema:**
```json
{
    "MobileDeviceAccessRuleId": "string"
}
```

---

### 10.2 `list-mobile-device-access-rules`

Lists mobile device access rules for an organization.

**Synopsis:**
```bash
aws workmail list-mobile-device-access-rules \
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
            "MobileDeviceAccessRuleId": "string",
            "Name": "string",
            "Description": "string",
            "Effect": "ALLOW|DENY",
            "DeviceTypes": ["string"],
            "NotDeviceTypes": ["string"],
            "DeviceModels": ["string"],
            "NotDeviceModels": ["string"],
            "DeviceOperatingSystems": ["string"],
            "NotDeviceOperatingSystems": ["string"],
            "DeviceUserAgents": ["string"],
            "NotDeviceUserAgents": ["string"],
            "DateCreated": "timestamp",
            "DateModified": "timestamp"
        }
    ]
}
```

---

### 10.3 `update-mobile-device-access-rule`

Updates a mobile device access rule.

**Synopsis:**
```bash
aws workmail update-mobile-device-access-rule \
    --organization-id <value> \
    --mobile-device-access-rule-id <value> \
    --name <value> \
    --effect <value> \
    [--description <value>] \
    [--device-types <value>] \
    [--not-device-types <value>] \
    [--device-models <value>] \
    [--not-device-models <value>] \
    [--device-operating-systems <value>] \
    [--not-device-operating-systems <value>] \
    [--device-user-agents <value>] \
    [--not-device-user-agents <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--mobile-device-access-rule-id` | **Yes** | string | -- | Rule ID to update |
| `--name` | **Yes** | string | -- | Updated rule name |
| `--effect` | **Yes** | string | -- | Updated effect: `ALLOW` or `DENY` |
| `--description` | No | string | None | Updated description |
| `--device-types` | No | list | None | Updated device types to match |
| `--not-device-types` | No | list | None | Updated device types to exclude |
| `--device-models` | No | list | None | Updated device models to match |
| `--not-device-models` | No | list | None | Updated device models to exclude |
| `--device-operating-systems` | No | list | None | Updated OS patterns to match |
| `--not-device-operating-systems` | No | list | None | Updated OS patterns to exclude |
| `--device-user-agents` | No | list | None | Updated user agents to match |
| `--not-device-user-agents` | No | list | None | Updated user agents to exclude |

**Output:** None

---

### 10.4 `delete-mobile-device-access-rule`

Deletes a mobile device access rule.

**Synopsis:**
```bash
aws workmail delete-mobile-device-access-rule \
    --organization-id <value> \
    --mobile-device-access-rule-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--mobile-device-access-rule-id` | **Yes** | string | -- | Rule ID to delete |

**Output:** None

---

### 10.5 `get-mobile-device-access-effect`

Tests the effect of mobile device access rules for a given device context.

**Synopsis:**
```bash
aws workmail get-mobile-device-access-effect \
    --organization-id <value> \
    [--device-type <value>] \
    [--device-model <value>] \
    [--device-operating-system <value>] \
    [--device-user-agent <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--device-type` | No | string | None | Device type to test |
| `--device-model` | No | string | None | Device model to test |
| `--device-operating-system` | No | string | None | OS to test |
| `--device-user-agent` | No | string | None | User agent to test |

**Output Schema:**
```json
{
    "Effect": "ALLOW|DENY",
    "MatchedRules": [
        {
            "MobileDeviceAccessRuleId": "string",
            "Name": "string"
        }
    ]
}
```

---

### 10.6 `put-mobile-device-access-override`

Creates or updates a mobile device access override for a specific user and device.

**Synopsis:**
```bash
aws workmail put-mobile-device-access-override \
    --organization-id <value> \
    --user-id <value> \
    --device-id <value> \
    --effect <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--user-id` | **Yes** | string | -- | User ID, username, or email |
| `--device-id` | **Yes** | string | -- | Mobile device ID (1-32 chars) |
| `--effect` | **Yes** | string | -- | Effect: `ALLOW` or `DENY` |
| `--description` | No | string | None | Override description (1-256 chars) |

**Output:** None

---

### 10.7 `get-mobile-device-access-override`

Gets a mobile device access override for a specific user and device.

**Synopsis:**
```bash
aws workmail get-mobile-device-access-override \
    --organization-id <value> \
    --user-id <value> \
    --device-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--user-id` | **Yes** | string | -- | User ID, username, or email |
| `--device-id` | **Yes** | string | -- | Mobile device ID |

**Output Schema:**
```json
{
    "UserId": "string",
    "DeviceId": "string",
    "Effect": "ALLOW|DENY",
    "Description": "string",
    "DateCreated": "timestamp",
    "DateModified": "timestamp"
}
```

---

### 10.8 `delete-mobile-device-access-override`

Deletes a mobile device access override.

**Synopsis:**
```bash
aws workmail delete-mobile-device-access-override \
    --organization-id <value> \
    --user-id <value> \
    --device-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--user-id` | **Yes** | string | -- | User ID, username, or email |
| `--device-id` | **Yes** | string | -- | Mobile device ID |

**Output:** None

---

### 10.9 `list-mobile-device-access-overrides`

Lists mobile device access overrides. **Paginated operation.**

**Synopsis:**
```bash
aws workmail list-mobile-device-access-overrides \
    --organization-id <value> \
    [--user-id <value>] \
    [--device-id <value>] \
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
| `--user-id` | No | string | None | Filter by user ID |
| `--device-id` | No | string | None | Filter by device ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "Overrides": [
        {
            "UserId": "string",
            "DeviceId": "string",
            "Effect": "ALLOW|DENY",
            "Description": "string",
            "DateCreated": "timestamp",
            "DateModified": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
