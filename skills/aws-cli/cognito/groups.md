# Groups

### 4.1 `create-group`

Creates a group in a user pool.

**Synopsis:**
```bash
aws cognito-idp create-group \
    --group-name <value> \
    --user-pool-id <value> \
    [--description <value>] \
    [--role-arn <value>] \
    [--precedence <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-name` | **Yes** | string | -- | Group name (1-128 chars) |
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--description` | No | string | None | Description (max 2048 chars) |
| `--role-arn` | No | string | None | IAM role ARN associated with the group |
| `--precedence` | No | integer | None | Precedence value (0 = highest). Used for role resolution when user belongs to multiple groups |

**Output Schema:**
```json
{
    "Group": {
        "GroupName": "string",
        "UserPoolId": "string",
        "Description": "string",
        "RoleArn": "string",
        "Precedence": "integer",
        "LastModifiedDate": "timestamp",
        "CreationDate": "timestamp"
    }
}
```

---

### 4.2 `delete-group`

Deletes a group. The group must be empty (no users).

**Synopsis:**
```bash
aws cognito-idp delete-group \
    --group-name <value> \
    --user-pool-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-name` | **Yes** | string | -- | Group name |
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |

**Output:** None

---

### 4.3 `get-group`

Gets information about a group.

**Synopsis:**
```bash
aws cognito-idp get-group \
    --group-name <value> \
    --user-pool-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-name` | **Yes** | string | -- | Group name |
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |

**Output Schema:** Same as `create-group`.

---

### 4.4 `list-groups`

Lists groups in a user pool. **Paginated operation.**

**Synopsis:**
```bash
aws cognito-idp list-groups \
    --user-pool-id <value> \
    [--limit <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--limit` | No | integer | 60 | Maximum items (1-60) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Groups": [
        {
            "GroupName": "string",
            "UserPoolId": "string",
            "Description": "string",
            "RoleArn": "string",
            "Precedence": "integer",
            "LastModifiedDate": "timestamp",
            "CreationDate": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.5 `update-group`

Updates a group.

**Synopsis:**
```bash
aws cognito-idp update-group \
    --group-name <value> \
    --user-pool-id <value> \
    [--description <value>] \
    [--role-arn <value>] \
    [--precedence <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-name` | **Yes** | string | -- | Group name |
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--description` | No | string | None | New description |
| `--role-arn` | No | string | None | New IAM role ARN |
| `--precedence` | No | integer | None | New precedence value |

**Output Schema:** Same as `create-group`.

---

### 4.6 `admin-add-user-to-group`

Adds a user to a group.

**Synopsis:**
```bash
aws cognito-idp admin-add-user-to-group \
    --user-pool-id <value> \
    --username <value> \
    --group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--username` | **Yes** | string | -- | Username |
| `--group-name` | **Yes** | string | -- | Group name |

**Output:** None

---

### 4.7 `admin-remove-user-from-group`

Removes a user from a group.

**Synopsis:**
```bash
aws cognito-idp admin-remove-user-from-group \
    --user-pool-id <value> \
    --username <value> \
    --group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--username` | **Yes** | string | -- | Username |
| `--group-name` | **Yes** | string | -- | Group name |

**Output:** None

---

### 4.8 `admin-list-groups-for-user`

Lists the groups a user belongs to. **Paginated operation.**

**Synopsis:**
```bash
aws cognito-idp admin-list-groups-for-user \
    --username <value> \
    --user-pool-id <value> \
    [--limit <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--username` | **Yes** | string | -- | Username |
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--limit` | No | integer | 60 | Maximum items (1-60) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Groups": [
        {
            "GroupName": "string",
            "UserPoolId": "string",
            "Description": "string",
            "RoleArn": "string",
            "Precedence": "integer",
            "LastModifiedDate": "timestamp",
            "CreationDate": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.9 `list-users-in-group`

Lists users in a group. **Paginated operation.**

**Synopsis:**
```bash
aws cognito-idp list-users-in-group \
    --user-pool-id <value> \
    --group-name <value> \
    [--limit <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--group-name` | **Yes** | string | -- | Group name |
| `--limit` | No | integer | 60 | Maximum items (1-60) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Users": [
        {
            "Username": "string",
            "Attributes": [{"Name": "string", "Value": "string"}],
            "UserCreateDate": "timestamp",
            "UserLastModifiedDate": "timestamp",
            "Enabled": "boolean",
            "UserStatus": "string"
        }
    ],
    "NextToken": "string"
}
```
