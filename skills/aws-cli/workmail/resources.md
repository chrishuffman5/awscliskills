# Resources

### 4.1 `create-resource`

Creates a room or equipment resource in a WorkMail organization.

**Synopsis:**
```bash
aws workmail create-resource \
    --organization-id <value> \
    --name <value> \
    --type <value> \
    [--description <value>] \
    [--hidden-from-global-address-list | --no-hidden-from-global-address-list] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--name` | **Yes** | string | -- | Resource name (1-20 chars) |
| `--type` | **Yes** | string | -- | Resource type: `ROOM` or `EQUIPMENT` |
| `--description` | No | string | None | Resource description (1-64 chars) |
| `--hidden-from-global-address-list` | No | boolean | false | Hide from address book |

**Output Schema:**
```json
{
    "ResourceId": "string"
}
```

---

### 4.2 `describe-resource`

Describes a resource including booking options and state.

**Synopsis:**
```bash
aws workmail describe-resource \
    --organization-id <value> \
    --resource-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--resource-id` | **Yes** | string | -- | Resource ID, name, or email |

**Output Schema:**
```json
{
    "ResourceId": "string",
    "Email": "string",
    "Name": "string",
    "Type": "ROOM|EQUIPMENT",
    "BookingOptions": {
        "AutoAcceptRequests": "boolean",
        "AutoDeclineRecurringRequests": "boolean",
        "AutoDeclineConflictingRequests": "boolean"
    },
    "State": "ENABLED|DISABLED|DELETED",
    "EnabledDate": "timestamp",
    "DisabledDate": "timestamp",
    "Description": "string",
    "HiddenFromGlobalAddressList": "boolean"
}
```

---

### 4.3 `list-resources`

Lists resources in an organization. **Paginated operation.**

**Synopsis:**
```bash
aws workmail list-resources \
    --organization-id <value> \
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
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--filters` | No | structure | None | Filter by name prefix, email prefix, or state |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "Resources": [
        {
            "Id": "string",
            "Email": "string",
            "Name": "string",
            "Type": "ROOM|EQUIPMENT",
            "State": "ENABLED|DISABLED|DELETED",
            "EnabledDate": "timestamp",
            "DisabledDate": "timestamp",
            "Description": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.4 `update-resource`

Updates resource properties including booking options.

**Synopsis:**
```bash
aws workmail update-resource \
    --organization-id <value> \
    --resource-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--type <value>] \
    [--booking-options <value>] \
    [--hidden-from-global-address-list | --no-hidden-from-global-address-list] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--resource-id` | **Yes** | string | -- | Resource ID |
| `--name` | No | string | None | Updated resource name |
| `--description` | No | string | None | Updated description |
| `--type` | No | string | None | Updated type: `ROOM` or `EQUIPMENT` |
| `--booking-options` | No | structure | None | Updated booking options |
| `--hidden-from-global-address-list` | No | boolean | None | Hide from address book |

**BookingOptions structure:**
```json
{
    "AutoAcceptRequests": true,
    "AutoDeclineRecurringRequests": false,
    "AutoDeclineConflictingRequests": true
}
```

**Output:** None

---

### 4.5 `delete-resource`

Deletes a resource from a WorkMail organization.

**Synopsis:**
```bash
aws workmail delete-resource \
    --organization-id <value> \
    --resource-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--resource-id` | **Yes** | string | -- | Resource ID to delete |

**Output:** None

---

### 4.6 `associate-delegate-to-resource`

Associates a delegate to a resource for booking management.

**Synopsis:**
```bash
aws workmail associate-delegate-to-resource \
    --organization-id <value> \
    --resource-id <value> \
    --entity-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--resource-id` | **Yes** | string | -- | Resource ID |
| `--entity-id` | **Yes** | string | -- | Delegate entity ID (user or group) |

**Output:** None

---

### 4.7 `disassociate-delegate-from-resource`

Removes a delegate from a resource.

**Synopsis:**
```bash
aws workmail disassociate-delegate-from-resource \
    --organization-id <value> \
    --resource-id <value> \
    --entity-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--resource-id` | **Yes** | string | -- | Resource ID |
| `--entity-id` | **Yes** | string | -- | Delegate entity ID to remove |

**Output:** None

---

### 4.8 `list-resource-delegates`

Lists delegates for a resource. **Paginated operation.**

**Synopsis:**
```bash
aws workmail list-resource-delegates \
    --organization-id <value> \
    --resource-id <value> \
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
| `--resource-id` | **Yes** | string | -- | Resource ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "Delegates": [
        {
            "Id": "string",
            "Type": "GROUP|USER"
        }
    ],
    "NextToken": "string"
}
```
