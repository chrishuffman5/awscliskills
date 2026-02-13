# Outposts Buckets

These commands manage S3 on Outposts buckets. Bucket names must use the Outposts ARN format: `arn:aws:s3-outposts:<region>:<account-id>:outpost/<outpost-id>/bucket/<bucket-name>`.

### 7.1 `create-bucket`

Creates a new S3 on Outposts bucket.

**Synopsis:**
```bash
aws s3control create-bucket \
    --bucket <value> \
    [--acl <value>] \
    [--create-bucket-configuration <value>] \
    [--grant-full-control <value>] \
    [--grant-read <value>] \
    [--grant-read-acp <value>] \
    [--grant-write <value>] \
    [--grant-write-acp <value>] \
    [--object-lock-enabled-for-bucket | --no-object-lock-enabled-for-bucket] \
    [--outpost-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name (3-255 chars) |
| `--acl` | No | string | None | Canned ACL: `private`, `public-read`, `public-read-write`, `authenticated-read` |
| `--create-bucket-configuration` | No | structure | None | Location constraint. Shorthand: `LocationConstraint=string` |
| `--grant-full-control` | No | string | None | Grant full control to specified grantees |
| `--grant-read` | No | string | None | Grant read access |
| `--grant-read-acp` | No | string | None | Grant read ACP access |
| `--grant-write` | No | string | None | Grant write access |
| `--grant-write-acp` | No | string | None | Grant write ACP access |
| `--object-lock-enabled-for-bucket` | No | boolean | false | Enable Object Lock |
| `--outpost-id` | No | string | None | Outpost ID for S3 on Outposts bucket |

**Output Schema:**
```json
{
    "Location": "string",
    "BucketArn": "string"
}
```

---

### 7.2 `delete-bucket`

Deletes an S3 on Outposts bucket. The bucket must be empty.

**Synopsis:**
```bash
aws s3control delete-bucket \
    --account-id <value> \
    --bucket <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--bucket` | **Yes** | string | -- | Bucket ARN |

**Output:** None

---

### 7.3 `get-bucket`

Returns metadata about an S3 on Outposts bucket.

**Synopsis:**
```bash
aws s3control get-bucket \
    --account-id <value> \
    --bucket <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--bucket` | **Yes** | string | -- | Bucket ARN |

**Output Schema:**
```json
{
    "Bucket": "string",
    "PublicAccessBlockEnabled": true|false,
    "CreationDate": "timestamp"
}
```

---

### 7.4 `list-regional-buckets`

Lists all regional buckets and S3 on Outposts buckets in the account. **Paginated.**

**Synopsis:**
```bash
aws s3control list-regional-buckets \
    --account-id <value> \
    [--outpost-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--outpost-id` | No | string | None | Filter by Outpost ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "RegionalBucketList": [
        {
            "Bucket": "string",
            "BucketArn": "string",
            "PublicAccessBlockEnabled": true|false,
            "CreationDate": "timestamp",
            "OutpostId": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.5 `get-bucket-policy`

Returns the policy for an S3 on Outposts bucket.

**Synopsis:**
```bash
aws s3control get-bucket-policy \
    --account-id <value> \
    --bucket <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--bucket` | **Yes** | string | -- | Bucket ARN |

**Output Schema:**
```json
{
    "Policy": "string"
}
```

---

### 7.6 `put-bucket-policy`

Sets the bucket policy for an S3 on Outposts bucket.

**Synopsis:**
```bash
aws s3control put-bucket-policy \
    --account-id <value> \
    --bucket <value> \
    --policy <value> \
    [--confirm-remove-self-bucket-access | --no-confirm-remove-self-bucket-access] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--bucket` | **Yes** | string | -- | Bucket ARN |
| `--policy` | **Yes** | string | -- | JSON policy document |
| `--confirm-remove-self-bucket-access` | No | boolean | false | Confirm you want to remove your own access |

**Output:** None

---

### 7.7 `delete-bucket-policy`

Deletes the bucket policy for an S3 on Outposts bucket.

**Synopsis:**
```bash
aws s3control delete-bucket-policy \
    --account-id <value> \
    --bucket <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--bucket` | **Yes** | string | -- | Bucket ARN |

**Output:** None

---

### 7.8 `get-bucket-tagging`

Returns the tag set of an S3 on Outposts bucket.

**Synopsis:**
```bash
aws s3control get-bucket-tagging \
    --account-id <value> \
    --bucket <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--bucket` | **Yes** | string | -- | Bucket ARN |

**Output Schema:**
```json
{
    "TagSet": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```

---

### 7.9 `put-bucket-tagging`

Sets the tag set for an S3 on Outposts bucket. Replaces existing tags.

**Synopsis:**
```bash
aws s3control put-bucket-tagging \
    --account-id <value> \
    --bucket <value> \
    --tagging <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--bucket` | **Yes** | string | -- | Bucket ARN |
| `--tagging` | **Yes** | structure | -- | Tag set. Shorthand: `TagSet=[{Key=string,Value=string},{Key=string,Value=string}]` |

**Output:** None

---

### 7.10 `delete-bucket-tagging`

Deletes the tag set from an S3 on Outposts bucket.

**Synopsis:**
```bash
aws s3control delete-bucket-tagging \
    --account-id <value> \
    --bucket <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--bucket` | **Yes** | string | -- | Bucket ARN |

**Output:** None

---

### 7.11 `get-bucket-lifecycle-configuration`

Returns the lifecycle configuration of an S3 on Outposts bucket.

**Synopsis:**
```bash
aws s3control get-bucket-lifecycle-configuration \
    --account-id <value> \
    --bucket <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--bucket` | **Yes** | string | -- | Bucket ARN |

**Output Schema:**
```json
{
    "Rules": [
        {
            "Expiration": {
                "Date": "timestamp",
                "Days": "integer",
                "ExpiredObjectDeleteMarker": true|false
            },
            "ID": "string",
            "Filter": {
                "Prefix": "string",
                "Tag": {"Key": "string", "Value": "string"},
                "And": {
                    "Prefix": "string",
                    "Tags": [{"Key": "string", "Value": "string"}],
                    "ObjectSizeGreaterThan": "long",
                    "ObjectSizeLessThan": "long"
                },
                "ObjectSizeGreaterThan": "long",
                "ObjectSizeLessThan": "long"
            },
            "Status": "Enabled|Disabled",
            "Transitions": [
                {
                    "Date": "timestamp",
                    "Days": "integer",
                    "StorageClass": "GLACIER|STANDARD_IA|ONEZONE_IA|INTELLIGENT_TIERING|DEEP_ARCHIVE"
                }
            ],
            "NoncurrentVersionTransitions": [
                {
                    "NoncurrentDays": "integer",
                    "StorageClass": "string"
                }
            ],
            "NoncurrentVersionExpiration": {
                "NoncurrentDays": "integer",
                "NewerNoncurrentVersions": "integer"
            },
            "AbortIncompleteMultipartUpload": {
                "DaysAfterInitiation": "integer"
            }
        }
    ]
}
```

---

### 7.12 `put-bucket-lifecycle-configuration`

Sets the lifecycle configuration for an S3 on Outposts bucket.

**Synopsis:**
```bash
aws s3control put-bucket-lifecycle-configuration \
    --account-id <value> \
    --bucket <value> \
    [--lifecycle-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--bucket` | **Yes** | string | -- | Bucket ARN |
| `--lifecycle-configuration` | No | structure | None | Lifecycle rules configuration |

**Output:** None

---

### 7.13 `delete-bucket-lifecycle-configuration`

Deletes the lifecycle configuration from an S3 on Outposts bucket.

**Synopsis:**
```bash
aws s3control delete-bucket-lifecycle-configuration \
    --account-id <value> \
    --bucket <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--bucket` | **Yes** | string | -- | Bucket ARN |

**Output:** None

---

### 7.14 `get-bucket-replication`

Returns the replication configuration of an S3 on Outposts bucket.

**Synopsis:**
```bash
aws s3control get-bucket-replication \
    --account-id <value> \
    --bucket <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--bucket` | **Yes** | string | -- | Bucket ARN |

**Output Schema:**
```json
{
    "ReplicationConfiguration": {
        "Role": "string",
        "Rules": [
            {
                "ID": "string",
                "Priority": "integer",
                "Prefix": "string",
                "Filter": {
                    "Prefix": "string",
                    "Tag": {"Key": "string", "Value": "string"},
                    "And": {"Prefix": "string", "Tags": []}
                },
                "Status": "Enabled|Disabled",
                "SourceSelectionCriteria": {
                    "SseKmsEncryptedObjects": {"Status": "Enabled|Disabled"},
                    "ReplicaModifications": {"Status": "Enabled|Disabled"}
                },
                "ExistingObjectReplication": {"Status": "Enabled|Disabled"},
                "Destination": {
                    "Account": "string",
                    "Bucket": "string",
                    "ReplicationTime": {"Status": "Enabled|Disabled", "Time": {"Minutes": "integer"}},
                    "AccessControlTranslation": {"Owner": "Destination"},
                    "EncryptionConfiguration": {"ReplicaKmsKeyID": "string"},
                    "Metrics": {"Status": "Enabled|Disabled", "EventThreshold": {"Minutes": "integer"}},
                    "StorageClass": "string"
                },
                "DeleteMarkerReplication": {"Status": "Enabled|Disabled"},
                "Bucket": "string"
            }
        ]
    }
}
```

---

### 7.15 `put-bucket-replication`

Sets the replication configuration for an S3 on Outposts bucket.

**Synopsis:**
```bash
aws s3control put-bucket-replication \
    --account-id <value> \
    --bucket <value> \
    --replication-configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--bucket` | **Yes** | string | -- | Bucket ARN |
| `--replication-configuration` | **Yes** | structure | -- | Replication configuration (JSON) |

**Output:** None

---

### 7.16 `delete-bucket-replication`

Deletes the replication configuration from an S3 on Outposts bucket.

**Synopsis:**
```bash
aws s3control delete-bucket-replication \
    --account-id <value> \
    --bucket <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--bucket` | **Yes** | string | -- | Bucket ARN |

**Output:** None

---

### 7.17 `get-bucket-versioning`

Returns the versioning state of an S3 on Outposts bucket.

**Synopsis:**
```bash
aws s3control get-bucket-versioning \
    --account-id <value> \
    --bucket <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--bucket` | **Yes** | string | -- | Bucket ARN |

**Output Schema:**
```json
{
    "Status": "Enabled|Suspended",
    "MFADelete": "Enabled|Disabled"
}
```

---

### 7.18 `put-bucket-versioning`

Sets the versioning state of an S3 on Outposts bucket.

**Synopsis:**
```bash
aws s3control put-bucket-versioning \
    --account-id <value> \
    --bucket <value> \
    --versioning-configuration <value> \
    [--mfa <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--bucket` | **Yes** | string | -- | Bucket ARN |
| `--versioning-configuration` | **Yes** | structure | -- | Versioning config. Shorthand: `MFADelete=Enabled\|Disabled,Status=Enabled\|Suspended` |
| `--mfa` | No | string | None | MFA device serial and authentication code |

**Output:** None
