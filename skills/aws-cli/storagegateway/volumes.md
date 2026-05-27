# Volumes

### 4.1 `create-cached-iscsi-volume`

Creates a cached iSCSI volume on a Volume Gateway. Data is stored in S3 with frequently accessed data cached locally.

**Synopsis:**
```bash
aws storagegateway create-cached-iscsi-volume \
    --gateway-arn <value> \
    --volume-size-in-bytes <value> \
    --target-name <value> \
    --network-interface-id <value> \
    --client-token <value> \
    [--snapshot-id <value>] \
    [--source-volume-arn <value>] \
    [--kms-encrypted | --no-kms-encrypted] \
    [--kms-key <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN (50-500 chars) |
| `--volume-size-in-bytes` | **Yes** | long | -- | Volume size in bytes |
| `--target-name` | **Yes** | string | -- | iSCSI target name (1-200 chars, pattern: `^[-\.;a-z0-9]+$`) |
| `--network-interface-id` | **Yes** | string | -- | Gateway network interface IP |
| `--client-token` | **Yes** | string | -- | Idempotency token (5-100 chars) |
| `--snapshot-id` | No | string | None | EBS snapshot ID to restore from |
| `--source-volume-arn` | No | string | None | Source volume ARN to clone from |
| `--kms-encrypted` | No | boolean | false | Enable KMS encryption |
| `--kms-key` | No | string | None | KMS key ARN (required if KMS encrypted) |
| `--tags` | No | list | None | Up to 50 key-value tags |

**Output Schema:**
```json
{
    "VolumeARN": "string",
    "TargetARN": "string"
}
```

---

### 4.2 `create-stored-iscsi-volume`

Creates a stored iSCSI volume on a Volume Gateway. All data is stored on the local gateway with asynchronous backup to S3.

**Synopsis:**
```bash
aws storagegateway create-stored-iscsi-volume \
    --gateway-arn <value> \
    --disk-id <value> \
    --preserve-existing-data | --no-preserve-existing-data \
    --target-name <value> \
    --network-interface-id <value> \
    [--snapshot-id <value>] \
    [--kms-encrypted | --no-kms-encrypted] \
    [--kms-key <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |
| `--disk-id` | **Yes** | string | -- | Local disk ID (1-300 chars) |
| `--preserve-existing-data` | **Yes** | boolean | -- | Preserve existing data on the disk |
| `--target-name` | **Yes** | string | -- | iSCSI target name (1-200 chars) |
| `--network-interface-id` | **Yes** | string | -- | Gateway network interface IP |
| `--snapshot-id` | No | string | None | EBS snapshot ID |
| `--kms-encrypted` | No | boolean | false | Enable KMS encryption |
| `--kms-key` | No | string | None | KMS key ARN |
| `--tags` | No | list | None | Up to 50 tags |

**Output Schema:**
```json
{
    "VolumeARN": "string",
    "VolumeSizeInBytes": "long",
    "TargetARN": "string"
}
```

---

### 4.3 `describe-cached-iscsi-volumes`

Returns a description of cached iSCSI volumes on a gateway.

**Synopsis:**
```bash
aws storagegateway describe-cached-iscsi-volumes \
    --volume-arns <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--volume-arns` | **Yes** | list(string) | -- | List of volume ARNs |

**Output Schema:**
```json
{
    "CachediSCSIVolumes": [
        {
            "VolumeARN": "string",
            "VolumeId": "string",
            "VolumeType": "string",
            "VolumeStatus": "string",
            "VolumeAttachmentStatus": "string",
            "VolumeSizeInBytes": "long",
            "VolumeProgress": "double",
            "SourceSnapshotId": "string",
            "VolumeiSCSIAttributes": {
                "TargetARN": "string",
                "NetworkInterfaceId": "string",
                "NetworkInterfacePort": "integer",
                "LunNumber": "integer",
                "ChapEnabled": "boolean"
            },
            "CreatedDate": "timestamp",
            "VolumeUsedInBytes": "long",
            "KMSKey": "string",
            "TargetName": "string"
        }
    ]
}
```

---

### 4.4 `describe-stored-iscsi-volumes`

Returns a description of stored iSCSI volumes on a gateway.

**Synopsis:**
```bash
aws storagegateway describe-stored-iscsi-volumes \
    --volume-arns <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--volume-arns` | **Yes** | list(string) | -- | List of volume ARNs |

**Output Schema:**
```json
{
    "StorediSCSIVolumes": [
        {
            "VolumeARN": "string",
            "VolumeId": "string",
            "VolumeType": "string",
            "VolumeStatus": "string",
            "VolumeAttachmentStatus": "string",
            "VolumeSizeInBytes": "long",
            "VolumeProgress": "double",
            "VolumeDiskId": "string",
            "SourceSnapshotId": "string",
            "PreservedExistingData": "boolean",
            "VolumeiSCSIAttributes": {
                "TargetARN": "string",
                "NetworkInterfaceId": "string",
                "NetworkInterfacePort": "integer",
                "LunNumber": "integer",
                "ChapEnabled": "boolean"
            },
            "CreatedDate": "timestamp",
            "VolumeUsedInBytes": "long",
            "KMSKey": "string",
            "TargetName": "string"
        }
    ]
}
```

---

### 4.5 `attach-volume`

Attaches an existing volume to a gateway, making it available as an iSCSI target.

**Synopsis:**
```bash
aws storagegateway attach-volume \
    --gateway-arn <value> \
    --volume-arn <value> \
    --network-interface-id <value> \
    [--target-name <value>] \
    [--disk-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |
| `--volume-arn` | **Yes** | string | -- | Volume ARN |
| `--network-interface-id` | **Yes** | string | -- | Network interface IP |
| `--target-name` | No | string | None | iSCSI target name |
| `--disk-id` | No | string | None | Disk ID (required for stored volumes) |

**Output Schema:**
```json
{
    "VolumeARN": "string",
    "TargetARN": "string"
}
```

---

### 4.6 `detach-volume`

Detaches a volume from a gateway. The volume becomes detached and can be attached to another gateway.

**Synopsis:**
```bash
aws storagegateway detach-volume \
    --volume-arn <value> \
    [--force-detach | --no-force-detach] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--volume-arn` | **Yes** | string | -- | Volume ARN |
| `--force-detach` | No | boolean | false | Force detach even if in use |

**Output Schema:**
```json
{
    "VolumeARN": "string"
}
```

---

### 4.7 `delete-volume`

Deletes a volume and the data stored on it.

**Synopsis:**
```bash
aws storagegateway delete-volume \
    --volume-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--volume-arn` | **Yes** | string | -- | Volume ARN |

**Output Schema:**
```json
{
    "VolumeARN": "string"
}
```

---

### 4.8 `list-volumes`

Lists volumes on a gateway. **Paginated operation.**

**Synopsis:**
```bash
aws storagegateway list-volumes \
    [--gateway-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | No | string | None | Gateway ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "GatewayARN": "string",
    "Marker": "string",
    "VolumeInfos": [
        {
            "VolumeARN": "string",
            "VolumeId": "string",
            "GatewayARN": "string",
            "GatewayId": "string",
            "VolumeType": "string",
            "VolumeSizeInBytes": "long",
            "VolumeAttachmentStatus": "string"
        }
    ]
}
```

---

### 4.9 `create-snapshot`

Creates a snapshot of a volume. Stored as an EBS snapshot in S3.

**Synopsis:**
```bash
aws storagegateway create-snapshot \
    --volume-arn <value> \
    --snapshot-description <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--volume-arn` | **Yes** | string | -- | Volume ARN |
| `--snapshot-description` | **Yes** | string | -- | Snapshot description (1-255 chars) |
| `--tags` | No | list | None | Up to 50 tags |

**Output Schema:**
```json
{
    "VolumeARN": "string",
    "SnapshotId": "string"
}
```

---

### 4.10 `update-snapshot-schedule`

Updates a volume snapshot schedule.

**Synopsis:**
```bash
aws storagegateway update-snapshot-schedule \
    --volume-arn <value> \
    --start-at <value> \
    --recurrence-in-hours <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--volume-arn` | **Yes** | string | -- | Volume ARN |
| `--start-at` | **Yes** | integer | -- | Hour of day (0-23) |
| `--recurrence-in-hours` | **Yes** | integer | -- | Frequency in hours (1, 2, 4, 8, 12, 24) |
| `--description` | No | string | None | Snapshot description |
| `--tags` | No | list | None | Up to 50 tags |

**Output Schema:**
```json
{
    "VolumeARN": "string"
}
```

---

### 4.11 `add-upload-buffer`

Adds upload buffer capacity to a gateway.

**Synopsis:**
```bash
aws storagegateway add-upload-buffer \
    --gateway-arn <value> \
    --disk-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |
| `--disk-ids` | **Yes** | list(string) | -- | List of local disk IDs |

**Output Schema:**
```json
{
    "GatewayARN": "string"
}
```

---

### 4.12 `describe-upload-buffer`

Returns information about the upload buffer of a gateway.

**Synopsis:**
```bash
aws storagegateway describe-upload-buffer \
    --gateway-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |

**Output Schema:**
```json
{
    "GatewayARN": "string",
    "DiskIds": ["string"],
    "UploadBufferUsedInBytes": "long",
    "UploadBufferAllocatedInBytes": "long"
}
```
