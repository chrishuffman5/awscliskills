# Identity Sources

### 4.1 `create-identity-source`

Creates an identity source to connect a Cognito user pool or OIDC provider to a policy store for token-based authorization.

**Synopsis:**
```bash
aws verifiedpermissions create-identity-source \
    --policy-store-id <value> \
    --configuration <value> \
    [--client-token <value>] \
    [--principal-entity-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-store-id` | **Yes** | string | -- | Policy store ID (1-200 chars) |
| `--configuration` | **Yes** | tagged union | -- | Identity provider configuration (Cognito or OIDC) |
| `--client-token` | No | string | Auto-generated | Idempotency token (1-64 chars) |
| `--principal-entity-type` | No | string | None | Entity type for authenticated principals (1-200 chars) |

**Configuration Structure (Cognito):**
```json
{
    "cognitoUserPoolConfiguration": {
        "userPoolArn": "string",
        "clientIds": ["string"],
        "groupConfiguration": {
            "groupEntityType": "string"
        }
    }
}
```

**Configuration Structure (OIDC):**
```json
{
    "openIdConnectConfiguration": {
        "issuer": "string",
        "entityIdPrefix": "string",
        "groupConfiguration": {
            "groupClaim": "string",
            "groupEntityType": "string"
        },
        "tokenSelection": {
            "accessTokenOnly": {
                "principalIdClaim": "string",
                "audiences": ["string"]
            },
            "identityTokenOnly": {
                "principalIdClaim": "string",
                "clientIds": ["string"]
            }
        }
    }
}
```

**Output Schema:**
```json
{
    "createdDate": "timestamp",
    "identitySourceId": "string",
    "lastUpdatedDate": "timestamp",
    "policyStoreId": "string"
}
```

---

### 4.2 `delete-identity-source`

Deletes the specified identity source.

**Synopsis:**
```bash
aws verifiedpermissions delete-identity-source \
    --policy-store-id <value> \
    --identity-source-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-store-id` | **Yes** | string | -- | Policy store ID |
| `--identity-source-id` | **Yes** | string | -- | ID of the identity source to delete |

**Output Schema:**

No output fields (empty response on success).

---

### 4.3 `get-identity-source`

Retrieves details about the specified identity source.

**Synopsis:**
```bash
aws verifiedpermissions get-identity-source \
    --policy-store-id <value> \
    --identity-source-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-store-id` | **Yes** | string | -- | Policy store ID |
| `--identity-source-id` | **Yes** | string | -- | ID of the identity source to retrieve |

**Output Schema:**
```json
{
    "createdDate": "timestamp",
    "details": {
        "clientIds": ["string"],
        "userPoolArn": "string",
        "discoveryUrl": "string",
        "openIdIssuer": "COGNITO"
    },
    "identitySourceId": "string",
    "lastUpdatedDate": "timestamp",
    "policyStoreId": "string",
    "principalEntityType": "string",
    "configuration": {
        "cognitoUserPoolConfiguration": {
            "userPoolArn": "string",
            "clientIds": ["string"],
            "issuer": "string",
            "groupConfiguration": {
                "groupEntityType": "string"
            }
        },
        "openIdConnectConfiguration": {
            "issuer": "string",
            "entityIdPrefix": "string",
            "groupConfiguration": {
                "groupClaim": "string",
                "groupEntityType": "string"
            },
            "tokenSelection": {
                "accessTokenOnly": {
                    "principalIdClaim": "string",
                    "audiences": ["string"]
                },
                "identityTokenOnly": {
                    "principalIdClaim": "string",
                    "clientIds": ["string"]
                }
            }
        }
    }
}
```

---

### 4.4 `list-identity-sources`

Lists identity sources in the specified policy store. **Paginated operation.**

**Synopsis:**
```bash
aws verifiedpermissions list-identity-sources \
    --policy-store-id <value> \
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
| `--policy-store-id` | **Yes** | string | -- | Policy store ID |
| `--filters` | No | list | None | Filters for identity source list |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "identitySources": [
        {
            "createdDate": "timestamp",
            "details": {
                "clientIds": ["string"],
                "userPoolArn": "string",
                "discoveryUrl": "string",
                "openIdIssuer": "COGNITO"
            },
            "identitySourceId": "string",
            "lastUpdatedDate": "timestamp",
            "policyStoreId": "string",
            "principalEntityType": "string",
            "configuration": {
                "cognitoUserPoolConfiguration": {
                    "userPoolArn": "string",
                    "clientIds": ["string"],
                    "issuer": "string",
                    "groupConfiguration": {
                        "groupEntityType": "string"
                    }
                },
                "openIdConnectConfiguration": {
                    "issuer": "string",
                    "entityIdPrefix": "string",
                    "groupConfiguration": {
                        "groupClaim": "string",
                        "groupEntityType": "string"
                    },
                    "tokenSelection": {}
                }
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 4.5 `update-identity-source`

Updates the specified identity source configuration.

**Synopsis:**
```bash
aws verifiedpermissions update-identity-source \
    --policy-store-id <value> \
    --identity-source-id <value> \
    --update-configuration <value> \
    [--principal-entity-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-store-id` | **Yes** | string | -- | Policy store ID |
| `--identity-source-id` | **Yes** | string | -- | ID of the identity source to update |
| `--update-configuration` | **Yes** | tagged union | -- | Updated identity provider configuration |
| `--principal-entity-type` | No | string | None | Updated entity type for authenticated principals |

**Output Schema:**
```json
{
    "createdDate": "timestamp",
    "identitySourceId": "string",
    "lastUpdatedDate": "timestamp",
    "policyStoreId": "string"
}
```
