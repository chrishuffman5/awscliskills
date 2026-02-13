# File Systems

### 1.1 `create-file-system`

Creates a new, empty file system. The operation requires a creation token to ensure idempotent creation.

**Synopsis:**
```bash
aws efs create-file-system \
    --creation-token <value> \
    [--performance-mode <value>] \
    [--encrypted | --no-encrypted] \
    [--kms-key-id <value>] \
    [--throughput-mode <value>] \
    [--provisioned-throughput-in-mibps <value>] \
    [--availability-zone-name <value>] \
    [--backup | --no-backup] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--creation-token` | **Yes** | string | -- | Idempotency token (up to 64 ASCII chars). Use a unique string per file system |
| `--performance-mode` | No | string | `generalPurpose` | Performance mode: `generalPurpose` or `maxIO` |
| `--encrypted` / `--no-encrypted` | No | boolean | false | Whether to encrypt the file system at rest |
| `--kms-key-id` | No | string | aws/elasticfilesystem | KMS key ID or ARN for encryption (requires `--encrypted`) |
| `--throughput-mode` | No | string | `bursting` | Throughput mode: `bursting`, `provisioned`, or `elastic` |
| `--provisioned-throughput-in-mibps` | No | double | -- | Provisioned throughput in MiB/s (required when throughput-mode is `provisioned`) |
| `--availability-zone-name` | No | string | -- | AZ name for One Zone file system (e.g., `us-east-1a`) |
| `--backup` / `--no-backup` | No | boolean | varies | Enable/disable automatic backups |
| `--tags` | No | list | None | Tags to add. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "OwnerId": "string",
    "CreationToken": "string",
    "FileSystemId": "string",
    "FileSystemArn": "string",
    "CreationTime": "timestamp",
    "LifeCycleState": "creating|available|updating|deleting|deleted|error",
    "Name": "string",
    "NumberOfMountTargets": "integer",
    "SizeInBytes": {
        "Value": "long",
        "Timestamp": "timestamp",
        "ValueInIA": "long",
        "ValueInStandard": "long",
        "ValueInArchive": "long"
    },
    "PerformanceMode": "generalPurpose|maxIO",
    "Encrypted": "boolean",
    "KmsKeyId": "string",
    "ThroughputMode": "bursting|provisioned|elastic",
    "ProvisionedThroughputInMibps": "double",
    "AvailabilityZoneId": "string",
    "AvailabilityZoneName": "string",
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ],
    "FileSystemProtection": {
        "ReplicationOverwriteProtection": "ENABLED|DISABLED|REPLICATING"
    }
}
```

---

### 1.2 `delete-file-system`

Deletes a file system. All mount targets must be deleted first. Cannot delete a file system that is part of an active replication configuration.

**Synopsis:**
```bash
aws efs delete-file-system \
    --file-system-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-id` | **Yes** | string | -- | ID of the file system to delete |

**Output:** None on success.

---

### 1.3 `describe-file-systems`

Returns the description of a specific or all EFS file systems owned by the caller. **Paginated operation.**

**Synopsis:**
```bash
aws efs describe-file-systems \
    [--max-items <value>] \
    [--creation-token <value>] \
    [--file-system-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-id` | No | string | -- | ID of a specific file system to describe |
| `--creation-token` | No | string | -- | Creation token to filter by |
| `--max-items` | No | integer | None | Total items to return |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |

**Output Schema:**
```json
{
    "FileSystems": [
        {
            "OwnerId": "string",
            "CreationToken": "string",
            "FileSystemId": "string",
            "FileSystemArn": "string",
            "CreationTime": "timestamp",
            "LifeCycleState": "creating|available|updating|deleting|deleted|error",
            "Name": "string",
            "NumberOfMountTargets": "integer",
            "SizeInBytes": {
                "Value": "long",
                "Timestamp": "timestamp",
                "ValueInIA": "long",
                "ValueInStandard": "long",
                "ValueInArchive": "long"
            },
            "PerformanceMode": "generalPurpose|maxIO",
            "Encrypted": "boolean",
            "KmsKeyId": "string",
            "ThroughputMode": "bursting|provisioned|elastic",
            "ProvisionedThroughputInMibps": "double",
            "AvailabilityZoneId": "string",
            "AvailabilityZoneName": "string",
            "Tags": [
                {
                    "Key": "string",
                    "Value": "string"
                }
            ],
            "FileSystemProtection": {
                "ReplicationOverwriteProtection": "ENABLED|DISABLED|REPLICATING"
            }
        }
    ],
    "NextMarker": "string"
}
```

---

### 1.4 `update-file-system`

Updates the throughput mode or provisioned throughput of an existing file system.

**Synopsis:**
```bash
aws efs update-file-system \
    --file-system-id <value> \
    [--throughput-mode <value>] \
    [--provisioned-throughput-in-mibps <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-id` | **Yes** | string | -- | ID of the file system to update |
| `--throughput-mode` | No | string | -- | New throughput mode: `bursting`, `provisioned`, or `elastic` |
| `--provisioned-throughput-in-mibps` | No | double | -- | Provisioned throughput in MiB/s (required when switching to `provisioned`) |

**Output Schema:** Same as `create-file-system` output.

---

### 1.5 `put-lifecycle-configuration`

Enables lifecycle management for a file system by creating a new lifecycle configuration. Replaces any existing configuration.

**Synopsis:**
```bash
aws efs put-lifecycle-configuration \
    --file-system-id <value> \
    --lifecycle-policies <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-id` | **Yes** | string | -- | ID of the file system |
| `--lifecycle-policies` | **Yes** | list | -- | Lifecycle policies. Shorthand: `TransitionToIA=AFTER_30_DAYS TransitionToPrimaryStorageClass=AFTER_1_ACCESS` |

**Lifecycle Policy Structure:**
```json
[
    {
        "TransitionToIA": "AFTER_7_DAYS|AFTER_14_DAYS|AFTER_30_DAYS|AFTER_60_DAYS|AFTER_90_DAYS|AFTER_1_DAY",
        "TransitionToPrimaryStorageClass": "AFTER_1_ACCESS",
        "TransitionToArchive": "AFTER_1_DAY|AFTER_7_DAYS|AFTER_14_DAYS|AFTER_30_DAYS|AFTER_60_DAYS|AFTER_90_DAYS|AFTER_180_DAYS|AFTER_270_DAYS|AFTER_365_DAYS"
    }
]
```

**Output Schema:**
```json
{
    "LifecyclePolicies": [
        {
            "TransitionToIA": "string",
            "TransitionToPrimaryStorageClass": "string",
            "TransitionToArchive": "string"
        }
    ]
}
```

---

### 1.6 `describe-lifecycle-configuration`

Returns the current lifecycle configuration for a file system.

**Synopsis:**
```bash
aws efs describe-lifecycle-configuration \
    --file-system-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-id` | **Yes** | string | -- | ID of the file system |

**Output Schema:**
```json
{
    "LifecyclePolicies": [
        {
            "TransitionToIA": "string",
            "TransitionToPrimaryStorageClass": "string",
            "TransitionToArchive": "string"
        }
    ]
}
```

---

### 1.7 `put-backup-policy`

Updates the backup policy for a file system.

**Synopsis:**
```bash
aws efs put-backup-policy \
    --file-system-id <value> \
    --backup-policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-id` | **Yes** | string | -- | ID of the file system |
| `--backup-policy` | **Yes** | structure | -- | Backup policy. Shorthand: `Status=ENABLED` or `Status=DISABLED` |

**Output Schema:**
```json
{
    "BackupPolicy": {
        "Status": "ENABLED|ENABLING|DISABLED|DISABLING"
    }
}
```

---

### 1.8 `describe-backup-policy`

Returns the backup policy for a file system.

**Synopsis:**
```bash
aws efs describe-backup-policy \
    --file-system-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-id` | **Yes** | string | -- | ID of the file system |

**Output Schema:**
```json
{
    "BackupPolicy": {
        "Status": "ENABLED|ENABLING|DISABLED|DISABLING"
    }
}
```

---

### 1.9 `put-file-system-policy`

Applies or updates the resource-level IAM policy for a file system. Used to control NFS access.

**Synopsis:**
```bash
aws efs put-file-system-policy \
    --file-system-id <value> \
    --policy <value> \
    [--bypass-policy-lockout-safety-check | --no-bypass-policy-lockout-safety-check] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-id` | **Yes** | string | -- | ID of the file system |
| `--policy` | **Yes** | string | -- | IAM resource policy JSON document (max 20,000 chars) |
| `--bypass-policy-lockout-safety-check` | No | boolean | false | Skip the lockout safety check (prevents accidental lockout) |

**Output Schema:**
```json
{
    "FileSystemId": "string",
    "Policy": "string"
}
```

---

### 1.10 `describe-file-system-policy`

Returns the resource-level IAM policy for a file system.

**Synopsis:**
```bash
aws efs describe-file-system-policy \
    --file-system-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-id` | **Yes** | string | -- | ID of the file system |

**Output Schema:**
```json
{
    "FileSystemId": "string",
    "Policy": "string"
}
```

---

### 1.11 `delete-file-system-policy`

Deletes the resource-level IAM policy from a file system, reverting to default (allow all).

**Synopsis:**
```bash
aws efs delete-file-system-policy \
    --file-system-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-id` | **Yes** | string | -- | ID of the file system |

**Output:** None on success.
