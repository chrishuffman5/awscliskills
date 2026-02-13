# File Shares

### 2.1 `create-nfs-file-share`

Creates an NFS file share on an S3 File Gateway. Maps an S3 bucket (or prefix) to an NFS mount point.

**Synopsis:**
```bash
aws storagegateway create-nfs-file-share \
    --client-token <value> \
    --gateway-arn <value> \
    --role <value> \
    --location-arn <value> \
    [--nfs-file-share-defaults <value>] \
    [--encryption-type <value>] \
    [--kms-key <value>] \
    [--default-storage-class <value>] \
    [--object-acl <value>] \
    [--client-list <value>] \
    [--squash <value>] \
    [--read-only | --no-read-only] \
    [--guess-mime-type-enabled | --no-guess-mime-type-enabled] \
    [--requester-pays | --no-requester-pays] \
    [--tags <value>] \
    [--file-share-name <value>] \
    [--cache-attributes <value>] \
    [--notification-policy <value>] \
    [--vpc-endpoint-dns-name <value>] \
    [--bucket-region <value>] \
    [--audit-destination-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--client-token` | **Yes** | string | -- | Idempotency token (5-100 chars) |
| `--gateway-arn` | **Yes** | string | -- | S3 File Gateway ARN |
| `--role` | **Yes** | string | -- | IAM role ARN for S3 access (20-2048 chars) |
| `--location-arn` | **Yes** | string | -- | S3 bucket ARN, access point ARN, or alias (16-1400 chars) |
| `--nfs-file-share-defaults` | No | structure | None | Default file/directory permissions (FileMode, DirectoryMode, GroupId, OwnerId) |
| `--encryption-type` | No | string | None | Encryption: `SseS3`, `SseKms`, `DsseKms` |
| `--kms-key` | No | string | None | KMS key ARN (required if KMS encryption) |
| `--default-storage-class` | No | string | `S3_STANDARD` | Storage class: `S3_STANDARD`, `S3_INTELLIGENT_TIERING`, `S3_STANDARD_IA`, `S3_ONEZONE_IA` |
| `--object-acl` | No | string | `private` | S3 object ACL |
| `--client-list` | No | list(string) | None | Allowed client CIDRs (1-100 entries) |
| `--squash` | No | string | `RootSquash` | User mapping: `RootSquash`, `NoSquash`, `AllSquash` |
| `--read-only` | No | boolean | false | Read-only file share |
| `--guess-mime-type-enabled` | No | boolean | true | Enable MIME type guessing |
| `--requester-pays` | No | boolean | false | Requester pays for data transfer |
| `--tags` | No | list | None | Up to 50 key-value tags |
| `--file-share-name` | No | string | None | File share name (1-255 chars, required if S3 prefix used) |
| `--cache-attributes` | No | structure | None | Cache stale timeout in seconds (0, 300-2592000) |
| `--notification-policy` | No | string | None | Upload notification policy JSON |
| `--vpc-endpoint-dns-name` | No | string | None | VPC endpoint DNS (required for VPC endpoint) |
| `--bucket-region` | No | string | None | S3 bucket region (required for VPC endpoint) |
| `--audit-destination-arn` | No | string | None | Audit log destination ARN |

**Output Schema:**
```json
{
    "FileShareARN": "string"
}
```

---

### 2.2 `update-nfs-file-share`

Updates an existing NFS file share configuration.

**Synopsis:**
```bash
aws storagegateway update-nfs-file-share \
    --file-share-arn <value> \
    [--nfs-file-share-defaults <value>] \
    [--encryption-type <value>] \
    [--kms-key <value>] \
    [--default-storage-class <value>] \
    [--object-acl <value>] \
    [--client-list <value>] \
    [--squash <value>] \
    [--read-only | --no-read-only] \
    [--guess-mime-type-enabled | --no-guess-mime-type-enabled] \
    [--requester-pays | --no-requester-pays] \
    [--file-share-name <value>] \
    [--cache-attributes <value>] \
    [--notification-policy <value>] \
    [--audit-destination-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-share-arn` | **Yes** | string | -- | File share ARN (50-500 chars) |
| All other parameters | No | -- | -- | Same as `create-nfs-file-share` (updates only specified fields) |

**Output Schema:**
```json
{
    "FileShareARN": "string"
}
```

---

### 2.3 `describe-nfs-file-shares`

Returns a description of NFS file shares.

**Synopsis:**
```bash
aws storagegateway describe-nfs-file-shares \
    --file-share-arn-list <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-share-arn-list` | **Yes** | list(string) | -- | List of file share ARNs (1-10 items) |

**Output Schema:**
```json
{
    "NFSFileShareInfoList": [
        {
            "NFSFileShareDefaults": {
                "FileMode": "string",
                "DirectoryMode": "string",
                "GroupId": "long",
                "OwnerId": "long"
            },
            "FileShareARN": "string",
            "FileShareId": "string",
            "FileShareStatus": "CREATING|UPDATING|AVAILABLE|DELETING|FORCE_DELETING",
            "GatewayARN": "string",
            "EncryptionType": "SseS3|SseKms|DsseKms",
            "KMSKey": "string",
            "Path": "string",
            "Role": "string",
            "LocationARN": "string",
            "DefaultStorageClass": "string",
            "ObjectACL": "string",
            "ClientList": ["string"],
            "Squash": "string",
            "ReadOnly": "boolean",
            "GuessMIMETypeEnabled": "boolean",
            "RequesterPays": "boolean",
            "Tags": [{"Key": "string", "Value": "string"}],
            "FileShareName": "string",
            "CacheAttributes": {"CacheStaleTimeoutInSeconds": "integer"},
            "NotificationPolicy": "string",
            "VPCEndpointDNSName": "string",
            "BucketRegion": "string",
            "AuditDestinationARN": "string"
        }
    ]
}
```

---

### 2.4 `create-smb-file-share`

Creates an SMB file share on an S3 File Gateway. Supports Active Directory or guest access authentication.

**Synopsis:**
```bash
aws storagegateway create-smb-file-share \
    --client-token <value> \
    --gateway-arn <value> \
    --role <value> \
    --location-arn <value> \
    [--encryption-type <value>] \
    [--kms-key <value>] \
    [--default-storage-class <value>] \
    [--object-acl <value>] \
    [--read-only | --no-read-only] \
    [--guess-mime-type-enabled | --no-guess-mime-type-enabled] \
    [--requester-pays | --no-requester-pays] \
    [--smbacl-enabled | --no-smbacl-enabled] \
    [--access-based-enumeration | --no-access-based-enumeration] \
    [--admin-user-list <value>] \
    [--valid-user-list <value>] \
    [--invalid-user-list <value>] \
    [--audit-destination-arn <value>] \
    [--authentication <value>] \
    [--case-sensitivity <value>] \
    [--tags <value>] \
    [--file-share-name <value>] \
    [--cache-attributes <value>] \
    [--notification-policy <value>] \
    [--vpc-endpoint-dns-name <value>] \
    [--bucket-region <value>] \
    [--oplocks-enabled | --no-oplocks-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--client-token` | **Yes** | string | -- | Idempotency token (5-100 chars) |
| `--gateway-arn` | **Yes** | string | -- | S3 File Gateway ARN |
| `--role` | **Yes** | string | -- | IAM role ARN for S3 access |
| `--location-arn` | **Yes** | string | -- | S3 bucket ARN or access point |
| `--encryption-type` | No | string | None | Encryption: `SseS3`, `SseKms`, `DsseKms` |
| `--kms-key` | No | string | None | KMS key ARN |
| `--default-storage-class` | No | string | `S3_STANDARD` | S3 storage class |
| `--object-acl` | No | string | `private` | S3 object ACL |
| `--read-only` | No | boolean | false | Read-only share |
| `--guess-mime-type-enabled` | No | boolean | true | Enable MIME type guessing |
| `--requester-pays` | No | boolean | false | Requester pays |
| `--smbacl-enabled` | No | boolean | None | Enable Windows ACLs |
| `--access-based-enumeration` | No | boolean | None | Only show accessible files |
| `--admin-user-list` | No | list(string) | None | AD admin users/groups (0-100 items) |
| `--valid-user-list` | No | list(string) | None | AD allowed users/groups |
| `--invalid-user-list` | No | list(string) | None | AD denied users/groups |
| `--audit-destination-arn` | No | string | None | Audit log destination ARN |
| `--authentication` | No | string | `ActiveDirectory` | Auth method: `ActiveDirectory`, `GuestAccess` |
| `--case-sensitivity` | No | string | `ClientSpecified` | Case: `ClientSpecified`, `CaseSensitive` |
| `--tags` | No | list | None | Up to 50 tags |
| `--file-share-name` | No | string | None | Share name (1-255 chars) |
| `--cache-attributes` | No | structure | None | Cache stale timeout |
| `--notification-policy` | No | string | None | Upload notification JSON |
| `--vpc-endpoint-dns-name` | No | string | None | VPC endpoint DNS |
| `--bucket-region` | No | string | None | S3 bucket region |
| `--oplocks-enabled` | No | boolean | None | Enable opportunistic locking |

**Output Schema:**
```json
{
    "FileShareARN": "string"
}
```

---

### 2.5 `update-smb-file-share`

Updates an existing SMB file share configuration.

**Synopsis:**
```bash
aws storagegateway update-smb-file-share \
    --file-share-arn <value> \
    [... same optional parameters as create-smb-file-share ...] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-share-arn` | **Yes** | string | -- | File share ARN |
| All other parameters | No | -- | -- | Same as `create-smb-file-share` |

**Output Schema:**
```json
{
    "FileShareARN": "string"
}
```

---

### 2.6 `describe-smb-file-shares`

Returns a description of SMB file shares.

**Synopsis:**
```bash
aws storagegateway describe-smb-file-shares \
    --file-share-arn-list <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-share-arn-list` | **Yes** | list(string) | -- | List of file share ARNs (1-10 items) |

**Output Schema:**
```json
{
    "SMBFileShareInfoList": [
        {
            "FileShareARN": "string",
            "FileShareId": "string",
            "FileShareStatus": "CREATING|UPDATING|AVAILABLE|DELETING|FORCE_DELETING",
            "GatewayARN": "string",
            "EncryptionType": "string",
            "KMSKey": "string",
            "Path": "string",
            "Role": "string",
            "LocationARN": "string",
            "DefaultStorageClass": "string",
            "ObjectACL": "string",
            "ReadOnly": "boolean",
            "GuessMIMETypeEnabled": "boolean",
            "RequesterPays": "boolean",
            "SMBACLEnabled": "boolean",
            "AccessBasedEnumeration": "boolean",
            "AdminUserList": ["string"],
            "ValidUserList": ["string"],
            "InvalidUserList": ["string"],
            "AuditDestinationARN": "string",
            "Authentication": "string",
            "CaseSensitivity": "string",
            "Tags": [{"Key": "string", "Value": "string"}],
            "FileShareName": "string",
            "CacheAttributes": {"CacheStaleTimeoutInSeconds": "integer"},
            "NotificationPolicy": "string",
            "VPCEndpointDNSName": "string",
            "BucketRegion": "string",
            "OplocksEnabled": "boolean"
        }
    ]
}
```

---

### 2.7 `delete-file-share`

Deletes a file share from an S3 File Gateway.

**Synopsis:**
```bash
aws storagegateway delete-file-share \
    --file-share-arn <value> \
    [--force-delete | --no-force-delete] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-share-arn` | **Yes** | string | -- | File share ARN |
| `--force-delete` | No | boolean | false | Force delete even if data is not fully uploaded |

**Output Schema:**
```json
{
    "FileShareARN": "string"
}
```

---

### 2.8 `list-file-shares`

Lists file shares on a gateway. **Paginated operation.**

**Synopsis:**
```bash
aws storagegateway list-file-shares \
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
| `--gateway-arn` | No | string | None | Gateway ARN to filter results |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Marker": "string",
    "NextMarker": "string",
    "FileShareInfoList": [
        {
            "FileShareType": "NFS|SMB",
            "FileShareARN": "string",
            "FileShareId": "string",
            "FileShareStatus": "string",
            "GatewayARN": "string"
        }
    ]
}
```

---

### 2.9 `refresh-cache`

Refreshes the file share cache from the S3 bucket. Only supported for S3 File Gateways.

**Synopsis:**
```bash
aws storagegateway refresh-cache \
    --file-share-arn <value> \
    [--folder-list <value>] \
    [--recursive | --no-recursive] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-share-arn` | **Yes** | string | -- | File share ARN |
| `--folder-list` | No | list(string) | None | Specific folders to refresh (1-50 items) |
| `--recursive` | No | boolean | None | Recursively refresh subfolders |

**Output Schema:**
```json
{
    "FileShareARN": "string",
    "NotificationId": "string"
}
```

---

### 2.10 `notify-when-uploaded`

Sends a notification when all files written to the NFS file share have been uploaded to S3.

**Synopsis:**
```bash
aws storagegateway notify-when-uploaded \
    --file-share-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-share-arn` | **Yes** | string | -- | File share ARN |

**Output Schema:**
```json
{
    "FileShareARN": "string",
    "NotificationId": "string"
}
```

---

### 2.11 `evict-files-failing-upload`

Evicts files that are failing to upload to Amazon S3 from the gateway cache.

**Synopsis:**
```bash
aws storagegateway evict-files-failing-upload \
    --file-share-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-share-arn` | **Yes** | string | -- | File share ARN |

**Output Schema:**
```json
{
    "NotificationId": "string"
}
```
