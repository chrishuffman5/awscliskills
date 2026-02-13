# Bucket Management (`aws s3api`)

### 2.1 `create-bucket`

Creates a new S3 bucket.

**Synopsis:**
```bash
aws s3api create-bucket \
    --bucket <value> \
    [--acl <value>] \
    [--create-bucket-configuration <value>] \
    [--grant-full-control <value>] \
    [--grant-read <value>] \
    [--grant-read-acp <value>] \
    [--grant-write <value>] \
    [--grant-write-acp <value>] \
    [--object-lock-enabled-for-bucket | --no-object-lock-enabled-for-bucket] \
    [--object-ownership <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--acl` | No | string | None | `private`, `public-read`, `public-read-write`, `authenticated-read` |
| `--create-bucket-configuration` | No | structure | None | Shorthand: `LocationConstraint=<region>`. Required for regions outside `us-east-1` |
| `--grant-full-control` | No | string | None | Grant full control to grantee |
| `--grant-read` | No | string | None | Grant list permission |
| `--grant-read-acp` | No | string | None | Grant read ACL permission |
| `--grant-write` | No | string | None | Grant create/delete permission |
| `--grant-write-acp` | No | string | None | Grant write ACL permission |
| `--object-lock-enabled-for-bucket` | No | boolean | false | Enable S3 Object Lock |
| `--object-ownership` | No | string | `BucketOwnerEnforced` | `BucketOwnerPreferred`, `ObjectWriter`, `BucketOwnerEnforced` |

**Output Schema:**
```json
{
    "Location": "string"
}
```

---

### 2.2 `delete-bucket`

Deletes an S3 bucket. The bucket must be empty.

**Synopsis:**
```bash
aws s3api delete-bucket \
    --bucket <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--expected-bucket-owner` | No | string | None | Expected account ID of bucket owner |

**Output:** None on success.

---

### 2.3 `head-bucket`

Checks whether a bucket exists and you have permission to access it.

**Synopsis:**
```bash
aws s3api head-bucket \
    --bucket <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--expected-bucket-owner` | No | string | None | Expected account ID of bucket owner |

**Output Schema:**
```json
{
    "BucketLocationType": "AvailabilityZone|LocalZone",
    "BucketLocationName": "string",
    "BucketRegion": "string",
    "AccessPointAlias": true|false
}
```

---

### 2.4 `list-buckets`

Lists all S3 buckets owned by the authenticated sender.

**Synopsis:**
```bash
aws s3api list-buckets \
    [--max-buckets <value>] \
    [--continuation-token <value>] \
    [--prefix <value>] \
    [--bucket-region <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-buckets` | No | integer | None | Maximum buckets to return (1-10000) |
| `--continuation-token` | No | string | None | Pagination token |
| `--prefix` | No | string | None | Filter by bucket name prefix |
| `--bucket-region` | No | string | None | Filter by region |

**Output Schema:**
```json
{
    "Buckets": [
        {
            "Name": "string",
            "CreationDate": "timestamp",
            "BucketRegion": "string"
        }
    ],
    "Owner": {
        "DisplayName": "string",
        "ID": "string"
    },
    "ContinuationToken": "string",
    "Prefix": "string"
}
```

---

### 2.5 `get-bucket-location`

Returns the region of a bucket.

**Synopsis:**
```bash
aws s3api get-bucket-location \
    --bucket <value> \
    [--expected-bucket-owner <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket` | **Yes** | string | -- | Bucket name |
| `--expected-bucket-owner` | No | string | None | Expected account ID of bucket owner |

**Output Schema:**
```json
{
    "LocationConstraint": "af-south-1|ap-east-1|ap-northeast-1|ap-northeast-2|ap-northeast-3|ap-south-1|ap-south-2|ap-southeast-1|ap-southeast-2|ap-southeast-3|ca-central-1|cn-north-1|cn-northwest-1|EU|eu-central-1|eu-north-1|eu-south-1|eu-south-2|eu-west-1|eu-west-2|eu-west-3|me-south-1|sa-east-1|us-east-2|us-gov-east-1|us-gov-west-1|us-west-1|us-west-2"
}
```

> **Note:** Buckets in `us-east-1` return `null` for `LocationConstraint`.

---

