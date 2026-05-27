# User Pool Clients

### 2.1 `create-user-pool-client`

Creates a new app client in a user pool.

**Synopsis:**
```bash
aws cognito-idp create-user-pool-client \
    --user-pool-id <value> \
    --client-name <value> \
    [--generate-secret | --no-generate-secret] \
    [--refresh-token-validity <value>] \
    [--access-token-validity <value>] \
    [--id-token-validity <value>] \
    [--token-validity-units <value>] \
    [--read-attributes <value>] \
    [--write-attributes <value>] \
    [--explicit-auth-flows <value>] \
    [--supported-identity-providers <value>] \
    [--callback-urls <value>] \
    [--logout-urls <value>] \
    [--default-redirect-uri <value>] \
    [--allowed-o-auth-flows <value>] \
    [--allowed-o-auth-scopes <value>] \
    [--allowed-o-auth-flows-user-pool-client | --no-allowed-o-auth-flows-user-pool-client] \
    [--prevent-user-existence-errors <value>] \
    [--enable-token-revocation | --no-enable-token-revocation] \
    [--enable-propagate-additional-user-context-data | --no-enable-propagate-additional-user-context-data] \
    [--auth-session-validity <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--client-name` | **Yes** | string | -- | Client name (1-128 chars) |
| `--generate-secret` | No | boolean | false | Generate a client secret (required for server-side apps) |
| `--refresh-token-validity` | No | integer | 30 | Refresh token expiration (in days by default, see token-validity-units) |
| `--access-token-validity` | No | integer | 60 | Access token expiration (in minutes by default) |
| `--id-token-validity` | No | integer | 60 | ID token expiration (in minutes by default) |
| `--token-validity-units` | No | structure | None | Units for token validity. Shorthand: `AccessToken=seconds|minutes|hours|days,IdToken=seconds|minutes|hours|days,RefreshToken=seconds|minutes|hours|days` |
| `--explicit-auth-flows` | No | list(string) | None | Auth flows: `ALLOW_USER_PASSWORD_AUTH`, `ALLOW_USER_SRP_AUTH`, `ALLOW_ADMIN_USER_PASSWORD_AUTH`, `ALLOW_CUSTOM_AUTH`, `ALLOW_REFRESH_TOKEN_AUTH` |
| `--supported-identity-providers` | No | list(string) | None | Identity providers: `COGNITO`, `Facebook`, `Google`, `LoginWithAmazon`, `SignInWithApple`, or SAML/OIDC provider name |
| `--callback-urls` | No | list(string) | None | Allowed callback URLs for OAuth |
| `--logout-urls` | No | list(string) | None | Allowed logout URLs |
| `--default-redirect-uri` | No | string | None | Default redirect URI (must be in callback-urls) |
| `--allowed-o-auth-flows` | No | list(string) | None | OAuth flows: `code`, `implicit`, `client_credentials` |
| `--allowed-o-auth-scopes` | No | list(string) | None | OAuth scopes: `phone`, `email`, `openid`, `profile`, `aws.cognito.signin.user.admin`, or custom scopes |
| `--allowed-o-auth-flows-user-pool-client` | No | boolean | false | Enable OAuth flows |
| `--read-attributes` | No | list(string) | None | Readable user attributes |
| `--write-attributes` | No | list(string) | None | Writable user attributes |
| `--prevent-user-existence-errors` | No | string | `ENABLED` | `ENABLED` or `LEGACY` |
| `--enable-token-revocation` | No | boolean | true | Enable token revocation |
| `--auth-session-validity` | No | integer | 3 | Auth session validity (3-15 minutes) |

**Output Schema:**
```json
{
    "UserPoolClient": {
        "UserPoolId": "string",
        "ClientName": "string",
        "ClientId": "string",
        "ClientSecret": "string",
        "LastModifiedDate": "timestamp",
        "CreationDate": "timestamp",
        "RefreshTokenValidity": "integer",
        "AccessTokenValidity": "integer",
        "IdTokenValidity": "integer",
        "TokenValidityUnits": {
            "AccessToken": "seconds|minutes|hours|days",
            "IdToken": "seconds|minutes|hours|days",
            "RefreshToken": "seconds|minutes|hours|days"
        },
        "ReadAttributes": ["string"],
        "WriteAttributes": ["string"],
        "ExplicitAuthFlows": ["string"],
        "SupportedIdentityProviders": ["string"],
        "CallbackURLs": ["string"],
        "LogoutURLs": ["string"],
        "DefaultRedirectURI": "string",
        "AllowedOAuthFlows": ["code|implicit|client_credentials"],
        "AllowedOAuthScopes": ["string"],
        "AllowedOAuthFlowsUserPoolClient": "boolean",
        "PreventUserExistenceErrors": "ENABLED|LEGACY",
        "EnableTokenRevocation": "boolean",
        "EnablePropagateAdditionalUserContextData": "boolean",
        "AuthSessionValidity": "integer"
    }
}
```

---

### 2.2 `delete-user-pool-client`

Deletes a user pool client.

**Synopsis:**
```bash
aws cognito-idp delete-user-pool-client \
    --user-pool-id <value> \
    --client-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--client-id` | **Yes** | string | -- | Client ID to delete |

**Output:** None

---

### 2.3 `describe-user-pool-client`

Gets detailed information about a user pool client.

**Synopsis:**
```bash
aws cognito-idp describe-user-pool-client \
    --user-pool-id <value> \
    --client-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--client-id` | **Yes** | string | -- | Client ID |

**Output Schema:** Same as `create-user-pool-client`.

---

### 2.4 `list-user-pool-clients`

Lists clients in a user pool. **Paginated operation.**

**Synopsis:**
```bash
aws cognito-idp list-user-pool-clients \
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
    "UserPoolClients": [
        {
            "ClientId": "string",
            "UserPoolId": "string",
            "ClientName": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.5 `update-user-pool-client`

Updates a user pool client. Accepts all the same optional parameters as `create-user-pool-client`.

**Synopsis:**
```bash
aws cognito-idp update-user-pool-client \
    --user-pool-id <value> \
    --client-id <value> \
    [--client-name <value>] \
    [--refresh-token-validity <value>] \
    [--access-token-validity <value>] \
    [--id-token-validity <value>] \
    [--token-validity-units <value>] \
    [--read-attributes <value>] \
    [--write-attributes <value>] \
    [--explicit-auth-flows <value>] \
    [--supported-identity-providers <value>] \
    [--callback-urls <value>] \
    [--logout-urls <value>] \
    [--default-redirect-uri <value>] \
    [--allowed-o-auth-flows <value>] \
    [--allowed-o-auth-scopes <value>] \
    [--allowed-o-auth-flows-user-pool-client | --no-allowed-o-auth-flows-user-pool-client] \
    [--prevent-user-existence-errors <value>] \
    [--enable-token-revocation | --no-enable-token-revocation] \
    [--auth-session-validity <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--client-id` | **Yes** | string | -- | Client ID |
| All other parameters are the same optional parameters as `create-user-pool-client`. |

**Output Schema:** Same as `create-user-pool-client`.
