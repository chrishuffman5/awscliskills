# Ledgers

### 1.1 `create-ledger`

Creates a new Amazon QLDB ledger in your account.

**Synopsis:**
```bash
aws qldb create-ledger \
    --name <value> \
    --permissions-mode <value> \
    [--tags <value>] \
    [--deletion-protection | --no-deletion-protection] \
    [--kms-key <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the ledger (unique per account per region) |
| `--permissions-mode` | **Yes** | string | -- | Permissions mode: `ALLOW_ALL` or `STANDARD` (recommended) |
| `--tags` | No | map | None | Key-value tag pairs. Shorthand: `KeyName1=string,KeyName2=string` |
| `--deletion-protection` | No | boolean | true | Enable deletion protection (default is enabled) |
| `--no-deletion-protection` | No | boolean | -- | Disable deletion protection |
| `--kms-key` | No | string | `AWS_OWNED_KMS_KEY` | KMS key for encryption at rest (key ID, ARN, alias name, or alias ARN) |

**Output Schema:**
```json
{
    "Name": "string",
    "Arn": "string",
    "State": "CREATING|ACTIVE|DELETING|DELETED",
    "CreationDateTime": "timestamp",
    "PermissionsMode": "ALLOW_ALL|STANDARD",
    "DeletionProtection": true|false,
    "KmsKeyArn": "string"
}
```

---

### 1.2 `delete-ledger`

Deletes a ledger and all of its contents. This action is irreversible. Deletion protection must be disabled first.

**Synopsis:**
```bash
aws qldb delete-ledger \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the ledger to delete |

**Output:** None (HTTP 200 on success)

---

### 1.3 `describe-ledger`

Returns information about a ledger, including its state, permissions mode, encryption at rest settings, and creation time.

**Synopsis:**
```bash
aws qldb describe-ledger \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the ledger to describe |

**Output Schema:**
```json
{
    "Name": "string",
    "Arn": "string",
    "State": "CREATING|ACTIVE|DELETING|DELETED",
    "CreationDateTime": "timestamp",
    "PermissionsMode": "ALLOW_ALL|STANDARD",
    "DeletionProtection": true|false,
    "EncryptionDescription": {
        "KmsKeyArn": "string",
        "EncryptionStatus": "ENABLED|UPDATING|KMS_KEY_INACCESSIBLE",
        "InaccessibleKmsKeyDateTime": "timestamp"
    }
}
```

---

### 1.4 `list-ledgers`

Returns a list of all ledgers in the current account and region. **Paginated operation.**

**Synopsis:**
```bash
aws qldb list-ledgers \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Maximum number of results per page (1-100) |
| `--next-token` | No | string | None | Pagination token from previous response |

**Output Schema:**
```json
{
    "Ledgers": [
        {
            "Name": "string",
            "State": "CREATING|ACTIVE|DELETING|DELETED",
            "CreationDateTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `update-ledger`

Updates properties of a ledger, including deletion protection and the KMS key used for encryption at rest.

**Synopsis:**
```bash
aws qldb update-ledger \
    --name <value> \
    [--deletion-protection | --no-deletion-protection] \
    [--kms-key <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the ledger to update |
| `--deletion-protection` | No | boolean | -- | Enable deletion protection |
| `--no-deletion-protection` | No | boolean | -- | Disable deletion protection |
| `--kms-key` | No | string | -- | KMS key for encryption at rest (key ID, ARN, alias name, or alias ARN). Use `AWS_OWNED_KMS_KEY` for the default. |

**Output Schema:**
```json
{
    "Name": "string",
    "Arn": "string",
    "State": "CREATING|ACTIVE|DELETING|DELETED",
    "CreationDateTime": "timestamp",
    "DeletionProtection": true|false,
    "EncryptionDescription": {
        "KmsKeyArn": "string",
        "EncryptionStatus": "ENABLED|UPDATING|KMS_KEY_INACCESSIBLE",
        "InaccessibleKmsKeyDateTime": "timestamp"
    }
}
```

---

### 1.6 `update-ledger-permissions-mode`

Updates the permissions mode of a ledger. You can set it to `STANDARD` for fine-grained IAM policies or `ALLOW_ALL` for legacy mode.

**Synopsis:**
```bash
aws qldb update-ledger-permissions-mode \
    --name <value> \
    --permissions-mode <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the ledger |
| `--permissions-mode` | **Yes** | string | -- | Permissions mode: `ALLOW_ALL` or `STANDARD` |

**Output Schema:**
```json
{
    "Name": "string",
    "Arn": "string",
    "PermissionsMode": "ALLOW_ALL|STANDARD"
}
```
