# Service-Specific Credentials

### 17.1 `create-service-specific-credential`

Creates a credential for services like CodeCommit, Amazon Keyspaces.

**Synopsis:**
```bash
aws iam create-service-specific-credential --user-name <value> --service-name <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-name` | **Yes** | string | -- | User name |
| `--service-name` | **Yes** | string | -- | Service name (e.g., `codecommit.amazonaws.com`) |

**Output Schema:**
```json
{
    "ServiceSpecificCredential": {
        "CreateDate": "timestamp",
        "ServiceName": "string",
        "ServiceUserName": "string",
        "ServicePassword": "string",
        "ServiceSpecificCredentialId": "string",
        "UserName": "string",
        "Status": "Active|Inactive"
    }
}
```

---

### 17.2 `list-service-specific-credentials`

Lists service-specific credentials for a user.

**Synopsis:**
```bash
aws iam list-service-specific-credentials [--user-name <value>] [--service-name <value>]
```

**Output Schema:**
```json
{
    "ServiceSpecificCredentials": [
        {
            "UserName": "string",
            "Status": "Active|Inactive",
            "ServiceUserName": "string",
            "CreateDate": "timestamp",
            "ServiceSpecificCredentialId": "string",
            "ServiceName": "string"
        }
    ]
}
```

---

### 17.3 `update-service-specific-credential`

Updates the status of a service-specific credential.

**Synopsis:**
```bash
aws iam update-service-specific-credential --service-specific-credential-id <value> --status <value> [--user-name <value>]
```

**Output:** None on success.

---

### 17.4 `reset-service-specific-credential`

Resets the password for a service-specific credential.

**Synopsis:**
```bash
aws iam reset-service-specific-credential --service-specific-credential-id <value> [--user-name <value>]
```

**Output Schema:** Same as `create-service-specific-credential`.

---

### 17.5 `delete-service-specific-credential`

Deletes a service-specific credential.

**Synopsis:**
```bash
aws iam delete-service-specific-credential --service-specific-credential-id <value> [--user-name <value>]
```

**Output:** None on success.

---
