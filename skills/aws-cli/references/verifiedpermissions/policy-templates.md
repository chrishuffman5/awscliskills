# Policy Templates

### 3.1 `create-policy-template`

Creates a policy template in the specified policy store. Templates use Cedar policy language with placeholder slots (`?principal`, `?resource`).

**Synopsis:**
```bash
aws verifiedpermissions create-policy-template \
    --policy-store-id <value> \
    --statement <value> \
    [--client-token <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-store-id` | **Yes** | string | -- | Policy store ID (1-200 chars) |
| `--statement` | **Yes** | string | -- | Cedar policy template body (1-10000 chars) |
| `--client-token` | No | string | Auto-generated | Idempotency token (1-64 chars) |
| `--description` | No | string | None | Description (max 150 chars) |

**Output Schema:**
```json
{
    "policyStoreId": "string",
    "policyTemplateId": "string",
    "createdDate": "timestamp",
    "lastUpdatedDate": "timestamp"
}
```

---

### 3.2 `delete-policy-template`

Deletes the specified policy template. Also deletes all template-linked policies that were created from this template.

**Synopsis:**
```bash
aws verifiedpermissions delete-policy-template \
    --policy-store-id <value> \
    --policy-template-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-store-id` | **Yes** | string | -- | Policy store ID |
| `--policy-template-id` | **Yes** | string | -- | ID of the policy template to delete |

**Output Schema:**

No output fields (empty response on success).

---

### 3.3 `get-policy-template`

Retrieves details about the specified policy template.

**Synopsis:**
```bash
aws verifiedpermissions get-policy-template \
    --policy-store-id <value> \
    --policy-template-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-store-id` | **Yes** | string | -- | Policy store ID |
| `--policy-template-id` | **Yes** | string | -- | ID of the policy template to retrieve |

**Output Schema:**
```json
{
    "policyStoreId": "string",
    "policyTemplateId": "string",
    "description": "string",
    "statement": "string",
    "createdDate": "timestamp",
    "lastUpdatedDate": "timestamp"
}
```

---

### 3.4 `list-policy-templates`

Lists all policy templates in the specified policy store. **Paginated operation.**

**Synopsis:**
```bash
aws verifiedpermissions list-policy-templates \
    --policy-store-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-store-id` | **Yes** | string | -- | Policy store ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "policyTemplates": [
        {
            "policyStoreId": "string",
            "policyTemplateId": "string",
            "description": "string",
            "createdDate": "timestamp",
            "lastUpdatedDate": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 3.5 `update-policy-template`

Updates the specified policy template. Template-linked policies are automatically updated when the template changes.

**Synopsis:**
```bash
aws verifiedpermissions update-policy-template \
    --policy-store-id <value> \
    --policy-template-id <value> \
    --statement <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-store-id` | **Yes** | string | -- | Policy store ID |
| `--policy-template-id` | **Yes** | string | -- | ID of the policy template to update |
| `--statement` | **Yes** | string | -- | Updated Cedar policy template body (1-10000 chars) |
| `--description` | No | string | None | Updated description (max 150 chars) |

**Output Schema:**
```json
{
    "policyStoreId": "string",
    "policyTemplateId": "string",
    "createdDate": "timestamp",
    "lastUpdatedDate": "timestamp"
}
```
