# Users

### 2.1 `create-user`

Creates a user in a WorkMail organization.

**Synopsis:**
```bash
aws workmail create-user \
    --organization-id <value> \
    --name <value> \
    --display-name <value> \
    [--password <value>] \
    [--role <value>] \
    [--first-name <value>] \
    [--last-name <value>] \
    [--hidden-from-global-address-list | --no-hidden-from-global-address-list] \
    [--identity-provider-user-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--name` | **Yes** | string | -- | User name (max 64 chars for WorkMail directory) |
| `--display-name` | **Yes** | string | -- | Display name (max 256 chars) |
| `--password` | No | string | None | User password (max 256 chars) |
| `--role` | No | string | USER | Role: `USER`, `RESOURCE`, `SYSTEM_USER`, `REMOTE_USER` |
| `--first-name` | No | string | None | First name (max 256 chars) |
| `--last-name` | No | string | None | Last name (max 256 chars) |
| `--hidden-from-global-address-list` | No | boolean | false | Hide from address book |
| `--identity-provider-user-id` | No | string | None | IAM Identity Center user ID |

**Output Schema:**
```json
{
    "UserId": "string"
}
```

---

### 2.2 `describe-user`

Describes a user including state, role, and contact details.

**Synopsis:**
```bash
aws workmail describe-user \
    --organization-id <value> \
    --user-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--user-id` | **Yes** | string | -- | User ID, username, or email |

**Output Schema:**
```json
{
    "UserId": "string",
    "Name": "string",
    "Email": "string",
    "DisplayName": "string",
    "State": "ENABLED|DISABLED|DELETED",
    "UserRole": "USER|RESOURCE|SYSTEM_USER|REMOTE_USER",
    "EnabledDate": "timestamp",
    "DisabledDate": "timestamp",
    "MailboxProvisionedDate": "timestamp",
    "MailboxDeprovisionedDate": "timestamp",
    "FirstName": "string",
    "LastName": "string",
    "HiddenFromGlobalAddressList": "boolean",
    "Initials": "string",
    "Telephone": "string",
    "Street": "string",
    "JobTitle": "string",
    "City": "string",
    "Company": "string",
    "ZipCode": "string",
    "Department": "string",
    "Country": "string",
    "Office": "string",
    "IdentityProviderUserId": "string",
    "IdentityProviderIdentityStoreId": "string"
}
```

---

### 2.3 `list-users`

Lists users in an organization. **Paginated operation.**

**Synopsis:**
```bash
aws workmail list-users \
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
| `--filters` | No | structure | None | Filter by username, display name, email prefix, state, or IdC ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |
| `--max-items` | No | integer | None | Max total items to return |

**Filters structure:**
```json
{
    "UsernamePrefix": "string",
    "DisplayNamePrefix": "string",
    "PrimaryEmailPrefix": "string",
    "State": "ENABLED|DISABLED|DELETED",
    "IdentityProviderUserIdPrefix": "string"
}
```

**Output Schema:**
```json
{
    "Users": [
        {
            "Id": "string",
            "Email": "string",
            "Name": "string",
            "DisplayName": "string",
            "State": "ENABLED|DISABLED|DELETED",
            "UserRole": "USER|RESOURCE|SYSTEM_USER|REMOTE_USER",
            "EnabledDate": "timestamp",
            "DisabledDate": "timestamp",
            "IdentityProviderUserId": "string",
            "IdentityProviderIdentityStoreId": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.4 `update-user`

Updates user properties such as display name, role, and contact details.

**Synopsis:**
```bash
aws workmail update-user \
    --organization-id <value> \
    --user-id <value> \
    [--role <value>] \
    [--display-name <value>] \
    [--first-name <value>] \
    [--last-name <value>] \
    [--hidden-from-global-address-list | --no-hidden-from-global-address-list] \
    [--initials <value>] \
    [--telephone <value>] \
    [--street <value>] \
    [--job-title <value>] \
    [--city <value>] \
    [--company <value>] \
    [--zip-code <value>] \
    [--department <value>] \
    [--country <value>] \
    [--office <value>] \
    [--identity-provider-user-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--user-id` | **Yes** | string | -- | User ID, username, or email |
| `--role` | No | string | None | Updated role: `USER`, `REMOTE_USER` |
| `--display-name` | No | string | None | Updated display name |
| `--first-name` | No | string | None | Updated first name |
| `--last-name` | No | string | None | Updated last name |
| `--hidden-from-global-address-list` | No | boolean | None | Hide from address book |
| `--initials` | No | string | None | User initials |
| `--telephone` | No | string | None | Phone number |
| `--street` | No | string | None | Street address |
| `--job-title` | No | string | None | Job title |
| `--city` | No | string | None | City |
| `--company` | No | string | None | Company |
| `--zip-code` | No | string | None | Zip code |
| `--department` | No | string | None | Department |
| `--country` | No | string | None | Country |
| `--office` | No | string | None | Office location |
| `--identity-provider-user-id` | No | string | None | IAM Identity Center user ID |

**Output:** None

---

### 2.5 `delete-user`

Deletes a user from a WorkMail organization.

**Synopsis:**
```bash
aws workmail delete-user \
    --organization-id <value> \
    --user-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--user-id` | **Yes** | string | -- | User ID to delete |

**Output:** None

---

### 2.6 `register-to-work-mail`

Registers an entity (user, group, or resource) for WorkMail email by assigning an email address.

**Synopsis:**
```bash
aws workmail register-to-work-mail \
    --organization-id <value> \
    --entity-id <value> \
    --email <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--entity-id` | **Yes** | string | -- | Entity ID (user, group, or resource) |
| `--email` | **Yes** | string | -- | Email address to assign |

**Output:** None

---

### 2.7 `deregister-from-work-mail`

Deregisters an entity from WorkMail, removing its email address.

**Synopsis:**
```bash
aws workmail deregister-from-work-mail \
    --organization-id <value> \
    --entity-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--entity-id` | **Yes** | string | -- | Entity ID to deregister |

**Output:** None

---

### 2.8 `reset-password`

Resets a user password.

**Synopsis:**
```bash
aws workmail reset-password \
    --organization-id <value> \
    --user-id <value> \
    --password <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--user-id` | **Yes** | string | -- | User ID |
| `--password` | **Yes** | string | -- | New password (max 256 chars) |

**Output:** None

---

### 2.9 `describe-entity`

Describes an entity (user, group, or resource) by ID or email.

**Synopsis:**
```bash
aws workmail describe-entity \
    --organization-id <value> \
    --email <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--email` | **Yes** | string | -- | Entity email address |

**Output Schema:**
```json
{
    "EntityId": "string",
    "Name": "string",
    "Type": "GROUP|USER|RESOURCE",
    "State": "ENABLED|DISABLED|DELETED"
}
```

---

### 2.10 `list-groups-for-entity`

Lists the groups an entity belongs to. **Paginated operation.**

**Synopsis:**
```bash
aws workmail list-groups-for-entity \
    --organization-id <value> \
    --entity-id <value> \
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
| `--entity-id` | **Yes** | string | -- | Entity ID |
| `--filters` | No | structure | None | Filter by group name prefix |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "Groups": [
        {
            "GroupId": "string",
            "GroupName": "string"
        }
    ],
    "NextToken": "string"
}
```
