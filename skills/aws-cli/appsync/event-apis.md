# Event APIs

### 2.1 `create-api`

Creates a new Event API for real-time pub/sub messaging.

**Synopsis:**
```bash
aws appsync create-api \
    --name <value> \
    --event-config <value> \
    [--owner-contact <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | API name (1-50 chars) |
| `--event-config` | **Yes** | structure | -- | Event API configuration |
| `--owner-contact` | No | string | None | Owner contact information |
| `--tags` | No | map | None | Resource tags (max 50) |

**EventConfig:**
```json
{
    "authProviders": [
        {
            "authType": "API_KEY|AWS_IAM|AMAZON_COGNITO_USER_POOLS|OPENID_CONNECT|AWS_LAMBDA",
            "cognitoConfig": {
                "userPoolId": "string",
                "awsRegion": "string",
                "appIdClientRegex": "string"
            },
            "openIDConnectConfig": {
                "issuer": "string",
                "clientId": "string",
                "iatTTL": long,
                "authTTL": long
            },
            "lambdaAuthorizerConfig": {
                "authorizerResultTtlInSeconds": integer,
                "authorizerUri": "string",
                "identityValidationExpression": "string"
            }
        }
    ],
    "connectionAuthModes": [{"authType": "string"}],
    "defaultPublishAuthModes": [{"authType": "string"}],
    "defaultSubscribeAuthModes": [{"authType": "string"}],
    "logConfig": {
        "logLevel": "NONE|ERROR|ALL|INFO|DEBUG",
        "cloudWatchLogsRoleArn": "string"
    }
}
```

**Output Schema:**
```json
{
    "api": {
        "apiId": "string",
        "name": "string",
        "ownerContact": "string",
        "tags": {"string": "string"},
        "dns": {"string": "string"},
        "apiArn": "string",
        "created": "timestamp",
        "xrayEnabled": boolean,
        "wafWebAclArn": "string",
        "eventConfig": {
            "authProviders": [],
            "connectionAuthModes": [],
            "defaultPublishAuthModes": [],
            "defaultSubscribeAuthModes": [],
            "logConfig": {
                "logLevel": "string",
                "cloudWatchLogsRoleArn": "string"
            }
        }
    }
}
```

---

### 2.2 `get-api`

Retrieves an Event API.

**Synopsis:**
```bash
aws appsync get-api \
    --api-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |

**Output Schema:** Same as `create-api`.

---

### 2.3 `list-apis`

Lists Event APIs. **Paginated operation.**

**Synopsis:**
```bash
aws appsync list-apis \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Results per page |
| `--max-items` | No | integer | None | Max total results |

**Output Schema:**
```json
{
    "apis": [
        {
            "apiId": "string",
            "name": "string",
            "ownerContact": "string",
            "tags": {},
            "dns": {},
            "apiArn": "string",
            "created": "timestamp",
            "xrayEnabled": boolean,
            "wafWebAclArn": "string",
            "eventConfig": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 2.4 `update-api`

Updates an Event API.

**Synopsis:**
```bash
aws appsync update-api \
    --api-id <value> \
    --name <value> \
    [--owner-contact <value>] \
    [--event-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--name` | **Yes** | string | -- | New API name |
| `--owner-contact` | No | string | None | Updated owner contact |
| `--event-config` | No | structure | None | Updated event configuration |

**Output Schema:** Same as `create-api`.

---

### 2.5 `delete-api`

Deletes an Event API.

**Synopsis:**
```bash
aws appsync delete-api \
    --api-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID to delete |

**Output:** None

---

### 2.6 `create-channel-namespace`

Creates a channel namespace for an Event API.

**Synopsis:**
```bash
aws appsync create-channel-namespace \
    --api-id <value> \
    --name <value> \
    [--subscribe-auth-modes <value>] \
    [--publish-auth-modes <value>] \
    [--code-handlers <value>] \
    [--tags <value>] \
    [--handler-configs <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--name` | **Yes** | string | -- | Namespace name (1-50 chars, alphanumeric and hyphens) |
| `--subscribe-auth-modes` | No | list | None | Auth modes for subscribing |
| `--publish-auth-modes` | No | list | None | Auth modes for publishing |
| `--code-handlers` | No | string | None | Event handler functions (1-32768 chars) |
| `--tags` | No | map | None | Resource tags (max 50) |
| `--handler-configs` | No | structure | None | Handler configuration for OnPublish/OnSubscribe |

**HandlerConfigs:**
```json
{
    "onPublish": {
        "behavior": "CODE|DIRECT",
        "integration": {
            "dataSourceName": "string",
            "lambdaConfig": {
                "invokeType": "REQUEST_RESPONSE|EVENT"
            }
        }
    },
    "onSubscribe": {
        "behavior": "CODE|DIRECT",
        "integration": {
            "dataSourceName": "string",
            "lambdaConfig": {
                "invokeType": "REQUEST_RESPONSE|EVENT"
            }
        }
    }
}
```

**Output Schema:**
```json
{
    "channelNamespace": {
        "apiId": "string",
        "name": "string",
        "subscribeAuthModes": [{"authType": "string"}],
        "publishAuthModes": [{"authType": "string"}],
        "codeHandlers": "string",
        "tags": {"string": "string"},
        "channelNamespaceArn": "string",
        "created": "timestamp",
        "lastModified": "timestamp",
        "handlerConfigs": {}
    }
}
```

---

### 2.7 `get-channel-namespace`

Retrieves a channel namespace.

**Synopsis:**
```bash
aws appsync get-channel-namespace \
    --api-id <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--name` | **Yes** | string | -- | The channel namespace name |

**Output Schema:** Same as `create-channel-namespace`.

---

### 2.8 `list-channel-namespaces`

Lists channel namespaces for an Event API. **Paginated operation.**

**Synopsis:**
```bash
aws appsync list-channel-namespaces \
    --api-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Results per page |
| `--max-items` | No | integer | None | Max total results |

**Output Schema:**
```json
{
    "channelNamespaces": [
        {
            "apiId": "string",
            "name": "string",
            "subscribeAuthModes": [],
            "publishAuthModes": [],
            "codeHandlers": "string",
            "tags": {},
            "channelNamespaceArn": "string",
            "created": "timestamp",
            "lastModified": "timestamp",
            "handlerConfigs": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 2.9 `update-channel-namespace`

Updates a channel namespace.

**Synopsis:**
```bash
aws appsync update-channel-namespace \
    --api-id <value> \
    --name <value> \
    [--subscribe-auth-modes <value>] \
    [--publish-auth-modes <value>] \
    [--code-handlers <value>] \
    [--handler-configs <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--name` | **Yes** | string | -- | The channel namespace name |
| `--subscribe-auth-modes` | No | list | None | Updated subscribe auth modes |
| `--publish-auth-modes` | No | list | None | Updated publish auth modes |
| `--code-handlers` | No | string | None | Updated event handler functions |
| `--handler-configs` | No | structure | None | Updated handler configuration |

**Output Schema:** Same as `create-channel-namespace`.

---

### 2.10 `delete-channel-namespace`

Deletes a channel namespace.

**Synopsis:**
```bash
aws appsync delete-channel-namespace \
    --api-id <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--name` | **Yes** | string | -- | The channel namespace name to delete |

**Output:** None
