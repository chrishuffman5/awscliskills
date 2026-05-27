# Groups

### 3.1 `create-group`

Creates a group in a WorkMail organization.

**Synopsis:**
```bash
aws workmail create-group \
    --organization-id <value> \
    --name <value> \
    [--hidden-from-global-address-list | --no-hidden-from-global-address-list] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--name` | **Yes** | string | -- | Group name (1-256 chars) |
| `--hidden-from-global-address-list` | No | boolean | false | Hide from address book |

**Output Schema:**
```json
{
    "GroupId": "string"
}
```

---

### 3.2 `describe-group`

Describes a group including state and email.

**Synopsis:**
```bash
aws workmail describe-group \
    --organization-id <value> \
    --group-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--group-id` | **Yes** | string | -- | Group ID, name, or email |

**Output Schema:**
```json
{
    "GroupId": "string",
    "Name": "string",
    "Email": "string",
    "State": "ENABLED|DISABLED|DELETED",
    "EnabledDate": "timestamp",
    "DisabledDate": "timestamp",
    "HiddenFromGlobalAddressList": "boolean"
}
```

---

### 3.3 `list-groups`

Lists groups in an organization. **Paginated operation.**

**Synopsis:**
```bash
aws workmail list-groups \
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
    "Groups": [
        {
            "Id": "string",
            "Email": "string",
            "Name": "string",
            "State": "ENABLED|DISABLED|DELETED",
            "EnabledDate": "timestamp",
            "DisabledDate": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.4 `update-group`

Updates group properties.

**Synopsis:**
```bash
aws workmail update-group \
    --organization-id <value> \
    --group-id <value> \
    [--hidden-from-global-address-list | --no-hidden-from-global-address-list] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--group-id` | **Yes** | string | -- | Group ID |
| `--hidden-from-global-address-list` | No | boolean | None | Hide from address book |

**Output:** None

---

### 3.5 `delete-group`

Deletes a group from a WorkMail organization.

**Synopsis:**
```bash
aws workmail delete-group \
    --organization-id <value> \
    --group-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--group-id` | **Yes** | string | -- | Group ID to delete |

**Output:** None

---

### 3.6 `associate-member-to-group`

Adds a member (user or group) to a group.

**Synopsis:**
```bash
aws workmail associate-member-to-group \
    --organization-id <value> \
    --group-id <value> \
    --member-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--group-id` | **Yes** | string | -- | Group ID |
| `--member-id` | **Yes** | string | -- | Member entity ID to add |

**Output:** None

---

### 3.7 `disassociate-member-from-group`

Removes a member from a group.

**Synopsis:**
```bash
aws workmail disassociate-member-from-group \
    --organization-id <value> \
    --group-id <value> \
    --member-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--group-id` | **Yes** | string | -- | Group ID |
| `--member-id` | **Yes** | string | -- | Member entity ID to remove |

**Output:** None

---

### 3.8 `list-group-members`

Lists members of a group. **Paginated operation.**

**Synopsis:**
```bash
aws workmail list-group-members \
    --organization-id <value> \
    --group-id <value> \
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
| `--group-id` | **Yes** | string | -- | Group ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "Members": [
        {
            "Id": "string",
            "Name": "string",
            "Type": "GROUP|USER",
            "State": "ENABLED|DISABLED|DELETED",
            "EnabledDate": "timestamp",
            "DisabledDate": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
