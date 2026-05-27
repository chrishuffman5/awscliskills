# Account Assignments

### 4.1 `create-account-assignment`

Assigns a user or group access to a specified AWS account using a permission set.

**Synopsis:**
```bash
aws sso-admin create-account-assignment \
    --instance-arn <value> \
    --target-id <value> \
    --target-type <value> \
    --permission-set-arn <value> \
    --principal-type <value> \
    --principal-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the Identity Center instance |
| `--target-id` | **Yes** | string | -- | AWS account ID (12 digits) |
| `--target-type` | **Yes** | string | -- | `AWS_ACCOUNT` |
| `--permission-set-arn` | **Yes** | string | -- | ARN of the permission set |
| `--principal-type` | **Yes** | string | -- | `USER` or `GROUP` |
| `--principal-id` | **Yes** | string | -- | GUID of the user or group in Identity Center |

**Output Schema:**
```json
{
    "AccountAssignmentCreationStatus": {
        "Status": "IN_PROGRESS|FAILED|SUCCEEDED",
        "RequestId": "string",
        "FailureReason": "string",
        "TargetId": "string",
        "TargetType": "AWS_ACCOUNT",
        "PermissionSetArn": "string",
        "PrincipalType": "USER|GROUP",
        "PrincipalId": "string",
        "CreatedDate": "timestamp"
    }
}
```

---

### 4.2 `delete-account-assignment`

Deletes a user or group access assignment from a specified AWS account.

**Synopsis:**
```bash
aws sso-admin delete-account-assignment \
    --instance-arn <value> \
    --target-id <value> \
    --target-type <value> \
    --permission-set-arn <value> \
    --principal-type <value> \
    --principal-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |
| `--target-id` | **Yes** | string | -- | AWS account ID |
| `--target-type` | **Yes** | string | -- | `AWS_ACCOUNT` |
| `--permission-set-arn` | **Yes** | string | -- | ARN of the permission set |
| `--principal-type` | **Yes** | string | -- | `USER` or `GROUP` |
| `--principal-id` | **Yes** | string | -- | GUID of the user or group |

**Output Schema:**
```json
{
    "AccountAssignmentDeletionStatus": {
        "Status": "IN_PROGRESS|FAILED|SUCCEEDED",
        "RequestId": "string",
        "FailureReason": "string",
        "TargetId": "string",
        "TargetType": "AWS_ACCOUNT",
        "PermissionSetArn": "string",
        "PrincipalType": "USER|GROUP",
        "PrincipalId": "string",
        "CreatedDate": "timestamp"
    }
}
```

---

### 4.3 `list-account-assignments`

Lists the assignments for a specified permission set and account. **Paginated operation.**

**Synopsis:**
```bash
aws sso-admin list-account-assignments \
    --instance-arn <value> \
    --account-id <value> \
    --permission-set-arn <value> \
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
| `--account-id` | **Yes** | string | -- | AWS account ID |
| `--permission-set-arn` | **Yes** | string | -- | ARN of the permission set |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AccountAssignments": [
        {
            "AccountId": "string",
            "PermissionSetArn": "string",
            "PrincipalType": "USER|GROUP",
            "PrincipalId": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.4 `list-account-assignments-for-principal`

Lists all account assignments for a specific user or group. **Paginated operation.**

**Synopsis:**
```bash
aws sso-admin list-account-assignments-for-principal \
    --instance-arn <value> \
    --principal-id <value> \
    --principal-type <value> \
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
| `--principal-id` | **Yes** | string | -- | GUID of the user or group |
| `--principal-type` | **Yes** | string | -- | `USER` or `GROUP` |
| `--filter` | No | structure | None | Filter by account ID. Structure: `AccountId=string` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AccountAssignments": [
        {
            "AccountId": "string",
            "PermissionSetArn": "string",
            "PrincipalId": "string",
            "PrincipalType": "USER|GROUP"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.5 `describe-account-assignment-creation-status`

Describes the status of an account assignment creation request.

**Synopsis:**
```bash
aws sso-admin describe-account-assignment-creation-status \
    --instance-arn <value> \
    --account-assignment-creation-request-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |
| `--account-assignment-creation-request-id` | **Yes** | string | -- | Request ID from the create call |

**Output Schema:**
```json
{
    "AccountAssignmentCreationStatus": {
        "Status": "IN_PROGRESS|FAILED|SUCCEEDED",
        "RequestId": "string",
        "FailureReason": "string",
        "TargetId": "string",
        "TargetType": "AWS_ACCOUNT",
        "PermissionSetArn": "string",
        "PrincipalType": "USER|GROUP",
        "PrincipalId": "string",
        "CreatedDate": "timestamp"
    }
}
```

---

### 4.6 `list-account-assignment-creation-status`

Lists the creation statuses for account assignments. **Paginated operation.**

**Synopsis:**
```bash
aws sso-admin list-account-assignment-creation-status \
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
    "AccountAssignmentsCreationStatus": [
        {
            "Status": "IN_PROGRESS|FAILED|SUCCEEDED",
            "RequestId": "string",
            "CreatedDate": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.7 `describe-account-assignment-deletion-status`

Describes the status of an account assignment deletion request.

**Synopsis:**
```bash
aws sso-admin describe-account-assignment-deletion-status \
    --instance-arn <value> \
    --account-assignment-deletion-request-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |
| `--account-assignment-deletion-request-id` | **Yes** | string | -- | Request ID from the delete call |

**Output Schema:**
```json
{
    "AccountAssignmentDeletionStatus": {
        "Status": "IN_PROGRESS|FAILED|SUCCEEDED",
        "RequestId": "string",
        "FailureReason": "string",
        "TargetId": "string",
        "TargetType": "AWS_ACCOUNT",
        "PermissionSetArn": "string",
        "PrincipalType": "USER|GROUP",
        "PrincipalId": "string",
        "CreatedDate": "timestamp"
    }
}
```

---

### 4.8 `list-account-assignment-deletion-status`

Lists the deletion statuses for account assignments. **Paginated operation.**

**Synopsis:**
```bash
aws sso-admin list-account-assignment-deletion-status \
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
| `--filter` | No | structure | None | Filter by status |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AccountAssignmentsDeletionStatus": [
        {
            "Status": "IN_PROGRESS|FAILED|SUCCEEDED",
            "RequestId": "string",
            "CreatedDate": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
