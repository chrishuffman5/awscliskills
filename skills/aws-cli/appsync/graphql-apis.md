# GraphQL APIs

### 1.1 `create-graphql-api`

Creates a new GraphQL API.

**Synopsis:**
```bash
aws appsync create-graphql-api \
    --name <value> \
    --authentication-type <value> \
    [--log-config <value>] \
    [--user-pool-config <value>] \
    [--open-id-connect-config <value>] \
    [--tags <value>] \
    [--additional-authentication-providers <value>] \
    [--xray-enabled | --no-xray-enabled] \
    [--lambda-authorizer-config <value>] \
    [--api-type <value>] \
    [--merged-api-execution-role-arn <value>] \
    [--visibility <value>] \
    [--owner-contact <value>] \
    [--introspection-config <value>] \
    [--query-depth-limit <value>] \
    [--resolver-count-limit <value>] \
    [--enhanced-metrics-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | API name (1-65536 chars) |
| `--authentication-type` | **Yes** | string | -- | `API_KEY`, `AWS_IAM`, `AMAZON_COGNITO_USER_POOLS`, `OPENID_CONNECT`, `AWS_LAMBDA` |
| `--log-config` | No | structure | None | CloudWatch Logs configuration |
| `--user-pool-config` | No | structure | None | Cognito user pool configuration |
| `--open-id-connect-config` | No | structure | None | OIDC provider configuration |
| `--tags` | No | map | None | Resource tags (max 50) |
| `--additional-authentication-providers` | No | list | None | Additional auth providers |
| `--xray-enabled` | No | boolean | false | Enable X-Ray tracing |
| `--lambda-authorizer-config` | No | structure | None | Lambda authorizer configuration |
| `--api-type` | No | string | `GRAPHQL` | `GRAPHQL` or `MERGED` |
| `--merged-api-execution-role-arn` | No | string | None | IAM role for merged API execution |
| `--visibility` | No | string | `GLOBAL` | `GLOBAL` or `PRIVATE` (immutable after creation) |
| `--owner-contact` | No | string | None | Owner contact info (0-256 chars) |
| `--introspection-config` | No | string | `ENABLED` | `ENABLED` or `DISABLED` |
| `--query-depth-limit` | No | integer | 0 | Max query depth (0=unlimited, 1-75) |
| `--resolver-count-limit` | No | integer | 0 | Max resolver invocations per request (0=10000, 1-10000) |
| `--enhanced-metrics-config` | No | structure | None | Enhanced metrics configuration |

**LogConfig:**
```json
{
    "fieldLogLevel": "NONE|ERROR|ALL|INFO|DEBUG",
    "cloudWatchLogsRoleArn": "string",
    "excludeVerboseContent": true|false
}
```

**UserPoolConfig:**
```json
{
    "userPoolId": "string",
    "awsRegion": "string",
    "defaultAction": "ALLOW|DENY",
    "appIdClientRegex": "string"
}
```

**OpenIDConnectConfig:**
```json
{
    "issuer": "string",
    "clientId": "string",
    "iatTTL": long,
    "authTTL": long
}
```

**LambdaAuthorizerConfig:**
```json
{
    "authorizerResultTtlInSeconds": integer,
    "authorizerUri": "string",
    "identityValidationExpression": "string"
}
```

**EnhancedMetricsConfig:**
```json
{
    "resolverLevelMetricsBehavior": "FULL_REQUEST_RESOLVER_METRICS|PER_RESOLVER_METRICS",
    "dataSourceLevelMetricsBehavior": "FULL_REQUEST_DATA_SOURCE_METRICS|PER_DATA_SOURCE_METRICS",
    "operationLevelMetricsConfig": "ENABLED|DISABLED"
}
```

**Output Schema:**
```json
{
    "graphqlApi": {
        "name": "string",
        "apiId": "string",
        "authenticationType": "API_KEY|AWS_IAM|AMAZON_COGNITO_USER_POOLS|OPENID_CONNECT|AWS_LAMBDA",
        "logConfig": {},
        "userPoolConfig": {},
        "openIDConnectConfig": {},
        "arn": "string",
        "uris": {"string": "string"},
        "tags": {"string": "string"},
        "additionalAuthenticationProviders": [],
        "xrayEnabled": boolean,
        "wafWebAclArn": "string",
        "lambdaAuthorizerConfig": {},
        "dns": {"string": "string"},
        "visibility": "GLOBAL|PRIVATE",
        "apiType": "GRAPHQL|MERGED",
        "mergedApiExecutionRoleArn": "string",
        "owner": "string",
        "ownerContact": "string",
        "introspectionConfig": "ENABLED|DISABLED",
        "queryDepthLimit": integer,
        "resolverCountLimit": integer,
        "enhancedMetricsConfig": {}
    }
}
```

---

### 1.2 `get-graphql-api`

Retrieves a GraphQL API.

**Synopsis:**
```bash
aws appsync get-graphql-api \
    --api-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |

**Output Schema:**
```json
{
    "graphqlApi": {
        "name": "string",
        "apiId": "string",
        "authenticationType": "API_KEY|AWS_IAM|AMAZON_COGNITO_USER_POOLS|OPENID_CONNECT|AWS_LAMBDA",
        "logConfig": {
            "fieldLogLevel": "NONE|ERROR|ALL|INFO|DEBUG",
            "cloudWatchLogsRoleArn": "string",
            "excludeVerboseContent": boolean
        },
        "userPoolConfig": {
            "userPoolId": "string",
            "awsRegion": "string",
            "defaultAction": "ALLOW|DENY",
            "appIdClientRegex": "string"
        },
        "openIDConnectConfig": {
            "issuer": "string",
            "clientId": "string",
            "iatTTL": long,
            "authTTL": long
        },
        "arn": "string",
        "uris": {"string": "string"},
        "tags": {"string": "string"},
        "additionalAuthenticationProviders": [],
        "xrayEnabled": boolean,
        "wafWebAclArn": "string",
        "lambdaAuthorizerConfig": {
            "authorizerResultTtlInSeconds": integer,
            "authorizerUri": "string",
            "identityValidationExpression": "string"
        },
        "dns": {"string": "string"},
        "visibility": "GLOBAL|PRIVATE",
        "apiType": "GRAPHQL|MERGED",
        "mergedApiExecutionRoleArn": "string",
        "owner": "string",
        "ownerContact": "string",
        "introspectionConfig": "ENABLED|DISABLED",
        "queryDepthLimit": integer,
        "resolverCountLimit": integer,
        "enhancedMetricsConfig": {
            "resolverLevelMetricsBehavior": "FULL_REQUEST_RESOLVER_METRICS|PER_RESOLVER_METRICS",
            "dataSourceLevelMetricsBehavior": "FULL_REQUEST_DATA_SOURCE_METRICS|PER_DATA_SOURCE_METRICS",
            "operationLevelMetricsConfig": "ENABLED|DISABLED"
        }
    }
}
```

---

### 1.3 `list-graphql-apis`

Lists GraphQL APIs. **Paginated operation.**

**Synopsis:**
```bash
aws appsync list-graphql-apis \
    [--api-type <value>] \
    [--owner <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-type` | No | string | None | Filter: `GRAPHQL` or `MERGED` |
| `--owner` | No | string | None | Filter: `CURRENT_ACCOUNT` or `OTHER_ACCOUNTS` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Results per page |
| `--max-items` | No | integer | None | Max total results |

**Output Schema:**
```json
{
    "graphqlApis": [
        {
            "name": "string",
            "apiId": "string",
            "authenticationType": "string",
            "logConfig": {},
            "userPoolConfig": {},
            "openIDConnectConfig": {},
            "arn": "string",
            "uris": {},
            "tags": {},
            "additionalAuthenticationProviders": [],
            "xrayEnabled": boolean,
            "wafWebAclArn": "string",
            "lambdaAuthorizerConfig": {},
            "dns": {},
            "visibility": "GLOBAL|PRIVATE",
            "apiType": "GRAPHQL|MERGED",
            "mergedApiExecutionRoleArn": "string",
            "owner": "string",
            "ownerContact": "string",
            "introspectionConfig": "ENABLED|DISABLED",
            "queryDepthLimit": integer,
            "resolverCountLimit": integer,
            "enhancedMetricsConfig": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 1.4 `update-graphql-api`

Updates a GraphQL API.

**Synopsis:**
```bash
aws appsync update-graphql-api \
    --api-id <value> \
    --name <value> \
    --authentication-type <value> \
    [--log-config <value>] \
    [--user-pool-config <value>] \
    [--open-id-connect-config <value>] \
    [--additional-authentication-providers <value>] \
    [--xray-enabled | --no-xray-enabled] \
    [--lambda-authorizer-config <value>] \
    [--merged-api-execution-role-arn <value>] \
    [--owner-contact <value>] \
    [--introspection-config <value>] \
    [--query-depth-limit <value>] \
    [--resolver-count-limit <value>] \
    [--enhanced-metrics-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--name` | **Yes** | string | -- | New API name |
| `--authentication-type` | **Yes** | string | -- | New primary auth type |
| `--log-config` | No | structure | None | CloudWatch Logs configuration |
| `--user-pool-config` | No | structure | None | Cognito user pool configuration |
| `--open-id-connect-config` | No | structure | None | OIDC configuration |
| `--additional-authentication-providers` | No | list | None | Additional auth providers |
| `--xray-enabled` | No | boolean | None | Enable/disable X-Ray |
| `--lambda-authorizer-config` | No | structure | None | Lambda authorizer configuration |
| `--merged-api-execution-role-arn` | No | string | None | IAM role for merged API |
| `--owner-contact` | No | string | None | Owner contact info |
| `--introspection-config` | No | string | `ENABLED` | `ENABLED` or `DISABLED` |
| `--query-depth-limit` | No | integer | 0 | Max query depth (0=unlimited) |
| `--resolver-count-limit` | No | integer | 0 | Max resolver invocations (0=10000) |
| `--enhanced-metrics-config` | No | structure | None | Enhanced metrics configuration |

**Output Schema:** Same as `create-graphql-api`.

---

### 1.5 `delete-graphql-api`

Deletes a GraphQL API.

**Synopsis:**
```bash
aws appsync delete-graphql-api \
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

### 1.6 `get-graphql-api-environment-variables`

Gets environment variables for a GraphQL API.

**Synopsis:**
```bash
aws appsync get-graphql-api-environment-variables \
    --api-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |

**Output Schema:**
```json
{
    "environmentVariables": {
        "string": "string"
    }
}
```

---

### 1.7 `put-graphql-api-environment-variables`

Sets environment variables for a GraphQL API (replaces all existing variables).

**Synopsis:**
```bash
aws appsync put-graphql-api-environment-variables \
    --api-id <value> \
    --environment-variables <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--environment-variables` | **Yes** | map | -- | Key-value pairs of environment variables |

**Output Schema:**
```json
{
    "environmentVariables": {
        "string": "string"
    }
}
```

---

### 1.8 `get-introspection-schema`

Gets the introspection schema for a GraphQL API.

**Synopsis:**
```bash
aws appsync get-introspection-schema \
    --api-id <value> \
    --format <value> \
    [--include-directives] \
    <outfile> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--format` | **Yes** | string | -- | `SDL` or `JSON` |
| `--include-directives` | No | boolean | false | Include directives in schema |
| `outfile` | **Yes** | string | -- | Output file path |

**Output:** Schema is written to the specified output file.

---

### 1.9 `start-schema-creation`

Uploads a GraphQL schema and begins creation. Asynchronous operation.

**Synopsis:**
```bash
aws appsync start-schema-creation \
    --api-id <value> \
    --definition <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--definition` | **Yes** | blob | -- | Schema definition (use `fileb://` for files) |

**Output Schema:**
```json
{
    "status": "PROCESSING|ACTIVE|DELETING|FAILED|SUCCESS|NOT_APPLICABLE"
}
```

---

### 1.10 `get-schema-creation-status`

Gets the status of a schema creation operation.

**Synopsis:**
```bash
aws appsync get-schema-creation-status \
    --api-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |

**Output Schema:**
```json
{
    "status": "PROCESSING|ACTIVE|DELETING|FAILED|SUCCESS|NOT_APPLICABLE",
    "details": "string"
}
```
