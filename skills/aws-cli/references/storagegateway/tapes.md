# Tapes

### 5.1 `create-tapes`

Creates one or more virtual tapes on a tape gateway. Cache storage must be allocated before creating tapes.

**Synopsis:**
```bash
aws storagegateway create-tapes \
    --gateway-arn <value> \
    --tape-size-in-bytes <value> \
    --client-token <value> \
    --num-tapes-to-create <value> \
    --tape-barcode-prefix <value> \
    [--kms-encrypted | --no-kms-encrypted] \
    [--kms-key <value>] \
    [--pool-id <value>] \
    [--worm | --no-worm] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Tape gateway ARN (50-500 chars) |
| `--tape-size-in-bytes` | **Yes** | long | -- | Tape size (must be gigabyte-aligned) |
| `--client-token` | **Yes** | string | -- | Idempotency token (5-100 chars) |
| `--num-tapes-to-create` | **Yes** | integer | -- | Number of tapes (1-10) |
| `--tape-barcode-prefix` | **Yes** | string | -- | Barcode prefix (1-4 uppercase letters A-Z) |
| `--kms-encrypted` | No | boolean | false | Enable KMS encryption |
| `--kms-key` | No | string | None | KMS key ARN |
| `--pool-id` | No | string | None | Tape pool ID for archival storage class |
| `--worm` | No | boolean | None | Write-once-read-many tape |
| `--tags` | No | list | None | Up to 50 tags |

**Output Schema:**
```json
{
    "TapeARNs": ["string"]
}
```

---

### 5.2 `create-tape-with-barcode`

Creates a single virtual tape with a specific barcode.

**Synopsis:**
```bash
aws storagegateway create-tape-with-barcode \
    --gateway-arn <value> \
    --tape-size-in-bytes <value> \
    --tape-barcode <value> \
    [--kms-encrypted | --no-kms-encrypted] \
    [--kms-key <value>] \
    [--pool-id <value>] \
    [--worm | --no-worm] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Tape gateway ARN |
| `--tape-size-in-bytes` | **Yes** | long | -- | Tape size (gigabyte-aligned) |
| `--tape-barcode` | **Yes** | string | -- | Unique barcode (5-16 chars, A-Z and 0-9) |
| `--kms-encrypted` | No | boolean | false | Enable KMS encryption |
| `--kms-key` | No | string | None | KMS key ARN |
| `--pool-id` | No | string | None | Tape pool ID |
| `--worm` | No | boolean | None | WORM tape |
| `--tags` | No | list | None | Up to 50 tags |

**Output Schema:**
```json
{
    "TapeARN": "string"
}
```

---

### 5.3 `describe-tapes`

Returns a description of virtual tapes on a gateway. **Paginated operation.**

**Synopsis:**
```bash
aws storagegateway describe-tapes \
    --gateway-arn <value> \
    [--tape-arns <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |
| `--tape-arns` | No | list(string) | None | Specific tape ARNs to describe |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Tapes": [
        {
            "TapeARN": "string",
            "TapeBarcode": "string",
            "TapeCreatedDate": "timestamp",
            "TapeSizeInBytes": "long",
            "TapeStatus": "string",
            "VTLDevice": "string",
            "Progress": "double",
            "TapeUsedInBytes": "long",
            "KMSKey": "string",
            "PoolId": "string",
            "Worm": "boolean",
            "RetentionStartDate": "timestamp",
            "PoolEntryDate": "timestamp"
        }
    ],
    "Marker": "string"
}
```

---

### 5.4 `list-tapes`

Lists virtual tapes across all gateways. **Paginated operation.**

**Synopsis:**
```bash
aws storagegateway list-tapes \
    [--tape-arns <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tape-arns` | No | list(string) | None | Filter by specific tape ARNs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "TapeInfos": [
        {
            "TapeARN": "string",
            "TapeBarcode": "string",
            "TapeSizeInBytes": "long",
            "TapeStatus": "string",
            "GatewayARN": "string",
            "PoolId": "string",
            "RetentionStartDate": "timestamp",
            "PoolEntryDate": "timestamp"
        }
    ],
    "Marker": "string"
}
```

---

### 5.5 `delete-tape`

Deletes a virtual tape from a tape gateway.

**Synopsis:**
```bash
aws storagegateway delete-tape \
    --gateway-arn <value> \
    --tape-arn <value> \
    [--bypass-governance-retention | --no-bypass-governance-retention] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |
| `--tape-arn` | **Yes** | string | -- | Tape ARN |
| `--bypass-governance-retention` | No | boolean | false | Bypass tape retention lock governance mode |

**Output Schema:**
```json
{
    "TapeARN": "string"
}
```

---

### 5.6 `delete-tape-archive`

Deletes a virtual tape from the archive (S3 Glacier or S3 Glacier Deep Archive).

**Synopsis:**
```bash
aws storagegateway delete-tape-archive \
    --tape-arn <value> \
    [--bypass-governance-retention | --no-bypass-governance-retention] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tape-arn` | **Yes** | string | -- | Tape ARN |
| `--bypass-governance-retention` | No | boolean | false | Bypass retention lock governance |

**Output Schema:**
```json
{
    "TapeARN": "string"
}
```

---

### 5.7 `describe-tape-archives`

Returns information about virtual tapes in the archive. **Paginated operation.**

**Synopsis:**
```bash
aws storagegateway describe-tape-archives \
    [--tape-arns <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tape-arns` | No | list(string) | None | Specific tape ARNs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "TapeArchives": [
        {
            "TapeARN": "string",
            "TapeBarcode": "string",
            "TapeCreatedDate": "timestamp",
            "TapeSizeInBytes": "long",
            "CompletionTime": "timestamp",
            "RetrievedTo": "string",
            "TapeStatus": "string",
            "TapeUsedInBytes": "long",
            "KMSKey": "string",
            "PoolId": "string",
            "Worm": "boolean",
            "RetentionStartDate": "timestamp",
            "PoolEntryDate": "timestamp"
        }
    ],
    "Marker": "string"
}
```

---

### 5.8 `retrieve-tape-archive`

Retrieves an archived virtual tape from S3 Glacier/Deep Archive to a tape gateway.

**Synopsis:**
```bash
aws storagegateway retrieve-tape-archive \
    --tape-arn <value> \
    --gateway-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tape-arn` | **Yes** | string | -- | Tape ARN |
| `--gateway-arn` | **Yes** | string | -- | Target gateway ARN |

**Output Schema:**
```json
{
    "TapeARN": "string"
}
```

---

### 5.9 `retrieve-tape-recovery-point`

Retrieves a virtual tape from a recovery point.

**Synopsis:**
```bash
aws storagegateway retrieve-tape-recovery-point \
    --tape-arn <value> \
    --gateway-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tape-arn` | **Yes** | string | -- | Tape ARN |
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |

**Output Schema:**
```json
{
    "TapeARN": "string"
}
```

---

### 5.10 `assign-tape-pool`

Assigns a tape to a pool. Tapes assigned to a pool are archived to the S3 storage class associated with that pool.

**Synopsis:**
```bash
aws storagegateway assign-tape-pool \
    --tape-arn <value> \
    --pool-id <value> \
    [--bypass-governance-retention | --no-bypass-governance-retention] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tape-arn` | **Yes** | string | -- | Tape ARN |
| `--pool-id` | **Yes** | string | -- | Pool ID (1-100 chars) |
| `--bypass-governance-retention` | No | boolean | false | Bypass retention lock governance |

**Output Schema:**
```json
{
    "TapeARN": "string"
}
```

---

### 5.11 `create-tape-pool`

Creates a custom tape pool for archiving virtual tapes.

**Synopsis:**
```bash
aws storagegateway create-tape-pool \
    --pool-name <value> \
    --storage-class <value> \
    [--retention-lock-type <value>] \
    [--retention-lock-time-in-days <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pool-name` | **Yes** | string | -- | Pool name (1-100 chars) |
| `--storage-class` | **Yes** | string | -- | Archive class: `DEEP_ARCHIVE`, `GLACIER` |
| `--retention-lock-type` | No | string | None | Lock type: `COMPLIANCE`, `GOVERNANCE`, `NONE` |
| `--retention-lock-time-in-days` | No | integer | None | Retention days (0-36500) |
| `--tags` | No | list | None | Up to 50 tags |

**Output Schema:**
```json
{
    "PoolARN": "string"
}
```

---

### 5.12 `list-tape-pools`

Lists custom tape pools. **Paginated operation.**

**Synopsis:**
```bash
aws storagegateway list-tape-pools \
    [--pool-arns <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pool-arns` | No | list(string) | None | Filter by pool ARNs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "PoolInfos": [
        {
            "PoolARN": "string",
            "PoolName": "string",
            "StorageClass": "DEEP_ARCHIVE|GLACIER",
            "RetentionLockType": "COMPLIANCE|GOVERNANCE|NONE",
            "RetentionLockTimeInDays": "integer",
            "PoolStatus": "ACTIVE|DELETED"
        }
    ],
    "Marker": "string"
}
```

---

### 5.13 `describe-vtl-devices`

Returns a description of VTL (Virtual Tape Library) devices on a tape gateway. **Paginated operation.**

**Synopsis:**
```bash
aws storagegateway describe-vtl-devices \
    --gateway-arn <value> \
    [--vtl-device-arns <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |
| `--vtl-device-arns` | No | list(string) | None | Specific VTL device ARNs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "GatewayARN": "string",
    "VTLDevices": [
        {
            "VTLDeviceARN": "string",
            "VTLDeviceType": "string",
            "VTLDeviceVendor": "string",
            "VTLDeviceProductIdentifier": "string",
            "DeviceiSCSIAttributes": {
                "TargetARN": "string",
                "NetworkInterfaceId": "string",
                "NetworkInterfacePort": "integer",
                "ChapEnabled": "boolean"
            }
        }
    ],
    "Marker": "string"
}
```
