# Instance Profiles

### 7.1 `create-instance-profile`

Creates an instance profile (container for an IAM role used by EC2/ECS instances).

**Synopsis:**
```bash
aws iam create-instance-profile \
    --instance-profile-name <value> \
    [--path <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-profile-name` | **Yes** | string | -- | Name (1-128 chars). Pattern: `[\w+=,.@-]+` |
| `--path` | No | string | `/` | Path prefix (1-512 chars) |
| `--tags` | No | list | None | Tags (max 50) |

**Output Schema:**
```json
{
    "InstanceProfile": {
        "Path": "string",
        "InstanceProfileName": "string",
        "InstanceProfileId": "string",
        "Arn": "string",
        "CreateDate": "timestamp",
        "Roles": [
            {
                "Path": "string",
                "RoleName": "string",
                "RoleId": "string",
                "Arn": "string",
                "CreateDate": "timestamp",
                "AssumeRolePolicyDocument": "string"
            }
        ],
        "Tags": [{ "Key": "string", "Value": "string" }]
    }
}
```

---

### 7.2 `get-instance-profile`

Retrieves information about the specified instance profile.

**Synopsis:**
```bash
aws iam get-instance-profile --instance-profile-name <value>
```

**Output Schema:** Same as `create-instance-profile`.

---

### 7.3 `list-instance-profiles`

Lists all instance profiles. **Paginated.**

**Synopsis:**
```bash
aws iam list-instance-profiles [--path-prefix <value>] [--starting-token <value>] [--max-items <value>]
```

**Output Schema:**
```json
{
    "InstanceProfiles": [
        {
            "Path": "string",
            "InstanceProfileName": "string",
            "InstanceProfileId": "string",
            "Arn": "string",
            "CreateDate": "timestamp",
            "Roles": [{ "RoleName": "string", "Arn": "string" }]
        }
    ],
    "IsTruncated": true|false,
    "Marker": "string"
}
```

---

### 7.4 `list-instance-profiles-for-role`

Lists instance profiles that contain the specified role. **Paginated.**

**Synopsis:**
```bash
aws iam list-instance-profiles-for-role --role-name <value> [--starting-token <value>] [--max-items <value>]
```

**Output Schema:** Same structure as `list-instance-profiles`.

---

### 7.5 `add-role-to-instance-profile`

Adds the specified role to the instance profile. An instance profile can contain only one role.

**Synopsis:**
```bash
aws iam add-role-to-instance-profile --instance-profile-name <value> --role-name <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-profile-name` | **Yes** | string | -- | Instance profile name |
| `--role-name` | **Yes** | string | -- | Role name to add |

**Output:** None on success.

---

### 7.6 `remove-role-from-instance-profile`

Removes the specified role from the instance profile.

**Synopsis:**
```bash
aws iam remove-role-from-instance-profile --instance-profile-name <value> --role-name <value>
```

**Output:** None on success.

---

### 7.7 `delete-instance-profile`

Deletes the instance profile. Must remove associated role first.

**Synopsis:**
```bash
aws iam delete-instance-profile --instance-profile-name <value>
```

**Output:** None on success.

---
