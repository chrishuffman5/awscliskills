# Multipart Uploads

### 5.1 `create-multipart-upload`

Initiates a multipart upload and returns an upload ID.

**Synopsis:**
```bash
aws s3api create-multipart-upload \
    --bucket <value> \
    --key <value> \
    [--acl <value>] \
    [--cache-control <value>] \
    [--content-disposition <value>] \
    [--content-encoding <value>] \
    [--content-language <value>] \
    [--content-type <value>] \
    [--expires <value>] \
    [--metadata <value>] \
    [--server-side-encryption <value>] \
    [--storage-class <value>] \
    [--tagging <value>] \
    [--ssekms-key-id <value>] \
    [--bucket-key-enabled | --no-bucket-key-enabled] \
    [--checksum-algorithm <value>] \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--key` | **Yes** | string | -- | Object key |
| `--acl` | No | string | None | `private`, `public-read`, `public-read-write`, `authenticated-read`, `aws-exec-read`, `bucket-owner-read`, `bucket-owner-full-control` |
| `--cache-control` | No | string | None | Cache-Control header |
| `--content-disposition` | No | string | None | Content-Disposition header |
| `--content-encoding` | No | string | None | Content-Encoding header |
| `--content-language` | No | string | None | Content-Language header |
| `--content-type` | No | string | None | MIME type |
| `--expires` | No | timestamp | None | Expiration date |
| `--metadata` | No | map | None | Custom metadata |
| `--server-side-encryption` | No | string | None | `AES256`, `aws:kms`, `aws:kms:dsse` |
| `--storage-class` | No | string | `STANDARD` | Storage class |
| `--tagging` | No | string | None | URL-encoded tag set |
| `--ssekms-key-id` | No | string | None | KMS key ID |
| `--bucket-key-enabled` | No | boolean | None | Use S3 Bucket Key |
| `--checksum-algorithm` | No | string | None | `CRC32`, `CRC32C`, `SHA1`, `SHA256`, `CRC64NVME` |
| `--object-lock-mode` | No | string | None | `GOVERNANCE`, `COMPLIANCE` |
| `--object-lock-retain-until-date` | No | timestamp | None | Lock expiration |
| `--object-lock-legal-hold-status` | No | string | None | `ON`, `OFF` |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output Schema:**
```json
{
    "Bucket": "string",
    "Key": "string",
    "UploadId": "string",
    "ServerSideEncryption": "AES256|aws:kms|aws:kms:dsse",
    "SSECustomerAlgorithm": "string",
    "SSECustomerKeyMD5": "string",
    "SSEKMSKeyId": "string",
    "SSEKMSEncryptionContext": "string",
    "BucketKeyEnabled": true|false,
    "RequestCharged": "requester",
    "ChecksumAlgorithm": "CRC32|CRC32C|SHA1|SHA256|CRC64NVME",
    "AbortDate": "timestamp",
    "AbortRuleId": "string"
}
```

---

### 5.2 `upload-part`

Uploads a part in a multipart upload. Part size minimum 5 MB (except last part).

**Synopsis:**
```bash
aws s3api upload-part \
    --bucket <value> \
    --key <value> \
    --part-number <value> \
    --upload-id <value> \
    [--body <value>] \
    [--content-length <value>] \
    [--content-md5 <value>] \
    [--checksum-algorithm <value>] \
    [--sse-customer-algorithm <value>] \
    [--sse-customer-key <value>] \
    [--request-payer <value>] \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--key` | **Yes** | string | -- | Object key |
| `--part-number` | **Yes** | integer | -- | Part number (1-10000) |
| `--upload-id` | **Yes** | string | -- | Upload ID from `create-multipart-upload` |
| `--body` | No | streaming blob | None | Part data (file path) |
| `--content-length` | No | long | None | Size in bytes |
| `--content-md5` | No | string | None | Base64-encoded MD5 digest |
| `--checksum-algorithm` | No | string | None | `CRC32`, `CRC32C`, `SHA1`, `SHA256`, `CRC64NVME` |
| `--sse-customer-algorithm` | No | string | None | SSE-C algorithm |
| `--sse-customer-key` | No | string | None | SSE-C key |
| `--request-payer` | No | string | None | `requester` |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output Schema:**
```json
{
    "ServerSideEncryption": "AES256|aws:kms|aws:kms:dsse",
    "ETag": "string",
    "ChecksumCRC32": "string",
    "ChecksumCRC32C": "string",
    "ChecksumSHA1": "string",
    "ChecksumSHA256": "string",
    "SSECustomerAlgorithm": "string",
    "SSECustomerKeyMD5": "string",
    "SSEKMSKeyId": "string",
    "BucketKeyEnabled": true|false,
    "RequestCharged": "requester"
}
```

---

### 5.3 `upload-part-copy`

Uploads a part by copying data from an existing object.

**Synopsis:**
```bash
aws s3api upload-part-copy \
    --bucket <value> \
    --copy-source <value> \
    --key <value> \
    --part-number <value> \
    --upload-id <value> \
    [--copy-source-range <value>] \
    [--copy-source-if-match <value>] \
    [--copy-source-if-none-match <value>] \
    [--copy-source-if-modified-since <value>] \
    [--copy-source-if-unmodified-since <value>] \
    [--sse-customer-algorithm <value>] \
    [--sse-customer-key <value>] \
    [--copy-source-sse-customer-algorithm <value>] \
    [--copy-source-sse-customer-key <value>] \
    [--request-payer <value>] \
    [--expected-bucket-owner <value>] \
    [--expected-source-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Destination bucket name |
| `--copy-source` | **Yes** | string | -- | Source: `bucket/key` or `bucket/key?versionId=id` |
| `--key` | **Yes** | string | -- | Object key |
| `--part-number` | **Yes** | integer | -- | Part number (1-10000) |
| `--upload-id` | **Yes** | string | -- | Upload ID |
| `--copy-source-range` | No | string | None | Byte range: `bytes=start-end` |
| `--copy-source-if-match` | No | string | None | Copy if source ETag matches |
| `--copy-source-if-none-match` | No | string | None | Copy if source ETag differs |
| `--copy-source-if-modified-since` | No | timestamp | None | Copy if modified after date |
| `--copy-source-if-unmodified-since` | No | timestamp | None | Copy if unmodified since date |
| `--request-payer` | No | string | None | `requester` |
| `--expected-bucket-owner` | No | string | None | Expected dest account ID |
| `--expected-source-bucket-owner` | No | string | None | Expected source account ID |

**Output Schema:**
```json
{
    "CopySourceVersionId": "string",
    "CopyPartResult": {
        "ETag": "string",
        "LastModified": "timestamp",
        "ChecksumCRC32": "string",
        "ChecksumCRC32C": "string",
        "ChecksumSHA1": "string",
        "ChecksumSHA256": "string"
    },
    "ServerSideEncryption": "AES256|aws:kms|aws:kms:dsse",
    "SSECustomerAlgorithm": "string",
    "SSECustomerKeyMD5": "string",
    "SSEKMSKeyId": "string",
    "BucketKeyEnabled": true|false,
    "RequestCharged": "requester"
}
```

---

### 5.4 `complete-multipart-upload`

Completes a multipart upload by assembling previously uploaded parts.

**Synopsis:**
```bash
aws s3api complete-multipart-upload \
    --bucket <value> \
    --key <value> \
    --upload-id <value> \
    [--multipart-upload <value>] \
    [--checksum-crc32 <value>] \
    [--checksum-crc32-c <value>] \
    [--checksum-sha1 <value>] \
    [--checksum-sha256 <value>] \
    [--request-payer <value>] \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--key` | **Yes** | string | -- | Object key |
| `--upload-id` | **Yes** | string | -- | Upload ID |
| `--multipart-upload` | No | structure | None | Parts list. Supports `file://` |
| `--request-payer` | No | string | None | `requester` |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Multipart Upload Structure:**
```json
{
    "Parts": [
        {
            "ETag": "string",
            "PartNumber": integer,
            "ChecksumCRC32": "string",
            "ChecksumCRC32C": "string",
            "ChecksumSHA1": "string",
            "ChecksumSHA256": "string"
        }
    ]
}
```

**Output Schema:**
```json
{
    "Location": "string",
    "Bucket": "string",
    "Key": "string",
    "Expiration": "string",
    "ETag": "string",
    "ChecksumCRC32": "string",
    "ChecksumCRC32C": "string",
    "ChecksumSHA1": "string",
    "ChecksumSHA256": "string",
    "ChecksumType": "COMPOSITE|FULL_OBJECT",
    "ServerSideEncryption": "AES256|aws:kms|aws:kms:dsse",
    "VersionId": "string",
    "SSEKMSKeyId": "string",
    "BucketKeyEnabled": true|false,
    "RequestCharged": "requester"
}
```

---

### 5.5 `abort-multipart-upload`

Aborts a multipart upload. After aborting, no additional parts can be uploaded.

**Synopsis:**
```bash
aws s3api abort-multipart-upload \
    --bucket <value> \
    --key <value> \
    --upload-id <value> \
    [--request-payer <value>] \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--key` | **Yes** | string | -- | Object key |
| `--upload-id` | **Yes** | string | -- | Upload ID |
| `--request-payer` | No | string | None | `requester` |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output Schema:**
```json
{
    "RequestCharged": "requester"
}
```

---

### 5.6 `list-multipart-uploads`

Lists in-progress multipart uploads in a bucket. **Paginated operation.**

**Synopsis:**
```bash
aws s3api list-multipart-uploads \
    --bucket <value> \
    [--delimiter <value>] \
    [--encoding-type <value>] \
    [--prefix <value>] \
    [--request-payer <value>] \
    [--expected-bucket-owner <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--delimiter` | No | string | None | Grouping character |
| `--encoding-type` | No | string | None | `url` |
| `--prefix` | No | string | None | Filter by key prefix |
| `--request-payer` | No | string | None | `requester` |
| `--expected-bucket-owner` | No | string | None | Expected account ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Bucket": "string",
    "KeyMarker": "string",
    "UploadIdMarker": "string",
    "NextKeyMarker": "string",
    "Prefix": "string",
    "Delimiter": "string",
    "NextUploadIdMarker": "string",
    "MaxUploads": integer,
    "IsTruncated": true|false,
    "Uploads": [
        {
            "UploadId": "string",
            "Key": "string",
            "Initiated": "timestamp",
            "StorageClass": "string",
            "Owner": {
                "DisplayName": "string",
                "ID": "string"
            },
            "Initiator": {
                "ID": "string",
                "DisplayName": "string"
            },
            "ChecksumAlgorithm": "CRC32|CRC32C|SHA1|SHA256|CRC64NVME"
        }
    ],
    "CommonPrefixes": [{"Prefix": "string"}],
    "EncodingType": "url",
    "RequestCharged": "requester"
}
```

---

### 5.7 `list-parts`

Lists the parts that have been uploaded for a specific multipart upload. **Paginated operation.**

**Synopsis:**
```bash
aws s3api list-parts \
    --bucket <value> \
    --key <value> \
    --upload-id <value> \
    [--request-payer <value>] \
    [--expected-bucket-owner <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--key` | **Yes** | string | -- | Object key |
| `--upload-id` | **Yes** | string | -- | Upload ID |
| `--request-payer` | No | string | None | `requester` |
| `--expected-bucket-owner` | No | string | None | Expected account ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AbortDate": "timestamp",
    "AbortRuleId": "string",
    "Bucket": "string",
    "Key": "string",
    "UploadId": "string",
    "PartNumberMarker": integer,
    "NextPartNumberMarker": integer,
    "MaxParts": integer,
    "IsTruncated": true|false,
    "Parts": [
        {
            "PartNumber": integer,
            "LastModified": "timestamp",
            "ETag": "string",
            "Size": long,
            "ChecksumCRC32": "string",
            "ChecksumCRC32C": "string",
            "ChecksumSHA1": "string",
            "ChecksumSHA256": "string"
        }
    ],
    "Initiator": {
        "ID": "string",
        "DisplayName": "string"
    },
    "Owner": {
        "DisplayName": "string",
        "ID": "string"
    },
    "StorageClass": "string",
    "RequestCharged": "requester",
    "ChecksumAlgorithm": "CRC32|CRC32C|SHA1|SHA256|CRC64NVME"
}
```

---

