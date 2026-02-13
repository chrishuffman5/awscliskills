# Object Operations

### 4.1 `put-object`

Adds an object to a bucket.

**Synopsis:**
```bash
aws s3api put-object \
    --bucket <value> \
    --key <value> \
    [--body <value>] \
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
    [--website-redirect-location <value>] \
    [--ssekms-key-id <value>] \
    [--bucket-key-enabled | --no-bucket-key-enabled] \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--key` | **Yes** | string | -- | Object key (min 1 char) |
| `--body` | No | streaming blob | None | Object data (file path, not prefixed with `file://`) |
| `--acl` | No | string | `private` | `private`, `public-read`, `public-read-write`, `authenticated-read`, `aws-exec-read`, `bucket-owner-read`, `bucket-owner-full-control` |
| `--content-type` | No | string | None | MIME type of the object |
| `--content-length` | No | long | None | Size of body in bytes |
| `--cache-control` | No | string | None | Cache-Control header |
| `--content-disposition` | No | string | None | Content-Disposition header |
| `--content-encoding` | No | string | None | Content-Encoding header |
| `--content-language` | No | string | None | Content-Language header |
| `--expires` | No | timestamp | None | Expiration date/time |
| `--metadata` | No | map | None | Custom metadata key-value pairs |
| `--server-side-encryption` | No | string | `AES256` | `AES256`, `aws:kms`, `aws:kms:dsse` |
| `--storage-class` | No | string | `STANDARD` | `STANDARD`, `STANDARD_IA`, `ONEZONE_IA`, `INTELLIGENT_TIERING`, `GLACIER`, `DEEP_ARCHIVE`, `GLACIER_IR` |
| `--tagging` | No | string | None | URL-encoded tag set (e.g. `Key1=Value1&Key2=Value2`) |
| `--website-redirect-location` | No | string | None | Redirect URL |
| `--ssekms-key-id` | No | string | `aws/s3` | KMS key ID, ARN, or alias |
| `--ssekms-encryption-context` | No | string | None | Base64-encoded JSON encryption context |
| `--bucket-key-enabled` | No | boolean | None | Use S3 Bucket Key with SSE-KMS |
| `--checksum-algorithm` | No | string | None | `CRC32`, `CRC32C`, `SHA1`, `SHA256`, `CRC64NVME` |
| `--object-lock-mode` | No | string | None | `GOVERNANCE`, `COMPLIANCE` |
| `--object-lock-retain-until-date` | No | timestamp | None | Lock expiration date |
| `--object-lock-legal-hold-status` | No | string | None | `ON`, `OFF` |
| `--request-payer` | No | string | None | `requester` |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output Schema:**
```json
{
    "Expiration": "string",
    "ETag": "string",
    "ChecksumCRC32": "string",
    "ChecksumCRC32C": "string",
    "ChecksumSHA1": "string",
    "ChecksumSHA256": "string",
    "ServerSideEncryption": "AES256|aws:kms|aws:kms:dsse",
    "VersionId": "string",
    "SSECustomerAlgorithm": "string",
    "SSECustomerKeyMD5": "string",
    "SSEKMSKeyId": "string",
    "SSEKMSEncryptionContext": "string",
    "BucketKeyEnabled": true|false,
    "Size": long,
    "RequestCharged": "requester"
}
```

---

### 4.2 `get-object`

Retrieves an object from S3.

**Synopsis:**
```bash
aws s3api get-object \
    --bucket <value> \
    --key <value> \
    <outfile> \
    [--if-match <value>] \
    [--if-modified-since <value>] \
    [--if-none-match <value>] \
    [--if-unmodified-since <value>] \
    [--range <value>] \
    [--version-id <value>] \
    [--part-number <value>] \
    [--sse-customer-algorithm <value>] \
    [--sse-customer-key <value>] \
    [--request-payer <value>] \
    [--expected-bucket-owner <value>] \
    [--checksum-mode <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--key` | **Yes** | string | -- | Object key |
| `outfile` | **Yes** | string | -- | Local file path to save content (positional, must be last) |
| `--if-match` | No | string | None | Return only if ETag matches |
| `--if-modified-since` | No | timestamp | None | Return only if modified since |
| `--if-none-match` | No | string | None | Return only if ETag differs |
| `--if-unmodified-since` | No | timestamp | None | Return only if unmodified since |
| `--range` | No | string | None | Byte range (e.g. `bytes=0-999`) |
| `--version-id` | No | string | None | Specific version ID |
| `--part-number` | No | integer | None | Part number (1-10000) |
| `--sse-customer-algorithm` | No | string | None | SSE-C algorithm (e.g. `AES256`) |
| `--sse-customer-key` | No | string | None | SSE-C encryption key |
| `--sse-customer-key-md5` | No | string | None | MD5 digest of SSE-C key |
| `--request-payer` | No | string | None | `requester` |
| `--expected-bucket-owner` | No | string | None | Expected account ID |
| `--checksum-mode` | No | string | None | `ENABLED` to retrieve checksum |

**Output Schema:**
```json
{
    "Body": "streaming blob",
    "DeleteMarker": true|false,
    "AcceptRanges": "string",
    "Expiration": "string",
    "Restore": "string",
    "LastModified": "timestamp",
    "ContentLength": long,
    "ETag": "string",
    "ChecksumCRC32": "string",
    "ChecksumCRC32C": "string",
    "ChecksumSHA1": "string",
    "ChecksumSHA256": "string",
    "MissingMeta": integer,
    "VersionId": "string",
    "CacheControl": "string",
    "ContentDisposition": "string",
    "ContentEncoding": "string",
    "ContentLanguage": "string",
    "ContentRange": "string",
    "ContentType": "string",
    "Expires": "timestamp",
    "WebsiteRedirectLocation": "string",
    "ServerSideEncryption": "AES256|aws:kms|aws:kms:dsse",
    "Metadata": {"string": "string"},
    "SSECustomerAlgorithm": "string",
    "SSECustomerKeyMD5": "string",
    "SSEKMSKeyId": "string",
    "BucketKeyEnabled": true|false,
    "StorageClass": "STANDARD|REDUCED_REDUNDANCY|STANDARD_IA|ONEZONE_IA|INTELLIGENT_TIERING|GLACIER|DEEP_ARCHIVE|GLACIER_IR|EXPRESS_ONEZONE",
    "RequestCharged": "requester",
    "ReplicationStatus": "COMPLETE|PENDING|FAILED|REPLICA|COMPLETED",
    "PartsCount": integer,
    "TagCount": integer,
    "ObjectLockMode": "GOVERNANCE|COMPLIANCE",
    "ObjectLockRetainUntilDate": "timestamp",
    "ObjectLockLegalHoldStatus": "ON|OFF"
}
```

---

### 4.3 `delete-object`

Deletes an object from a bucket.

**Synopsis:**
```bash
aws s3api delete-object \
    --bucket <value> \
    --key <value> \
    [--mfa <value>] \
    [--version-id <value>] \
    [--request-payer <value>] \
    [--bypass-governance-retention | --no-bypass-governance-retention] \
    [--expected-bucket-owner <value>] \
    [--if-match <value>] \
    [--if-match-last-modified-time <value>] \
    [--if-match-size <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--key` | **Yes** | string | -- | Object key |
| `--mfa` | No | string | None | MFA device serial and token |
| `--version-id` | No | string | None | Version ID to delete |
| `--request-payer` | No | string | None | `requester` |
| `--bypass-governance-retention` | No | boolean | false | Bypass Governance-type Object Lock |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output Schema:**
```json
{
    "DeleteMarker": true|false,
    "VersionId": "string",
    "RequestCharged": "requester"
}
```

---

### 4.4 `delete-objects`

Deletes multiple objects from a bucket in a single request (up to 1000 keys).

**Synopsis:**
```bash
aws s3api delete-objects \
    --bucket <value> \
    --delete <value> \
    [--mfa <value>] \
    [--request-payer <value>] \
    [--bypass-governance-retention | --no-bypass-governance-retention] \
    [--expected-bucket-owner <value>] \
    [--checksum-algorithm <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--delete` | **Yes** | structure | -- | Delete request. Supports `file://` |
| `--mfa` | No | string | None | MFA device serial and token |
| `--request-payer` | No | string | None | `requester` |
| `--bypass-governance-retention` | No | boolean | false | Bypass Governance Object Lock |
| `--expected-bucket-owner` | No | string | None | Expected account ID |
| `--checksum-algorithm` | No | string | None | `CRC32`, `CRC32C`, `SHA1`, `SHA256` |

**Delete Structure:**
```json
{
    "Objects": [
        {
            "Key": "string",
            "VersionId": "string"
        }
    ],
    "Quiet": true|false
}
```

**Output Schema:**
```json
{
    "Deleted": [
        {
            "Key": "string",
            "VersionId": "string",
            "DeleteMarker": true|false,
            "DeleteMarkerVersionId": "string"
        }
    ],
    "Errors": [
        {
            "Key": "string",
            "VersionId": "string",
            "Code": "string",
            "Message": "string"
        }
    ],
    "RequestCharged": "requester"
}
```

---

### 4.5 `copy-object`

Creates a copy of an object already stored in S3.

**Synopsis:**
```bash
aws s3api copy-object \
    --bucket <value> \
    --copy-source <value> \
    --key <value> \
    [--acl <value>] \
    [--metadata <value>] \
    [--metadata-directive <value>] \
    [--tagging <value>] \
    [--tagging-directive <value>] \
    [--server-side-encryption <value>] \
    [--storage-class <value>] \
    [--ssekms-key-id <value>] \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Destination bucket name |
| `--copy-source` | **Yes** | string | -- | Source: `bucket/key` or with version `bucket/key?versionId=id` |
| `--key` | **Yes** | string | -- | Destination object key |
| `--acl` | No | string | `private` | Canned ACL for destination |
| `--metadata` | No | map | None | Custom metadata (requires `--metadata-directive REPLACE`) |
| `--metadata-directive` | No | string | `COPY` | `COPY` or `REPLACE` |
| `--tagging` | No | string | None | Tag set (requires `--tagging-directive REPLACE`) |
| `--tagging-directive` | No | string | `COPY` | `COPY` or `REPLACE` |
| `--server-side-encryption` | No | string | None | `AES256`, `aws:kms`, `aws:kms:dsse` |
| `--storage-class` | No | string | `STANDARD` | Destination storage class |
| `--ssekms-key-id` | No | string | None | KMS key ID |
| `--copy-source-if-match` | No | string | None | Copy if source ETag matches |
| `--copy-source-if-none-match` | No | string | None | Copy if source ETag differs |
| `--copy-source-if-modified-since` | No | timestamp | None | Copy if source modified after date |
| `--copy-source-if-unmodified-since` | No | timestamp | None | Copy if source not modified since |
| `--checksum-algorithm` | No | string | None | `CRC32`, `CRC32C`, `SHA1`, `SHA256` |
| `--object-lock-mode` | No | string | None | `GOVERNANCE`, `COMPLIANCE` |
| `--object-lock-retain-until-date` | No | timestamp | None | Lock expiration date |
| `--object-lock-legal-hold-status` | No | string | None | `ON`, `OFF` |
| `--request-payer` | No | string | None | `requester` |
| `--expected-bucket-owner` | No | string | None | Expected destination account ID |
| `--expected-source-bucket-owner` | No | string | None | Expected source account ID |

**Output Schema:**
```json
{
    "CopyObjectResult": {
        "ETag": "string",
        "LastModified": "timestamp",
        "ChecksumCRC32": "string",
        "ChecksumCRC32C": "string",
        "ChecksumSHA1": "string",
        "ChecksumSHA256": "string"
    },
    "Expiration": "string",
    "CopySourceVersionId": "string",
    "VersionId": "string",
    "ServerSideEncryption": "AES256|aws:kms|aws:kms:dsse",
    "SSECustomerAlgorithm": "string",
    "SSECustomerKeyMD5": "string",
    "SSEKMSKeyId": "string",
    "SSEKMSEncryptionContext": "string",
    "BucketKeyEnabled": true|false,
    "RequestCharged": "requester"
}
```

---

### 4.6 `head-object`

Retrieves metadata from an object without returning the object itself.

**Synopsis:**
```bash
aws s3api head-object \
    --bucket <value> \
    --key <value> \
    [--if-match <value>] \
    [--if-modified-since <value>] \
    [--if-none-match <value>] \
    [--if-unmodified-since <value>] \
    [--range <value>] \
    [--version-id <value>] \
    [--part-number <value>] \
    [--sse-customer-algorithm <value>] \
    [--sse-customer-key <value>] \
    [--request-payer <value>] \
    [--expected-bucket-owner <value>] \
    [--checksum-mode <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--key` | **Yes** | string | -- | Object key |
| `--if-match` | No | string | None | Return only if ETag matches |
| `--if-modified-since` | No | timestamp | None | Return only if modified since |
| `--if-none-match` | No | string | None | Return only if ETag differs |
| `--if-unmodified-since` | No | timestamp | None | Return only if unmodified since |
| `--range` | No | string | None | Byte range (affects ContentLength only) |
| `--version-id` | No | string | None | Specific version ID |
| `--part-number` | No | integer | None | Part number (1-10000) |
| `--sse-customer-algorithm` | No | string | None | SSE-C algorithm |
| `--sse-customer-key` | No | string | None | SSE-C encryption key |
| `--sse-customer-key-md5` | No | string | None | MD5 digest of SSE-C key |
| `--request-payer` | No | string | None | `requester` |
| `--expected-bucket-owner` | No | string | None | Expected account ID |
| `--checksum-mode` | No | string | None | `ENABLED` |

**Output Schema:**
```json
{
    "AcceptRanges": "string",
    "Expiration": "string",
    "Restore": "string",
    "ArchiveStatus": "ARCHIVE_ACCESS|DEEP_ARCHIVE_ACCESS",
    "LastModified": "timestamp",
    "ContentLength": long,
    "ChecksumCRC32": "string",
    "ChecksumCRC32C": "string",
    "ChecksumSHA1": "string",
    "ChecksumSHA256": "string",
    "ETag": "string",
    "MissingMeta": integer,
    "VersionId": "string",
    "CacheControl": "string",
    "ContentDisposition": "string",
    "ContentEncoding": "string",
    "ContentLanguage": "string",
    "ContentType": "string",
    "Expires": "timestamp",
    "WebsiteRedirectLocation": "string",
    "ServerSideEncryption": "AES256|aws:kms|aws:kms:dsse",
    "Metadata": {"string": "string"},
    "SSECustomerAlgorithm": "string",
    "SSECustomerKeyMD5": "string",
    "SSEKMSKeyId": "string",
    "BucketKeyEnabled": true|false,
    "StorageClass": "STANDARD|REDUCED_REDUNDANCY|STANDARD_IA|ONEZONE_IA|INTELLIGENT_TIERING|GLACIER|DEEP_ARCHIVE|GLACIER_IR|EXPRESS_ONEZONE",
    "RequestCharged": "requester",
    "ReplicationStatus": "COMPLETE|PENDING|FAILED|REPLICA|COMPLETED",
    "PartsCount": integer,
    "ObjectLockMode": "GOVERNANCE|COMPLIANCE",
    "ObjectLockRetainUntilDate": "timestamp",
    "ObjectLockLegalHoldStatus": "ON|OFF"
}
```

---

### 4.7 `list-objects-v2`

Lists objects in a bucket. Returns up to 1000 objects per request. **Paginated operation.**

**Synopsis:**
```bash
aws s3api list-objects-v2 \
    --bucket <value> \
    [--delimiter <value>] \
    [--encoding-type <value>] \
    [--prefix <value>] \
    [--fetch-owner | --no-fetch-owner] \
    [--start-after <value>] \
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
| `--delimiter` | No | string | None | Grouping character (commonly `/`) |
| `--encoding-type` | No | string | None | `url` to URL-encode keys |
| `--prefix` | No | string | None | Return only keys with this prefix |
| `--fetch-owner` | No | boolean | false | Include owner field |
| `--start-after` | No | string | None | Start listing after this key |
| `--request-payer` | No | string | None | `requester` |
| `--expected-bucket-owner` | No | string | None | Expected account ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "IsTruncated": true|false,
    "Contents": [
        {
            "Key": "string",
            "LastModified": "timestamp",
            "ETag": "string",
            "ChecksumAlgorithm": ["CRC32|CRC32C|SHA1|SHA256"],
            "Size": long,
            "StorageClass": "STANDARD|REDUCED_REDUNDANCY|GLACIER|STANDARD_IA|ONEZONE_IA|INTELLIGENT_TIERING|DEEP_ARCHIVE|GLACIER_IR|EXPRESS_ONEZONE",
            "Owner": {
                "DisplayName": "string",
                "ID": "string"
            },
            "RestoreStatus": {
                "IsRestoreInProgress": true|false,
                "RestoreExpiryDate": "timestamp"
            }
        }
    ],
    "Name": "string",
    "Prefix": "string",
    "Delimiter": "string",
    "MaxKeys": integer,
    "CommonPrefixes": [
        {
            "Prefix": "string"
        }
    ],
    "EncodingType": "url",
    "KeyCount": integer,
    "ContinuationToken": "string",
    "NextContinuationToken": "string",
    "StartAfter": "string",
    "RequestCharged": "requester"
}
```

---

### 4.8 `list-object-versions`

Lists all versions of objects in a bucket. **Paginated operation.**

**Synopsis:**
```bash
aws s3api list-object-versions \
    --bucket <value> \
    [--delimiter <value>] \
    [--encoding-type <value>] \
    [--prefix <value>] \
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
| `--expected-bucket-owner` | No | string | None | Expected account ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "IsTruncated": true|false,
    "Versions": [
        {
            "ETag": "string",
            "ChecksumAlgorithm": ["string"],
            "Size": long,
            "StorageClass": "STANDARD",
            "Key": "string",
            "VersionId": "string",
            "IsLatest": true|false,
            "LastModified": "timestamp",
            "Owner": {
                "DisplayName": "string",
                "ID": "string"
            },
            "RestoreStatus": {
                "IsRestoreInProgress": true|false,
                "RestoreExpiryDate": "timestamp"
            }
        }
    ],
    "DeleteMarkers": [
        {
            "Owner": {
                "DisplayName": "string",
                "ID": "string"
            },
            "Key": "string",
            "VersionId": "string",
            "IsLatest": true|false,
            "LastModified": "timestamp"
        }
    ],
    "Name": "string",
    "Prefix": "string",
    "Delimiter": "string",
    "MaxKeys": integer,
    "CommonPrefixes": [{"Prefix": "string"}],
    "EncodingType": "url",
    "RequestCharged": "requester"
}
```

---

### 4.9 `restore-object`

Restores an archived object (Glacier, Deep Archive) for temporary access.

**Synopsis:**
```bash
aws s3api restore-object \
    --bucket <value> \
    --key <value> \
    [--version-id <value>] \
    [--restore-request <value>] \
    [--request-payer <value>] \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--key` | **Yes** | string | -- | Object key |
| `--version-id` | No | string | None | Version ID |
| `--restore-request` | No | structure | None | Restore configuration |
| `--request-payer` | No | string | None | `requester` |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Restore Request Structure:**
```json
{
    "Days": integer,
    "GlacierJobParameters": {
        "Tier": "Standard|Bulk|Expedited"
    },
    "Tier": "Standard|Bulk|Expedited"
}
```

**Output Schema:**
```json
{
    "RequestCharged": "requester",
    "RestoreOutputPath": "string"
}
```

---

### 4.10 `get-object-acl`

Returns the ACL of an object.

**Synopsis:**
```bash
aws s3api get-object-acl \
    --bucket <value> \
    --key <value> \
    [--version-id <value>] \
    [--request-payer <value>] \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--key` | **Yes** | string | -- | Object key |
| `--version-id` | No | string | None | Version ID |
| `--request-payer` | No | string | None | `requester` |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output Schema:**
```json
{
    "Owner": {
        "DisplayName": "string",
        "ID": "string"
    },
    "Grants": [
        {
            "Grantee": {
                "DisplayName": "string",
                "EmailAddress": "string",
                "ID": "string",
                "Type": "CanonicalUser|AmazonCustomerByEmail|Group",
                "URI": "string"
            },
            "Permission": "FULL_CONTROL|WRITE|WRITE_ACP|READ|READ_ACP"
        }
    ],
    "RequestCharged": "requester"
}
```

---

### 4.11 `put-object-acl`

Sets the ACL for an object.

**Synopsis:**
```bash
aws s3api put-object-acl \
    --bucket <value> \
    --key <value> \
    [--acl <value>] \
    [--access-control-policy <value>] \
    [--grant-full-control <value>] \
    [--grant-read <value>] \
    [--grant-read-acp <value>] \
    [--grant-write-acp <value>] \
    [--version-id <value>] \
    [--request-payer <value>] \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--key` | **Yes** | string | -- | Object key |
| `--acl` | No | string | None | `private`, `public-read`, `public-read-write`, `authenticated-read`, `aws-exec-read`, `bucket-owner-read`, `bucket-owner-full-control` |
| `--access-control-policy` | No | structure | None | Full ACL document |
| `--grant-full-control` | No | string | None | Grant grantee full control |
| `--grant-read` | No | string | None | Grant grantee read |
| `--grant-read-acp` | No | string | None | Grant grantee read ACL |
| `--grant-write-acp` | No | string | None | Grant grantee write ACL |
| `--version-id` | No | string | None | Version ID |
| `--request-payer` | No | string | None | `requester` |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output Schema:**
```json
{
    "RequestCharged": "requester"
}
```

---

### 4.12 `get-object-tagging`

Returns the tag set of an object.

**Synopsis:**
```bash
aws s3api get-object-tagging \
    --bucket <value> \
    --key <value> \
    [--version-id <value>] \
    [--request-payer <value>] \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--key` | **Yes** | string | -- | Object key |
| `--version-id` | No | string | None | Version ID |
| `--request-payer` | No | string | None | `requester` |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output Schema:**
```json
{
    "VersionId": "string",
    "TagSet": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```

---

### 4.13 `put-object-tagging`

Sets the tag set for an object.

**Synopsis:**
```bash
aws s3api put-object-tagging \
    --bucket <value> \
    --key <value> \
    --tagging <value> \
    [--version-id <value>] \
    [--request-payer <value>] \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--key` | **Yes** | string | -- | Object key |
| `--tagging` | **Yes** | structure | -- | `TagSet=[{Key=string,Value=string}]`. Supports `file://` |
| `--version-id` | No | string | None | Version ID |
| `--request-payer` | No | string | None | `requester` |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output Schema:**
```json
{
    "VersionId": "string"
}
```

---

### 4.14 `delete-object-tagging`

Removes the tag set from an object.

**Synopsis:**
```bash
aws s3api delete-object-tagging \
    --bucket <value> \
    --key <value> \
    [--version-id <value>] \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--key` | **Yes** | string | -- | Object key |
| `--version-id` | No | string | None | Version ID |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output Schema:**
```json
{
    "VersionId": "string"
}
```

---

### 4.15 `get-object-attributes`

Retrieves specific attributes of an object without returning the object body.

**Synopsis:**
```bash
aws s3api get-object-attributes \
    --bucket <value> \
    --key <value> \
    --object-attributes <value> \
    [--version-id <value>] \
    [--max-parts <value>] \
    [--part-number-marker <value>] \
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
| `--object-attributes` | **Yes** | list | -- | Attributes to retrieve: `ETag`, `Checksum`, `ObjectParts`, `StorageClass`, `ObjectSize` |
| `--version-id` | No | string | None | Version ID |
| `--max-parts` | No | integer | None | Max parts to return |
| `--part-number-marker` | No | integer | None | Part number after which listing begins |
| `--sse-customer-algorithm` | No | string | None | SSE-C algorithm |
| `--sse-customer-key` | No | string | None | SSE-C key |
| `--request-payer` | No | string | None | `requester` |
| `--expected-bucket-owner` | No | string | None | Expected account ID |

**Output Schema:**
```json
{
    "DeleteMarker": true|false,
    "LastModified": "timestamp",
    "VersionId": "string",
    "RequestCharged": "requester",
    "ETag": "string",
    "Checksum": {
        "ChecksumCRC32": "string",
        "ChecksumCRC32C": "string",
        "ChecksumSHA1": "string",
        "ChecksumSHA256": "string",
        "ChecksumType": "COMPOSITE|FULL_OBJECT"
    },
    "ObjectParts": {
        "TotalPartsCount": integer,
        "PartNumberMarker": integer,
        "NextPartNumberMarker": integer,
        "MaxParts": integer,
        "IsTruncated": true|false,
        "Parts": [
            {
                "PartNumber": integer,
                "Size": long,
                "ChecksumCRC32": "string",
                "ChecksumCRC32C": "string",
                "ChecksumSHA1": "string",
                "ChecksumSHA256": "string"
            }
        ]
    },
    "StorageClass": "string",
    "ObjectSize": long
}
```

---

