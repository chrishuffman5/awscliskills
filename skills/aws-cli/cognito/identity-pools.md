# Identity Pools (Federated Identities)

> These commands use the `aws cognito-identity` service, not `aws cognito-idp`.

### 6.1 `create-identity-pool`

Creates a new identity pool (federated identities).

**Synopsis:**
```bash
aws cognito-identity create-identity-pool \
    --identity-pool-name <value> \
    [--allow-unauthenticated-identities | --no-allow-unauthenticated-identities] \
    [--allow-classic-flow | --no-allow-classic-flow] \
    [--supported-login-providers <value>] \
    [--developer-provider-name <value>] \
    [--open-id-connect-provider-arns <value>] \
    [--cognito-identity-providers <value>] \
    [--saml-provider-arns <value>] \
    [--identity-pool-tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-pool-name` | **Yes** | string | -- | Name of the identity pool (1-128 chars) |
| `--allow-unauthenticated-identities` | No | boolean | false | Allow unauthenticated (guest) identities |
| `--allow-classic-flow` | No | boolean | false | Enable classic (basic) auth flow |
| `--supported-login-providers` | No | map | None | Social login providers. Shorthand: `graph.facebook.com=app_id,accounts.google.com=client_id` |
| `--developer-provider-name` | No | string | None | Developer provider name for custom auth |
| `--open-id-connect-provider-arns` | No | list(string) | None | OIDC provider ARNs |
| `--cognito-identity-providers` | No | list | None | Cognito user pool providers. Shorthand: `ProviderName=string,ClientId=string,ServerSideTokenCheck=boolean` |
| `--saml-provider-arns` | No | list(string) | None | SAML provider ARNs |
| `--identity-pool-tags` | No | map | None | Key-value tags |

**Output Schema:**
```json
{
    "IdentityPoolId": "string",
    "IdentityPoolName": "string",
    "AllowUnauthenticatedIdentities": "boolean",
    "AllowClassicFlow": "boolean",
    "SupportedLoginProviders": {
        "string": "string"
    },
    "DeveloperProviderName": "string",
    "OpenIdConnectProviderARNs": ["string"],
    "CognitoIdentityProviders": [
        {
            "ProviderName": "string",
            "ClientId": "string",
            "ServerSideTokenCheck": "boolean"
        }
    ],
    "SamlProviderARNs": ["string"],
    "IdentityPoolTags": {
        "string": "string"
    }
}
```

---

### 6.2 `delete-identity-pool`

Deletes an identity pool.

**Synopsis:**
```bash
aws cognito-identity delete-identity-pool \
    --identity-pool-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-pool-id` | **Yes** | string | -- | ID of the identity pool |

**Output:** None

---

### 6.3 `describe-identity-pool`

Gets information about an identity pool.

**Synopsis:**
```bash
aws cognito-identity describe-identity-pool \
    --identity-pool-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-pool-id` | **Yes** | string | -- | ID of the identity pool |

**Output Schema:** Same as `create-identity-pool`.

---

### 6.4 `list-identity-pools`

Lists identity pools. **Paginated operation.**

**Synopsis:**
```bash
aws cognito-identity list-identity-pools \
    --max-results <value> \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | **Yes** | integer | -- | Maximum items (1-60) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "IdentityPools": [
        {
            "IdentityPoolId": "string",
            "IdentityPoolName": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.5 `update-identity-pool`

Updates an identity pool. Accepts all the same parameters as `create-identity-pool` plus the pool ID.

**Synopsis:**
```bash
aws cognito-identity update-identity-pool \
    --identity-pool-id <value> \
    --identity-pool-name <value> \
    [--allow-unauthenticated-identities | --no-allow-unauthenticated-identities] \
    [--allow-classic-flow | --no-allow-classic-flow] \
    [--supported-login-providers <value>] \
    [--developer-provider-name <value>] \
    [--open-id-connect-provider-arns <value>] \
    [--cognito-identity-providers <value>] \
    [--saml-provider-arns <value>] \
    [--identity-pool-tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-pool-id` | **Yes** | string | -- | ID of the identity pool |
| `--identity-pool-name` | **Yes** | string | -- | Updated name |
| All other parameters are the same as `create-identity-pool`. |

**Output Schema:** Same as `create-identity-pool`.

---

### 6.6 `get-id`

Gets or creates an identity ID for a user. Returns an existing identity if one exists, otherwise creates a new one.

**Synopsis:**
```bash
aws cognito-identity get-id \
    --identity-pool-id <value> \
    [--account-id <value>] \
    [--logins <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-pool-id` | **Yes** | string | -- | ID of the identity pool |
| `--account-id` | No | string | None | AWS account ID |
| `--logins` | No | map | None | Login provider tokens. Shorthand: `cognito-idp.us-east-1.amazonaws.com/us-east-1_abc123=id_token` |

**Output Schema:**
```json
{
    "IdentityId": "string"
}
```

---

### 6.7 `get-credentials-for-identity`

Gets temporary AWS credentials for an identity. Returns access key, secret key, session token, and expiration.

**Synopsis:**
```bash
aws cognito-identity get-credentials-for-identity \
    --identity-id <value> \
    [--logins <value>] \
    [--custom-role-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-id` | **Yes** | string | -- | Identity ID from `get-id` |
| `--logins` | No | map | None | Login provider tokens |
| `--custom-role-arn` | No | string | None | Custom IAM role ARN to assume |

**Output Schema:**
```json
{
    "IdentityId": "string",
    "Credentials": {
        "AccessKeyId": "string",
        "SecretKey": "string",
        "SessionToken": "string",
        "Expiration": "timestamp"
    }
}
```

---

### 6.8 `get-open-id-token-for-developer-identity`

Gets an OpenID token for a developer-authenticated identity.

**Synopsis:**
```bash
aws cognito-identity get-open-id-token-for-developer-identity \
    --identity-pool-id <value> \
    --logins <value> \
    [--identity-id <value>] \
    [--principal-tags <value>] \
    [--token-duration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-pool-id` | **Yes** | string | -- | ID of the identity pool |
| `--logins` | **Yes** | map | -- | Developer provider logins. Shorthand: `developer_provider_name=user_identifier` |
| `--identity-id` | No | string | None | Existing identity ID |
| `--principal-tags` | No | map | None | Session tags for ABAC |
| `--token-duration` | No | long | 86400 | Token duration in seconds (1-86400) |

**Output Schema:**
```json
{
    "IdentityId": "string",
    "Token": "string"
}
```

---

### 6.9 `set-identity-pool-roles`

Sets the IAM roles for an identity pool.

**Synopsis:**
```bash
aws cognito-identity set-identity-pool-roles \
    --identity-pool-id <value> \
    --roles <value> \
    [--role-mappings <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-pool-id` | **Yes** | string | -- | ID of the identity pool |
| `--roles` | **Yes** | map | -- | Role mapping. Shorthand: `authenticated=arn:aws:iam::123456789012:role/AuthRole,unauthenticated=arn:aws:iam::123456789012:role/UnauthRole` |
| `--role-mappings` | No | map | None | Advanced role mapping rules per provider |

**Output:** None

---

### 6.10 `get-identity-pool-roles`

Gets the IAM roles for an identity pool.

**Synopsis:**
```bash
aws cognito-identity get-identity-pool-roles \
    --identity-pool-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-pool-id` | **Yes** | string | -- | ID of the identity pool |

**Output Schema:**
```json
{
    "IdentityPoolId": "string",
    "Roles": {
        "authenticated": "string",
        "unauthenticated": "string"
    },
    "RoleMappings": {
        "string": {
            "Type": "Token|Rules",
            "AmbiguousRoleResolution": "AuthenticatedRole|Deny",
            "RulesConfiguration": {
                "Rules": [
                    {
                        "Claim": "string",
                        "MatchType": "Equals|Contains|StartsWith|NotEqual",
                        "Value": "string",
                        "RoleARN": "string"
                    }
                ]
            }
        }
    }
}
```
