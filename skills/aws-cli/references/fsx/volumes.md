# Volumes

### 3.1 `create-volume`

Creates an ONTAP or OpenZFS volume.

**Synopsis:**
```bash
aws fsx create-volume \
    --volume-type <value> \
    --name <value> \
    [--ontap-configuration <value>] \
    [--open-zfs-configuration <value>] \
    [--tags <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--volume-type` | **Yes** | string | -- | `ONTAP` or `OPENZFS` |
| `--name` | **Yes** | string | -- | Volume name (1-203 chars) |
| `--ontap-configuration` | No | structure | None | ONTAP volume config |
| `--open-zfs-configuration` | No | structure | None | OpenZFS volume config |
| `--tags` | No | list | None | Tags (max 50) |

**ONTAP Configuration (key fields):**
```json
{
    "JunctionPath": "string (required)",
    "StorageVirtualMachineId": "string (required)",
    "SizeInMegabytes": "integer",
    "SizeInBytes": "long",
    "StorageEfficiencyEnabled": "boolean (required for RW)",
    "SecurityStyle": "UNIX|NTFS|MIXED",
    "OntapVolumeType": "RW|DP",
    "VolumeStyle": "FLEXVOL|FLEXGROUP",
    "TieringPolicy": {
        "CoolingPeriod": "integer (2-183 days)",
        "Name": "SNAPSHOT_ONLY|AUTO|ALL|NONE"
    },
    "SnaplockConfiguration": {
        "SnaplockType": "COMPLIANCE|ENTERPRISE",
        "RetentionPeriod": {},
        "PrivilegedDelete": "DISABLED|ENABLED|PERMANENTLY_DISABLED"
    },
    "SnapshotPolicy": "string",
    "CopyTagsToBackups": "boolean"
}
```

**OpenZFS Configuration (key fields):**
```json
{
    "ParentVolumeId": "string (required)",
    "StorageCapacityReservationGiB": "integer",
    "StorageCapacityQuotaGiB": "integer",
    "RecordSizeKiB": "integer (4-4096)",
    "DataCompressionType": "NONE|ZSTD|LZ4",
    "CopyTagsToSnapshots": "boolean",
    "ReadOnly": "boolean",
    "NfsExports": [],
    "UserAndGroupQuotas": [],
    "OriginSnapshot": {
        "SnapshotARN": "string",
        "CopyStrategy": "CLONE|FULL_COPY|INCREMENTAL_COPY"
    }
}
```

**Output Schema:**
```json
{
    "Volume": {
        "CreationTime": "timestamp",
        "FileSystemId": "string",
        "Lifecycle": "CREATING|CREATED|DELETING|FAILED|MISCONFIGURED|PENDING|AVAILABLE",
        "Name": "string",
        "VolumeId": "string",
        "VolumeType": "ONTAP|OPENZFS",
        "ResourceARN": "string",
        "Tags": [],
        "OntapConfiguration": {},
        "OpenZfsConfiguration": {},
        "AdministrativeActions": []
    }
}
```

---

### 3.2 `create-volume-from-backup`

Creates an ONTAP volume from an existing backup.

**Synopsis:**
```bash
aws fsx create-volume-from-backup \
    --backup-id <value> \
    --name <value> \
    [--ontap-configuration <value>] \
    [--tags <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-id` | **Yes** | string | -- | Backup ID to restore from |
| `--name` | **Yes** | string | -- | Volume name |
| `--ontap-configuration` | No | structure | None | ONTAP config overrides |
| `--tags` | No | list | None | Tags |

**Output:** Same as `create-volume`

---

### 3.3 `describe-volumes`

Returns descriptions of volumes. **Paginated operation.**

**Synopsis:**
```bash
aws fsx describe-volumes \
    [--volume-ids <value>] \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--volume-ids` | No | list | None | Volume IDs (max 50) |
| `--filters` | No | list | None | Filters: `file-system-id`, `storage-virtual-machine-id` |

**Output Schema:**
```json
{
    "Volumes": [
        {
            "VolumeId": "string",
            "Name": "string",
            "FileSystemId": "string",
            "Lifecycle": "string",
            "VolumeType": "ONTAP|OPENZFS",
            "ResourceARN": "string",
            "Tags": [],
            "OntapConfiguration": {},
            "OpenZfsConfiguration": {},
            "AdministrativeActions": []
        }
    ],
    "NextToken": "string"
}
```

---

### 3.4 `update-volume`

Updates a volume's configuration.

**Synopsis:**
```bash
aws fsx update-volume \
    --volume-id <value> \
    [--name <value>] \
    [--ontap-configuration <value>] \
    [--open-zfs-configuration <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--volume-id` | **Yes** | string | -- | Volume ID |
| `--name` | No | string | None | New volume name |
| `--ontap-configuration` | No | structure | None | ONTAP config updates |
| `--open-zfs-configuration` | No | structure | None | OpenZFS config updates |

**Output:** Same as `create-volume`

---

### 3.5 `delete-volume`

Deletes a volume.

**Synopsis:**
```bash
aws fsx delete-volume \
    --volume-id <value> \
    [--ontap-configuration <value>] \
    [--open-zfs-configuration <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--volume-id` | **Yes** | string | -- | Volume ID |
| `--ontap-configuration` | No | structure | None | ONTAP delete options (skip final backup, backup tags) |
| `--open-zfs-configuration` | No | structure | None | OpenZFS delete options |

**ONTAP Delete Configuration:**
```json
{
    "SkipFinalBackup": "boolean",
    "FinalBackupTags": [],
    "BypassSnaplockEnterpriseRetention": "boolean"
}
```

**Output Schema:**
```json
{
    "VolumeId": "string",
    "Lifecycle": "DELETING",
    "OntapResponse": {
        "FinalBackupId": "string",
        "FinalBackupTags": []
    }
}
```

---

### 3.6 `copy-snapshot-and-update-volume`

Copies a snapshot and updates a volume with it.

**Synopsis:**
```bash
aws fsx copy-snapshot-and-update-volume \
    --volume-id <value> \
    --source-snapshot-arn <value> \
    [--copy-strategy <value>] \
    [--options <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--volume-id` | **Yes** | string | -- | Target volume ID |
| `--source-snapshot-arn` | **Yes** | string | -- | Source snapshot ARN |
| `--copy-strategy` | No | string | None | `CLONE`, `FULL_COPY`, or `INCREMENTAL_COPY` |
| `--options` | No | list | None | Options: `DELETE_INTERMEDIATE_SNAPSHOTS`, `DELETE_CLONED_VOLUMES` |

**Output Schema:**
```json
{
    "VolumeId": "string",
    "Lifecycle": "string",
    "AdministrativeActions": []
}
```

---

### 3.7 `restore-volume-from-snapshot`

Restores a volume to a previous snapshot.

**Synopsis:**
```bash
aws fsx restore-volume-from-snapshot \
    --volume-id <value> \
    --snapshot-id <value> \
    [--options <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--volume-id` | **Yes** | string | -- | Volume ID |
| `--snapshot-id` | **Yes** | string | -- | Snapshot ID to restore to |
| `--options` | No | list | None | Options: `DELETE_INTERMEDIATE_SNAPSHOTS`, `DELETE_CLONED_VOLUMES` |

**Output Schema:**
```json
{
    "VolumeId": "string",
    "Lifecycle": "string",
    "AdministrativeActions": []
}
```
