# Roles

### 3.1 `create-role`

Creates a new IAM role with a trust policy.

**Synopsis:**
```bash
aws iam create-role \
    --role-name <value> \
    --assume-role-policy-document <value> \
    [--path <value>] \
    [--description <value>] \
    [--max-session-duration <value>] \
    [--permissions-boundary <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--role-name` | **Yes** | string | -- | Role name (1-64 chars). Pattern: `[\w+=,.@-]+` |
| `--assume-role-policy-document` | **Yes** | string | -- | Trust policy JSON (max 131072 chars). Use `file://` for file input |
| `--path` | No | string | `/` | Path prefix (1-512 chars) |
| `--description` | No | string | None | Description (max 1000 chars) |
| `--max-session-duration` | No | integer | 3600 | Max session in seconds (3600-43200) |
| `--permissions-boundary` | No | string | None | ARN of permissions boundary policy |
| `--tags` | No | list | None | Tags (max 50). Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "Role": {
        "Path": "string",
        "RoleName": "string",
        "RoleId": "string",
        "Arn": "string",
        "CreateDate": "timestamp",
        "AssumeRolePolicyDocument": "string",
        "Description": "string",
        "MaxSessionDuration": integer,
        "PermissionsBoundary": {
            "PermissionsBoundaryType": "PermissionsBoundaryPolicy",
            "PermissionsBoundaryArn": "string"
        },
        "Tags": [{ "Key": "string", "Value": "string" }],
        "RoleLastUsed": {
            "LastUsedDate": "timestamp",
            "Region": "string"
        }
    }
}
```

---

### 3.2 `get-role`

Retrieves information about the specified role.

**Synopsis:**
```bash
aws iam get-role --role-name <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--role-name` | **Yes** | string | -- | Role name (1-64 chars) |

**Output Schema:**
```json
{
    "Role": {
        "Path": "string",
        "RoleName": "string",
        "RoleId": "string",
        "Arn": "string",
        "CreateDate": "timestamp",
        "AssumeRolePolicyDocument": "string",
        "Description": "string",
        "MaxSessionDuration": integer,
        "PermissionsBoundary": {
            "PermissionsBoundaryType": "PermissionsBoundaryPolicy",
            "PermissionsBoundaryArn": "string"
        },
        "Tags": [{ "Key": "string", "Value": "string" }],
        "RoleLastUsed": {
            "LastUsedDate": "timestamp",
            "Region": "string"
        }
    }
}
```

---

### 3.3 `list-roles`

Lists IAM roles. **Paginated.**

**Synopsis:**
```bash
aws iam list-roles \
    [--path-prefix <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--path-prefix` | No | string | `/` | Filter by path prefix |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Roles": [
        {
            "Path": "string",
            "RoleName": "string",
            "RoleId": "string",
            "Arn": "string",
            "CreateDate": "timestamp",
            "AssumeRolePolicyDocument": "string",
            "Description": "string",
            "MaxSessionDuration": integer
        }
    ],
    "IsTruncated": true|false,
    "Marker": "string"
}
```

---

### 3.4 `update-role`

Updates the maximum session duration for a role.

**Synopsis:**
```bash
aws iam update-role --role-name <value> [--description <value>] [--max-session-duration <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--role-name` | **Yes** | string | -- | Role name |
| `--description` | No | string | unchanged | New description |
| `--max-session-duration` | No | integer | unchanged | Max session seconds (3600-43200) |

**Output:** None on success.

---

### 3.5 `update-role-description`

Updates only the description of a role.

**Synopsis:**
```bash
aws iam update-role-description --role-name <value> --description <value>
```

**Output Schema:**
```json
{
    "Role": {
        "Path": "string",
        "RoleName": "string",
        "RoleId": "string",
        "Arn": "string",
        "CreateDate": "timestamp",
        "AssumeRolePolicyDocument": "string",
        "Description": "string",
        "MaxSessionDuration": integer
    }
}
```

---

### 3.6 `update-assume-role-policy`

Updates the trust policy (assume role policy document) for a role.

**Synopsis:**
```bash
aws iam update-assume-role-policy --role-name <value> --policy-document <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--role-name` | **Yes** | string | -- | Role name |
| `--policy-document` | **Yes** | string | -- | Trust policy JSON. Use `file://` for file input |

**Output:** None on success.

---

### 3.7 `delete-role`

Deletes the specified role. Role must have no attached policies, inline policies, or instance profiles.

**Synopsis:**
```bash
aws iam delete-role --role-name <value>
```

**Output:** None on success.

---
