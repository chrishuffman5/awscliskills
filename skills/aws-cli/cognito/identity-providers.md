# Identity Providers

### 5.1 `create-identity-provider`

Creates a third-party identity provider (SAML, OIDC, or social) in a user pool.

**Synopsis:**
```bash
aws cognito-idp create-identity-provider \
    --user-pool-id <value> \
    --provider-name <value> \
    --provider-type <value> \
    --provider-details <value> \
    [--attribute-mapping <value>] \
    [--idp-identifiers <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--provider-name` | **Yes** | string | -- | Provider name (1-32 chars for social, 1-40 for SAML/OIDC) |
| `--provider-type` | **Yes** | string | -- | Type: `SAML`, `Facebook`, `Google`, `LoginWithAmazon`, `SignInWithApple`, `OIDC` |
| `--provider-details` | **Yes** | map | -- | Provider-specific config (see below) |
| `--attribute-mapping` | No | map | None | Maps provider attributes to user pool attributes |
| `--idp-identifiers` | No | list(string) | None | IdP identifiers (max 50) |

**Provider Details by Type:**

- **SAML**: `MetadataURL=string` or `MetadataFile=string`, `IDPSignout=true|false`
- **OIDC**: `client_id=string`, `client_secret=string`, `authorize_scopes=string`, `oidc_issuer=string`, `attributes_request_method=GET|POST`
- **Google**: `client_id=string`, `client_secret=string`, `authorize_scopes=string`
- **Facebook**: `client_id=string`, `client_secret=string`, `authorize_scopes=string`, `api_version=string`
- **LoginWithAmazon**: `client_id=string`, `client_secret=string`, `authorize_scopes=string`
- **SignInWithApple**: `client_id=string`, `team_id=string`, `key_id=string`, `private_key=string`, `authorize_scopes=string`

**Output Schema:**
```json
{
    "IdentityProvider": {
        "UserPoolId": "string",
        "ProviderName": "string",
        "ProviderType": "SAML|Facebook|Google|LoginWithAmazon|SignInWithApple|OIDC",
        "ProviderDetails": {
            "string": "string"
        },
        "AttributeMapping": {
            "string": "string"
        },
        "IdpIdentifiers": ["string"],
        "LastModifiedDate": "timestamp",
        "CreationDate": "timestamp"
    }
}
```

---

### 5.2 `delete-identity-provider`

Deletes an identity provider.

**Synopsis:**
```bash
aws cognito-idp delete-identity-provider \
    --user-pool-id <value> \
    --provider-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--provider-name` | **Yes** | string | -- | Provider name |

**Output:** None

---

### 5.3 `describe-identity-provider`

Gets information about an identity provider.

**Synopsis:**
```bash
aws cognito-idp describe-identity-provider \
    --user-pool-id <value> \
    --provider-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--provider-name` | **Yes** | string | -- | Provider name |

**Output Schema:** Same as `create-identity-provider`.

---

### 5.4 `list-identity-providers`

Lists identity providers for a user pool. **Paginated operation.**

**Synopsis:**
```bash
aws cognito-idp list-identity-providers \
    --user-pool-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--max-results` | No | integer | 60 | Maximum items (1-60) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Providers": [
        {
            "ProviderName": "string",
            "ProviderType": "SAML|Facebook|Google|LoginWithAmazon|SignInWithApple|OIDC",
            "LastModifiedDate": "timestamp",
            "CreationDate": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.5 `update-identity-provider`

Updates an identity provider.

**Synopsis:**
```bash
aws cognito-idp update-identity-provider \
    --user-pool-id <value> \
    --provider-name <value> \
    [--provider-details <value>] \
    [--attribute-mapping <value>] \
    [--idp-identifiers <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--provider-name` | **Yes** | string | -- | Provider name |
| `--provider-details` | No | map | None | Updated provider details |
| `--attribute-mapping` | No | map | None | Updated attribute mapping |
| `--idp-identifiers` | No | list(string) | None | Updated IdP identifiers |

**Output Schema:** Same as `create-identity-provider`.
