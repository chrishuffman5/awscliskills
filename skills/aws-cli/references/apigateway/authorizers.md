# Authorizers

### 5.1 `create-authorizer`

Creates an authorizer for a REST API.

**Synopsis:**
```bash
aws apigateway create-authorizer \
    --rest-api-id <value> \
    --name <value> \
    --type <value> \
    [--provider-arns <value>] \
    [--auth-type <value>] \
    [--authorizer-uri <value>] \
    [--authorizer-credentials <value>] \
    [--identity-source <value>] \
    [--identity-validation-expression <value>] \
    [--authorizer-result-ttl-in-seconds <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--name` | **Yes** | string | -- | Name of the authorizer |
| `--type` | **Yes** | string | -- | Authorizer type: `TOKEN`, `REQUEST`, `COGNITO_USER_POOLS` |
| `--provider-arns` | Cond. | list(string) | None | Cognito user pool ARNs (required for `COGNITO_USER_POOLS`) |
| `--auth-type` | No | string | None | Optional customer-defined auth type string |
| `--authorizer-uri` | Cond. | string | None | Lambda function URI (required for `TOKEN` and `REQUEST`) |
| `--authorizer-credentials` | No | string | None | IAM role ARN for invoking the authorizer Lambda |
| `--identity-source` | No | string | `method.request.header.Authorization` | Identity source. For `TOKEN`: header. For `REQUEST`: comma-separated list of sources |
| `--identity-validation-expression` | No | string | None | Regex to validate the token (for `TOKEN` type) |
| `--authorizer-result-ttl-in-seconds` | No | integer | 300 | TTL for cached authorizer results (0-3600). Set to 0 to disable caching |

**Output Schema:**
```json
{
    "id": "string",
    "name": "string",
    "type": "TOKEN|REQUEST|COGNITO_USER_POOLS",
    "providerARNs": ["string"],
    "authType": "string",
    "authorizerUri": "string",
    "authorizerCredentials": "string",
    "identitySource": "string",
    "identityValidationExpression": "string",
    "authorizerResultTtlInSeconds": "integer"
}
```

---

### 5.2 `delete-authorizer`

Deletes an authorizer.

**Synopsis:**
```bash
aws apigateway delete-authorizer \
    --rest-api-id <value> \
    --authorizer-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--authorizer-id` | **Yes** | string | -- | ID of the authorizer to delete |

**Output:** None

---

### 5.3 `get-authorizer`

Gets information about an authorizer.

**Synopsis:**
```bash
aws apigateway get-authorizer \
    --rest-api-id <value> \
    --authorizer-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--authorizer-id` | **Yes** | string | -- | ID of the authorizer |

**Output Schema:** Same as `create-authorizer`.

---

### 5.4 `get-authorizers`

Lists authorizers for a REST API. **Paginated operation.**

**Synopsis:**
```bash
aws apigateway get-authorizers \
    --rest-api-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "items": [
        {
            "id": "string",
            "name": "string",
            "type": "TOKEN|REQUEST|COGNITO_USER_POOLS",
            "providerARNs": ["string"],
            "authType": "string",
            "authorizerUri": "string",
            "authorizerCredentials": "string",
            "identitySource": "string",
            "identityValidationExpression": "string",
            "authorizerResultTtlInSeconds": "integer"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.5 `update-authorizer`

Updates an authorizer using patch operations.

**Synopsis:**
```bash
aws apigateway update-authorizer \
    --rest-api-id <value> \
    --authorizer-id <value> \
    [--patch-operations <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--authorizer-id` | **Yes** | string | -- | ID of the authorizer |
| `--patch-operations` | No | list | None | Patch operations. Shorthand: `op=replace,path=/name,value=new-name` |

**Supported Patch Paths:**
- `/name` — Authorizer name
- `/type` — Authorizer type
- `/authorizerUri` — Lambda function URI
- `/authorizerCredentials` — IAM role ARN
- `/identitySource` — Identity source
- `/identityValidationExpression` — Token validation regex
- `/authorizerResultTtlInSeconds` — Cache TTL
- `/providerARNs` — Cognito user pool ARNs

**Output Schema:** Same as `create-authorizer`.
