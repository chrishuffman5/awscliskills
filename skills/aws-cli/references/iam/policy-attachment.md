# Policy Attachment

### 5.1 `attach-role-policy`

Attaches a managed policy to a role.

**Synopsis:**
```bash
aws iam attach-role-policy --role-name <value> --policy-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--role-name` | **Yes** | string | -- | Role name (1-64 chars) |
| `--policy-arn` | **Yes** | string | -- | ARN of the managed policy (20-2048 chars) |

**Output:** None on success.

---

### 5.2 `detach-role-policy`

Detaches a managed policy from a role.

**Synopsis:**
```bash
aws iam detach-role-policy --role-name <value> --policy-arn <value>
```

**Output:** None on success.

---

### 5.3 `attach-user-policy`

Attaches a managed policy to a user.

**Synopsis:**
```bash
aws iam attach-user-policy --user-name <value> --policy-arn <value>
```

**Output:** None on success.

---

### 5.4 `detach-user-policy`

Detaches a managed policy from a user.

**Synopsis:**
```bash
aws iam detach-user-policy --user-name <value> --policy-arn <value>
```

**Output:** None on success.

---

### 5.5 `attach-group-policy`

Attaches a managed policy to a group.

**Synopsis:**
```bash
aws iam attach-group-policy --group-name <value> --policy-arn <value>
```

**Output:** None on success.

---

### 5.6 `detach-group-policy`

Detaches a managed policy from a group.

**Synopsis:**
```bash
aws iam detach-group-policy --group-name <value> --policy-arn <value>
```

**Output:** None on success.

---

### 5.7 `list-attached-role-policies`

Lists managed policies attached to a role. **Paginated.**

**Synopsis:**
```bash
aws iam list-attached-role-policies \
    --role-name <value> \
    [--path-prefix <value>] \
    [--starting-token <value>] \
    [--max-items <value>]
```

**Output Schema:**
```json
{
    "AttachedPolicies": [
        {
            "PolicyName": "string",
            "PolicyArn": "string"
        }
    ],
    "IsTruncated": true|false,
    "Marker": "string"
}
```

---

### 5.8 `list-attached-user-policies`

Lists managed policies attached to a user. **Paginated.**

**Synopsis:**
```bash
aws iam list-attached-user-policies --user-name <value> [--path-prefix <value>] [--starting-token <value>] [--max-items <value>]
```

**Output Schema:** Same structure as `list-attached-role-policies`.

---

### 5.9 `list-attached-group-policies`

Lists managed policies attached to a group. **Paginated.**

**Synopsis:**
```bash
aws iam list-attached-group-policies --group-name <value> [--path-prefix <value>] [--starting-token <value>] [--max-items <value>]
```

**Output Schema:** Same structure as `list-attached-role-policies`.

---

### 5.10 `list-entities-for-policy`

Lists all IAM users, groups, and roles that a managed policy is attached to. **Paginated.**

**Synopsis:**
```bash
aws iam list-entities-for-policy \
    --policy-arn <value> \
    [--entity-filter <value>] \
    [--path-prefix <value>] \
    [--policy-usage-filter <value>] \
    [--starting-token <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-arn` | **Yes** | string | -- | ARN of the policy |
| `--entity-filter` | No | string | None | `User`, `Role`, `Group`, `LocalManagedPolicy`, `AWSManagedPolicy` |
| `--path-prefix` | No | string | None | Filter entities by path |
| `--policy-usage-filter` | No | string | None | `PermissionsPolicy` or `PermissionsBoundary` |

**Output Schema:**
```json
{
    "PolicyGroups": [{ "GroupName": "string", "GroupId": "string" }],
    "PolicyUsers": [{ "UserName": "string", "UserId": "string" }],
    "PolicyRoles": [{ "RoleName": "string", "RoleId": "string" }],
    "IsTruncated": true|false,
    "Marker": "string"
}
```

---
