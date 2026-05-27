# Application Config

### 6.1 `put-application-access-scope`

Creates or updates an access scope for an application.

**Synopsis:**
```bash
aws sso-admin put-application-access-scope \
    --application-arn <value> \
    --scope <value> \
    [--authorized-targets <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-arn` | **Yes** | string | -- | ARN of the application |
| `--scope` | **Yes** | string | -- | Scope name |
| `--authorized-targets` | No | list(string) | None | Application ARNs authorized for this scope |

**Output Schema:**

No output on success (HTTP 200).

---

### 6.2 `get-application-access-scope`

Gets an access scope for an application.

**Synopsis:**
```bash
aws sso-admin get-application-access-scope \
    --application-arn <value> \
    --scope <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-arn` | **Yes** | string | -- | ARN of the application |
| `--scope` | **Yes** | string | -- | Scope name |

**Output Schema:**
```json
{
    "Scope": "string",
    "AuthorizedTargets": ["string"]
}
```

---

### 6.3 `delete-application-access-scope`

Deletes an access scope from an application.

**Synopsis:**
```bash
aws sso-admin delete-application-access-scope \
    --application-arn <value> \
    --scope <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-arn` | **Yes** | string | -- | ARN of the application |
| `--scope` | **Yes** | string | -- | Scope name to delete |

**Output Schema:**

No output on success (HTTP 200).

---

### 6.4 `list-application-access-scopes`

Lists all access scopes for an application. **Paginated operation.**

**Synopsis:**
```bash
aws sso-admin list-application-access-scopes \
    --application-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-arn` | **Yes** | string | -- | ARN of the application |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Scopes": [
        {
            "Scope": "string",
            "AuthorizedTargets": ["string"]
        }
    ],
    "NextToken": "string"
}
```

---

### 6.5 `put-application-assignment-configuration`

Sets the assignment requirement for an application.

**Synopsis:**
```bash
aws sso-admin put-application-assignment-configuration \
    --application-arn <value> \
    --assignment-required | --no-assignment-required \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-arn` | **Yes** | string | -- | ARN of the application |
| `--assignment-required` | **Yes** | boolean | -- | Whether users must be assigned to access the application |

**Output Schema:**

No output on success (HTTP 200).

---

### 6.6 `get-application-assignment-configuration`

Gets the assignment configuration for an application.

**Synopsis:**
```bash
aws sso-admin get-application-assignment-configuration \
    --application-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-arn` | **Yes** | string | -- | ARN of the application |

**Output Schema:**
```json
{
    "AssignmentRequired": "boolean"
}
```

---

### 6.7 `put-application-authentication-method`

Sets an authentication method for an application.

**Synopsis:**
```bash
aws sso-admin put-application-authentication-method \
    --application-arn <value> \
    --authentication-method-type <value> \
    --authentication-method <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-arn` | **Yes** | string | -- | ARN of the application |
| `--authentication-method-type` | **Yes** | string | -- | `IAM` |
| `--authentication-method` | **Yes** | structure | -- | Authentication method configuration |

**Output Schema:**

No output on success (HTTP 200).

---

### 6.8 `get-application-authentication-method`

Gets an authentication method for an application.

**Synopsis:**
```bash
aws sso-admin get-application-authentication-method \
    --application-arn <value> \
    --authentication-method-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-arn` | **Yes** | string | -- | ARN of the application |
| `--authentication-method-type` | **Yes** | string | -- | `IAM` |

**Output Schema:**
```json
{
    "AuthenticationMethod": {
        "Iam": {
            "ActorPolicy": "structure"
        }
    }
}
```

---

### 6.9 `delete-application-authentication-method`

Deletes an authentication method from an application.

**Synopsis:**
```bash
aws sso-admin delete-application-authentication-method \
    --application-arn <value> \
    --authentication-method-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-arn` | **Yes** | string | -- | ARN of the application |
| `--authentication-method-type` | **Yes** | string | -- | `IAM` |

**Output Schema:**

No output on success (HTTP 200).

---

### 6.10 `list-application-authentication-methods`

Lists authentication methods for an application. **Paginated operation.**

**Synopsis:**
```bash
aws sso-admin list-application-authentication-methods \
    --application-arn <value> \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-arn` | **Yes** | string | -- | ARN of the application |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AuthenticationMethods": [
        {
            "AuthenticationMethod": {
                "Iam": {
                    "ActorPolicy": "structure"
                }
            },
            "AuthenticationMethodType": "IAM"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.11 `put-application-grant`

Creates or updates a grant for an application.

**Synopsis:**
```bash
aws sso-admin put-application-grant \
    --application-arn <value> \
    --grant-type <value> \
    --grant <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-arn` | **Yes** | string | -- | ARN of the application |
| `--grant-type` | **Yes** | string | -- | Grant type: `authorization_code`, `urn:ietf:params:oauth:grant-type:jwt-bearer`, `urn:ietf:params:oauth:grant-type:token-exchange`, `refresh_token` |
| `--grant` | **Yes** | tagged union | -- | Grant configuration |

**Output Schema:**

No output on success (HTTP 200).

---

### 6.12 `get-application-grant`

Gets a grant for an application.

**Synopsis:**
```bash
aws sso-admin get-application-grant \
    --application-arn <value> \
    --grant-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-arn` | **Yes** | string | -- | ARN of the application |
| `--grant-type` | **Yes** | string | -- | Grant type |

**Output Schema:**
```json
{
    "Grant": {
        "AuthorizationCode": {
            "RedirectUris": ["string"]
        },
        "JwtBearer": {
            "AuthorizedTokenIssuers": [
                {
                    "TrustedTokenIssuerArn": "string",
                    "AuthorizedAudiences": ["string"]
                }
            ]
        },
        "RefreshToken": {},
        "TokenExchange": {}
    }
}
```

---

### 6.13 `delete-application-grant`

Deletes a grant from an application.

**Synopsis:**
```bash
aws sso-admin delete-application-grant \
    --application-arn <value> \
    --grant-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-arn` | **Yes** | string | -- | ARN of the application |
| `--grant-type` | **Yes** | string | -- | Grant type to delete |

**Output Schema:**

No output on success (HTTP 200).

---

### 6.14 `list-application-grants`

Lists all grants for an application. **Paginated operation.**

**Synopsis:**
```bash
aws sso-admin list-application-grants \
    --application-arn <value> \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-arn` | **Yes** | string | -- | ARN of the application |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Grants": [
        {
            "GrantType": "string",
            "Grant": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 6.15 `put-application-session-configuration`

Sets session configuration for an application.

**Synopsis:**
```bash
aws sso-admin put-application-session-configuration \
    --application-arn <value> \
    --session-configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-arn` | **Yes** | string | -- | ARN of the application |
| `--session-configuration` | **Yes** | structure | -- | Session configuration. Structure: `SessionDuration=string` (ISO-8601) |

**Output Schema:**

No output on success (HTTP 200).

---

### 6.16 `get-application-session-configuration`

Gets session configuration for an application.

**Synopsis:**
```bash
aws sso-admin get-application-session-configuration \
    --application-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-arn` | **Yes** | string | -- | ARN of the application |

**Output Schema:**
```json
{
    "SessionConfiguration": {
        "SessionDuration": "string"
    }
}
```

---

### 6.17 `describe-application-provider`

Describes an application provider.

**Synopsis:**
```bash
aws sso-admin describe-application-provider \
    --application-provider-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-provider-arn` | **Yes** | string | -- | ARN of the application provider |

**Output Schema:**
```json
{
    "ApplicationProviderArn": "string",
    "DisplayData": {
        "DisplayName": "string",
        "IconUrl": "string",
        "Description": "string"
    },
    "FederationProtocol": "SAML|OAUTH",
    "ResourceServerConfig": {
        "Scopes": {}
    }
}
```
