# Tokens

### 4.1 `create-token`

Creates a long-lived refresh token (JWT) used to obtain access tokens for calling License Manager operations.

**Synopsis:**
```bash
aws license-manager create-token \
    --license-arn <value> \
    --client-token <value> \
    [--role-arns <value>] \
    [--expiration-in-days <value>] \
    [--token-properties <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--license-arn` | **Yes** | string | -- | ARN of the license (mapped to `aud` claim in JWT) |
| `--client-token` | **Yes** | string | -- | Idempotency token (valid for 10 minutes, max 2048 chars) |
| `--role-arns` | No | list(string) | None | IAM role ARNs to embed in the token |
| `--expiration-in-days` | No | integer | 365 | Token expiration in days from creation |
| `--token-properties` | No | list(string) | None | Data included in JWT `amr` claim (max 3 items) |

**Output Schema:**
```json
{
    "TokenId": "string",
    "TokenType": "REFRESH_TOKEN",
    "Token": "string"
}
```

---

### 4.2 `delete-token`

Deletes a token.

**Synopsis:**
```bash
aws license-manager delete-token \
    --token-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--token-id` | **Yes** | string | -- | Token ID to delete |

**Output:** None

---

### 4.3 `list-tokens`

Lists tokens. **Paginated operation.**

**Synopsis:**
```bash
aws license-manager list-tokens \
    [--token-ids <value>] \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--token-ids` | No | list(string) | None | Token IDs to filter by |
| `--filters` | No | list | None | Filters: `LicenseArn`, `Status` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Tokens": [
        {
            "TokenId": "string",
            "TokenType": "REFRESH_TOKEN",
            "LicenseArn": "string",
            "ExpirationTime": "string",
            "TokenProperties": ["string"],
            "RoleArns": ["string"],
            "Status": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.4 `get-access-token`

Gets a temporary access token from a refresh token.

**Synopsis:**
```bash
aws license-manager get-access-token \
    --token <value> \
    [--token-properties <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--token` | **Yes** | string | -- | Refresh token (JWT, max 4096 chars) |
| `--token-properties` | No | list(string) | None | Token properties to include (max 3 items) |

**Output Schema:**
```json
{
    "AccessToken": "string"
}
```
