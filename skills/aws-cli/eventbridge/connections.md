# Connections

### 6.1 `create-connection`

Creates a connection for use with API destinations. Connections store authorization credentials for external HTTP endpoints.

**Synopsis:**
```bash
aws events create-connection \
    --name <value> \
    --authorization-type <value> \
    --auth-parameters <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Connection name |
| `--authorization-type` | **Yes** | string | -- | Authorization type: `BASIC`, `OAUTH_CLIENT_CREDENTIALS`, or `API_KEY` |
| `--auth-parameters` | **Yes** | structure | -- | Authorization parameters |
| `--description` | No | string | None | Connection description |

**Auth Parameters — BASIC:**
```json
{
    "BasicAuthParameters": {
        "Username": "string",
        "Password": "string"
    },
    "InvocationHttpParameters": {
        "HeaderParameters": [
            {
                "Key": "string",
                "Value": "string",
                "IsValueSecret": true|false
            }
        ],
        "QueryStringParameters": [
            {
                "Key": "string",
                "Value": "string",
                "IsValueSecret": true|false
            }
        ],
        "BodyParameters": [
            {
                "Key": "string",
                "Value": "string",
                "IsValueSecret": true|false
            }
        ]
    }
}
```

**Auth Parameters — API_KEY:**
```json
{
    "ApiKeyAuthParameters": {
        "ApiKeyName": "string",
        "ApiKeyValue": "string"
    },
    "InvocationHttpParameters": {}
}
```

**Auth Parameters — OAUTH_CLIENT_CREDENTIALS:**
```json
{
    "OAuthParameters": {
        "ClientParameters": {
            "ClientID": "string",
            "ClientSecret": "string"
        },
        "AuthorizationEndpoint": "string",
        "HttpMethod": "GET|POST|PUT",
        "OAuthHttpParameters": {
            "HeaderParameters": [],
            "QueryStringParameters": [],
            "BodyParameters": []
        }
    },
    "InvocationHttpParameters": {}
}
```

**Output Schema:**
```json
{
    "ConnectionArn": "string",
    "ConnectionState": "CREATING|UPDATING|DELETING|AUTHORIZED|DEAUTHORIZED|AUTHORIZING|DEAUTHORIZING",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp"
}
```

---

### 6.2 `delete-connection`

Deletes a connection.

**Synopsis:**
```bash
aws events delete-connection \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Connection name or ARN to delete |

**Output Schema:**
```json
{
    "ConnectionArn": "string",
    "ConnectionState": "DELETING",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp",
    "LastAuthorizedTime": "timestamp"
}
```

---

### 6.3 `describe-connection`

Retrieves details about a connection.

**Synopsis:**
```bash
aws events describe-connection \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Connection name or ARN |

**Output Schema:**
```json
{
    "ConnectionArn": "string",
    "Name": "string",
    "Description": "string",
    "ConnectionState": "CREATING|UPDATING|DELETING|AUTHORIZED|DEAUTHORIZED|AUTHORIZING|DEAUTHORIZING",
    "StateReason": "string",
    "AuthorizationType": "BASIC|OAUTH_CLIENT_CREDENTIALS|API_KEY",
    "AuthParameters": {
        "BasicAuthParameters": {
            "Username": "string"
        },
        "OAuthParameters": {
            "ClientParameters": {
                "ClientID": "string"
            },
            "AuthorizationEndpoint": "string",
            "HttpMethod": "GET|POST|PUT",
            "OAuthHttpParameters": {}
        },
        "ApiKeyAuthParameters": {
            "ApiKeyName": "string"
        },
        "InvocationHttpParameters": {}
    },
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp",
    "LastAuthorizedTime": "timestamp"
}
```

---

### 6.4 `list-connections`

Lists all connections. Supports filtering by name prefix, state, or connection name. **Paginated operation.**

**Synopsis:**
```bash
aws events list-connections \
    [--name-prefix <value>] \
    [--connection-state <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name-prefix` | No | string | None | Filter by connection name prefix |
| `--connection-state` | No | string | None | Filter by state |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Connections": [
        {
            "ConnectionArn": "string",
            "Name": "string",
            "ConnectionState": "string",
            "StateReason": "string",
            "AuthorizationType": "BASIC|OAUTH_CLIENT_CREDENTIALS|API_KEY",
            "CreationTime": "timestamp",
            "LastModifiedTime": "timestamp",
            "LastAuthorizedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.5 `update-connection`

Updates a connection's authorization parameters and description.

**Synopsis:**
```bash
aws events update-connection \
    --name <value> \
    [--description <value>] \
    [--authorization-type <value>] \
    [--auth-parameters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Connection name or ARN |
| `--description` | No | string | None | Updated description |
| `--authorization-type` | No | string | None | Updated authorization type |
| `--auth-parameters` | No | structure | None | Updated auth parameters (same structure as create) |

**Output Schema:**
```json
{
    "ConnectionArn": "string",
    "ConnectionState": "UPDATING",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp",
    "LastAuthorizedTime": "timestamp"
}
```

---

### 6.6 `deauthorize-connection`

Removes the authorization credentials from a connection, requiring reauthorization.

**Synopsis:**
```bash
aws events deauthorize-connection \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Connection name or ARN |

**Output Schema:**
```json
{
    "ConnectionArn": "string",
    "ConnectionState": "DEAUTHORIZING",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp",
    "LastAuthorizedTime": "timestamp"
}
```
