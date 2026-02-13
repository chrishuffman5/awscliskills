# Permissions Boundaries

### 18.1 `put-role-permissions-boundary`

Sets a managed policy as the permissions boundary for a role.

**Synopsis:**
```bash
aws iam put-role-permissions-boundary --role-name <value> --permissions-boundary <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--role-name` | **Yes** | string | -- | Role name |
| `--permissions-boundary` | **Yes** | string | -- | ARN of the managed policy |

**Output:** None on success.

---

### 18.2 `delete-role-permissions-boundary`

Removes the permissions boundary from a role.

**Synopsis:**
```bash
aws iam delete-role-permissions-boundary --role-name <value>
```

**Output:** None on success.

---

### 18.3 `put-user-permissions-boundary`

Sets a managed policy as the permissions boundary for a user.

**Synopsis:**
```bash
aws iam put-user-permissions-boundary --user-name <value> --permissions-boundary <value>
```

**Output:** None on success.

---

### 18.4 `delete-user-permissions-boundary`

Removes the permissions boundary from a user.

**Synopsis:**
```bash
aws iam delete-user-permissions-boundary --user-name <value>
```

**Output:** None on success.

---
