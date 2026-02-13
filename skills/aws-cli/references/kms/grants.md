# Grants

### 3.1 `create-grant`

Adds a grant to a KMS key, delegating permissions to a grantee principal.

**Synopsis:**
```bash
aws kms create-grant \
    --key-id <value> \
    --grantee-principal <value> \
    --operations <value> \
    [--retiring-principal <value>] \
    [--constraints <value>] \
    [--grant-tokens <value>] \
    [--name <value>] \
    [--dry-run | --no-dry-run]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Key ID or key ARN (1-2048 chars) |
| `--grantee-principal` | **Yes** | string | -- | IAM principal ARN receiving permissions (1-256 chars) |
| `--operations` | **Yes** | list | -- | Permitted operations: `Decrypt`, `Encrypt`, `GenerateDataKey`, `GenerateDataKeyWithoutPlaintext`, `ReEncryptFrom`, `ReEncryptTo`, `Sign`, `Verify`, `GetPublicKey`, `CreateGrant`, `RetireGrant`, `DescribeKey`, `GenerateDataKeyPair`, `GenerateDataKeyPairWithoutPlaintext`, `GenerateMac`, `VerifyMac`, `DeriveSharedSecret` |
| `--retiring-principal` | No | string | None | Principal allowed to retire the grant (1-256 chars) |
| `--constraints` | No | structure | None | Grant constraints: `EncryptionContextEquals` and/or `EncryptionContextSubset` (up to 8 pairs each) |
| `--grant-tokens` | No | list | None | Grant tokens (0-10 items) |
| `--name` | No | string | None | Friendly name to prevent duplicates (1-256 chars) |
| `--dry-run` | No | boolean | `false` | Test request without executing |

**Output Schema:**
```json
{
    "GrantToken": "string",
    "GrantId": "string"
}
```

---

### 3.2 `list-grants`

Lists grants for a KMS key. **Paginated.**

**Synopsis:**
```bash
aws kms list-grants \
    --key-id <value> \
    [--grant-id <value>] \
    [--grantee-principal <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Key ID or key ARN (1-2048 chars) |
| `--grant-id` | No | string | None | Filter by specific grant ID (1-128 chars) |
| `--grantee-principal` | No | string | None | Filter by grantee principal ARN (1-256 chars) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Grants": [
        {
            "KeyId": "string",
            "GrantId": "string",
            "GranteePrincipal": "string",
            "RetiringPrincipal": "string",
            "IssuingAccount": "string",
            "Operations": ["string"],
            "Constraints": {
                "EncryptionContextSubset": {"string": "string"},
                "EncryptionContextEquals": {"string": "string"}
            },
            "Name": "string",
            "CreationDate": "timestamp"
        }
    ],
    "NextMarker": "string",
    "Truncated": true|false
}
```

---

### 3.3 `list-retirable-grants`

Lists grants that a specified principal can retire. **Paginated.**

**Synopsis:**
```bash
aws kms list-retirable-grants \
    --retiring-principal <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--retiring-principal` | **Yes** | string | -- | Principal ARN (1-256 chars) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:** Same as `list-grants`.

---

### 3.4 `retire-grant`

Retires a grant. Cleans up after operations permitted by the grant are complete.

**Synopsis:**
```bash
aws kms retire-grant \
    [--grant-token <value>] \
    [--key-id <value>] \
    [--grant-id <value>] \
    [--dry-run | --no-dry-run]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--grant-token` | No | string | -- | Grant token (1-8192 chars). Use either `--grant-token` or `--key-id` + `--grant-id` |
| `--key-id` | No | string | -- | Key ID or key ARN (1-2048 chars). Required with `--grant-id` |
| `--grant-id` | No | string | -- | Grant ID (1-128 chars). Required with `--key-id` |
| `--dry-run` | No | boolean | `false` | Test request without executing |

**Output:** None

---

### 3.5 `revoke-grant`

Revokes a grant immediately, revoking all permissions.

**Synopsis:**
```bash
aws kms revoke-grant \
    --key-id <value> \
    --grant-id <value> \
    [--dry-run | --no-dry-run]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Key ID or key ARN (1-2048 chars) |
| `--grant-id` | **Yes** | string | -- | Grant ID to revoke (1-128 chars) |
| `--dry-run` | No | boolean | `false` | Test request without executing |

**Output:** None

---
