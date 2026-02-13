# Users

### 6.1 `create-user`

Creates a new user for Redis/Valkey RBAC (Role-Based Access Control).

**Synopsis:**
```bash
aws elasticache create-user \
    --user-id <value> \
    --user-name <value> \
    --engine <value> \
    --access-string <value> \
    [--passwords <value>] \
    [--no-password-required | --no-no-password-required] \
    [--tags <value>] \
    [--authentication-mode <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-id` | **Yes** | string | -- | Unique user ID |
| `--user-name` | **Yes** | string | -- | User name for authentication |
| `--engine` | **Yes** | string | -- | Engine: `redis` or `valkey` |
| `--access-string` | **Yes** | string | -- | ACL access string (e.g., `on ~* +@all`) |
| `--passwords` | No | list(string) | -- | Up to two passwords (for rotation) |
| `--no-password-required` | No | boolean | false | Allow access without password |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--authentication-mode` | No | structure | -- | Authentication mode. Shorthand: `Type=password\|iam\|no-password-required,Passwords=string,string` |

**Output Schema:**
```json
{
    "UserId": "string",
    "UserName": "string",
    "Status": "active|modifying|deleting",
    "Engine": "string",
    "MinimumEngineVersion": "string",
    "AccessString": "string",
    "UserGroupIds": ["string"],
    "Authentication": {
        "Type": "password|no-password|iam",
        "PasswordCount": "integer"
    },
    "ARN": "string"
}
```

---

### 6.2 `delete-user`

Deletes a user. The user must not belong to any user group.

**Synopsis:**
```bash
aws elasticache delete-user \
    --user-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-id` | **Yes** | string | -- | ID of the user to delete |

**Output Schema:** Same as `create-user` output.

---

### 6.3 `describe-users`

Returns a list of users. **Paginated operation.**

**Synopsis:**
```bash
aws elasticache describe-users \
    [--engine <value>] \
    [--user-id <value>] \
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
| `--engine` | No | string | -- | Filter by engine |
| `--user-id` | No | string | -- | Specific user ID |
| `--filters` | No | list | -- | Filters. Shorthand: `Name=string,Values=string,string ...` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Users": [
        {
            "UserId": "string",
            "UserName": "string",
            "Status": "string",
            "Engine": "string",
            "MinimumEngineVersion": "string",
            "AccessString": "string",
            "UserGroupIds": ["string"],
            "Authentication": {
                "Type": "string",
                "PasswordCount": "integer"
            },
            "ARN": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.4 `modify-user`

Changes user password(s), access string, or authentication mode.

**Synopsis:**
```bash
aws elasticache modify-user \
    --user-id <value> \
    [--access-string <value>] \
    [--append-access-string <value>] \
    [--passwords <value>] \
    [--no-password-required | --no-no-password-required] \
    [--authentication-mode <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-id` | **Yes** | string | -- | ID of the user to modify |
| `--access-string` | No | string | -- | New access string (replaces existing) |
| `--append-access-string` | No | string | -- | Access string to append to existing |
| `--passwords` | No | list(string) | -- | New passwords (up to two) |
| `--no-password-required` | No | boolean | -- | Allow passwordless access |
| `--authentication-mode` | No | structure | -- | New authentication mode |

**Output Schema:** Same as `create-user` output.

---

### 6.5 `create-user-group`

Creates a new user group for RBAC. A user group can be associated with replication groups to control access.

**Synopsis:**
```bash
aws elasticache create-user-group \
    --user-group-id <value> \
    --engine <value> \
    [--user-ids <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-group-id` | **Yes** | string | -- | Unique ID for the user group |
| `--engine` | **Yes** | string | -- | Engine: `redis` or `valkey` |
| `--user-ids` | No | list(string) | -- | User IDs to add to the group (must include `default` user) |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "UserGroupId": "string",
    "Status": "creating|active|modifying|deleting",
    "Engine": "string",
    "UserIds": ["string"],
    "MinimumEngineVersion": "string",
    "PendingChanges": {
        "UserIdsToRemove": ["string"],
        "UserIdsToAdd": ["string"]
    },
    "ReplicationGroups": ["string"],
    "ServerlessCaches": ["string"],
    "ARN": "string"
}
```

---

### 6.6 `delete-user-group`

Deletes a user group. The group must not be associated with any replication groups.

**Synopsis:**
```bash
aws elasticache delete-user-group \
    --user-group-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-group-id` | **Yes** | string | -- | ID of the user group to delete |

**Output Schema:** Same as `create-user-group` output.

---

### 6.7 `describe-user-groups`

Returns a list of user groups. **Paginated operation.**

**Synopsis:**
```bash
aws elasticache describe-user-groups \
    [--user-group-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-group-id` | No | string | -- | Specific user group ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "UserGroups": [
        {
            "UserGroupId": "string",
            "Status": "string",
            "Engine": "string",
            "UserIds": ["string"],
            "MinimumEngineVersion": "string",
            "PendingChanges": {},
            "ReplicationGroups": ["string"],
            "ServerlessCaches": ["string"],
            "ARN": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.8 `modify-user-group`

Adds or removes users from a user group.

**Synopsis:**
```bash
aws elasticache modify-user-group \
    --user-group-id <value> \
    [--user-ids-to-add <value>] \
    [--user-ids-to-remove <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-group-id` | **Yes** | string | -- | ID of the user group |
| `--user-ids-to-add` | No | list(string) | -- | User IDs to add |
| `--user-ids-to-remove` | No | list(string) | -- | User IDs to remove |

**Output Schema:** Same as `create-user-group` output.
