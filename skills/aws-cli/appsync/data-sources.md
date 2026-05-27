# Data Sources

### 3.1 `create-data-source`

Creates a data source for a GraphQL API.

**Synopsis:**
```bash
aws appsync create-data-source \
    --api-id <value> \
    --name <value> \
    --type <value> \
    [--description <value>] \
    [--service-role-arn <value>] \
    [--dynamodb-config <value>] \
    [--lambda-config <value>] \
    [--elasticsearch-config <value>] \
    [--open-search-service-config <value>] \
    [--http-config <value>] \
    [--relational-database-config <value>] \
    [--event-bridge-config <value>] \
    [--metrics-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--name` | **Yes** | string | -- | Data source name (1-65536 chars) |
| `--type` | **Yes** | string | -- | `AWS_LAMBDA`, `AMAZON_DYNAMODB`, `AMAZON_ELASTICSEARCH`, `NONE`, `HTTP`, `RELATIONAL_DATABASE`, `AMAZON_OPENSEARCH_SERVICE`, `AMAZON_EVENTBRIDGE`, `AMAZON_BEDROCK_RUNTIME` |
| `--description` | No | string | None | Description |
| `--service-role-arn` | No | string | None | IAM service role ARN |
| `--dynamodb-config` | No | structure | None | DynamoDB settings |
| `--lambda-config` | No | structure | None | Lambda settings |
| `--elasticsearch-config` | No | structure | None | OpenSearch settings (deprecated) |
| `--open-search-service-config` | No | structure | None | OpenSearch Service settings |
| `--http-config` | No | structure | None | HTTP endpoint settings |
| `--relational-database-config` | No | structure | None | RDS settings |
| `--event-bridge-config` | No | structure | None | EventBridge settings |
| `--metrics-config` | No | string | None | `ENABLED` or `DISABLED` |

**DynamodbConfig:**
```json
{
    "tableName": "string",
    "awsRegion": "string",
    "useCallerCredentials": true|false,
    "deltaSyncConfig": {
        "baseTableTTL": long,
        "deltaSyncTableName": "string",
        "deltaSyncTableTTL": long
    },
    "versioned": true|false
}
```

**LambdaConfig:**
```json
{
    "lambdaFunctionArn": "string"
}
```

**OpenSearchServiceConfig:**
```json
{
    "endpoint": "string",
    "awsRegion": "string"
}
```

**HttpConfig:**
```json
{
    "endpoint": "string",
    "authorizationConfig": {
        "authorizationType": "AWS_IAM",
        "awsIamConfig": {
            "signingRegion": "string",
            "signingServiceName": "string"
        }
    }
}
```

**RelationalDatabaseConfig:**
```json
{
    "relationalDatabaseSourceType": "RDS_HTTP_ENDPOINT",
    "rdsHttpEndpointConfig": {
        "awsRegion": "string",
        "dbClusterIdentifier": "string",
        "databaseName": "string",
        "schema": "string",
        "awsSecretStoreArn": "string"
    }
}
```

**EventBridgeConfig:**
```json
{
    "eventBusArn": "string"
}
```

**Output Schema:**
```json
{
    "dataSource": {
        "dataSourceArn": "string",
        "name": "string",
        "description": "string",
        "type": "string",
        "serviceRoleArn": "string",
        "dynamodbConfig": {
            "tableName": "string",
            "awsRegion": "string",
            "useCallerCredentials": boolean,
            "deltaSyncConfig": {},
            "versioned": boolean
        },
        "lambdaConfig": {"lambdaFunctionArn": "string"},
        "elasticsearchConfig": {"endpoint": "string", "awsRegion": "string"},
        "openSearchServiceConfig": {"endpoint": "string", "awsRegion": "string"},
        "httpConfig": {
            "endpoint": "string",
            "authorizationConfig": {}
        },
        "relationalDatabaseConfig": {
            "relationalDatabaseSourceType": "string",
            "rdsHttpEndpointConfig": {}
        },
        "eventBridgeConfig": {"eventBusArn": "string"},
        "metricsConfig": "ENABLED|DISABLED"
    }
}
```

---

### 3.2 `get-data-source`

Retrieves a data source.

**Synopsis:**
```bash
aws appsync get-data-source \
    --api-id <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--name` | **Yes** | string | -- | The data source name |

**Output Schema:** Same as `create-data-source`.

---

### 3.3 `list-data-sources`

Lists data sources for a GraphQL API. **Paginated operation.**

**Synopsis:**
```bash
aws appsync list-data-sources \
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
    "dataSources": [
        {
            "dataSourceArn": "string",
            "name": "string",
            "description": "string",
            "type": "string",
            "serviceRoleArn": "string",
            "dynamodbConfig": {},
            "lambdaConfig": {},
            "elasticsearchConfig": {},
            "openSearchServiceConfig": {},
            "httpConfig": {},
            "relationalDatabaseConfig": {},
            "eventBridgeConfig": {},
            "metricsConfig": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 3.4 `update-data-source`

Updates a data source.

**Synopsis:**
```bash
aws appsync update-data-source \
    --api-id <value> \
    --name <value> \
    --type <value> \
    [--description <value>] \
    [--service-role-arn <value>] \
    [--dynamodb-config <value>] \
    [--lambda-config <value>] \
    [--elasticsearch-config <value>] \
    [--open-search-service-config <value>] \
    [--http-config <value>] \
    [--relational-database-config <value>] \
    [--event-bridge-config <value>] \
    [--metrics-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--name` | **Yes** | string | -- | The data source name |
| `--type` | **Yes** | string | -- | The new data source type |
| `--description` | No | string | None | Updated description |
| `--service-role-arn` | No | string | None | Updated IAM role |
| `--dynamodb-config` | No | structure | None | Updated DynamoDB config |
| `--lambda-config` | No | structure | None | Updated Lambda config |
| `--elasticsearch-config` | No | structure | None | Updated OpenSearch config (deprecated) |
| `--open-search-service-config` | No | structure | None | Updated OpenSearch config |
| `--http-config` | No | structure | None | Updated HTTP config |
| `--relational-database-config` | No | structure | None | Updated RDS config |
| `--event-bridge-config` | No | structure | None | Updated EventBridge config |
| `--metrics-config` | No | string | None | `ENABLED` or `DISABLED` |

**Output Schema:** Same as `create-data-source`.

---

### 3.5 `delete-data-source`

Deletes a data source.

**Synopsis:**
```bash
aws appsync delete-data-source \
    --api-id <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The API ID |
| `--name` | **Yes** | string | -- | The data source name to delete |

**Output:** None

---

### 3.6 `start-data-source-introspection`

Starts introspection of a data source to discover its schema. Asynchronous operation.

**Synopsis:**
```bash
aws appsync start-data-source-introspection \
    [--rds-data-api-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rds-data-api-config` | No | structure | None | RDS Data API configuration for introspection |

**RdsDataApiConfig:**
```json
{
    "resourceArn": "string",
    "secretArn": "string",
    "databaseName": "string"
}
```

**Output Schema:**
```json
{
    "introspectionId": "string",
    "introspectionStatus": "PROCESSING|FAILED|SUCCESS",
    "introspectionStatusDetail": "string"
}
```

---

### 3.7 `get-data-source-introspection`

Gets the results of a data source introspection.

**Synopsis:**
```bash
aws appsync get-data-source-introspection \
    --introspection-id <value> \
    [--include-models-sdl] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--introspection-id` | **Yes** | string | -- | The introspection ID from start-data-source-introspection |
| `--include-models-sdl` | No | boolean | false | Include GraphQL SDL of discovered models |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Results per page |
| `--max-items` | No | integer | None | Max total results |

**Output Schema:**
```json
{
    "introspectionId": "string",
    "introspectionStatus": "PROCESSING|FAILED|SUCCESS",
    "introspectionStatusDetail": "string",
    "introspectionResult": {
        "models": [
            {
                "name": "string",
                "fields": [
                    {
                        "name": "string",
                        "type": {"kind": "string", "name": "string", "type": {}},
                        "length": long
                    }
                ],
                "primaryKey": {"name": "string", "fields": ["string"]},
                "indexes": [{"name": "string", "fields": ["string"]}],
                "sdl": "string"
            }
        ],
        "nextToken": "string"
    }
}
```
