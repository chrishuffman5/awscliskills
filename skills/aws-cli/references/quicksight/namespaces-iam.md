# Namespaces & IAM

### 12.1 `create-namespace`

Creates a QuickSight namespace for multi-tenancy.

**Synopsis:**
```bash
aws quicksight create-namespace \
    --aws-account-id <value> \
    --namespace <value> \
    --identity-store <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--namespace` | **Yes** | string | -- | Namespace name |
| `--identity-store` | **Yes** | string | -- | `QUICKSIGHT` |
| `--tags` | No | list | None | Resource tags |

**Output Schema:**
```json
{
    "Arn": "string",
    "Name": "string",
    "CapacityRegion": "string",
    "CreationStatus": "CREATED|CREATING|DELETING|RETRYABLE_FAILURE|NON_RETRYABLE_FAILURE",
    "IdentityStore": "QUICKSIGHT",
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 12.2 `describe-namespace`

Describes a namespace.

**Synopsis:**
```bash
aws quicksight describe-namespace \
    --aws-account-id <value> \
    --namespace <value>
```

**Output Schema:**
```json
{
    "Namespace": {
        "Name": "string",
        "Arn": "string",
        "CapacityRegion": "string",
        "CreationStatus": "string",
        "IdentityStore": "QUICKSIGHT",
        "NamespaceError": {
            "Type": "string",
            "Message": "string"
        }
    },
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 12.3 `delete-namespace`

Deletes a namespace.

**Synopsis:**
```bash
aws quicksight delete-namespace \
    --aws-account-id <value> \
    --namespace <value>
```

---

### 12.4 `list-namespaces`

Lists namespaces. **Paginated operation.**

**Synopsis:**
```bash
aws quicksight list-namespaces \
    --aws-account-id <value> \
    [--starting-token <value>] [--page-size <value>] [--max-items <value>]
```

---

### 12.5 `create-iam-policy-assignment`

Creates an IAM policy assignment for a QuickSight group or user.

**Synopsis:**
```bash
aws quicksight create-iam-policy-assignment \
    --aws-account-id <value> \
    --namespace <value> \
    --assignment-name <value> \
    --assignment-status <value> \
    [--policy-arn <value>] \
    [--identities <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--namespace` | **Yes** | string | -- | Namespace |
| `--assignment-name` | **Yes** | string | -- | Assignment name |
| `--assignment-status` | **Yes** | string | -- | `ENABLED`, `DISABLED`, `DRAFT` |
| `--policy-arn` | No | string | None | IAM policy ARN |
| `--identities` | No | map | None | Map of identity type to list of identities |

**Identities Structure:**
```json
{
    "User": ["user1", "user2"],
    "Group": ["group1"]
}
```

**Output Schema:**
```json
{
    "AssignmentName": "string",
    "AssignmentId": "string",
    "AssignmentStatus": "ENABLED|DISABLED|DRAFT",
    "PolicyArn": "string",
    "Identities": {},
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 12.6 `describe-iam-policy-assignment` / `update-iam-policy-assignment` / `delete-iam-policy-assignment`

Manage IAM policy assignments.

**Synopsis:**
```bash
aws quicksight describe-iam-policy-assignment \
    --aws-account-id <value> --namespace <value> --assignment-name <value>

aws quicksight update-iam-policy-assignment \
    --aws-account-id <value> --namespace <value> --assignment-name <value> \
    [--assignment-status <value>] [--policy-arn <value>] [--identities <value>]

aws quicksight delete-iam-policy-assignment \
    --aws-account-id <value> --namespace <value> --assignment-name <value>
```

---

### 12.7 `list-iam-policy-assignments` / `list-iam-policy-assignments-for-user`

List IAM policy assignments. **Paginated operations.**

**Synopsis:**
```bash
aws quicksight list-iam-policy-assignments \
    --aws-account-id <value> --namespace <value> [--assignment-status <value>]

aws quicksight list-iam-policy-assignments-for-user \
    --aws-account-id <value> --namespace <value> --user-name <value>
```

---

### 12.8 `create-role-membership` / `delete-role-membership` / `list-role-memberships`

Manage QuickSight role memberships (mapping groups to QuickSight roles).

**Synopsis:**
```bash
aws quicksight create-role-membership \
    --aws-account-id <value> --namespace <value> \
    --role <value> --member-name <value>

aws quicksight delete-role-membership \
    --aws-account-id <value> --namespace <value> \
    --role <value> --member-name <value>

aws quicksight list-role-memberships \
    --aws-account-id <value> --namespace <value> --role <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--role` | **Yes** | string | -- | `ADMIN`, `AUTHOR`, `READER`, `ADMIN_PRO`, `AUTHOR_PRO`, `READER_PRO` |
| `--member-name` | **Yes** | string | -- | Group name to map to the role |
