# Policy Stores

### 1.1 `create-policy-store`

Creates a new policy store for storing Cedar policies and schemas.

**Synopsis:**
```bash
aws verifiedpermissions create-policy-store \
    --validation-settings <value> \
    [--client-token <value>] \
    [--description <value>] \
    [--deletion-protection <value>] \
    [--encryption-settings <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--validation-settings` | **Yes** | structure | -- | Validation mode. Shorthand: `mode=STRICT\|OFF` |
| `--client-token` | No | string | Auto-generated | Idempotency token (1-64 chars) |
| `--description` | No | string | None | Descriptive text (max 150 chars) |
| `--deletion-protection` | No | string | `DISABLED` | Enable/disable deletion protection: `ENABLED\|DISABLED` |
| `--encryption-settings` | No | tagged union | None | KMS encryption settings or default AWS-owned encryption |
| `--tags` | No | map | None | Key-value pairs for tagging (max 200 tags) |

**Output Schema:**
```json
{
    "policyStoreId": "string",
    "arn": "string",
    "createdDate": "timestamp",
    "lastUpdatedDate": "timestamp"
}
```

---

### 1.2 `delete-policy-store`

Deletes the specified policy store. All policies, policy templates, identity sources, and schemas in the store are removed.

**Synopsis:**
```bash
aws verifiedpermissions delete-policy-store \
    --policy-store-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-store-id` | **Yes** | string | -- | ID of the policy store to delete |

**Output Schema:**

No output fields (empty response on success).

---

### 1.3 `get-policy-store`

Retrieves details about the specified policy store.

**Synopsis:**
```bash
aws verifiedpermissions get-policy-store \
    --policy-store-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-store-id` | **Yes** | string | -- | ID of the policy store to retrieve |

**Output Schema:**
```json
{
    "policyStoreId": "string",
    "arn": "string",
    "validationSettings": {
        "mode": "STRICT|OFF"
    },
    "createdDate": "timestamp",
    "lastUpdatedDate": "timestamp",
    "description": "string",
    "deletionProtection": "ENABLED|DISABLED"
}
```

---

### 1.4 `list-policy-stores`

Lists all policy stores in the account. **Paginated operation.**

**Synopsis:**
```bash
aws verifiedpermissions list-policy-stores \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "policyStores": [
        {
            "policyStoreId": "string",
            "arn": "string",
            "createdDate": "timestamp",
            "lastUpdatedDate": "timestamp",
            "description": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.5 `update-policy-store`

Updates the specified policy store settings (validation mode, description, deletion protection).

**Synopsis:**
```bash
aws verifiedpermissions update-policy-store \
    --policy-store-id <value> \
    --validation-settings <value> \
    [--description <value>] \
    [--deletion-protection <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-store-id` | **Yes** | string | -- | ID of the policy store to update |
| `--validation-settings` | **Yes** | structure | -- | Validation mode. Shorthand: `mode=STRICT\|OFF` |
| `--description` | No | string | None | Updated description (max 150 chars) |
| `--deletion-protection` | No | string | None | Enable/disable deletion protection: `ENABLED\|DISABLED` |

**Output Schema:**
```json
{
    "policyStoreId": "string",
    "arn": "string",
    "createdDate": "timestamp",
    "lastUpdatedDate": "timestamp"
}
```
