# Backup Vaults

### 2.1 `create-backup-vault`

Creates a backup vault to store recovery points.

**Synopsis:**
```bash
aws backup create-backup-vault \
    --backup-vault-name <value> \
    [--backup-vault-tags <value>] \
    [--encryption-key-arn <value>] \
    [--creator-request-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-vault-name` | **Yes** | string | -- | Vault name (2-50 chars, `^[a-zA-Z0-9\-\_]{2,50}$`) |
| `--backup-vault-tags` | No | map | None | Key-value tags |
| `--encryption-key-arn` | No | string | None | KMS key ARN for encryption |
| `--creator-request-id` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "BackupVaultName": "string",
    "BackupVaultArn": "string",
    "CreationDate": "timestamp"
}
```

---

### 2.2 `delete-backup-vault`

Deletes a backup vault. Vault must be empty (no recovery points).

**Synopsis:**
```bash
aws backup delete-backup-vault \
    --backup-vault-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-vault-name` | **Yes** | string | -- | Vault name |

**Output:** None

---

### 2.3 `describe-backup-vault`

Returns metadata about a backup vault.

**Synopsis:**
```bash
aws backup describe-backup-vault \
    --backup-vault-name <value> \
    [--backup-vault-account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-vault-name` | **Yes** | string | -- | Vault name |
| `--backup-vault-account-id` | No | string | None | Account ID for cross-account vaults |

**Output Schema:**
```json
{
    "BackupVaultName": "string",
    "BackupVaultArn": "string",
    "VaultType": "BACKUP_VAULT|LOGICALLY_AIR_GAPPED_BACKUP_VAULT",
    "VaultState": "CREATING|AVAILABLE|FAILED",
    "EncryptionKeyArn": "string",
    "CreationDate": "timestamp",
    "CreatorRequestId": "string",
    "NumberOfRecoveryPoints": "long",
    "Locked": "boolean",
    "MinRetentionDays": "long",
    "MaxRetentionDays": "long",
    "LockDate": "timestamp"
}
```

---

### 2.4 `list-backup-vaults`

Lists backup vaults in the account. **Paginated operation.**

**Synopsis:**
```bash
aws backup list-backup-vaults \
    [--by-vault-type <value>] \
    [--by-shared | --no-by-shared] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--by-vault-type` | No | string | None | Filter: `BACKUP_VAULT`, `LOGICALLY_AIR_GAPPED_BACKUP_VAULT` |
| `--by-shared` | No | boolean | None | Filter shared vaults |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "BackupVaultList": [
        {
            "BackupVaultName": "string",
            "BackupVaultArn": "string",
            "VaultType": "string",
            "VaultState": "string",
            "CreationDate": "timestamp",
            "EncryptionKeyArn": "string",
            "CreatorRequestId": "string",
            "NumberOfRecoveryPoints": "long",
            "Locked": "boolean",
            "MinRetentionDays": "long",
            "MaxRetentionDays": "long",
            "LockDate": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.5 `put-backup-vault-lock-configuration`

Applies Backup Vault Lock to a vault. Enforces retention and immutability policies. Once in governance mode, transitions to compliance mode after 72 hours (irreversible).

**Synopsis:**
```bash
aws backup put-backup-vault-lock-configuration \
    --backup-vault-name <value> \
    [--min-retention-days <value>] \
    [--max-retention-days <value>] \
    [--changeable-for-days <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-vault-name` | **Yes** | string | -- | Vault name |
| `--min-retention-days` | No | long | None | Minimum retention in days |
| `--max-retention-days` | No | long | None | Maximum retention in days |
| `--changeable-for-days` | No | long | None | Days before lock becomes immutable (min 3) |

**Output:** None

---

### 2.6 `put-backup-vault-access-policy`

Sets a resource-based policy on a vault for cross-account access.

**Synopsis:**
```bash
aws backup put-backup-vault-access-policy \
    --backup-vault-name <value> \
    --policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-vault-name` | **Yes** | string | -- | Vault name |
| `--policy` | **Yes** | string | -- | JSON resource policy document |

**Output:** None

---

### 2.7 `put-backup-vault-notifications`

Sets up SNS notifications for backup vault events.

**Synopsis:**
```bash
aws backup put-backup-vault-notifications \
    --backup-vault-name <value> \
    --sns-topic-arn <value> \
    --backup-vault-events <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-vault-name` | **Yes** | string | -- | Vault name |
| `--sns-topic-arn` | **Yes** | string | -- | SNS topic ARN |
| `--backup-vault-events` | **Yes** | list(string) | -- | Events: `BACKUP_JOB_STARTED`, `BACKUP_JOB_COMPLETED`, `BACKUP_JOB_FAILED`, `RESTORE_JOB_STARTED`, `RESTORE_JOB_COMPLETED`, `RESTORE_JOB_FAILED`, `COPY_JOB_STARTED`, `COPY_JOB_SUCCESSFUL`, `COPY_JOB_FAILED`, `RECOVERY_POINT_MODIFIED`, `BACKUP_PLAN_CREATED`, `BACKUP_PLAN_MODIFIED`, `S3_BACKUP_OBJECT_FAILED`, `S3_RESTORE_OBJECT_FAILED` |

**Output:** None
