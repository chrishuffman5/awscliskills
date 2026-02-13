# Object Lambda

### 2.1 `create-access-point-for-object-lambda`

Creates an Object Lambda Access Point. Object Lambda Access Points allow you to transform data as it is retrieved from S3 using AWS Lambda functions.

**Synopsis:**
```bash
aws s3control create-access-point-for-object-lambda \
    --account-id <value> \
    --name <value> \
    --configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--name` | **Yes** | string | -- | Object Lambda Access Point name (3-45 chars) |
| `--configuration` | **Yes** | structure | -- | Object Lambda configuration |

**Configuration Structure:**
```json
{
    "SupportingAccessPoint": "string",
    "CloudWatchMetricsEnabled": true|false,
    "AllowedFeatures": ["GetObject-Range", "GetObject-PartNumber", "HeadObject-Range", "HeadObject-PartNumber"],
    "TransformationConfigurations": [
        {
            "Actions": ["GetObject", "HeadObject", "ListObjects", "ListObjectsV2"],
            "ContentTransformation": {
                "AwsLambda": {
                    "FunctionArn": "string",
                    "FunctionPayload": "string"
                }
            }
        }
    ]
}
```

**Output Schema:**
```json
{
    "ObjectLambdaAccessPointArn": "string"
}
```

---

### 2.2 `delete-access-point-for-object-lambda`

Deletes the specified Object Lambda Access Point.

**Synopsis:**
```bash
aws s3control delete-access-point-for-object-lambda \
    --account-id <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--name` | **Yes** | string | -- | Object Lambda Access Point name |

**Output:** None

---

### 2.3 `get-access-point-for-object-lambda`

Returns configuration information about the specified Object Lambda Access Point.

**Synopsis:**
```bash
aws s3control get-access-point-for-object-lambda \
    --account-id <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--name` | **Yes** | string | -- | Object Lambda Access Point name |

**Output Schema:**
```json
{
    "Name": "string",
    "PublicAccessBlockConfiguration": {
        "BlockPublicAcls": true|false,
        "IgnorePublicAcls": true|false,
        "BlockPublicPolicy": true|false,
        "RestrictPublicBuckets": true|false
    },
    "CreationDate": "timestamp",
    "Alias": {
        "Value": "string",
        "Status": "PROVISIONING|READY"
    }
}
```

---

### 2.4 `list-access-points-for-object-lambda`

Returns a list of Object Lambda Access Points for the specified account. **Paginated.**

**Synopsis:**
```bash
aws s3control list-access-points-for-object-lambda \
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
| `--page-size` | No | integer | None | Items per API call (max 1000) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ObjectLambdaAccessPointList": [
        {
            "Name": "string",
            "ObjectLambdaAccessPointArn": "string",
            "Alias": {
                "Value": "string",
                "Status": "PROVISIONING|READY"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 2.5 `put-access-point-configuration-for-object-lambda`

Sets the configuration for an Object Lambda Access Point.

**Synopsis:**
```bash
aws s3control put-access-point-configuration-for-object-lambda \
    --account-id <value> \
    --name <value> \
    --configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--name` | **Yes** | string | -- | Object Lambda Access Point name |
| `--configuration` | **Yes** | structure | -- | Object Lambda configuration (same structure as create) |

**Output:** None

---

### 2.6 `get-access-point-configuration-for-object-lambda`

Returns the configuration for an Object Lambda Access Point.

**Synopsis:**
```bash
aws s3control get-access-point-configuration-for-object-lambda \
    --account-id <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--name` | **Yes** | string | -- | Object Lambda Access Point name |

**Output Schema:**
```json
{
    "Configuration": {
        "SupportingAccessPoint": "string",
        "CloudWatchMetricsEnabled": true|false,
        "AllowedFeatures": ["GetObject-Range", "GetObject-PartNumber", "HeadObject-Range", "HeadObject-PartNumber"],
        "TransformationConfigurations": [
            {
                "Actions": ["GetObject", "HeadObject", "ListObjects", "ListObjectsV2"],
                "ContentTransformation": {
                    "AwsLambda": {
                        "FunctionArn": "string",
                        "FunctionPayload": "string"
                    }
                }
            }
        ]
    }
}
```

---

### 2.7 `put-access-point-policy-for-object-lambda`

Sets a policy for an Object Lambda Access Point.

**Synopsis:**
```bash
aws s3control put-access-point-policy-for-object-lambda \
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
| `--name` | **Yes** | string | -- | Object Lambda Access Point name |
| `--policy` | **Yes** | string | -- | JSON policy document |

**Output:** None

---

### 2.8 `get-access-point-policy-for-object-lambda`

Returns the policy for an Object Lambda Access Point.

**Synopsis:**
```bash
aws s3control get-access-point-policy-for-object-lambda \
    --account-id <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--name` | **Yes** | string | -- | Object Lambda Access Point name |

**Output Schema:**
```json
{
    "Policy": "string"
}
```

---

### 2.9 `delete-access-point-policy-for-object-lambda`

Removes the policy from an Object Lambda Access Point.

**Synopsis:**
```bash
aws s3control delete-access-point-policy-for-object-lambda \
    --account-id <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--name` | **Yes** | string | -- | Object Lambda Access Point name |

**Output:** None

---

### 2.10 `get-access-point-policy-status-for-object-lambda`

Returns the policy status for an Object Lambda Access Point policy.

**Synopsis:**
```bash
aws s3control get-access-point-policy-status-for-object-lambda \
    --account-id <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--name` | **Yes** | string | -- | Object Lambda Access Point name |

**Output Schema:**
```json
{
    "PolicyStatus": {
        "IsPublic": true|false
    }
}
```
