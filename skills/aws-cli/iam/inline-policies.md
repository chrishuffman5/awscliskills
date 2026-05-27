# Inline Policies

### 6.1 `put-role-policy`

Creates or updates an inline policy embedded in a role.

**Synopsis:**
```bash
aws iam put-role-policy \
    --role-name <value> \
    --policy-name <value> \
    --policy-document <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--role-name` | **Yes** | string | -- | Role name |
| `--policy-name` | **Yes** | string | -- | Inline policy name (1-128 chars) |
| `--policy-document` | **Yes** | string | -- | Policy JSON. Use `file://` for file input |

**Output:** None on success.

---

### 6.2 `get-role-policy`

Retrieves an inline policy document embedded in a role.

**Synopsis:**
```bash
aws iam get-role-policy --role-name <value> --policy-name <value>
```

**Output Schema:**
```json
{
    "RoleName": "string",
    "PolicyName": "string",
    "PolicyDocument": "string (URL-encoded JSON)"
}
```

---

### 6.3 `delete-role-policy`

Deletes an inline policy from a role.

**Synopsis:**
```bash
aws iam delete-role-policy --role-name <value> --policy-name <value>
```

**Output:** None on success.

---

### 6.4 `list-role-policies`

Lists names of inline policies embedded in a role. **Paginated.**

**Synopsis:**
```bash
aws iam list-role-policies --role-name <value> [--starting-token <value>] [--max-items <value>]
```

**Output Schema:**
```json
{
    "PolicyNames": ["string"],
    "IsTruncated": true|false,
    "Marker": "string"
}
```

---

### 6.5 `put-user-policy`

Creates or updates an inline policy for a user.

**Synopsis:**
```bash
aws iam put-user-policy --user-name <value> --policy-name <value> --policy-document <value>
```

**Output:** None on success.

---

### 6.6 `get-user-policy`

Retrieves an inline policy document for a user.

**Synopsis:**
```bash
aws iam get-user-policy --user-name <value> --policy-name <value>
```

**Output Schema:**
```json
{
    "UserName": "string",
    "PolicyName": "string",
    "PolicyDocument": "string (URL-encoded JSON)"
}
```

---

### 6.7 `delete-user-policy`

Deletes an inline policy from a user.

**Synopsis:**
```bash
aws iam delete-user-policy --user-name <value> --policy-name <value>
```

**Output:** None on success.

---

### 6.8 `list-user-policies`

Lists names of inline policies for a user. **Paginated.**

**Synopsis:**
```bash
aws iam list-user-policies --user-name <value> [--starting-token <value>] [--max-items <value>]
```

**Output Schema:**
```json
{
    "PolicyNames": ["string"],
    "IsTruncated": true|false,
    "Marker": "string"
}
```

---

### 6.9 `put-group-policy`

Creates or updates an inline policy for a group.

**Synopsis:**
```bash
aws iam put-group-policy --group-name <value> --policy-name <value> --policy-document <value>
```

**Output:** None on success.

---

### 6.10 `get-group-policy`

Retrieves an inline policy document for a group.

**Synopsis:**
```bash
aws iam get-group-policy --group-name <value> --policy-name <value>
```

**Output Schema:**
```json
{
    "GroupName": "string",
    "PolicyName": "string",
    "PolicyDocument": "string (URL-encoded JSON)"
}
```

---

### 6.11 `delete-group-policy`

Deletes an inline policy from a group.

**Synopsis:**
```bash
aws iam delete-group-policy --group-name <value> --policy-name <value>
```

**Output:** None on success.

---

### 6.12 `list-group-policies`

Lists names of inline policies for a group. **Paginated.**

**Synopsis:**
```bash
aws iam list-group-policies --group-name <value> [--starting-token <value>] [--max-items <value>]
```

**Output Schema:**
```json
{
    "PolicyNames": ["string"],
    "IsTruncated": true|false,
    "Marker": "string"
}
```

---
