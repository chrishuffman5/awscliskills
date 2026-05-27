# Instances

### 1.1 `create-instance`

Creates an IAM Identity Center instance.

**Synopsis:**
```bash
aws sso-admin create-instance \
    [--name <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | No | string | None | Name of the instance (1-32 chars) |
| `--client-token` | No | string | None | Idempotency token |
| `--tags` | No | list(structure) | None | Tags (max 75). Structure: `Key=string,Value=string` |

**Output Schema:**
```json
{
    "InstanceArn": "string"
}
```

---

### 1.2 `delete-instance`

Deletes an IAM Identity Center instance.

**Synopsis:**
```bash
aws sso-admin delete-instance \
    --instance-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the instance to delete |

**Output Schema:**

No output on success (HTTP 200).

---

### 1.3 `describe-instance`

Describes an IAM Identity Center instance.

**Synopsis:**
```bash
aws sso-admin describe-instance \
    --instance-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |

**Output Schema:**
```json
{
    "InstanceArn": "string",
    "IdentityStoreId": "string",
    "OwnerAccountId": "string",
    "Name": "string",
    "CreatedDate": "timestamp",
    "Status": "CREATE_IN_PROGRESS|DELETE_IN_PROGRESS|ACTIVE"
}
```

---

### 1.4 `list-instances`

Lists all IAM Identity Center instances. **Paginated operation.**

**Synopsis:**
```bash
aws sso-admin list-instances \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Instances": [
        {
            "InstanceArn": "string",
            "IdentityStoreId": "string",
            "OwnerAccountId": "string",
            "Name": "string",
            "CreatedDate": "timestamp",
            "Status": "CREATE_IN_PROGRESS|DELETE_IN_PROGRESS|ACTIVE"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `update-instance`

Updates an IAM Identity Center instance name.

**Synopsis:**
```bash
aws sso-admin update-instance \
    --instance-arn <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |
| `--name` | **Yes** | string | -- | New name for the instance |

**Output Schema:**

No output on success (HTTP 200).

---

### 1.6 `create-instance-access-control-attribute-configuration`

Enables attribute-based access control (ABAC) for the specified instance.

**Synopsis:**
```bash
aws sso-admin create-instance-access-control-attribute-configuration \
    --instance-arn <value> \
    --instance-access-control-attribute-configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |
| `--instance-access-control-attribute-configuration` | **Yes** | structure | -- | ABAC attribute configuration |

**Configuration Structure:**
```json
{
    "AccessControlAttributes": [
        {
            "Key": "string",
            "Value": {
                "Source": ["string"]
            }
        }
    ]
}
```

**Output Schema:**

No output on success (HTTP 200).

---

### 1.7 `delete-instance-access-control-attribute-configuration`

Disables ABAC for the specified instance.

**Synopsis:**
```bash
aws sso-admin delete-instance-access-control-attribute-configuration \
    --instance-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |

**Output Schema:**

No output on success (HTTP 200).

---

### 1.8 `describe-instance-access-control-attribute-configuration`

Describes the ABAC configuration for the specified instance.

**Synopsis:**
```bash
aws sso-admin describe-instance-access-control-attribute-configuration \
    --instance-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |

**Output Schema:**
```json
{
    "Status": "ENABLED|CREATION_IN_PROGRESS|CREATION_FAILED",
    "StatusReason": "string",
    "InstanceAccessControlAttributeConfiguration": {
        "AccessControlAttributes": [
            {
                "Key": "string",
                "Value": {
                    "Source": ["string"]
                }
            }
        ]
    }
}
```

---

### 1.9 `update-instance-access-control-attribute-configuration`

Updates the ABAC configuration for the specified instance.

**Synopsis:**
```bash
aws sso-admin update-instance-access-control-attribute-configuration \
    --instance-arn <value> \
    --instance-access-control-attribute-configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |
| `--instance-access-control-attribute-configuration` | **Yes** | structure | -- | Updated ABAC configuration |

**Output Schema:**

No output on success (HTTP 200).

---

### 1.10 `add-region`

Adds a region to an IAM Identity Center instance for multi-region support.

**Synopsis:**
```bash
aws sso-admin add-region \
    --instance-arn <value> \
    --region-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |
| `--region-name` | **Yes** | string | -- | AWS region to add |

**Output Schema:**

No output on success (HTTP 200).

---

### 1.11 `remove-region`

Removes a region from an IAM Identity Center instance.

**Synopsis:**
```bash
aws sso-admin remove-region \
    --instance-arn <value> \
    --region-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |
| `--region-name` | **Yes** | string | -- | AWS region to remove |

**Output Schema:**

No output on success (HTTP 200).

---

### 1.12 `describe-region`

Describes a region configuration for an IAM Identity Center instance.

**Synopsis:**
```bash
aws sso-admin describe-region \
    --instance-arn <value> \
    --region-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |
| `--region-name` | **Yes** | string | -- | AWS region to describe |

**Output Schema:**
```json
{
    "RegionName": "string",
    "Status": "ENABLED|ENABLING|DISABLED|DISABLING"
}
```

---

### 1.13 `list-regions`

Lists regions configured for an IAM Identity Center instance. **Paginated operation.**

**Synopsis:**
```bash
aws sso-admin list-regions \
    --instance-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Regions": [
        {
            "RegionName": "string",
            "Status": "ENABLED|ENABLING|DISABLED|DISABLING"
        }
    ],
    "NextToken": "string"
}
```
