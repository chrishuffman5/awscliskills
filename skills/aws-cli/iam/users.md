# Users

### 1.1 `create-user`

Creates a new IAM user.

**Synopsis:**
```bash
aws iam create-user \
    --user-name <value> \
    [--path <value>] \
    [--permissions-boundary <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-name` | **Yes** | string | -- | User name (1-64 chars). Pattern: `[\w+=,.@-]+` |
| `--path` | No | string | `/` | Path prefix (1-512 chars). Must begin and end with `/` |
| `--permissions-boundary` | No | string | None | ARN of managed policy for permissions boundary (20-2048 chars) |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` (max 50) |

**Output Schema:**
```json
{
    "User": {
        "Path": "string",
        "UserName": "string",
        "UserId": "string",
        "Arn": "string",
        "CreateDate": "timestamp",
        "PermissionsBoundary": {
            "PermissionsBoundaryType": "PermissionsBoundaryPolicy",
            "PermissionsBoundaryArn": "string"
        },
        "Tags": [{ "Key": "string", "Value": "string" }]
    }
}
```

---

### 1.2 `get-user`

Retrieves information about the specified IAM user, or the calling user if no name given.

**Synopsis:**
```bash
aws iam get-user [--user-name <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-name` | No | string | caller | User name (1-128 chars) |

**Output Schema:**
```json
{
    "User": {
        "Path": "string",
        "UserName": "string",
        "UserId": "string",
        "Arn": "string",
        "CreateDate": "timestamp",
        "PasswordLastUsed": "timestamp",
        "PermissionsBoundary": {
            "PermissionsBoundaryType": "PermissionsBoundaryPolicy",
            "PermissionsBoundaryArn": "string"
        },
        "Tags": [{ "Key": "string", "Value": "string" }]
    }
}
```

---

### 1.3 `list-users`

Lists all IAM users. **Paginated.**

**Synopsis:**
```bash
aws iam list-users \
    [--path-prefix <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--path-prefix` | No | string | `/` | Filter by path prefix (1-512 chars) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Users": [
        {
            "Path": "string",
            "UserName": "string",
            "UserId": "string",
            "Arn": "string",
            "CreateDate": "timestamp",
            "PasswordLastUsed": "timestamp",
            "PermissionsBoundary": {
                "PermissionsBoundaryType": "PermissionsBoundaryPolicy",
                "PermissionsBoundaryArn": "string"
            },
            "Tags": [{ "Key": "string", "Value": "string" }]
        }
    ],
    "IsTruncated": true|false,
    "Marker": "string"
}
```

---

### 1.4 `update-user`

Changes the name and/or path of the specified IAM user.

**Synopsis:**
```bash
aws iam update-user \
    --user-name <value> \
    [--new-path <value>] \
    [--new-user-name <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-name` | **Yes** | string | -- | Current user name |
| `--new-path` | No | string | unchanged | New path (1-512 chars) |
| `--new-user-name` | No | string | unchanged | New user name (1-64 chars) |

**Output:** None on success.

---

### 1.5 `delete-user`

Deletes the specified IAM user. User must have no attached resources (keys, policies, groups, MFA, etc.).

**Synopsis:**
```bash
aws iam delete-user --user-name <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-name` | **Yes** | string | -- | User name to delete |

**Output:** None on success.

---
