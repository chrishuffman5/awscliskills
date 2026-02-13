# File Systems

### 1.1 `create-file-system`

Creates a new FSx file system (Windows, Lustre, ONTAP, or OpenZFS).

**Synopsis:**
```bash
aws fsx create-file-system \
    --file-system-type <value> \
    --subnet-ids <value> \
    [--storage-capacity <value>] \
    [--storage-type <value>] \
    [--security-group-ids <value>] \
    [--tags <value>] \
    [--kms-key-id <value>] \
    [--windows-configuration <value>] \
    [--lustre-configuration <value>] \
    [--ontap-configuration <value>] \
    [--open-zfs-configuration <value>] \
    [--file-system-type-version <value>] \
    [--network-type <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-type` | **Yes** | string | -- | `WINDOWS`, `LUSTRE`, `ONTAP`, or `OPENZFS` |
| `--subnet-ids` | **Yes** | list | -- | Subnet IDs (1 for single-AZ, 2 for multi-AZ) |
| `--storage-capacity` | No | integer | Type-dependent | Capacity in GiB |
| `--storage-type` | No | string | `SSD` | `SSD`, `HDD`, or `INTELLIGENT_TIERING` |
| `--security-group-ids` | No | list | Default SG | EC2 security group IDs |
| `--tags` | No | list | None | Tags (max 50) |
| `--kms-key-id` | No | string | FSx-managed | KMS key for encryption |
| `--windows-configuration` | No | structure | None | Windows File Server config (required if type=WINDOWS) |
| `--lustre-configuration` | No | structure | None | Lustre config (required if type=LUSTRE) |
| `--ontap-configuration` | No | structure | None | ONTAP config (required if type=ONTAP) |
| `--open-zfs-configuration` | No | structure | None | OpenZFS config (required if type=OPENZFS) |
| `--file-system-type-version` | No | string | None | Lustre version: `2.10`, `2.12`, `2.15` |
| `--network-type` | No | string | `IPV4` | `IPV4` or `DUAL` |
| `--client-request-token` | No | string | Auto | Idempotency token |

**Windows Configuration (key fields):**
```json
{
    "ThroughputCapacity": "integer (required, 8-100000 MB/s)",
    "DeploymentType": "SINGLE_AZ_1|SINGLE_AZ_2|MULTI_AZ_1",
    "ActiveDirectoryId": "string",
    "PreferredSubnetId": "string (required for MULTI_AZ_1)",
    "AutomaticBackupRetentionDays": "integer (0-90, default: 30)",
    "DailyAutomaticBackupStartTime": "string (HH:MM)",
    "WeeklyMaintenanceStartTime": "string (d:HH:MM)",
    "CopyTagsToBackups": "boolean",
    "Aliases": ["string"],
    "AuditLogConfiguration": {},
    "DiskIopsConfiguration": {}
}
```

**Lustre Configuration (key fields):**
```json
{
    "DeploymentType": "SCRATCH_1|SCRATCH_2|PERSISTENT_1|PERSISTENT_2",
    "PerUnitStorageThroughput": "integer (12-1000 MB/s/TiB)",
    "DataCompressionType": "NONE|LZ4",
    "AutomaticBackupRetentionDays": "integer (0-90)",
    "LogConfiguration": {},
    "MetadataConfiguration": {},
    "EfaEnabled": "boolean"
}
```

**ONTAP Configuration (key fields):**
```json
{
    "DeploymentType": "SINGLE_AZ_1|SINGLE_AZ_2|MULTI_AZ_1|MULTI_AZ_2",
    "ThroughputCapacity": "integer (8-100000 MBps)",
    "HAPairs": "integer (1-12)",
    "FsxAdminPassword": "string (8-50 chars)",
    "PreferredSubnetId": "string (required for multi-AZ)",
    "RouteTableIds": ["string"],
    "AutomaticBackupRetentionDays": "integer (0-90, default: 30)",
    "DiskIopsConfiguration": {},
    "EndpointIpAddressRange": "string"
}
```

**OpenZFS Configuration (key fields):**
```json
{
    "DeploymentType": "SINGLE_AZ_1|SINGLE_AZ_2|SINGLE_AZ_HA_1|SINGLE_AZ_HA_2|MULTI_AZ_1",
    "ThroughputCapacity": "integer (required)",
    "AutomaticBackupRetentionDays": "integer (0-90, default: 30)",
    "CopyTagsToBackups": "boolean",
    "CopyTagsToVolumes": "boolean",
    "RootVolumeConfiguration": {},
    "DiskIopsConfiguration": {},
    "PreferredSubnetId": "string (required for MULTI_AZ_1)",
    "RouteTableIds": ["string"]
}
```

**Output Schema:**
```json
{
    "FileSystem": {
        "OwnerId": "string",
        "CreationTime": "timestamp",
        "FileSystemId": "string",
        "FileSystemType": "WINDOWS|LUSTRE|ONTAP|OPENZFS",
        "Lifecycle": "AVAILABLE|CREATING|DELETING|FAILED|MISCONFIGURED|UPDATING|MISCONFIGURED_UNAVAILABLE",
        "StorageCapacity": "integer",
        "StorageType": "SSD|HDD|INTELLIGENT_TIERING",
        "VpcId": "string",
        "SubnetIds": ["string"],
        "DNSName": "string",
        "KmsKeyId": "string",
        "ResourceARN": "string",
        "Tags": []
    }
}
```

---

### 1.2 `create-file-system-from-backup`

Creates a new file system from an existing backup.

**Synopsis:**
```bash
aws fsx create-file-system-from-backup \
    --backup-id <value> \
    --subnet-ids <value> \
    [--security-group-ids <value>] \
    [--tags <value>] \
    [--windows-configuration <value>] \
    [--lustre-configuration <value>] \
    [--storage-type <value>] \
    [--kms-key-id <value>] \
    [--file-system-type-version <value>] \
    [--open-zfs-configuration <value>] \
    [--storage-capacity <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-id` | **Yes** | string | -- | Backup ID to restore from |
| `--subnet-ids` | **Yes** | list | -- | Subnet IDs |
| `--security-group-ids` | No | list | Default SG | Security group IDs |
| `--tags` | No | list | None | Tags |
| `--windows-configuration` | No | structure | None | Override Windows config |
| `--lustre-configuration` | No | structure | None | Override Lustre config |
| `--open-zfs-configuration` | No | structure | None | Override OpenZFS config |
| `--storage-type` | No | string | None | Storage type override |
| `--storage-capacity` | No | integer | None | Storage capacity override |

**Output:** Same as `create-file-system`

---

### 1.3 `describe-file-systems`

Returns descriptions of file systems. **Paginated operation.**

**Synopsis:**
```bash
aws fsx describe-file-systems \
    [--file-system-ids <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-ids` | No | list | None | File system IDs (max 50) |

**Output Schema:**
```json
{
    "FileSystems": [
        {
            "OwnerId": "string",
            "CreationTime": "timestamp",
            "FileSystemId": "string",
            "FileSystemType": "WINDOWS|LUSTRE|ONTAP|OPENZFS",
            "Lifecycle": "string",
            "StorageCapacity": "integer",
            "StorageType": "string",
            "VpcId": "string",
            "SubnetIds": ["string"],
            "DNSName": "string",
            "ResourceARN": "string",
            "Tags": [],
            "WindowsConfiguration": {},
            "LustreConfiguration": {},
            "OntapConfiguration": {},
            "OpenZfsConfiguration": {},
            "AdministrativeActions": []
        }
    ],
    "NextToken": "string"
}
```

---

### 1.4 `update-file-system`

Updates a file system's configuration (throughput, storage capacity, maintenance window, etc.).

**Synopsis:**
```bash
aws fsx update-file-system \
    --file-system-id <value> \
    [--storage-capacity <value>] \
    [--storage-type <value>] \
    [--windows-configuration <value>] \
    [--lustre-configuration <value>] \
    [--ontap-configuration <value>] \
    [--open-zfs-configuration <value>] \
    [--file-system-type-version <value>] \
    [--network-type <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-id` | **Yes** | string | -- | File system ID |
| `--storage-capacity` | No | integer | None | New storage capacity in GiB |
| `--storage-type` | No | string | None | `SSD`, `HDD`, or `INTELLIGENT_TIERING` |
| `--windows-configuration` | No | structure | None | Windows config updates |
| `--lustre-configuration` | No | structure | None | Lustre config updates |
| `--ontap-configuration` | No | structure | None | ONTAP config updates |
| `--open-zfs-configuration` | No | structure | None | OpenZFS config updates |

**Output:** Same as `create-file-system`

---

### 1.5 `delete-file-system`

Deletes a file system. Optionally creates a final backup.

**Synopsis:**
```bash
aws fsx delete-file-system \
    --file-system-id <value> \
    [--windows-configuration <value>] \
    [--lustre-configuration <value>] \
    [--open-zfs-configuration <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-id` | **Yes** | string | -- | File system ID |
| `--windows-configuration` | No | structure | None | Final backup options for Windows |
| `--lustre-configuration` | No | structure | None | Final backup options for Lustre |
| `--open-zfs-configuration` | No | structure | None | Final backup/snapshot options for OpenZFS |

**Output Schema:**
```json
{
    "FileSystemId": "string",
    "Lifecycle": "DELETING",
    "WindowsResponse": {
        "FinalBackupId": "string",
        "FinalBackupTags": []
    },
    "LustreResponse": {
        "FinalBackupId": "string",
        "FinalBackupTags": []
    },
    "OpenZFSResponse": {
        "FinalBackupId": "string",
        "FinalBackupTags": []
    }
}
```

---

### 1.6 `associate-file-system-aliases`

Associates one or more DNS aliases with a Windows File Server file system.

**Synopsis:**
```bash
aws fsx associate-file-system-aliases \
    --file-system-id <value> \
    --aliases <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-id` | **Yes** | string | -- | File system ID |
| `--aliases` | **Yes** | list | -- | DNS aliases (max 50) |

**Output Schema:**
```json
{
    "Aliases": [
        {
            "Name": "string",
            "Lifecycle": "AVAILABLE|CREATING|DELETING|CREATE_FAILED|DELETE_FAILED"
        }
    ]
}
```

---

### 1.7 `disassociate-file-system-aliases`

Disassociates DNS aliases from a Windows File Server file system.

**Synopsis:**
```bash
aws fsx disassociate-file-system-aliases \
    --file-system-id <value> \
    --aliases <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-id` | **Yes** | string | -- | File system ID |
| `--aliases` | **Yes** | list | -- | DNS aliases to remove |

**Output Schema:**
```json
{
    "Aliases": [
        {
            "Name": "string",
            "Lifecycle": "DELETING"
        }
    ]
}
```

---

### 1.8 `describe-file-system-aliases`

Returns DNS aliases associated with a file system. **Paginated operation.**

**Synopsis:**
```bash
aws fsx describe-file-system-aliases \
    --file-system-id <value> \
    [--client-request-token <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-id` | **Yes** | string | -- | File system ID |

**Output Schema:**
```json
{
    "Aliases": [
        {
            "Name": "string",
            "Lifecycle": "AVAILABLE|CREATING|DELETING|CREATE_FAILED|DELETE_FAILED"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.9 `describe-shared-vpc-configuration`

Returns the shared VPC configuration for the account.

**Synopsis:**
```bash
aws fsx describe-shared-vpc-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "EnableFsxRouteTableUpdatesFromParticipantAccounts": "string"
}
```

---

### 1.10 `update-shared-vpc-configuration`

Updates the shared VPC configuration.

**Synopsis:**
```bash
aws fsx update-shared-vpc-configuration \
    [--enable-fsx-route-table-updates-from-participant-accounts <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--enable-fsx-route-table-updates-from-participant-accounts` | No | string | None | `true` or `false` |

**Output Schema:**
```json
{
    "EnableFsxRouteTableUpdatesFromParticipantAccounts": "string"
}
```

---

### 1.11 `release-file-system-nfs-v3-locks`

Releases all NFS v3 locks on a file system.

**Synopsis:**
```bash
aws fsx release-file-system-nfs-v3-locks \
    --file-system-id <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-id` | **Yes** | string | -- | File system ID |

**Output:** Returns `FileSystem` object

---

### 1.12 `start-misconfigured-state-recovery`

Initiates recovery for a misconfigured file system.

**Synopsis:**
```bash
aws fsx start-misconfigured-state-recovery \
    --file-system-id <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-id` | **Yes** | string | -- | File system ID |

**Output:** Returns `FileSystem` object
