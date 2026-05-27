# Trusted Token Issuers

### 7.1 `create-trusted-token-issuer`

Creates a trusted token issuer for the specified IAM Identity Center instance.

**Synopsis:**
```bash
aws sso-admin create-trusted-token-issuer \
    --instance-arn <value> \
    --name <value> \
    --trusted-token-issuer-type <value> \
    --trusted-token-issuer-configuration <value> \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the Identity Center instance |
| `--name` | **Yes** | string | -- | Name of the trusted token issuer (1-100 chars) |
| `--trusted-token-issuer-type` | **Yes** | string | -- | `OIDC_JWT` |
| `--trusted-token-issuer-configuration` | **Yes** | tagged union | -- | Issuer configuration |
| `--client-token` | No | string | None | Idempotency token |
| `--tags` | No | list(structure) | None | Tags (max 75) |

**Configuration Structure (OIDC_JWT):**
```json
{
    "OidcJwtConfiguration": {
        "IssuerUrl": "string",
        "ClaimAttributePath": "string",
        "IdentityStoreAttributePath": "string",
        "JwksRetrievalOption": "OPEN_ID_DISCOVERY"
    }
}
```

**Output Schema:**
```json
{
    "TrustedTokenIssuerArn": "string"
}
```

---

### 7.2 `delete-trusted-token-issuer`

Deletes a trusted token issuer.

**Synopsis:**
```bash
aws sso-admin delete-trusted-token-issuer \
    --trusted-token-issuer-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trusted-token-issuer-arn` | **Yes** | string | -- | ARN of the trusted token issuer to delete |

**Output Schema:**

No output on success (HTTP 200).

---

### 7.3 `describe-trusted-token-issuer`

Describes a trusted token issuer.

**Synopsis:**
```bash
aws sso-admin describe-trusted-token-issuer \
    --trusted-token-issuer-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trusted-token-issuer-arn` | **Yes** | string | -- | ARN of the trusted token issuer |

**Output Schema:**
```json
{
    "TrustedTokenIssuerArn": "string",
    "Name": "string",
    "TrustedTokenIssuerType": "OIDC_JWT",
    "TrustedTokenIssuerConfiguration": {
        "OidcJwtConfiguration": {
            "IssuerUrl": "string",
            "ClaimAttributePath": "string",
            "IdentityStoreAttributePath": "string",
            "JwksRetrievalOption": "OPEN_ID_DISCOVERY"
        }
    }
}
```

---

### 7.4 `update-trusted-token-issuer`

Updates a trusted token issuer configuration.

**Synopsis:**
```bash
aws sso-admin update-trusted-token-issuer \
    --trusted-token-issuer-arn <value> \
    [--name <value>] \
    [--trusted-token-issuer-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trusted-token-issuer-arn` | **Yes** | string | -- | ARN of the trusted token issuer |
| `--name` | No | string | None | Updated name |
| `--trusted-token-issuer-configuration` | No | tagged union | None | Updated configuration |

**Output Schema:**

No output on success (HTTP 200).

---

### 7.5 `list-trusted-token-issuers`

Lists all trusted token issuers for an instance. **Paginated operation.**

**Synopsis:**
```bash
aws sso-admin list-trusted-token-issuers \
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
    "TrustedTokenIssuers": [
        {
            "TrustedTokenIssuerArn": "string",
            "Name": "string",
            "TrustedTokenIssuerType": "OIDC_JWT"
        }
    ],
    "NextToken": "string"
}
```
