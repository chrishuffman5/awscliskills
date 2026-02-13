# Mount Targets

### 2.1 `create-mount-target`

Creates a mount target for a file system in a subnet. You can only create one mount target per Availability Zone. For Regional file systems you need one mount target per AZ; for One Zone file systems you need one in the file system's AZ.

**Synopsis:**
```bash
aws efs create-mount-target \
    --file-system-id <value> \
    --subnet-id <value> \
    [--ip-address <value>] \
    [--security-groups <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-id` | **Yes** | string | -- | ID of the file system |
| `--subnet-id` | **Yes** | string | -- | Subnet to create the mount target in |
| `--ip-address` | No | string | auto-assigned | Specific IPv4 address within the subnet's CIDR range |
| `--security-groups` | No | list(string) | VPC default SG | Up to 5 security group IDs |

**Output Schema:**
```json
{
    "OwnerId": "string",
    "MountTargetId": "string",
    "FileSystemId": "string",
    "SubnetId": "string",
    "LifeCycleState": "creating|available|updating|deleting|deleted|error",
    "IpAddress": "string",
    "NetworkInterfaceId": "string",
    "AvailabilityZoneId": "string",
    "AvailabilityZoneName": "string",
    "VpcId": "string"
}
```

---

### 2.2 `delete-mount-target`

Deletes the specified mount target. This also deletes the associated network interface.

**Synopsis:**
```bash
aws efs delete-mount-target \
    --mount-target-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--mount-target-id` | **Yes** | string | -- | ID of the mount target to delete |

**Output:** None on success.

---

### 2.3 `describe-mount-targets`

Returns the descriptions of all mount targets, or specific mount targets, for a file system. At least one of file-system-id, mount-target-id, or access-point-id must be provided. **Paginated operation.**

**Synopsis:**
```bash
aws efs describe-mount-targets \
    [--max-items <value>] \
    [--file-system-id <value>] \
    [--mount-target-id <value>] \
    [--access-point-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-id` | No | string | -- | File system ID to describe mount targets for |
| `--mount-target-id` | No | string | -- | Specific mount target ID to describe |
| `--access-point-id` | No | string | -- | Access point ID to describe mount targets for |
| `--max-items` | No | integer | None | Total items to return |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |

**Output Schema:**
```json
{
    "MountTargets": [
        {
            "OwnerId": "string",
            "MountTargetId": "string",
            "FileSystemId": "string",
            "SubnetId": "string",
            "LifeCycleState": "creating|available|updating|deleting|deleted|error",
            "IpAddress": "string",
            "NetworkInterfaceId": "string",
            "AvailabilityZoneId": "string",
            "AvailabilityZoneName": "string",
            "VpcId": "string"
        }
    ],
    "NextMarker": "string"
}
```

---

### 2.4 `describe-mount-target-security-groups`

Returns the security groups currently in effect for a mount target.

**Synopsis:**
```bash
aws efs describe-mount-target-security-groups \
    --mount-target-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--mount-target-id` | **Yes** | string | -- | ID of the mount target |

**Output Schema:**
```json
{
    "SecurityGroups": ["string"]
}
```

---

### 2.5 `modify-mount-target-security-groups`

Modifies the set of security groups in effect for a mount target. Replaces the entire set.

**Synopsis:**
```bash
aws efs modify-mount-target-security-groups \
    --mount-target-id <value> \
    [--security-groups <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--mount-target-id` | **Yes** | string | -- | ID of the mount target |
| `--security-groups` | No | list(string) | VPC default SG | Up to 5 security group IDs. Omit to reset to VPC default |

**Output:** None on success.
