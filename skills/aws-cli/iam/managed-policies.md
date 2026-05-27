# Managed Policies

### 4.1 `create-policy`

Creates a new managed policy.

**Synopsis:**
```bash
aws iam create-policy \
    --policy-name <value> \
    --policy-document <value> \
    [--path <value>] \
    [--description <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-name` | **Yes** | string | -- | Policy name (1-128 chars). Pattern: `[\w+=,.@-]+` |
| `--policy-document` | **Yes** | string | -- | Policy JSON (max 131072 chars). Use `file://` for file input |
| `--path` | No | string | `/` | Path prefix (1-512 chars) |
| `--description` | No | string | None | Description (max 1000 chars). Immutable after creation |
| `--tags` | No | list | None | Tags (max 50) |

**Output Schema:**
```json
{
    "Policy": {
        "PolicyName": "string",
        "PolicyId": "string",
        "Arn": "string",
        "Path": "string",
        "DefaultVersionId": "string",
        "AttachmentCount": integer,
        "PermissionsBoundaryUsageCount": integer,
        "IsAttachable": true|false,
        "Description": "string",
        "CreateDate": "timestamp",
        "UpdateDate": "timestamp",
        "Tags": [{ "Key": "string", "Value": "string" }]
    }
}
```

---

### 4.2 `get-policy`

Retrieves metadata about a managed policy (not the policy document).

**Synopsis:**
```bash
aws iam get-policy --policy-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-arn` | **Yes** | string | -- | ARN of the policy (20-2048 chars) |

**Output Schema:**
```json
{
    "Policy": {
        "PolicyName": "string",
        "PolicyId": "string",
        "Arn": "string",
        "Path": "string",
        "DefaultVersionId": "string",
        "AttachmentCount": integer,
        "PermissionsBoundaryUsageCount": integer,
        "IsAttachable": true|false,
        "Description": "string",
        "CreateDate": "timestamp",
        "UpdateDate": "timestamp",
        "Tags": [{ "Key": "string", "Value": "string" }]
    }
}
```

---

### 4.3 `list-policies`

Lists all managed policies. **Paginated.**

**Synopsis:**
```bash
aws iam list-policies \
    [--scope <value>] \
    [--only-attached | --no-only-attached] \
    [--path-prefix <value>] \
    [--policy-usage-filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scope` | No | string | `All` | `All`, `AWS` (AWS-managed), or `Local` (customer-managed) |
| `--only-attached` | No | boolean | false | Show only attached policies |
| `--path-prefix` | No | string | `/` | Filter by path prefix |
| `--policy-usage-filter` | No | string | None | `PermissionsPolicy` or `PermissionsBoundary` |

**Output Schema:**
```json
{
    "Policies": [
        {
            "PolicyName": "string",
            "PolicyId": "string",
            "Arn": "string",
            "Path": "string",
            "DefaultVersionId": "string",
            "AttachmentCount": integer,
            "PermissionsBoundaryUsageCount": integer,
            "IsAttachable": true|false,
            "Description": "string",
            "CreateDate": "timestamp",
            "UpdateDate": "timestamp"
        }
    ],
    "IsTruncated": true|false,
    "Marker": "string"
}
```

---

### 4.4 `create-policy-version`

Creates a new version of a managed policy. Max 5 versions per policy.

**Synopsis:**
```bash
aws iam create-policy-version \
    --policy-arn <value> \
    --policy-document <value> \
    [--set-as-default | --no-set-as-default]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-arn` | **Yes** | string | -- | ARN of the policy |
| `--policy-document` | **Yes** | string | -- | New policy JSON. Use `file://` for file input |
| `--set-as-default` | No | boolean | true | Set as the default version |

**Output Schema:**
```json
{
    "PolicyVersion": {
        "Document": "string",
        "VersionId": "string",
        "IsDefaultVersion": true|false,
        "CreateDate": "timestamp"
    }
}
```

---

### 4.5 `get-policy-version`

Retrieves the policy document for a specific version.

**Synopsis:**
```bash
aws iam get-policy-version --policy-arn <value> --version-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-arn` | **Yes** | string | -- | ARN of the policy |
| `--version-id` | **Yes** | string | -- | Version ID (e.g., `v1`, `v2`) |

**Output Schema:**
```json
{
    "PolicyVersion": {
        "Document": "string (URL-encoded JSON)",
        "VersionId": "string",
        "IsDefaultVersion": true|false,
        "CreateDate": "timestamp"
    }
}
```

---

### 4.6 `list-policy-versions`

Lists versions of a managed policy. **Paginated.**

**Synopsis:**
```bash
aws iam list-policy-versions --policy-arn <value> [--starting-token <value>] [--max-items <value>]
```

**Output Schema:**
```json
{
    "Versions": [
        {
            "Document": "string",
            "VersionId": "string",
            "IsDefaultVersion": true|false,
            "CreateDate": "timestamp"
        }
    ],
    "IsTruncated": true|false,
    "Marker": "string"
}
```

---

### 4.7 `set-default-policy-version`

Sets the specified version as the default (active) version.

**Synopsis:**
```bash
aws iam set-default-policy-version --policy-arn <value> --version-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-arn` | **Yes** | string | -- | ARN of the policy |
| `--version-id` | **Yes** | string | -- | Version to set as default |

**Output:** None on success.

---

### 4.8 `delete-policy-version`

Deletes a policy version. Cannot delete the default version.

**Synopsis:**
```bash
aws iam delete-policy-version --policy-arn <value> --version-id <value>
```

**Output:** None on success.

---

### 4.9 `delete-policy`

Deletes a managed policy. Must detach from all entities and delete all non-default versions first.

**Synopsis:**
```bash
aws iam delete-policy --policy-arn <value>
```

**Output:** None on success.

---
