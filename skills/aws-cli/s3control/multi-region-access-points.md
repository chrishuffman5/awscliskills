# Multi-Region Access Points

### 4.1 `create-multi-region-access-point`

Creates a Multi-Region Access Point (MRAP) spanning multiple S3 buckets in different AWS Regions. This is an asynchronous operation.

**Synopsis:**
```bash
aws s3control create-multi-region-access-point \
    --account-id <value> \
    --details <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--details` | **Yes** | structure | -- | MRAP configuration details |
| `--client-token` | No | string | None | Idempotency token (max 64 chars) |

**Details Structure:**
```json
{
    "Name": "string",
    "PublicAccessBlock": {
        "BlockPublicAcls": true|false,
        "IgnorePublicAcls": true|false,
        "BlockPublicPolicy": true|false,
        "RestrictPublicBuckets": true|false
    },
    "Regions": [
        {
            "Bucket": "string",
            "BucketAccountId": "string"
        }
    ]
}
```

> **Note:** MRAP create/delete requests are always routed to US West (Oregon) Region. The `--region us-west-2` flag is recommended.

**Output Schema:**
```json
{
    "RequestTokenARN": "string"
}
```

---

### 4.2 `delete-multi-region-access-point`

Deletes a Multi-Region Access Point. This is an asynchronous operation.

**Synopsis:**
```bash
aws s3control delete-multi-region-access-point \
    --account-id <value> \
    --details <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--details` | **Yes** | structure | -- | Name of the MRAP. Shorthand: `Name=string` |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "RequestTokenARN": "string"
}
```

---

### 4.3 `get-multi-region-access-point`

Returns configuration and status for a Multi-Region Access Point.

**Synopsis:**
```bash
aws s3control get-multi-region-access-point \
    --account-id <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--name` | **Yes** | string | -- | MRAP name (max 50 chars, pattern: `^[a-z0-9][-a-z0-9]{1,48}[a-z0-9]$`) |

**Output Schema:**
```json
{
    "AccessPoint": {
        "Name": "string",
        "Alias": "string",
        "CreatedAt": "timestamp",
        "PublicAccessBlock": {
            "BlockPublicAcls": true|false,
            "IgnorePublicAcls": true|false,
            "BlockPublicPolicy": true|false,
            "RestrictPublicBuckets": true|false
        },
        "Status": "READY|INCONSISTENT_ACROSS_REGIONS|CREATING|PARTIALLY_CREATED|PARTIALLY_DELETED|DELETING",
        "Regions": [
            {
                "Bucket": "string",
                "Region": "string",
                "BucketAccountId": "string"
            }
        ]
    }
}
```

---

### 4.4 `list-multi-region-access-points`

Returns a list of Multi-Region Access Points. **Paginated.**

**Synopsis:**
```bash
aws s3control list-multi-region-access-points \
    --account-id <value> \
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
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AccessPoints": [
        {
            "Name": "string",
            "Alias": "string",
            "CreatedAt": "timestamp",
            "PublicAccessBlock": {
                "BlockPublicAcls": true|false,
                "IgnorePublicAcls": true|false,
                "BlockPublicPolicy": true|false,
                "RestrictPublicBuckets": true|false
            },
            "Status": "string",
            "Regions": [
                {
                    "Bucket": "string",
                    "Region": "string",
                    "BucketAccountId": "string"
                }
            ]
        }
    ],
    "NextToken": "string"
}
```

---

### 4.5 `get-multi-region-access-point-policy`

Returns the access point policy for a Multi-Region Access Point.

**Synopsis:**
```bash
aws s3control get-multi-region-access-point-policy \
    --account-id <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--name` | **Yes** | string | -- | MRAP name |

**Output Schema:**
```json
{
    "Policy": {
        "Established": {
            "Policy": "string"
        },
        "Proposed": {
            "Policy": "string"
        }
    }
}
```

---

### 4.6 `put-multi-region-access-point-policy`

Associates an access point policy with a Multi-Region Access Point. This is an asynchronous operation.

**Synopsis:**
```bash
aws s3control put-multi-region-access-point-policy \
    --account-id <value> \
    --details <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--details` | **Yes** | structure | -- | Policy details. Shorthand: `Name=string,Policy=string` |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "RequestTokenARN": "string"
}
```

---

### 4.7 `get-multi-region-access-point-policy-status`

Indicates whether the MRAP policy allows public access.

**Synopsis:**
```bash
aws s3control get-multi-region-access-point-policy-status \
    --account-id <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--name` | **Yes** | string | -- | MRAP name |

**Output Schema:**
```json
{
    "Established": {
        "IsPublic": true|false
    }
}
```

---

### 4.8 `get-multi-region-access-point-routes`

Returns the routing configuration for a Multi-Region Access Point.

**Synopsis:**
```bash
aws s3control get-multi-region-access-point-routes \
    --account-id <value> \
    --mrap <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--mrap` | **Yes** | string | -- | MRAP ARN or alias |

**Output Schema:**
```json
{
    "Mrap": "string",
    "Routes": [
        {
            "Bucket": "string",
            "Region": "string",
            "TrafficDialPercentage": "integer"
        }
    ]
}
```

---

### 4.9 `submit-multi-region-access-point-routes`

Submits an updated route configuration for a Multi-Region Access Point. This is an asynchronous operation.

**Synopsis:**
```bash
aws s3control submit-multi-region-access-point-routes \
    --account-id <value> \
    --mrap <value> \
    --route-updates <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--mrap` | **Yes** | string | -- | MRAP ARN or alias |
| `--route-updates` | **Yes** | list | -- | Route update entries. Shorthand: `Bucket=string,Region=string,TrafficDialPercentage=integer ...` |

**Output:** None

---

### 4.10 `describe-multi-region-access-point-operation`

Retrieves the status of an asynchronous MRAP operation (create, delete, or policy update).

**Synopsis:**
```bash
aws s3control describe-multi-region-access-point-operation \
    --account-id <value> \
    --request-token-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--request-token-arn` | **Yes** | string | -- | The token ARN from the async operation |

**Output Schema:**
```json
{
    "AsyncOperation": {
        "CreationTime": "timestamp",
        "Operation": "CreateMultiRegionAccessPoint|DeleteMultiRegionAccessPoint|PutMultiRegionAccessPointPolicy",
        "RequestTokenARN": "string",
        "RequestParameters": {
            "CreateMultiRegionAccessPointRequest": {
                "Name": "string",
                "PublicAccessBlock": {},
                "Regions": []
            },
            "DeleteMultiRegionAccessPointRequest": {
                "Name": "string"
            },
            "PutMultiRegionAccessPointPolicyRequest": {
                "Name": "string",
                "Policy": "string"
            }
        },
        "RequestStatus": "string",
        "ResponseDetails": {
            "MultiRegionAccessPointDetails": {
                "Regions": [
                    {
                        "Name": "string",
                        "RequestStatus": "string"
                    }
                ]
            },
            "ErrorDetails": {
                "Code": "string",
                "Message": "string",
                "Resource": "string",
                "RequestId": "string"
            }
        }
    }
}
```
