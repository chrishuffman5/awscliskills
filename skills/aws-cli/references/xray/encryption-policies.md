# Encryption & Policies

### 7.1 `get-encryption-config`

Returns the encryption configuration for X-Ray data.

**Synopsis:**
```bash
aws xray get-encryption-config \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

No required parameters.

**Output Schema:**
```json
{
    "EncryptionConfig": {
        "KeyId": "string",
        "Status": "UPDATING|ACTIVE",
        "Type": "NONE|KMS"
    }
}
```

---

### 7.2 `put-encryption-config`

Updates the encryption configuration for X-Ray data.

**Synopsis:**
```bash
aws xray put-encryption-config \
    --type <value> \
    [--key-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | **Yes** | string | -- | Encryption type: `NONE` (AWS-owned key), `KMS` (customer-managed key) |
| `--key-id` | No | string | None | KMS key ID or ARN (required when type is `KMS`) |

**Output Schema:**
```json
{
    "EncryptionConfig": {
        "KeyId": "string",
        "Status": "UPDATING|ACTIVE",
        "Type": "NONE|KMS"
    }
}
```

---

### 7.3 `list-resource-policies`

Returns a list of resource policies attached to the X-Ray service. **Paginated operation.**

**Synopsis:**
```bash
aws xray list-resource-policies \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "ResourcePolicies": [
        {
            "PolicyName": "string",
            "PolicyDocument": "string",
            "PolicyRevisionId": "string",
            "LastUpdatedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.4 `put-resource-policy`

Sets or updates a resource policy for the X-Ray service. Used for cross-account observability.

**Synopsis:**
```bash
aws xray put-resource-policy \
    --policy-name <value> \
    --policy-document <value> \
    [--policy-revision-id <value>] \
    [--bypass-policy-lockout-check | --no-bypass-policy-lockout-check] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-name` | **Yes** | string | -- | Name of the resource policy |
| `--policy-document` | **Yes** | string | -- | JSON policy document (max 5120 chars) |
| `--policy-revision-id` | No | string | None | Current revision ID for optimistic locking |
| `--bypass-policy-lockout-check` | No | boolean | false | Bypass the lockout safety check |

**Output Schema:**
```json
{
    "ResourcePolicy": {
        "PolicyName": "string",
        "PolicyDocument": "string",
        "PolicyRevisionId": "string",
        "LastUpdatedTime": "timestamp"
    }
}
```

---

### 7.5 `delete-resource-policy`

Deletes a resource policy from X-Ray.

**Synopsis:**
```bash
aws xray delete-resource-policy \
    --policy-name <value> \
    [--policy-revision-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-name` | **Yes** | string | -- | Name of the resource policy to delete |
| `--policy-revision-id` | No | string | None | Current revision ID for optimistic locking |

**Output Schema:**
```json
{}
```
