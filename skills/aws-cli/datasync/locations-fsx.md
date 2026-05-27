# Locations (FSx)

### 4.1 `create-location-fsx-windows`

Creates a transfer location for an Amazon FSx for Windows File Server file system.

**Synopsis:**
```bash
aws datasync create-location-fsx-windows \
    --fsx-filesystem-arn <value> \
    --security-group-arns <value> \
    --user <value> \
    --password <value> \
    [--subdirectory <value>] \
    [--domain <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fsx-filesystem-arn` | **Yes** | string | -- | ARN of the FSx for Windows file system |
| `--security-group-arns` | **Yes** | list(string) | -- | Security group ARNs (max 5) |
| `--user` | **Yes** | string | -- | User with mount/access permissions (max 104 chars) |
| `--password` | **Yes** | string | -- | User password (max 104 chars) |
| `--subdirectory` | No | string | `/` | Share name and optional subdirectory |
| `--domain` | No | string | None | Windows domain name (max 253 chars) |
| `--tags` | No | list | None | Tags (max 50) |

**Output Schema:**
```json
{
    "LocationArn": "string"
}
```

---

### 4.2 `create-location-fsx-lustre`

Creates a transfer location for an Amazon FSx for Lustre file system.

**Synopsis:**
```bash
aws datasync create-location-fsx-lustre \
    --fsx-filesystem-arn <value> \
    --security-group-arns <value> \
    [--subdirectory <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fsx-filesystem-arn` | **Yes** | string | -- | ARN of the FSx for Lustre file system |
| `--security-group-arns` | **Yes** | list(string) | -- | Security group ARNs (max 5) |
| `--subdirectory` | No | string | `/` | Mount path in the file system |
| `--tags` | No | list | None | Tags (max 50) |

**Output Schema:**
```json
{
    "LocationArn": "string"
}
```

---

### 4.3 `create-location-fsx-ontap`

Creates a transfer location for an Amazon FSx for NetApp ONTAP file system.

**Synopsis:**
```bash
aws datasync create-location-fsx-ontap \
    --protocol <value> \
    --security-group-arns <value> \
    --storage-virtual-machine-arn <value> \
    [--subdirectory <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--protocol` | **Yes** | structure | -- | Data transfer protocol (NFS or SMB) |
| `--security-group-arns` | **Yes** | list(string) | -- | Security group ARNs (max 5) |
| `--storage-virtual-machine-arn` | **Yes** | string | -- | ARN of the storage virtual machine (SVM) |
| `--subdirectory` | No | string | None | Path to file share in SVM (max 255 chars) |
| `--tags` | No | list | None | Tags (max 50) |

**Protocol Structure (NFS shorthand):**
```
NFS={MountOptions={Version=NFS3}}
```

**Protocol Structure (SMB shorthand):**
```
SMB={Domain=string,MountOptions={Version=SMB3},Password=string,User=string}
```

**NFS Mount Version Values:** `AUTOMATIC` | `NFS3` | `NFS4_0` | `NFS4_1`

**SMB Mount Version Values:** `AUTOMATIC` | `SMB2` | `SMB3` | `SMB1` | `SMB2_0`

> **Note:** Only NFS3 is currently supported for FSx for ONTAP. SMB1 is not available for ONTAP locations.

**Output Schema:**
```json
{
    "LocationArn": "string"
}
```

---

### 4.4 `create-location-fsx-open-zfs`

Creates a transfer location for an Amazon FSx for OpenZFS file system.

**Synopsis:**
```bash
aws datasync create-location-fsx-open-zfs \
    --fsx-filesystem-arn <value> \
    --protocol <value> \
    --security-group-arns <value> \
    [--subdirectory <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fsx-filesystem-arn` | **Yes** | string | -- | ARN of the FSx for OpenZFS file system |
| `--protocol` | **Yes** | structure | -- | Data transfer protocol (NFS only) |
| `--security-group-arns` | **Yes** | list(string) | -- | Security group ARNs (max 5) |
| `--subdirectory` | No | string | None | Subdirectory path (must begin with `/fsx`) |
| `--tags` | No | list | None | Tags (max 50) |

**Protocol Structure (NFS shorthand):**
```
NFS={MountOptions={Version=NFS4_1}}
```

**NFS Mount Version Values:** `AUTOMATIC` | `NFS3` | `NFS4_0` | `NFS4_1`

> **Note:** SMB protocol is not supported for FSx for OpenZFS locations.

**Output Schema:**
```json
{
    "LocationArn": "string"
}
```

---

### 4.5 `describe-location-fsx-windows`

Gets details about an FSx for Windows File Server location.

**Synopsis:**
```bash
aws datasync describe-location-fsx-windows \
    --location-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--location-arn` | **Yes** | string | -- | ARN of the FSx for Windows location |

**Output Schema:**
```json
{
    "LocationArn": "string",
    "LocationUri": "string",
    "SecurityGroupArns": ["string"],
    "User": "string",
    "Domain": "string",
    "CreationTime": "timestamp"
}
```

---

### 4.6 `describe-location-fsx-lustre`

Gets details about an FSx for Lustre location.

**Synopsis:**
```bash
aws datasync describe-location-fsx-lustre \
    --location-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--location-arn` | **Yes** | string | -- | ARN of the FSx for Lustre location |

**Output Schema:**
```json
{
    "LocationArn": "string",
    "LocationUri": "string",
    "SecurityGroupArns": ["string"],
    "CreationTime": "timestamp"
}
```

---

### 4.7 `describe-location-fsx-ontap`

Gets details about an FSx for ONTAP location.

**Synopsis:**
```bash
aws datasync describe-location-fsx-ontap \
    --location-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--location-arn` | **Yes** | string | -- | ARN of the FSx for ONTAP location |

**Output Schema:**
```json
{
    "LocationArn": "string",
    "LocationUri": "string",
    "Protocol": {
        "NFS": {
            "MountOptions": {
                "Version": "AUTOMATIC|NFS3|NFS4_0|NFS4_1"
            }
        },
        "SMB": {
            "Domain": "string",
            "MountOptions": {
                "Version": "AUTOMATIC|SMB2|SMB3|SMB1|SMB2_0"
            },
            "User": "string"
        }
    },
    "SecurityGroupArns": ["string"],
    "StorageVirtualMachineArn": "string",
    "FsxFilesystemArn": "string",
    "CreationTime": "timestamp"
}
```

> **Note:** The `Password` field is not returned in describe responses for security reasons.

---

### 4.8 `describe-location-fsx-open-zfs`

Gets details about an FSx for OpenZFS location.

**Synopsis:**
```bash
aws datasync describe-location-fsx-open-zfs \
    --location-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--location-arn` | **Yes** | string | -- | ARN of the FSx for OpenZFS location |

**Output Schema:**
```json
{
    "LocationArn": "string",
    "LocationUri": "string",
    "SecurityGroupArns": ["string"],
    "Protocol": {
        "NFS": {
            "MountOptions": {
                "Version": "AUTOMATIC|NFS3|NFS4_0|NFS4_1"
            }
        }
    },
    "CreationTime": "timestamp"
}
```

---

### 4.9 `update-location-fsx-windows`

Updates an FSx for Windows File Server location configuration.

**Synopsis:**
```bash
aws datasync update-location-fsx-windows \
    --location-arn <value> \
    [--subdirectory <value>] \
    [--domain <value>] \
    [--user <value>] \
    [--password <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--location-arn` | **Yes** | string | -- | ARN of the FSx for Windows location |
| `--subdirectory` | No | string | None | New share name/subdirectory |
| `--domain` | No | string | None | New domain name |
| `--user` | No | string | None | New user |
| `--password` | No | string | None | New password |

**Output:** None on success.

---

### 4.10 `update-location-fsx-lustre`

Updates an FSx for Lustre location configuration.

**Synopsis:**
```bash
aws datasync update-location-fsx-lustre \
    --location-arn <value> \
    [--subdirectory <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--location-arn` | **Yes** | string | -- | ARN of the FSx for Lustre location |
| `--subdirectory` | No | string | None | New mount path |

**Output:** None on success.

---

### 4.11 `update-location-fsx-ontap`

Updates an FSx for ONTAP location configuration.

**Synopsis:**
```bash
aws datasync update-location-fsx-ontap \
    --location-arn <value> \
    [--protocol <value>] \
    [--subdirectory <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--location-arn` | **Yes** | string | -- | ARN of the FSx for ONTAP location |
| `--protocol` | No | structure | None | New protocol config |
| `--subdirectory` | No | string | None | New path in SVM |

**Output:** None on success.

---

### 4.12 `update-location-fsx-open-zfs`

Updates an FSx for OpenZFS location configuration.

**Synopsis:**
```bash
aws datasync update-location-fsx-open-zfs \
    --location-arn <value> \
    [--protocol <value>] \
    [--subdirectory <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--location-arn` | **Yes** | string | -- | ARN of the FSx for OpenZFS location |
| `--protocol` | No | structure | None | New protocol config (NFS only) |
| `--subdirectory` | No | string | None | New subdirectory path |

**Output:** None on success.
