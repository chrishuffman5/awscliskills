# Serverless Snapshots (`aws redshift-serverless`)

### 16.1 `create-snapshot`

Creates a serverless snapshot.

**Synopsis:**
```bash
aws redshift-serverless create-snapshot \
    --namespace-name <value> \
    --snapshot-name <value> \
    [--retention-period <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--namespace-name` | **Yes** | string | -- | Namespace to snapshot |
| `--snapshot-name` | **Yes** | string | -- | Snapshot name |
| `--retention-period` | No | integer | -- | Retention period in days |
| `--tags` | No | list | -- | Tags |

**Output Schema:**
```json
{
    "snapshot": {
        "snapshotName": "string",
        "snapshotArn": "string",
        "namespaceName": "string",
        "namespaceArn": "string",
        "status": "CREATING|AVAILABLE|DELETING|FAILED",
        "snapshotCreateTime": "timestamp",
        "snapshotRetentionPeriod": "integer",
        "snapshotRetentionStartTime": "timestamp",
        "adminUsername": "string",
        "kmsKeyId": "string",
        "ownerAccount": "string",
        "accountsWithRestoreAccess": ["string"],
        "accountsWithProvisionedRestoreAccess": ["string"],
        "adminPasswordSecretArn": "string",
        "adminPasswordSecretKmsKeyId": "string"
    }
}
```

---

### 16.2 `delete-snapshot`

Deletes a serverless snapshot.

**Synopsis:**
```bash
aws redshift-serverless delete-snapshot \
    --snapshot-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--snapshot-name` | **Yes** | string | -- | Snapshot to delete |

**Output Schema:**
```json
{
    "snapshot": {
        "snapshotName": "string",
        "status": "DELETING"
    }
}
```

---

### 16.3 `get-snapshot`

Returns information about a serverless snapshot.

**Synopsis:**
```bash
aws redshift-serverless get-snapshot \
    [--snapshot-name <value>] \
    [--snapshot-arn <value>] \
    [--owner-account <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--snapshot-name` | No | string | -- | Snapshot name (either this or `--snapshot-arn` required) |
| `--snapshot-arn` | No | string | -- | Snapshot ARN |
| `--owner-account` | No | string | -- | Owner account |

**Output Schema:**
```json
{
    "snapshot": {
        "snapshotName": "string",
        "snapshotArn": "string",
        "namespaceName": "string",
        "namespaceArn": "string",
        "status": "string",
        "snapshotCreateTime": "timestamp",
        "snapshotRetentionPeriod": "integer",
        "adminUsername": "string",
        "kmsKeyId": "string",
        "ownerAccount": "string",
        "accountsWithRestoreAccess": ["string"]
    }
}
```

---

### 16.4 `list-snapshots`

Lists serverless snapshots. **Paginated operation.**

**Synopsis:**
```bash
aws redshift-serverless list-snapshots \
    [--namespace-name <value>] \
    [--namespace-arn <value>] \
    [--owner-account <value>] \
    [--start-time <value>] \
    [--end-time <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--namespace-name` | No | string | -- | Filter by namespace name |
| `--namespace-arn` | No | string | -- | Filter by namespace ARN |
| `--owner-account` | No | string | -- | Filter by owner account |
| `--start-time` | No | timestamp | -- | Filter after this time |
| `--end-time` | No | timestamp | -- | Filter before this time |
| `--next-token` | No | string | -- | Pagination token |
| `--max-results` | No | integer | -- | Maximum results |

**Output Schema:**
```json
{
    "snapshots": [
        {
            "snapshotName": "string",
            "snapshotArn": "string",
            "namespaceName": "string",
            "status": "string",
            "snapshotCreateTime": "timestamp",
            "snapshotRetentionPeriod": "integer",
            "adminUsername": "string",
            "ownerAccount": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 16.5 `update-snapshot`

Updates the retention period of a serverless snapshot.

**Synopsis:**
```bash
aws redshift-serverless update-snapshot \
    --snapshot-name <value> \
    [--retention-period <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--snapshot-name` | **Yes** | string | -- | Snapshot to update |
| `--retention-period` | No | integer | -- | New retention period in days |

**Output Schema:**
```json
{
    "snapshot": {
        "snapshotName": "string",
        "snapshotRetentionPeriod": "integer",
        "status": "string"
    }
}
```

---

### 16.6 `restore-from-snapshot`

Restores a namespace from a serverless snapshot.

**Synopsis:**
```bash
aws redshift-serverless restore-from-snapshot \
    --namespace-name <value> \
    --workgroup-name <value> \
    [--snapshot-name <value>] \
    [--snapshot-arn <value>] \
    [--owner-account <value>] \
    [--manage-admin-password | --no-manage-admin-password] \
    [--admin-password-secret-kms-key-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--namespace-name` | **Yes** | string | -- | Namespace name for the restored namespace |
| `--workgroup-name` | **Yes** | string | -- | Workgroup name for the restored workgroup |
| `--snapshot-name` | No | string | -- | Snapshot to restore from |
| `--snapshot-arn` | No | string | -- | Snapshot ARN |
| `--owner-account` | No | string | -- | Account that owns the snapshot |
| `--manage-admin-password` | No | boolean | -- | Use Secrets Manager for admin password |
| `--admin-password-secret-kms-key-id` | No | string | -- | KMS key for Secrets Manager secret |

**Output Schema:**
```json
{
    "snapshotName": "string",
    "ownerAccount": "string",
    "namespace": {
        "namespaceName": "string",
        "namespaceArn": "string",
        "status": "MODIFYING"
    }
}
```

---

### 16.7 `convert-recovery-point-to-snapshot`

Converts a recovery point to a snapshot.

**Synopsis:**
```bash
aws redshift-serverless convert-recovery-point-to-snapshot \
    --recovery-point-id <value> \
    --snapshot-name <value> \
    [--retention-period <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--recovery-point-id` | **Yes** | string | -- | Recovery point ID to convert |
| `--snapshot-name` | **Yes** | string | -- | Name for the new snapshot |
| `--retention-period` | No | integer | -- | Retention period in days |
| `--tags` | No | list | -- | Tags |

**Output Schema:**
```json
{
    "snapshot": {
        "snapshotName": "string",
        "snapshotArn": "string",
        "namespaceName": "string",
        "status": "CREATING"
    }
}
```

---

### 16.8 `get-recovery-point`

Returns information about a recovery point.

**Synopsis:**
```bash
aws redshift-serverless get-recovery-point \
    --recovery-point-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--recovery-point-id` | **Yes** | string | -- | Recovery point ID |

**Output Schema:**
```json
{
    "recoveryPoint": {
        "recoveryPointId": "string",
        "recoveryPointCreateTime": "timestamp",
        "namespaceName": "string",
        "namespaceArn": "string",
        "totalSizeInMegaBytes": "double",
        "workgroupName": "string"
    }
}
```

---

### 16.9 `list-recovery-points`

Lists recovery points. **Paginated operation.**

**Synopsis:**
```bash
aws redshift-serverless list-recovery-points \
    [--namespace-name <value>] \
    [--namespace-arn <value>] \
    [--start-time <value>] \
    [--end-time <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--namespace-name` | No | string | -- | Filter by namespace |
| `--namespace-arn` | No | string | -- | Filter by namespace ARN |
| `--start-time` | No | timestamp | -- | Filter after this time |
| `--end-time` | No | timestamp | -- | Filter before this time |
| `--next-token` | No | string | -- | Pagination token |
| `--max-results` | No | integer | -- | Maximum results |

**Output Schema:**
```json
{
    "recoveryPoints": [
        {
            "recoveryPointId": "string",
            "recoveryPointCreateTime": "timestamp",
            "namespaceName": "string",
            "namespaceArn": "string",
            "totalSizeInMegaBytes": "double",
            "workgroupName": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 16.10 `restore-table-from-snapshot`

Restores a single table from a snapshot to the current namespace.

**Synopsis:**
```bash
aws redshift-serverless restore-table-from-snapshot \
    --namespace-name <value> \
    --workgroup-name <value> \
    --snapshot-name <value> \
    --source-database-name <value> \
    --source-table-name <value> \
    --new-table-name <value> \
    [--source-schema-name <value>] \
    [--target-database-name <value>] \
    [--target-schema-name <value>] \
    [--activate-case-sensitive-identifier | --no-activate-case-sensitive-identifier] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--namespace-name` | **Yes** | string | -- | Target namespace |
| `--workgroup-name` | **Yes** | string | -- | Target workgroup |
| `--snapshot-name` | **Yes** | string | -- | Source snapshot name |
| `--source-database-name` | **Yes** | string | -- | Source database name |
| `--source-table-name` | **Yes** | string | -- | Source table name |
| `--new-table-name` | **Yes** | string | -- | Name for the restored table |
| `--source-schema-name` | No | string | `public` | Source schema name |
| `--target-database-name` | No | string | -- | Target database name |
| `--target-schema-name` | No | string | -- | Target schema name |
| `--activate-case-sensitive-identifier` | No | boolean | -- | Enable case-sensitive identifiers |

**Output Schema:**
```json
{
    "tableRestoreStatus": {
        "tableRestoreRequestId": "string",
        "status": "PENDING|IN_PROGRESS|SUCCEEDED|FAILED|CANCELED",
        "message": "string",
        "requestTime": "timestamp",
        "namespaceName": "string",
        "workgroupName": "string",
        "snapshotName": "string",
        "progressInMegaBytes": "long",
        "totalDataInMegaBytes": "long",
        "sourceDatabaseName": "string",
        "sourceSchemaName": "string",
        "sourceTableName": "string",
        "targetDatabaseName": "string",
        "targetSchemaName": "string",
        "newTableName": "string",
        "recoveryPointId": "string"
    }
}
```
