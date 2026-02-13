# Groups

### 2.1 `create-group`

Creates a new IAM group.

**Synopsis:**
```bash
aws iam create-group --group-name <value> [--path <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-name` | **Yes** | string | -- | Group name (1-128 chars). Pattern: `[\w+=,.@-]+` |
| `--path` | No | string | `/` | Path prefix (1-512 chars) |

**Output Schema:**
```json
{
    "Group": {
        "Path": "string",
        "GroupName": "string",
        "GroupId": "string",
        "Arn": "string",
        "CreateDate": "timestamp"
    }
}
```

---

### 2.2 `get-group`

Returns group details and a list of users in the group. **Paginated.**

**Synopsis:**
```bash
aws iam get-group \
    --group-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-name` | **Yes** | string | -- | Group name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Group": {
        "Path": "string",
        "GroupName": "string",
        "GroupId": "string",
        "Arn": "string",
        "CreateDate": "timestamp"
    },
    "Users": [
        {
            "Path": "string",
            "UserName": "string",
            "UserId": "string",
            "Arn": "string",
            "CreateDate": "timestamp"
        }
    ],
    "IsTruncated": true|false,
    "Marker": "string"
}
```

---

### 2.3 `list-groups`

Lists all IAM groups. **Paginated.**

**Synopsis:**
```bash
aws iam list-groups \
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
    "Groups": [
        {
            "Path": "string",
            "GroupName": "string",
            "GroupId": "string",
            "Arn": "string",
            "CreateDate": "timestamp"
        }
    ],
    "IsTruncated": true|false,
    "Marker": "string"
}
```

---

### 2.4 `update-group`

Changes the name and/or path of a group.

**Synopsis:**
```bash
aws iam update-group --group-name <value> [--new-path <value>] [--new-group-name <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-name` | **Yes** | string | -- | Current group name |
| `--new-path` | No | string | unchanged | New path |
| `--new-group-name` | No | string | unchanged | New group name |

**Output:** None on success.

---

### 2.5 `delete-group`

Deletes the specified group. Group must have no users, policies, or attached policies.

**Synopsis:**
```bash
aws iam delete-group --group-name <value>
```

**Output:** None on success.

---

### 2.6 `add-user-to-group`

Adds the specified user to the specified group.

**Synopsis:**
```bash
aws iam add-user-to-group --group-name <value> --user-name <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-name` | **Yes** | string | -- | Group name |
| `--user-name` | **Yes** | string | -- | User name to add |

**Output:** None on success.

---

### 2.7 `remove-user-from-group`

Removes the specified user from the specified group.

**Synopsis:**
```bash
aws iam remove-user-from-group --group-name <value> --user-name <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-name` | **Yes** | string | -- | Group name |
| `--user-name` | **Yes** | string | -- | User name to remove |

**Output:** None on success.

---

### 2.8 `list-groups-for-user`

Lists the groups a user belongs to. **Paginated.**

**Synopsis:**
```bash
aws iam list-groups-for-user --user-name <value> [--starting-token <value>] [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-name` | **Yes** | string | -- | User name |

**Output Schema:**
```json
{
    "Groups": [
        {
            "Path": "string",
            "GroupName": "string",
            "GroupId": "string",
            "Arn": "string",
            "CreateDate": "timestamp"
        }
    ],
    "IsTruncated": true|false,
    "Marker": "string"
}
```

---
