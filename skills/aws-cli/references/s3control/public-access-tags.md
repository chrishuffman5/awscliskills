# Public Access & Tags

### 8.1 `put-public-access-block`

Creates or modifies the `PublicAccessBlock` configuration for an AWS account. This applies to all S3 buckets in the account.

**Synopsis:**
```bash
aws s3control put-public-access-block \
    --public-access-block-configuration <value> \
    --account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--public-access-block-configuration` | **Yes** | structure | -- | Public access block settings |
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |

**PublicAccessBlockConfiguration Structure:**
```json
{
    "BlockPublicAcls": true|false,
    "IgnorePublicAcls": true|false,
    "BlockPublicPolicy": true|false,
    "RestrictPublicBuckets": true|false
}
```

| Setting | Description |
|---------|-------------|
| `BlockPublicAcls` | Reject PUT requests that include a public ACL and reject PUT Object calls with public ACLs |
| `IgnorePublicAcls` | Ignore all public ACLs on buckets and objects |
| `BlockPublicPolicy` | Reject PUT bucket policy calls if the policy grants public access |
| `RestrictPublicBuckets` | Restrict access to buckets with public policies to AWS service principals and authorized users only |

**Shorthand:**
```bash
--public-access-block-configuration \
  BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=true,RestrictPublicBuckets=true
```

**Output:** None

---

### 8.2 `get-public-access-block`

Retrieves the `PublicAccessBlock` configuration for an AWS account.

**Synopsis:**
```bash
aws s3control get-public-access-block \
    --account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |

**Output Schema:**
```json
{
    "PublicAccessBlockConfiguration": {
        "BlockPublicAcls": true|false,
        "IgnorePublicAcls": true|false,
        "BlockPublicPolicy": true|false,
        "RestrictPublicBuckets": true|false
    }
}
```

---

### 8.3 `delete-public-access-block`

Removes the `PublicAccessBlock` configuration for an AWS account.

**Synopsis:**
```bash
aws s3control delete-public-access-block \
    --account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |

**Output:** None

---

### 8.4 `tag-resource`

Adds tags to an S3 Control resource (Access Grants instance, location, grant, Storage Lens group, or job).

**Synopsis:**
```bash
aws s3control tag-resource \
    --account-id <value> \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | list | -- | Tags to add. Shorthand: `Key=string,Value=string ...` |

**Output:** None

---

### 8.5 `untag-resource`

Removes tags from an S3 Control resource.

**Synopsis:**
```bash
aws s3control untag-resource \
    --account-id <value> \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output:** None

---

### 8.6 `list-tags-for-resource`

Returns the tags on an S3 Control resource.

**Synopsis:**
```bash
aws s3control list-tags-for-resource \
    --account-id <value> \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |

**Output Schema:**
```json
{
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```
