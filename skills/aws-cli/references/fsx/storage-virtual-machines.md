# Storage Virtual Machines

Storage Virtual Machines (SVMs) are used exclusively with FSx for NetApp ONTAP. Each SVM is an isolated file server with its own endpoints, Active Directory configuration, and volumes.

### 5.1 `create-storage-virtual-machine`

Creates an ONTAP SVM.

**Synopsis:**
```bash
aws fsx create-storage-virtual-machine \
    --file-system-id <value> \
    --name <value> \
    [--active-directory-configuration <value>] \
    [--svm-admin-password <value>] \
    [--root-volume-security-style <value>] \
    [--tags <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-id` | **Yes** | string | -- | ONTAP file system ID |
| `--name` | **Yes** | string | -- | SVM name (1-47 chars) |
| `--active-directory-configuration` | No | structure | None | AD configuration for SMB |
| `--svm-admin-password` | No | string | None | Admin password (8-50 chars) |
| `--root-volume-security-style` | No | string | None | `UNIX`, `NTFS`, or `MIXED` |
| `--tags` | No | list | None | Tags (max 50) |

**Active Directory Configuration:**
```json
{
    "NetBiosName": "string",
    "SelfManagedActiveDirectoryConfiguration": {
        "DomainName": "string (required)",
        "OrganizationalUnitDistinguishedName": "string",
        "FileSystemAdministratorsGroup": "string",
        "UserName": "string (required)",
        "Password": "string (required)",
        "DnsIps": ["string (required, 1-3)"],
        "DomainJoinServiceAccountSecret": "string"
    }
}
```

**Output Schema:**
```json
{
    "StorageVirtualMachine": {
        "CreationTime": "timestamp",
        "FileSystemId": "string",
        "Lifecycle": "CREATED|CREATING|DELETING|FAILED|MISCONFIGURED|PENDING",
        "Name": "string",
        "StorageVirtualMachineId": "string",
        "ResourceARN": "string",
        "UUID": "string",
        "Subtype": "DEFAULT|DP_DESTINATION|SYNC_DESTINATION|SYNC_SOURCE",
        "RootVolumeSecurityStyle": "UNIX|NTFS|MIXED",
        "ActiveDirectoryConfiguration": {},
        "Endpoints": {
            "Iscsi": {
                "DNSName": "string",
                "IpAddresses": ["string"]
            },
            "Management": {
                "DNSName": "string",
                "IpAddresses": ["string"]
            },
            "Nfs": {
                "DNSName": "string",
                "IpAddresses": ["string"]
            },
            "Smb": {
                "DNSName": "string",
                "IpAddresses": ["string"]
            }
        },
        "Tags": []
    }
}
```

---

### 5.2 `describe-storage-virtual-machines`

Returns descriptions of SVMs. **Paginated operation.**

**Synopsis:**
```bash
aws fsx describe-storage-virtual-machines \
    [--storage-virtual-machine-ids <value>] \
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
| `--storage-virtual-machine-ids` | No | list | None | SVM IDs (max 50) |
| `--filters` | No | list | None | Filters: `file-system-id` |

**Output Schema:**
```json
{
    "StorageVirtualMachines": [
        {
            "StorageVirtualMachineId": "string",
            "Name": "string",
            "FileSystemId": "string",
            "Lifecycle": "string",
            "Subtype": "string",
            "Endpoints": {},
            "ActiveDirectoryConfiguration": {},
            "ResourceARN": "string",
            "Tags": []
        }
    ],
    "NextToken": "string"
}
```

---

### 5.3 `update-storage-virtual-machine`

Updates an SVM's configuration (AD, password).

**Synopsis:**
```bash
aws fsx update-storage-virtual-machine \
    --storage-virtual-machine-id <value> \
    [--active-directory-configuration <value>] \
    [--svm-admin-password <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--storage-virtual-machine-id` | **Yes** | string | -- | SVM ID |
| `--active-directory-configuration` | No | structure | None | AD config updates |
| `--svm-admin-password` | No | string | None | New admin password |

**Output:** Same as `create-storage-virtual-machine`

---

### 5.4 `delete-storage-virtual-machine`

Deletes an SVM. All volumes on the SVM must be deleted first.

**Synopsis:**
```bash
aws fsx delete-storage-virtual-machine \
    --storage-virtual-machine-id <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--storage-virtual-machine-id` | **Yes** | string | -- | SVM ID |

**Output Schema:**
```json
{
    "StorageVirtualMachineId": "string",
    "Lifecycle": "DELETING"
}
```
