# Identity Providers

### 6.1 `associate-identity-provider-config`

Associates an OIDC identity provider configuration with a cluster for authentication.

**Synopsis:**
```bash
aws eks associate-identity-provider-config \
    --cluster-name <value> \
    --oidc <value> \
    [--tags <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--oidc` | **Yes** | structure | -- | OIDC config. Shorthand: `identityProviderConfigName=string,issuerUrl=string,clientId=string,usernameClaim=string,usernamePrefix=string,groupsClaim=string,groupsPrefix=string,requiredClaims={key=value}` |
| `--tags` | No | map | None | Tags |
| `--client-request-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "update": {
        "id": "string",
        "status": "InProgress|Failed|Cancelled|Successful",
        "type": "AssociateIdentityProviderConfig",
        "params": [],
        "createdAt": "timestamp",
        "errors": []
    },
    "tags": {"string": "string"}
}
```

---

### 6.2 `disassociate-identity-provider-config`

Disassociates an identity provider configuration from a cluster.

**Synopsis:**
```bash
aws eks disassociate-identity-provider-config \
    --cluster-name <value> \
    --identity-provider-config <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--identity-provider-config` | **Yes** | structure | -- | Identity provider config. Shorthand: `type=oidc,name=string` |
| `--client-request-token` | No | string | None | Idempotency token |

**Output Schema:** Update object.

---

### 6.3 `describe-identity-provider-config`

Describes an identity provider configuration.

**Synopsis:**
```bash
aws eks describe-identity-provider-config \
    --cluster-name <value> \
    --identity-provider-config <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--identity-provider-config` | **Yes** | structure | -- | Shorthand: `type=oidc,name=string` |

**Output Schema:**
```json
{
    "identityProviderConfig": {
        "oidc": {
            "identityProviderConfigName": "string",
            "identityProviderConfigArn": "string",
            "clusterName": "string",
            "issuerUrl": "string",
            "clientId": "string",
            "usernameClaim": "string",
            "usernamePrefix": "string",
            "groupsClaim": "string",
            "groupsPrefix": "string",
            "requiredClaims": {"string": "string"},
            "tags": {"string": "string"},
            "status": "CREATING|DELETING|ACTIVE"
        }
    }
}
```

---

### 6.4 `list-identity-provider-configs`

Lists the identity provider configurations for a cluster. **Paginated operation.**

**Synopsis:**
```bash
aws eks list-identity-provider-configs \
    --cluster-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "identityProviderConfigs": [
        {
            "type": "oidc",
            "name": "string"
        }
    ],
    "nextToken": "string"
}
```
