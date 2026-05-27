# Policies

### 4.1 `create-policy`

Creates a policy of a specified type in the organization.

**Synopsis:**
```bash
aws organizations create-policy \
    --content <value> \
    --description <value> \
    --name <value> \
    --type <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--content` | **Yes** | string | -- | Policy content (JSON string or `file://` path) |
| `--description` | **Yes** | string | -- | Description of the policy |
| `--name` | **Yes** | string | -- | Friendly name for the policy |
| `--type` | **Yes** | string | -- | Policy type: `SERVICE_CONTROL_POLICY`, `TAG_POLICY`, `BACKUP_POLICY`, `AISERVICES_OPT_OUT_POLICY` |
| `--tags` | No | list | None | Tags for the policy |

**Output Schema:**
```json
{
    "Policy": {
        "PolicySummary": {
            "Id": "string",
            "Arn": "string",
            "Name": "string",
            "Description": "string",
            "Type": "SERVICE_CONTROL_POLICY|TAG_POLICY|BACKUP_POLICY|AISERVICES_OPT_OUT_POLICY",
            "AwsManaged": true|false
        },
        "Content": "string"
    }
}
```

---

### 4.2 `delete-policy`

Deletes a policy from the organization. The policy must first be detached from all targets.

**Synopsis:**
```bash
aws organizations delete-policy \
    --policy-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-id` | **Yes** | string | -- | ID of the policy to delete (e.g., `p-abc12345`) |

**Output Schema:**
```json
{}
```

---

### 4.3 `describe-policy`

Retrieves information about a policy.

**Synopsis:**
```bash
aws organizations describe-policy \
    --policy-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-id` | **Yes** | string | -- | ID of the policy |

**Output Schema:**
```json
{
    "Policy": {
        "PolicySummary": {
            "Id": "string",
            "Arn": "string",
            "Name": "string",
            "Description": "string",
            "Type": "SERVICE_CONTROL_POLICY|TAG_POLICY|BACKUP_POLICY|AISERVICES_OPT_OUT_POLICY",
            "AwsManaged": true|false
        },
        "Content": "string"
    }
}
```

---

### 4.4 `update-policy`

Updates an existing policy with new name, description, or content.

**Synopsis:**
```bash
aws organizations update-policy \
    --policy-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--content <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-id` | **Yes** | string | -- | ID of the policy to update |
| `--name` | No | string | None | New name |
| `--description` | No | string | None | New description |
| `--content` | No | string | None | New policy content |

**Output Schema:**
```json
{
    "Policy": {
        "PolicySummary": {
            "Id": "string",
            "Arn": "string",
            "Name": "string",
            "Description": "string",
            "Type": "string",
            "AwsManaged": true|false
        },
        "Content": "string"
    }
}
```

---

### 4.5 `list-policies`

Lists all policies of a specified type. **Paginated operation.**

**Synopsis:**
```bash
aws organizations list-policies \
    --filter <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter` | **Yes** | string | -- | Policy type: `SERVICE_CONTROL_POLICY`, `TAG_POLICY`, `BACKUP_POLICY`, `AISERVICES_OPT_OUT_POLICY` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Policies": [
        {
            "Id": "string",
            "Arn": "string",
            "Name": "string",
            "Description": "string",
            "Type": "string",
            "AwsManaged": true|false
        }
    ],
    "NextToken": "string"
}
```

---

### 4.6 `list-policies-for-target`

Lists the policies attached to a specified target (root, OU, or account). **Paginated operation.**

**Synopsis:**
```bash
aws organizations list-policies-for-target \
    --target-id <value> \
    --filter <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-id` | **Yes** | string | -- | Root, OU, or account ID |
| `--filter` | **Yes** | string | -- | Policy type filter |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Policies": [
        {
            "Id": "string",
            "Arn": "string",
            "Name": "string",
            "Description": "string",
            "Type": "string",
            "AwsManaged": true|false
        }
    ],
    "NextToken": "string"
}
```

---

### 4.7 `list-targets-for-policy`

Lists all roots, OUs, and accounts that a policy is attached to. **Paginated operation.**

**Synopsis:**
```bash
aws organizations list-targets-for-policy \
    --policy-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-id` | **Yes** | string | -- | ID of the policy |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Targets": [
        {
            "TargetId": "string",
            "Arn": "string",
            "Name": "string",
            "Type": "ACCOUNT|ORGANIZATIONAL_UNIT|ROOT"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.8 `attach-policy`

Attaches a policy to a root, OU, or individual account.

**Synopsis:**
```bash
aws organizations attach-policy \
    --policy-id <value> \
    --target-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-id` | **Yes** | string | -- | ID of the policy to attach |
| `--target-id` | **Yes** | string | -- | Root, OU, or account ID |

**Output Schema:**
```json
{}
```

---

### 4.9 `detach-policy`

Detaches a policy from a target root, OU, or account.

**Synopsis:**
```bash
aws organizations detach-policy \
    --policy-id <value> \
    --target-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-id` | **Yes** | string | -- | ID of the policy to detach |
| `--target-id` | **Yes** | string | -- | Root, OU, or account ID |

**Output Schema:**
```json
{}
```

---

### 4.10 `describe-effective-policy`

Returns the effective policy for an account (the merged result of all inherited policies of that type).

**Synopsis:**
```bash
aws organizations describe-effective-policy \
    --policy-type <value> \
    [--target-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-type` | **Yes** | string | -- | Policy type: `TAG_POLICY`, `BACKUP_POLICY`, `AISERVICES_OPT_OUT_POLICY` |
| `--target-id` | No | string | None | Account ID (defaults to calling account) |

**Output Schema:**
```json
{
    "EffectivePolicy": {
        "PolicyContent": "string",
        "LastUpdatedTimestamp": "timestamp",
        "TargetId": "string",
        "PolicyType": "TAG_POLICY|BACKUP_POLICY|AISERVICES_OPT_OUT_POLICY"
    }
}
```

---

### 4.11 `enable-policy-type`

Enables a policy type on a root.

**Synopsis:**
```bash
aws organizations enable-policy-type \
    --root-id <value> \
    --policy-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--root-id` | **Yes** | string | -- | Root ID (e.g., `r-abc1`) |
| `--policy-type` | **Yes** | string | -- | Policy type: `SERVICE_CONTROL_POLICY`, `TAG_POLICY`, `BACKUP_POLICY`, `AISERVICES_OPT_OUT_POLICY` |

**Output Schema:**
```json
{
    "Root": {
        "Id": "string",
        "Arn": "string",
        "Name": "string",
        "PolicyTypes": [
            {
                "Type": "string",
                "Status": "ENABLED|PENDING_ENABLE|PENDING_DISABLE"
            }
        ]
    }
}
```

---

### 4.12 `disable-policy-type`

Disables a policy type on a root. All policies of that type must be detached first.

**Synopsis:**
```bash
aws organizations disable-policy-type \
    --root-id <value> \
    --policy-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--root-id` | **Yes** | string | -- | Root ID |
| `--policy-type` | **Yes** | string | -- | Policy type to disable |

**Output Schema:**
```json
{
    "Root": {
        "Id": "string",
        "Arn": "string",
        "Name": "string",
        "PolicyTypes": [
            {
                "Type": "string",
                "Status": "ENABLED|PENDING_ENABLE|PENDING_DISABLE"
            }
        ]
    }
}
```
