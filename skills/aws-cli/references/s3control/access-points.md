# Access Points

### 1.1 `create-access-point`

Creates an access point and associates it with the specified S3 bucket or directory bucket.

**Synopsis:**
```bash
aws s3control create-access-point \
    --account-id <value> \
    --name <value> \
    --bucket <value> \
    [--vpc-configuration <value>] \
    [--public-access-block-configuration <value>] \
    [--bucket-account-id <value>] \
    [--scope <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit). Pattern: `^\d{12}$` |
| `--name` | **Yes** | string | -- | Access point name (3-255 chars) |
| `--bucket` | **Yes** | string | -- | Bucket name or ARN. For Outposts: `arn:aws:s3-outposts:<Region>:<account-id>:outpost/<outpost-id>/bucket/<name>` |
| `--vpc-configuration` | No | structure | None | Restrict to a VPC. Shorthand: `VpcId=string`. Required for S3 on Outposts |
| `--public-access-block-configuration` | No | structure | None | Public access block settings. Not supported for Outposts |
| `--bucket-account-id` | No | string | None | Account ID owning the bucket (for cross-account access points) |
| `--scope` | No | structure | None | Filter scope for directory buckets. Structure: `Prefixes=string,string,Permissions=string,string` |
| `--tags` | No | list | None | Key-value tags (max 50). Shorthand: `Key=string,Value=string ...` |

**PublicAccessBlockConfiguration Structure:**
```json
{
    "BlockPublicAcls": true|false,
    "IgnorePublicAcls": true|false,
    "BlockPublicPolicy": true|false,
    "RestrictPublicBuckets": true|false
}
```

**Output Schema:**
```json
{
    "AccessPointArn": "string",
    "Alias": "string"
}
```

---

### 1.2 `delete-access-point`

Deletes the specified access point.

**Synopsis:**
```bash
aws s3control delete-access-point \
    --account-id <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--name` | **Yes** | string | -- | Access point name or ARN (for Outposts) |

**Output:** None

---

### 1.3 `get-access-point`

Returns configuration information about the specified access point.

**Synopsis:**
```bash
aws s3control get-access-point \
    --account-id <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--name` | **Yes** | string | -- | Access point name or ARN (for Outposts) |

**Output Schema:**
```json
{
    "Name": "string",
    "Bucket": "string",
    "NetworkOrigin": "Internet|VPC",
    "VpcConfiguration": {
        "VpcId": "string"
    },
    "PublicAccessBlockConfiguration": {
        "BlockPublicAcls": true|false,
        "IgnorePublicAcls": true|false,
        "BlockPublicPolicy": true|false,
        "RestrictPublicBuckets": true|false
    },
    "CreationDate": "timestamp",
    "Alias": "string",
    "AccessPointArn": "string",
    "Endpoints": {
        "key": "value"
    },
    "BucketAccountId": "string"
}
```

---

### 1.4 `list-access-points`

Returns a list of access points associated with the specified bucket or account. **Paginated.**

**Synopsis:**
```bash
aws s3control list-access-points \
    --account-id <value> \
    [--bucket <value>] \
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
| `--bucket` | No | string | None | Filter by bucket name or ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 1000) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AccessPointList": [
        {
            "Name": "string",
            "NetworkOrigin": "Internet|VPC",
            "VpcConfiguration": {
                "VpcId": "string"
            },
            "Bucket": "string",
            "AccessPointArn": "string",
            "Alias": "string",
            "BucketAccountId": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `list-access-points-for-directory-buckets`

Returns a list of access points for directory buckets. **Paginated.**

**Synopsis:**
```bash
aws s3control list-access-points-for-directory-buckets \
    --account-id <value> \
    [--directory-bucket <value>] \
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
| `--directory-bucket` | No | string | None | Filter by directory bucket name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AccessPointList": [
        {
            "Name": "string",
            "Bucket": "string",
            "AccessPointArn": "string",
            "Alias": "string",
            "BucketAccountId": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.6 `put-access-point-policy`

Associates an access point policy with the specified access point.

**Synopsis:**
```bash
aws s3control put-access-point-policy \
    --account-id <value> \
    --name <value> \
    --policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--name` | **Yes** | string | -- | Access point name |
| `--policy` | **Yes** | string | -- | JSON policy document |

**Output:** None

---

### 1.7 `get-access-point-policy`

Returns the access point policy associated with the specified access point.

**Synopsis:**
```bash
aws s3control get-access-point-policy \
    --account-id <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--name` | **Yes** | string | -- | Access point name or ARN |

**Output Schema:**
```json
{
    "Policy": "string"
}
```

---

### 1.8 `delete-access-point-policy`

Deletes the access point policy for the specified access point.

**Synopsis:**
```bash
aws s3control delete-access-point-policy \
    --account-id <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--name` | **Yes** | string | -- | Access point name or ARN |

**Output:** None

---

### 1.9 `get-access-point-policy-status`

Indicates whether the specified access point currently has a policy that allows public access.

**Synopsis:**
```bash
aws s3control get-access-point-policy-status \
    --account-id <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--name` | **Yes** | string | -- | Access point name |

**Output Schema:**
```json
{
    "PolicyStatus": {
        "IsPublic": true|false
    }
}
```

---

### 1.10 `put-access-point-scope`

Sets the scope for an access point. Only supported for access points on directory buckets.

**Synopsis:**
```bash
aws s3control put-access-point-scope \
    --account-id <value> \
    --name <value> \
    --scope <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--name` | **Yes** | string | -- | Access point name |
| `--scope` | **Yes** | structure | -- | Scope configuration with Prefixes and Permissions |

**Scope Structure:**
```json
{
    "Prefixes": ["string"],
    "Permissions": ["GetObject", "GetObjectAttributes", "ListMultipartUploadParts", "ListBucket", "ListBucketMultipartUploads", "PutObject", "DeleteObject", "AbortMultipartUpload"]
}
```

**Output:** None

---

### 1.11 `get-access-point-scope`

Returns the scope of the specified access point.

**Synopsis:**
```bash
aws s3control get-access-point-scope \
    --account-id <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--name` | **Yes** | string | -- | Access point name |

**Output Schema:**
```json
{
    "Scope": {
        "Prefixes": ["string"],
        "Permissions": ["string"]
    }
}
```

---

### 1.12 `delete-access-point-scope`

Deletes the scope of the specified access point.

**Synopsis:**
```bash
aws s3control delete-access-point-scope \
    --account-id <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--name` | **Yes** | string | -- | Access point name |

**Output:** None
