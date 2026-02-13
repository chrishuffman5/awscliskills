# Web Identity

> Commands use `aws workspaces-web` CLI prefix.

### 12.1 `create-identity-provider`

Creates an identity provider resource for a web portal.

**Synopsis:**
```bash
aws workspaces-web create-identity-provider \
    --portal-arn <value> \
    --identity-provider-name <value> \
    --identity-provider-type <value> \
    --identity-provider-details <value> \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--portal-arn` | **Yes** | string | -- | The ARN of the portal |
| `--identity-provider-name` | **Yes** | string | -- | The name of the identity provider (1-32 chars) |
| `--identity-provider-type` | **Yes** | string | -- | The type: `SAML`, `Facebook`, `Google`, `LoginWithAmazon`, `SignInWithApple`, `OIDC` |
| `--identity-provider-details` | **Yes** | map | -- | Provider details (key-value pairs specific to provider type) |
| `--client-token` | No | string | None | Idempotency token |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "identityProviderArn": "string"
}
```

---

### 12.2 `delete-identity-provider`

Deletes an identity provider.

**Synopsis:**
```bash
aws workspaces-web delete-identity-provider \
    --identity-provider-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-provider-arn` | **Yes** | string | -- | The ARN of the identity provider to delete |

**Output Schema:**
```json
{}
```

---

### 12.3 `get-identity-provider`

Gets an identity provider.

**Synopsis:**
```bash
aws workspaces-web get-identity-provider \
    --identity-provider-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-provider-arn` | **Yes** | string | -- | The ARN of the identity provider |

**Output Schema:**
```json
{
    "identityProvider": {
        "identityProviderArn": "string",
        "identityProviderName": "string",
        "identityProviderType": "SAML|Facebook|Google|LoginWithAmazon|SignInWithApple|OIDC",
        "identityProviderDetails": {
            "string": "string"
        }
    }
}
```

---

### 12.4 `list-identity-providers`

Lists identity providers for a portal. **Paginated operation.**

**Synopsis:**
```bash
aws workspaces-web list-identity-providers \
    --portal-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--portal-arn` | **Yes** | string | -- | The ARN of the portal |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "identityProviders": [
        {
            "identityProviderArn": "string",
            "identityProviderName": "string",
            "identityProviderType": "SAML|Facebook|Google|LoginWithAmazon|SignInWithApple|OIDC"
        }
    ],
    "nextToken": "string"
}
```

---

### 12.5 `update-identity-provider`

Updates an identity provider.

**Synopsis:**
```bash
aws workspaces-web update-identity-provider \
    --identity-provider-arn <value> \
    [--identity-provider-name <value>] \
    [--identity-provider-type <value>] \
    [--identity-provider-details <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-provider-arn` | **Yes** | string | -- | The ARN of the identity provider to update |
| `--identity-provider-name` | No | string | None | New name |
| `--identity-provider-type` | No | string | None | New type: `SAML`, `Facebook`, `Google`, `LoginWithAmazon`, `SignInWithApple`, `OIDC` |
| `--identity-provider-details` | No | map | None | Updated provider details |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "identityProvider": {
        "identityProviderArn": "string",
        "identityProviderName": "string",
        "identityProviderType": "SAML|Facebook|Google|LoginWithAmazon|SignInWithApple|OIDC",
        "identityProviderDetails": {
            "string": "string"
        }
    }
}
```
