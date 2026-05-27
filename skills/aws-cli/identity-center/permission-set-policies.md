# Permission Set Policies

### 3.1 `attach-managed-policy-to-permission-set`

Attaches an AWS managed policy to a permission set.

**Synopsis:**
```bash
aws sso-admin attach-managed-policy-to-permission-set \
    --instance-arn <value> \
    --permission-set-arn <value> \
    --managed-policy-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |
| `--permission-set-arn` | **Yes** | string | -- | ARN of the permission set |
| `--managed-policy-arn` | **Yes** | string | -- | ARN of the AWS managed policy |

**Output Schema:**

No output on success (HTTP 200).

---

### 3.2 `detach-managed-policy-from-permission-set`

Detaches an AWS managed policy from a permission set.

**Synopsis:**
```bash
aws sso-admin detach-managed-policy-from-permission-set \
    --instance-arn <value> \
    --permission-set-arn <value> \
    --managed-policy-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |
| `--permission-set-arn` | **Yes** | string | -- | ARN of the permission set |
| `--managed-policy-arn` | **Yes** | string | -- | ARN of the managed policy to detach |

**Output Schema:**

No output on success (HTTP 200).

---

### 3.3 `list-managed-policies-in-permission-set`

Lists all AWS managed policies attached to a permission set. **Paginated operation.**

**Synopsis:**
```bash
aws sso-admin list-managed-policies-in-permission-set \
    --instance-arn <value> \
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
| `--permission-set-arn` | **Yes** | string | -- | ARN of the permission set |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AttachedManagedPolicies": [
        {
            "Name": "string",
            "Arn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.4 `attach-customer-managed-policy-reference-to-permission-set`

Attaches a customer-managed IAM policy to a permission set.

**Synopsis:**
```bash
aws sso-admin attach-customer-managed-policy-reference-to-permission-set \
    --instance-arn <value> \
    --permission-set-arn <value> \
    --customer-managed-policy-reference <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |
| `--permission-set-arn` | **Yes** | string | -- | ARN of the permission set |
| `--customer-managed-policy-reference` | **Yes** | structure | -- | Policy reference. Structure: `Name=string,Path=string` |

**Output Schema:**

No output on success (HTTP 200).

---

### 3.5 `detach-customer-managed-policy-reference-from-permission-set`

Detaches a customer-managed IAM policy from a permission set.

**Synopsis:**
```bash
aws sso-admin detach-customer-managed-policy-reference-from-permission-set \
    --instance-arn <value> \
    --permission-set-arn <value> \
    --customer-managed-policy-reference <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |
| `--permission-set-arn` | **Yes** | string | -- | ARN of the permission set |
| `--customer-managed-policy-reference` | **Yes** | structure | -- | Policy reference to detach |

**Output Schema:**

No output on success (HTTP 200).

---

### 3.6 `list-customer-managed-policy-references-in-permission-set`

Lists all customer-managed policies attached to a permission set. **Paginated operation.**

**Synopsis:**
```bash
aws sso-admin list-customer-managed-policy-references-in-permission-set \
    --instance-arn <value> \
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
| `--permission-set-arn` | **Yes** | string | -- | ARN of the permission set |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CustomerManagedPolicyReferences": [
        {
            "Name": "string",
            "Path": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.7 `put-inline-policy-to-permission-set`

Adds an inline IAM policy to a permission set. Replaces any existing inline policy.

**Synopsis:**
```bash
aws sso-admin put-inline-policy-to-permission-set \
    --instance-arn <value> \
    --permission-set-arn <value> \
    --inline-policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |
| `--permission-set-arn` | **Yes** | string | -- | ARN of the permission set |
| `--inline-policy` | **Yes** | string | -- | JSON IAM policy document |

**Output Schema:**

No output on success (HTTP 200).

---

### 3.8 `get-inline-policy-for-permission-set`

Gets the inline IAM policy attached to a permission set.

**Synopsis:**
```bash
aws sso-admin get-inline-policy-for-permission-set \
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
    "InlinePolicy": "string"
}
```

---

### 3.9 `delete-inline-policy-from-permission-set`

Deletes the inline IAM policy from a permission set.

**Synopsis:**
```bash
aws sso-admin delete-inline-policy-from-permission-set \
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

No output on success (HTTP 200).

---

### 3.10 `put-permissions-boundary-to-permission-set`

Adds a permissions boundary to a permission set.

**Synopsis:**
```bash
aws sso-admin put-permissions-boundary-to-permission-set \
    --instance-arn <value> \
    --permission-set-arn <value> \
    --permissions-boundary <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |
| `--permission-set-arn` | **Yes** | string | -- | ARN of the permission set |
| `--permissions-boundary` | **Yes** | structure | -- | Boundary config: `CustomerManagedPolicyReference={Name=string,Path=string}` or `ManagedPolicyArn=string` |

**Output Schema:**

No output on success (HTTP 200).

---

### 3.11 `get-permissions-boundary-for-permission-set`

Gets the permissions boundary for a permission set.

**Synopsis:**
```bash
aws sso-admin get-permissions-boundary-for-permission-set \
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
    "PermissionsBoundary": {
        "CustomerManagedPolicyReference": {
            "Name": "string",
            "Path": "string"
        },
        "ManagedPolicyArn": "string"
    }
}
```

---

### 3.12 `delete-permissions-boundary-from-permission-set`

Deletes the permissions boundary from a permission set.

**Synopsis:**
```bash
aws sso-admin delete-permissions-boundary-from-permission-set \
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

No output on success (HTTP 200).
