# Permission Sets

### 2.1 `create-permission-set`

Creates a permission set within a specified IAM Identity Center instance.

**Synopsis:**
```bash
aws sso-admin create-permission-set \
    --instance-arn <value> \
    --name <value> \
    [--description <value>] \
    [--session-duration <value>] \
    [--relay-state <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the Identity Center instance |
| `--name` | **Yes** | string | -- | Permission set name (1-32 chars) |
| `--description` | No | string | None | Description (max 700 chars) |
| `--session-duration` | No | string | None | Session length in ISO-8601 format (e.g., `PT8H`) |
| `--relay-state` | No | string | None | Redirect URL for federation (max 240 chars) |
| `--tags` | No | list(structure) | None | Tags (max 75). Structure: `Key=string,Value=string` |

**Output Schema:**
```json
{
    "PermissionSet": {
        "Name": "string",
        "PermissionSetArn": "string",
        "Description": "string",
        "CreatedDate": "timestamp",
        "SessionDuration": "string",
        "RelayState": "string"
    }
}
```

---

### 2.2 `delete-permission-set`

Deletes the specified permission set.

**Synopsis:**
```bash
aws sso-admin delete-permission-set \
    --instance-arn <value> \
    --permission-set-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |
| `--permission-set-arn` | **Yes** | string | -- | ARN of the permission set to delete |

**Output Schema:**

No output on success (HTTP 200).

---

### 2.3 `describe-permission-set`

Gets the details of a permission set.

**Synopsis:**
```bash
aws sso-admin describe-permission-set \
    --instance-arn <value> \
    --permission-set-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |
| `--permission-set-arn` | **Yes** | string | -- | ARN of the permission set |

**Output Schema:**
```json
{
    "PermissionSet": {
        "Name": "string",
        "PermissionSetArn": "string",
        "Description": "string",
        "CreatedDate": "timestamp",
        "SessionDuration": "string",
        "RelayState": "string"
    }
}
```

---

### 2.4 `update-permission-set`

Updates an existing permission set.

**Synopsis:**
```bash
aws sso-admin update-permission-set \
    --instance-arn <value> \
    --permission-set-arn <value> \
    [--description <value>] \
    [--session-duration <value>] \
    [--relay-state <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |
| `--permission-set-arn` | **Yes** | string | -- | ARN of the permission set |
| `--description` | No | string | None | Updated description |
| `--session-duration` | No | string | None | Updated session duration |
| `--relay-state` | No | string | None | Updated relay state URL |

**Output Schema:**

No output on success (HTTP 200).

---

### 2.5 `list-permission-sets`

Lists all permission sets for an instance. **Paginated operation.**

**Synopsis:**
```bash
aws sso-admin list-permission-sets \
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
    "PermissionSets": ["string"],
    "NextToken": "string"
}
```

---

### 2.6 `list-permission-sets-provisioned-to-account`

Lists all permission sets provisioned to a specified AWS account. **Paginated operation.**

**Synopsis:**
```bash
aws sso-admin list-permission-sets-provisioned-to-account \
    --instance-arn <value> \
    --account-id <value> \
    [--provisioning-status <value>] \
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
| `--account-id` | **Yes** | string | -- | AWS account ID (12 digits) |
| `--provisioning-status` | No | string | None | Filter: `LATEST_PERMISSION_SET_PROVISIONED`, `LATEST_PERMISSION_SET_NOT_PROVISIONED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "PermissionSets": ["string"],
    "NextToken": "string"
}
```

---

### 2.7 `list-accounts-for-provisioned-permission-set`

Lists all accounts where the specified permission set is provisioned. **Paginated operation.**

**Synopsis:**
```bash
aws sso-admin list-accounts-for-provisioned-permission-set \
    --instance-arn <value> \
    --permission-set-arn <value> \
    [--provisioning-status <value>] \
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
| `--permission-set-arn` | **Yes** | string | -- | ARN of the permission set |
| `--provisioning-status` | No | string | None | Filter by provisioning status |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AccountIds": ["string"],
    "NextToken": "string"
}
```

---

### 2.8 `provision-permission-set`

Provisions a permission set to specified target accounts.

**Synopsis:**
```bash
aws sso-admin provision-permission-set \
    --instance-arn <value> \
    --permission-set-arn <value> \
    --target-type <value> \
    [--target-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |
| `--permission-set-arn` | **Yes** | string | -- | ARN of the permission set |
| `--target-type` | **Yes** | string | -- | `AWS_ACCOUNT` or `ALL_PROVISIONED_ACCOUNTS` |
| `--target-id` | No | string | None | AWS account ID (required if target-type is `AWS_ACCOUNT`) |

**Output Schema:**
```json
{
    "PermissionSetProvisioningStatus": {
        "Status": "IN_PROGRESS|FAILED|SUCCEEDED",
        "RequestId": "string",
        "AccountId": "string",
        "PermissionSetArn": "string",
        "FailureReason": "string",
        "CreatedDate": "timestamp"
    }
}
```

---

### 2.9 `describe-permission-set-provisioning-status`

Describes the status of a permission set provisioning request.

**Synopsis:**
```bash
aws sso-admin describe-permission-set-provisioning-status \
    --instance-arn <value> \
    --provision-permission-set-request-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |
| `--provision-permission-set-request-id` | **Yes** | string | -- | Request ID from the provision call |

**Output Schema:**
```json
{
    "PermissionSetProvisioningStatus": {
        "Status": "IN_PROGRESS|FAILED|SUCCEEDED",
        "RequestId": "string",
        "AccountId": "string",
        "PermissionSetArn": "string",
        "FailureReason": "string",
        "CreatedDate": "timestamp"
    }
}
```

---

### 2.10 `list-permission-set-provisioning-status`

Lists the status of permission set provisioning requests. **Paginated operation.**

**Synopsis:**
```bash
aws sso-admin list-permission-set-provisioning-status \
    --instance-arn <value> \
    [--filter <value>] \
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
| `--filter` | No | structure | None | Filter by status. Structure: `Status=IN_PROGRESS\|FAILED\|SUCCEEDED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "PermissionSetsProvisioningStatus": [
        {
            "Status": "IN_PROGRESS|FAILED|SUCCEEDED",
            "RequestId": "string",
            "CreatedDate": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
