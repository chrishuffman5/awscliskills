# Recovery Points

### 6.1 `describe-recovery-point`

Returns detailed information about a recovery point.

**Synopsis:**
```bash
aws backup describe-recovery-point \
    --backup-vault-name <value> \
    --recovery-point-arn <value> \
    [--backup-vault-account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-vault-name` | **Yes** | string | -- | Vault name containing the recovery point |
| `--recovery-point-arn` | **Yes** | string | -- | Recovery point ARN |
| `--backup-vault-account-id` | No | string | None | Account ID for cross-account |

**Output Schema:**
```json
{
    "RecoveryPointArn": "string",
    "BackupVaultName": "string",
    "BackupVaultArn": "string",
    "SourceBackupVaultArn": "string",
    "ResourceArn": "string",
    "ResourceType": "string",
    "CreatedBy": {
        "BackupPlanId": "string",
        "BackupPlanArn": "string",
        "BackupPlanVersion": "string",
        "BackupRuleId": "string"
    },
    "IamRoleArn": "string",
    "Status": "COMPLETED|PARTIAL|DELETING|EXPIRED",
    "StatusMessage": "string",
    "CreationDate": "timestamp",
    "CompletionDate": "timestamp",
    "BackupSizeInBytes": "long",
    "CalculatedLifecycle": {
        "MoveToColdStorageAt": "timestamp",
        "DeleteAt": "timestamp"
    },
    "Lifecycle": {
        "MoveToColdStorageAfterDays": "long",
        "DeleteAfterDays": "long",
        "OptInToArchiveForSupportedResources": "boolean"
    },
    "EncryptionKeyArn": "string",
    "IsEncrypted": "boolean",
    "StorageClass": "WARM|COLD|DELETED",
    "LastRestoreTime": "timestamp",
    "ParentRecoveryPointArn": "string",
    "CompositeMemberIdentifier": "string",
    "IsParent": "boolean",
    "ResourceName": "string",
    "VaultType": "BACKUP_VAULT|LOGICALLY_AIR_GAPPED_BACKUP_VAULT",
    "IndexStatus": "PENDING|ACTIVE|FAILED|DELETING",
    "IndexStatusMessage": "string"
}
```

---

### 6.2 `list-recovery-points-by-backup-vault`

Lists recovery points in a vault. **Paginated operation.**

**Synopsis:**
```bash
aws backup list-recovery-points-by-backup-vault \
    --backup-vault-name <value> \
    [--backup-vault-account-id <value>] \
    [--by-resource-arn <value>] \
    [--by-resource-type <value>] \
    [--by-backup-plan-id <value>] \
    [--by-created-before <value>] \
    [--by-created-after <value>] \
    [--by-parent-recovery-point-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "NextToken": "string",
    "RecoveryPoints": [
        {
            "RecoveryPointArn": "string",
            "BackupVaultName": "string",
            "BackupVaultArn": "string",
            "SourceBackupVaultArn": "string",
            "ResourceArn": "string",
            "ResourceType": "string",
            "CreatedBy": {},
            "IamRoleArn": "string",
            "Status": "string",
            "CreationDate": "timestamp",
            "CompletionDate": "timestamp",
            "BackupSizeInBytes": "long",
            "Lifecycle": {},
            "EncryptionKeyArn": "string",
            "IsEncrypted": "boolean",
            "StorageClass": "string",
            "IsParent": "boolean",
            "ParentRecoveryPointArn": "string",
            "ResourceName": "string",
            "VaultType": "string",
            "IndexStatus": "string"
        }
    ]
}
```

---

### 6.3 `list-recovery-points-by-resource`

Lists recovery points for a specific resource. **Paginated operation.**

**Synopsis:**
```bash
aws backup list-recovery-points-by-resource \
    --resource-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |

**Output Schema:**
```json
{
    "NextToken": "string",
    "RecoveryPoints": [
        {
            "RecoveryPointArn": "string",
            "CreationDate": "timestamp",
            "Status": "string",
            "StatusMessage": "string",
            "EncryptionKeyArn": "string",
            "BackupSizeBytes": "long",
            "BackupVaultName": "string",
            "IsParent": "boolean",
            "ParentRecoveryPointArn": "string",
            "ResourceName": "string",
            "VaultType": "string",
            "IndexStatus": "string"
        }
    ]
}
```

---

### 6.4 `delete-recovery-point`

Deletes a recovery point from a vault.

**Synopsis:**
```bash
aws backup delete-recovery-point \
    --backup-vault-name <value> \
    --recovery-point-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-vault-name` | **Yes** | string | -- | Vault name |
| `--recovery-point-arn` | **Yes** | string | -- | Recovery point ARN |

**Output:** None

---

### 6.5 `update-recovery-point-lifecycle`

Sets the transition to cold storage and retention period for a recovery point.

**Synopsis:**
```bash
aws backup update-recovery-point-lifecycle \
    --backup-vault-name <value> \
    --recovery-point-arn <value> \
    [--lifecycle <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-vault-name` | **Yes** | string | -- | Vault name |
| `--recovery-point-arn` | **Yes** | string | -- | Recovery point ARN |
| `--lifecycle` | No | structure | None | Cold storage transition and deletion settings |

**Output Schema:**
```json
{
    "BackupVaultArn": "string",
    "RecoveryPointArn": "string",
    "Lifecycle": {
        "MoveToColdStorageAfterDays": "long",
        "DeleteAfterDays": "long",
        "OptInToArchiveForSupportedResources": "boolean"
    },
    "CalculatedLifecycle": {
        "MoveToColdStorageAt": "timestamp",
        "DeleteAt": "timestamp"
    }
}
```

---

### 6.6 `get-recovery-point-restore-metadata`

Returns metadata needed to restore a resource from a recovery point.

**Synopsis:**
```bash
aws backup get-recovery-point-restore-metadata \
    --backup-vault-name <value> \
    --recovery-point-arn <value> \
    [--backup-vault-account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-vault-name` | **Yes** | string | -- | Vault name |
| `--recovery-point-arn` | **Yes** | string | -- | Recovery point ARN |
| `--backup-vault-account-id` | No | string | None | Account ID |

**Output Schema:**
```json
{
    "BackupVaultArn": "string",
    "RecoveryPointArn": "string",
    "RestoreMetadata": {"string": "string"},
    "ResourceType": "string"
}
```
