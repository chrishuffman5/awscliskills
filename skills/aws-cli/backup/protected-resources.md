# Protected Resources

### 7.1 `describe-protected-resource`

Returns information about a resource that has been backed up by AWS Backup.

**Synopsis:**
```bash
aws backup describe-protected-resource \
    --resource-arn <value> \
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
    "ResourceArn": "string",
    "ResourceType": "string",
    "LastBackupTime": "timestamp",
    "ResourceName": "string",
    "LastBackupVaultArn": "string",
    "LastRecoveryPointArn": "string"
}
```

---

### 7.2 `list-protected-resources`

Lists all resources that have been backed up. **Paginated operation.**

**Synopsis:**
```bash
aws backup list-protected-resources \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "Results": [
        {
            "ResourceArn": "string",
            "ResourceType": "string",
            "LastBackupTime": "timestamp",
            "ResourceName": "string",
            "LastBackupVaultArn": "string",
            "LastRecoveryPointArn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.3 `list-protected-resources-by-backup-vault`

Lists resources protected by a specific vault. **Paginated operation.**

**Synopsis:**
```bash
aws backup list-protected-resources-by-backup-vault \
    --backup-vault-name <value> \
    [--backup-vault-account-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-vault-name` | **Yes** | string | -- | Vault name |
| `--backup-vault-account-id` | No | string | None | Account ID |

---

### 7.4 `get-supported-resource-types`

Returns a list of resource types supported by AWS Backup.

**Synopsis:**
```bash
aws backup get-supported-resource-types \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "ResourceTypes": ["string"]
}
```
