# Login Profiles

### 9.1 `create-login-profile`

Creates a password for a user to access the AWS Management Console.

**Synopsis:**
```bash
aws iam create-login-profile \
    --user-name <value> \
    --password <value> \
    [--password-reset-required | --no-password-reset-required]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-name` | **Yes** | string | -- | User name |
| `--password` | **Yes** | string | -- | Console password (1-128 chars) |
| `--password-reset-required` | No | boolean | false | Force password change on first login |

**Output Schema:**
```json
{
    "LoginProfile": {
        "UserName": "string",
        "CreateDate": "timestamp",
        "PasswordResetRequired": true|false
    }
}
```

---

### 9.2 `get-login-profile`

Retrieves login profile for a user.

**Synopsis:**
```bash
aws iam get-login-profile --user-name <value>
```

**Output Schema:** Same as `create-login-profile`.

---

### 9.3 `update-login-profile`

Updates the password for a user.

**Synopsis:**
```bash
aws iam update-login-profile --user-name <value> [--password <value>] [--password-reset-required | --no-password-reset-required]
```

**Output:** None on success.

---

### 9.4 `delete-login-profile`

Deletes the login profile (console password) for a user.

**Synopsis:**
```bash
aws iam delete-login-profile --user-name <value>
```

**Output:** None on success.

---
