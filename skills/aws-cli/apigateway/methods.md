# Methods

### 3.1 `put-method`

Adds a method to a resource with authorization settings.

**Synopsis:**
```bash
aws apigateway put-method \
    --rest-api-id <value> \
    --resource-id <value> \
    --http-method <value> \
    --authorization-type <value> \
    [--authorizer-id <value>] \
    [--api-key-required | --no-api-key-required] \
    [--operation-name <value>] \
    [--request-parameters <value>] \
    [--request-models <value>] \
    [--request-validator-id <value>] \
    [--authorization-scopes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--resource-id` | **Yes** | string | -- | ID of the resource |
| `--http-method` | **Yes** | string | -- | HTTP method: `GET`, `POST`, `PUT`, `DELETE`, `PATCH`, `HEAD`, `OPTIONS`, `ANY` |
| `--authorization-type` | **Yes** | string | -- | Authorization type: `NONE`, `AWS_IAM`, `CUSTOM`, `COGNITO_USER_POOLS` |
| `--authorizer-id` | No | string | None | ID of the authorizer (required when authorization-type is `CUSTOM` or `COGNITO_USER_POOLS`) |
| `--api-key-required` | No | boolean | false | Whether API key is required |
| `--operation-name` | No | string | None | Human-friendly operation name |
| `--request-parameters` | No | map | None | Request parameters. Shorthand: `method.request.querystring.name=true,method.request.header.X-Custom=false` |
| `--request-models` | No | map | None | Request models by content type. Shorthand: `application/json=ModelName` |
| `--request-validator-id` | No | string | None | ID of request validator |
| `--authorization-scopes` | No | list(string) | None | OAuth scopes for COGNITO_USER_POOLS authorization |

**Output Schema:**
```json
{
    "httpMethod": "string",
    "authorizationType": "string",
    "authorizerId": "string",
    "apiKeyRequired": "boolean",
    "requestValidatorId": "string",
    "operationName": "string",
    "requestParameters": {
        "string": "boolean"
    },
    "requestModels": {
        "string": "string"
    },
    "methodResponses": {},
    "methodIntegration": null,
    "authorizationScopes": ["string"]
}
```

---

### 3.2 `get-method`

Gets information about a method on a resource.

**Synopsis:**
```bash
aws apigateway get-method \
    --rest-api-id <value> \
    --resource-id <value> \
    --http-method <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--resource-id` | **Yes** | string | -- | ID of the resource |
| `--http-method` | **Yes** | string | -- | HTTP method |

**Output Schema:**
```json
{
    "httpMethod": "string",
    "authorizationType": "string",
    "authorizerId": "string",
    "apiKeyRequired": "boolean",
    "requestValidatorId": "string",
    "operationName": "string",
    "requestParameters": {
        "string": "boolean"
    },
    "requestModels": {
        "string": "string"
    },
    "methodResponses": {
        "string": {
            "statusCode": "string",
            "responseParameters": {
                "string": "boolean"
            },
            "responseModels": {
                "string": "string"
            }
        }
    },
    "methodIntegration": {
        "type": "HTTP|AWS|MOCK|HTTP_PROXY|AWS_PROXY",
        "httpMethod": "string",
        "uri": "string",
        "connectionType": "INTERNET|VPC_LINK",
        "connectionId": "string",
        "credentials": "string",
        "requestParameters": {},
        "requestTemplates": {},
        "passthroughBehavior": "string",
        "contentHandling": "CONVERT_TO_BINARY|CONVERT_TO_TEXT",
        "timeoutInMillis": "integer",
        "cacheNamespace": "string",
        "cacheKeyParameters": ["string"],
        "integrationResponses": {}
    },
    "authorizationScopes": ["string"]
}
```

---

### 3.3 `delete-method`

Deletes a method from a resource.

**Synopsis:**
```bash
aws apigateway delete-method \
    --rest-api-id <value> \
    --resource-id <value> \
    --http-method <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--resource-id` | **Yes** | string | -- | ID of the resource |
| `--http-method` | **Yes** | string | -- | HTTP method |

**Output:** None

---

### 3.4 `put-method-response`

Adds a method response to a method.

**Synopsis:**
```bash
aws apigateway put-method-response \
    --rest-api-id <value> \
    --resource-id <value> \
    --http-method <value> \
    --status-code <value> \
    [--response-parameters <value>] \
    [--response-models <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--resource-id` | **Yes** | string | -- | ID of the resource |
| `--http-method` | **Yes** | string | -- | HTTP method |
| `--status-code` | **Yes** | string | -- | HTTP status code (e.g., `200`, `400`, `500`) |
| `--response-parameters` | No | map | None | Response parameters. Shorthand: `method.response.header.X-Custom=true` |
| `--response-models` | No | map | None | Response models by content type. Shorthand: `application/json=ModelName` |

**Output Schema:**
```json
{
    "statusCode": "string",
    "responseParameters": {
        "string": "boolean"
    },
    "responseModels": {
        "string": "string"
    }
}
```

---

### 3.5 `get-method-response`

Gets a method response.

**Synopsis:**
```bash
aws apigateway get-method-response \
    --rest-api-id <value> \
    --resource-id <value> \
    --http-method <value> \
    --status-code <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--resource-id` | **Yes** | string | -- | ID of the resource |
| `--http-method` | **Yes** | string | -- | HTTP method |
| `--status-code` | **Yes** | string | -- | HTTP status code |

**Output Schema:** Same as `put-method-response`.

---

### 3.6 `delete-method-response`

Deletes a method response.

**Synopsis:**
```bash
aws apigateway delete-method-response \
    --rest-api-id <value> \
    --resource-id <value> \
    --http-method <value> \
    --status-code <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--resource-id` | **Yes** | string | -- | ID of the resource |
| `--http-method` | **Yes** | string | -- | HTTP method |
| `--status-code` | **Yes** | string | -- | HTTP status code |

**Output:** None

---

### 3.7 `put-integration`

Sets up an integration for a method.

**Synopsis:**
```bash
aws apigateway put-integration \
    --rest-api-id <value> \
    --resource-id <value> \
    --http-method <value> \
    --type <value> \
    [--integration-http-method <value>] \
    [--uri <value>] \
    [--connection-type <value>] \
    [--connection-id <value>] \
    [--credentials <value>] \
    [--request-parameters <value>] \
    [--request-templates <value>] \
    [--passthrough-behavior <value>] \
    [--cache-namespace <value>] \
    [--cache-key-parameters <value>] \
    [--content-handling <value>] \
    [--timeout-in-millis <value>] \
    [--tls-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--resource-id` | **Yes** | string | -- | ID of the resource |
| `--http-method` | **Yes** | string | -- | HTTP method |
| `--type` | **Yes** | string | -- | Integration type: `HTTP`, `AWS`, `MOCK`, `HTTP_PROXY`, `AWS_PROXY` |
| `--integration-http-method` | Cond. | string | None | HTTP method for the backend (required for HTTP, AWS, HTTP_PROXY, AWS_PROXY). Usually `POST` for Lambda |
| `--uri` | Cond. | string | None | Integration endpoint URI (required for HTTP, AWS, HTTP_PROXY, AWS_PROXY) |
| `--connection-type` | No | string | `INTERNET` | Connection type: `INTERNET` or `VPC_LINK` |
| `--connection-id` | Cond. | string | None | VPC link ID (required when connection-type is `VPC_LINK`) |
| `--credentials` | No | string | None | IAM role ARN for API Gateway to assume when calling the backend |
| `--request-parameters` | No | map | None | Maps method request parameters to integration request parameters |
| `--request-templates` | No | map | None | Velocity templates by content type |
| `--passthrough-behavior` | No | string | None | Passthrough: `WHEN_NO_MATCH`, `WHEN_NO_TEMPLATES`, `NEVER` |
| `--cache-namespace` | No | string | None | Cache namespace |
| `--cache-key-parameters` | No | list(string) | None | Cache key parameters |
| `--content-handling` | No | string | None | Content handling: `CONVERT_TO_BINARY` or `CONVERT_TO_TEXT` |
| `--timeout-in-millis` | No | integer | 29000 | Integration timeout (50-29000 ms) |
| `--tls-config` | No | structure | None | TLS configuration. Shorthand: `insecureSkipVerification=true\|false` |

**Output Schema:**
```json
{
    "type": "HTTP|AWS|MOCK|HTTP_PROXY|AWS_PROXY",
    "httpMethod": "string",
    "uri": "string",
    "connectionType": "INTERNET|VPC_LINK",
    "connectionId": "string",
    "credentials": "string",
    "requestParameters": {
        "string": "string"
    },
    "requestTemplates": {
        "string": "string"
    },
    "passthroughBehavior": "WHEN_NO_MATCH|WHEN_NO_TEMPLATES|NEVER",
    "contentHandling": "CONVERT_TO_BINARY|CONVERT_TO_TEXT",
    "timeoutInMillis": "integer",
    "cacheNamespace": "string",
    "cacheKeyParameters": ["string"],
    "integrationResponses": {},
    "tlsConfig": {
        "insecureSkipVerification": "boolean"
    }
}
```

---

### 3.8 `get-integration`

Gets the integration for a method.

**Synopsis:**
```bash
aws apigateway get-integration \
    --rest-api-id <value> \
    --resource-id <value> \
    --http-method <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--resource-id` | **Yes** | string | -- | ID of the resource |
| `--http-method` | **Yes** | string | -- | HTTP method |

**Output Schema:** Same as `put-integration`.

---

### 3.9 `delete-integration`

Deletes an integration from a method.

**Synopsis:**
```bash
aws apigateway delete-integration \
    --rest-api-id <value> \
    --resource-id <value> \
    --http-method <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--resource-id` | **Yes** | string | -- | ID of the resource |
| `--http-method` | **Yes** | string | -- | HTTP method |

**Output:** None

---

### 3.10 `put-integration-response`

Creates an integration response for an integration.

**Synopsis:**
```bash
aws apigateway put-integration-response \
    --rest-api-id <value> \
    --resource-id <value> \
    --http-method <value> \
    --status-code <value> \
    [--selection-pattern <value>] \
    [--response-parameters <value>] \
    [--response-templates <value>] \
    [--content-handling <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--resource-id` | **Yes** | string | -- | ID of the resource |
| `--http-method` | **Yes** | string | -- | HTTP method |
| `--status-code` | **Yes** | string | -- | HTTP status code for this response |
| `--selection-pattern` | No | string | None | Regex pattern to match error messages for routing |
| `--response-parameters` | No | map | None | Maps integration response parameters to method response parameters |
| `--response-templates` | No | map | None | Velocity templates by content type |
| `--content-handling` | No | string | None | Content handling: `CONVERT_TO_BINARY` or `CONVERT_TO_TEXT` |

**Output Schema:**
```json
{
    "statusCode": "string",
    "selectionPattern": "string",
    "responseParameters": {
        "string": "string"
    },
    "responseTemplates": {
        "string": "string"
    },
    "contentHandling": "CONVERT_TO_BINARY|CONVERT_TO_TEXT"
}
```

---

### 3.11 `get-integration-response`

Gets an integration response.

**Synopsis:**
```bash
aws apigateway get-integration-response \
    --rest-api-id <value> \
    --resource-id <value> \
    --http-method <value> \
    --status-code <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--resource-id` | **Yes** | string | -- | ID of the resource |
| `--http-method` | **Yes** | string | -- | HTTP method |
| `--status-code` | **Yes** | string | -- | HTTP status code |

**Output Schema:** Same as `put-integration-response`.

---

### 3.12 `delete-integration-response`

Deletes an integration response.

**Synopsis:**
```bash
aws apigateway delete-integration-response \
    --rest-api-id <value> \
    --resource-id <value> \
    --http-method <value> \
    --status-code <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--resource-id` | **Yes** | string | -- | ID of the resource |
| `--http-method` | **Yes** | string | -- | HTTP method |
| `--status-code` | **Yes** | string | -- | HTTP status code |

**Output:** None
