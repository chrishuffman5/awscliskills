# SSH Public Keys

### 12.1 `upload-ssh-public-key`

Uploads an SSH public key for use with CodeCommit.

**Synopsis:**
```bash
aws iam upload-ssh-public-key --user-name <value> --ssh-public-key-body <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-name` | **Yes** | string | -- | User name |
| `--ssh-public-key-body` | **Yes** | string | -- | SSH public key (1-16384 chars) |

**Output Schema:**
```json
{
    "SSHPublicKey": {
        "UserName": "string",
        "SSHPublicKeyId": "string",
        "Fingerprint": "string",
        "SSHPublicKeyBody": "string",
        "Status": "Active|Inactive",
        "UploadDate": "timestamp"
    }
}
```

---

### 12.2 `get-ssh-public-key`

Retrieves an SSH public key.

**Synopsis:**
```bash
aws iam get-ssh-public-key --user-name <value> --ssh-public-key-id <value> --encoding <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-name` | **Yes** | string | -- | User name |
| `--ssh-public-key-id` | **Yes** | string | -- | SSH key ID (20 chars) |
| `--encoding` | **Yes** | string | -- | `SSH` or `PEM` |

**Output Schema:** Same as `upload-ssh-public-key`.

---

### 12.3 `list-ssh-public-keys`

Lists SSH public keys for a user. **Paginated.**

**Synopsis:**
```bash
aws iam list-ssh-public-keys [--user-name <value>] [--starting-token <value>] [--max-items <value>]
```

**Output Schema:**
```json
{
    "SSHPublicKeys": [
        {
            "UserName": "string",
            "SSHPublicKeyId": "string",
            "Status": "Active|Inactive",
            "UploadDate": "timestamp"
        }
    ],
    "IsTruncated": true|false,
    "Marker": "string"
}
```

---

### 12.4 `update-ssh-public-key`

Sets the status of an SSH public key to Active or Inactive.

**Synopsis:**
```bash
aws iam update-ssh-public-key --user-name <value> --ssh-public-key-id <value> --status <value>
```

**Output:** None on success.

---

### 12.5 `delete-ssh-public-key`

Deletes an SSH public key.

**Synopsis:**
```bash
aws iam delete-ssh-public-key --user-name <value> --ssh-public-key-id <value>
```

**Output:** None on success.

---
