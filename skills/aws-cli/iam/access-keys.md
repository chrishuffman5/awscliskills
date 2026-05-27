# Access Keys

### 8.1 `create-access-key`

Creates a new access key pair (access key ID + secret access key).

**Synopsis:**
```bash
aws iam create-access-key [--user-name <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-name` | No | string | caller | User name. If omitted, uses calling identity |

**Output Schema:**
```json
{
    "AccessKey": {
        "UserName": "string",
        "AccessKeyId": "string",
        "Status": "Active|Inactive",
        "SecretAccessKey": "string",
        "CreateDate": "timestamp"
    }
}
```

> **Note:** `SecretAccessKey` is only available at creation time. Store it securely immediately.

---

### 8.2 `list-access-keys`

Lists access key IDs for a user. **Paginated.**

**Synopsis:**
```bash
aws iam list-access-keys [--user-name <value>] [--starting-token <value>] [--max-items <value>]
```

**Output Schema:**
```json
{
    "AccessKeyMetadata": [
        {
            "UserName": "string",
            "AccessKeyId": "string",
            "Status": "Active|Inactive",
            "CreateDate": "timestamp"
        }
    ],
    "IsTruncated": true|false,
    "Marker": "string"
}
```

---

### 8.3 `get-access-key-last-used`

Retrieves information about when the access key was last used.

**Synopsis:**
```bash
aws iam get-access-key-last-used --access-key-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--access-key-id` | **Yes** | string | -- | Access key ID (16-128 chars) |

**Output Schema:**
```json
{
    "UserName": "string",
    "AccessKeyLastUsed": {
        "LastUsedDate": "timestamp",
        "ServiceName": "string",
        "Region": "string"
    }
}
```

---

### 8.4 `update-access-key`

Changes the status of an access key (Active/Inactive).

**Synopsis:**
```bash
aws iam update-access-key --access-key-id <value> --status <value> [--user-name <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--access-key-id` | **Yes** | string | -- | Access key ID |
| `--status` | **Yes** | string | -- | `Active` or `Inactive` |
| `--user-name` | No | string | caller | User name |

**Output:** None on success.

---

### 8.5 `delete-access-key`

Deletes an access key pair.

**Synopsis:**
```bash
aws iam delete-access-key --access-key-id <value> [--user-name <value>]
```

**Output:** None on success.

---
