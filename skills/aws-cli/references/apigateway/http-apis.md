# HTTP & WebSocket APIs (API Gateway v2)

All commands in this file use the `aws apigatewayv2` service prefix.

## APIs

### 10.1 `create-api`

Creates an HTTP or WebSocket API.

**Synopsis:**
```bash
aws apigatewayv2 create-api \
    --name <value> \
    --protocol-type <value> \
    [--api-key-selection-expression <value>] \
    [--cors-configuration <value>] \
    [--credentials-arn <value>] \
    [--description <value>] \
    [--disable-schema-validation | --no-disable-schema-validation] \
    [--disable-execute-api-endpoint | --no-disable-execute-api-endpoint] \
    [--route-key <value>] \
    [--route-selection-expression <value>] \
    [--tags <value>] \
    [--target <value>] \
    [--version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | API name |
| `--protocol-type` | **Yes** | string | -- | Protocol: `HTTP` or `WEBSOCKET` |
| `--api-key-selection-expression` | No | string | `$request.header.x-api-key` | API key selection expression (WebSocket only) |
| `--cors-configuration` | No | structure | None | CORS config. JSON: `{"allowOrigins":["*"],"allowMethods":["GET","POST"],"allowHeaders":["content-type"],"maxAge":300}` |
| `--credentials-arn` | No | string | None | IAM role ARN for quick create integration |
| `--description` | No | string | None | Description |
| `--disable-schema-validation` | No | boolean | false | Disable request/response schema validation |
| `--disable-execute-api-endpoint` | No | boolean | false | Disable default execute-api endpoint |
| `--route-key` | No | string | None | Route key for quick create (e.g., `GET /pets`) |
| `--route-selection-expression` | No | string | `$request.method $request.path` | Route selection expression (WebSocket: `$request.body.action`) |
| `--tags` | No | map | None | Key-value tags |
| `--target` | No | string | None | Quick create target (Lambda ARN or HTTP URL) |
| `--version` | No | string | None | Version identifier |

**Output Schema:**
```json
{
    "ApiEndpoint": "string",
    "ApiGatewayManaged": "boolean",
    "ApiId": "string",
    "ApiKeySelectionExpression": "string",
    "CorsConfiguration": {
        "AllowCredentials": "boolean",
        "AllowHeaders": ["string"],
        "AllowMethods": ["string"],
        "AllowOrigins": ["string"],
        "ExposeHeaders": ["string"],
        "MaxAge": "integer"
    },
    "CreatedDate": "timestamp",
    "Description": "string",
    "DisableSchemaValidation": "boolean",
    "DisableExecuteApiEndpoint": "boolean",
    "ImportInfo": ["string"],
    "Name": "string",
    "ProtocolType": "HTTP|WEBSOCKET",
    "RouteSelectionExpression": "string",
    "Tags": {},
    "Version": "string",
    "Warnings": ["string"]
}
```

---

### 10.2 `delete-api`

Deletes an API.

**Synopsis:**
```bash
aws apigatewayv2 delete-api \
    --api-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | API ID |

**Output:** None

---

### 10.3 `get-api`

Gets information about an API.

**Synopsis:**
```bash
aws apigatewayv2 get-api \
    --api-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | API ID |

**Output Schema:** Same as `create-api`.

---

### 10.4 `get-apis`

Lists APIs. **Paginated operation.**

**Synopsis:**
```bash
aws apigatewayv2 get-apis \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | string | None | Maximum number of items to return |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Items": [
        {
            "ApiEndpoint": "string",
            "ApiId": "string",
            "Name": "string",
            "ProtocolType": "HTTP|WEBSOCKET",
            "Description": "string",
            "Tags": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 10.5 `update-api`

Updates an API.

**Synopsis:**
```bash
aws apigatewayv2 update-api \
    --api-id <value> \
    [--api-key-selection-expression <value>] \
    [--cors-configuration <value>] \
    [--credentials-arn <value>] \
    [--description <value>] \
    [--disable-schema-validation | --no-disable-schema-validation] \
    [--disable-execute-api-endpoint | --no-disable-execute-api-endpoint] \
    [--name <value>] \
    [--route-key <value>] \
    [--route-selection-expression <value>] \
    [--target <value>] \
    [--version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | API ID |
| `--name` | No | string | None | New API name |
| `--description` | No | string | None | New description |
| `--cors-configuration` | No | structure | None | CORS configuration |
| `--disable-execute-api-endpoint` | No | boolean | None | Disable default endpoint |
| `--version` | No | string | None | Version identifier |
| `--route-selection-expression` | No | string | None | Route selection expression |

**Output Schema:** Same as `create-api`.

---

## Routes

### 10.6 `create-route`

Creates a route for an API.

**Synopsis:**
```bash
aws apigatewayv2 create-route \
    --api-id <value> \
    --route-key <value> \
    [--api-key-required | --no-api-key-required] \
    [--authorization-scopes <value>] \
    [--authorization-type <value>] \
    [--authorizer-id <value>] \
    [--model-selection-expression <value>] \
    [--operation-name <value>] \
    [--request-models <value>] \
    [--request-parameters <value>] \
    [--route-response-selection-expression <value>] \
    [--target <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | API ID |
| `--route-key` | **Yes** | string | -- | Route key (e.g., `GET /users`, `$connect`, `$default`) |
| `--api-key-required` | No | boolean | false | Whether API key is required |
| `--authorization-scopes` | No | list(string) | None | OAuth scopes |
| `--authorization-type` | No | string | `NONE` | Auth type: `NONE`, `AWS_IAM`, `CUSTOM`, `JWT` |
| `--authorizer-id` | No | string | None | Authorizer ID |
| `--model-selection-expression` | No | string | None | Model selection expression |
| `--operation-name` | No | string | None | Operation name |
| `--request-models` | No | map | None | Request models by content type |
| `--request-parameters` | No | map | None | Request parameters |
| `--route-response-selection-expression` | No | string | None | Route response selection expression |
| `--target` | No | string | None | Target for the route (e.g., `integrations/<integration-id>`) |

**Output Schema:**
```json
{
    "ApiGatewayManaged": "boolean",
    "ApiKeyRequired": "boolean",
    "AuthorizationScopes": ["string"],
    "AuthorizationType": "NONE|AWS_IAM|CUSTOM|JWT",
    "AuthorizerId": "string",
    "ModelSelectionExpression": "string",
    "OperationName": "string",
    "RequestModels": {},
    "RequestParameters": {},
    "RouteId": "string",
    "RouteKey": "string",
    "RouteResponseSelectionExpression": "string",
    "Target": "string"
}
```

---

### 10.7 `delete-route`

Deletes a route.

**Synopsis:**
```bash
aws apigatewayv2 delete-route \
    --api-id <value> \
    --route-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | API ID |
| `--route-id` | **Yes** | string | -- | Route ID |

**Output:** None

---

### 10.8 `get-route`

Gets information about a route.

**Synopsis:**
```bash
aws apigatewayv2 get-route \
    --api-id <value> \
    --route-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | API ID |
| `--route-id` | **Yes** | string | -- | Route ID |

**Output Schema:** Same as `create-route`.

---

### 10.9 `get-routes`

Lists routes for an API. **Paginated operation.**

**Synopsis:**
```bash
aws apigatewayv2 get-routes \
    --api-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | API ID |
| `--max-results` | No | string | None | Maximum items |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Items": [
        {
            "RouteId": "string",
            "RouteKey": "string",
            "AuthorizationType": "string",
            "Target": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 10.10 `update-route`

Updates a route.

**Synopsis:**
```bash
aws apigatewayv2 update-route \
    --api-id <value> \
    --route-id <value> \
    [--authorization-scopes <value>] \
    [--authorization-type <value>] \
    [--authorizer-id <value>] \
    [--model-selection-expression <value>] \
    [--operation-name <value>] \
    [--request-models <value>] \
    [--request-parameters <value>] \
    [--route-key <value>] \
    [--route-response-selection-expression <value>] \
    [--target <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | API ID |
| `--route-id` | **Yes** | string | -- | Route ID |
| `--route-key` | No | string | None | New route key |
| `--authorization-type` | No | string | None | Auth type |
| `--authorizer-id` | No | string | None | Authorizer ID |
| `--target` | No | string | None | Integration target |

**Output Schema:** Same as `create-route`.

---

## Integrations

### 10.11 `create-integration`

Creates an integration for an API.

**Synopsis:**
```bash
aws apigatewayv2 create-integration \
    --api-id <value> \
    --integration-type <value> \
    [--connection-id <value>] \
    [--connection-type <value>] \
    [--content-handling-strategy <value>] \
    [--credentials-arn <value>] \
    [--description <value>] \
    [--integration-method <value>] \
    [--integration-subtype <value>] \
    [--integration-uri <value>] \
    [--passthrough-behavior <value>] \
    [--payload-format-version <value>] \
    [--request-parameters <value>] \
    [--request-templates <value>] \
    [--response-parameters <value>] \
    [--template-selection-expression <value>] \
    [--timeout-in-millis <value>] \
    [--tls-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | API ID |
| `--integration-type` | **Yes** | string | -- | Type: `AWS`, `HTTP`, `MOCK`, `HTTP_PROXY`, `AWS_PROXY` |
| `--connection-id` | No | string | None | VPC link ID |
| `--connection-type` | No | string | `INTERNET` | Connection type: `INTERNET` or `VPC_LINK` |
| `--content-handling-strategy` | No | string | None | Content handling: `CONVERT_TO_BINARY` or `CONVERT_TO_TEXT` |
| `--credentials-arn` | No | string | None | IAM role ARN for the integration |
| `--description` | No | string | None | Description |
| `--integration-method` | No | string | None | HTTP method for the backend |
| `--integration-subtype` | No | string | None | AWS service integration subtype (e.g., `EventBridge-PutEvents`) |
| `--integration-uri` | No | string | None | Integration URI (Lambda ARN or HTTP URL) |
| `--passthrough-behavior` | No | string | None | Passthrough: `WHEN_NO_MATCH`, `NEVER`, `WHEN_NO_TEMPLATES` |
| `--payload-format-version` | No | string | `1.0` | Payload format version: `1.0` or `2.0` |
| `--request-parameters` | No | map | None | Request parameter mappings |
| `--request-templates` | No | map | None | Request templates by content type |
| `--response-parameters` | No | map | None | Response parameter mappings |
| `--template-selection-expression` | No | string | None | Template selection expression |
| `--timeout-in-millis` | No | integer | 30000 | Integration timeout (50-30000 ms) |
| `--tls-config` | No | structure | None | TLS config. Shorthand: `ServerNameToVerify=string` |

**Output Schema:**
```json
{
    "ApiGatewayManaged": "boolean",
    "ConnectionId": "string",
    "ConnectionType": "INTERNET|VPC_LINK",
    "ContentHandlingStrategy": "CONVERT_TO_BINARY|CONVERT_TO_TEXT",
    "CredentialsArn": "string",
    "Description": "string",
    "IntegrationId": "string",
    "IntegrationMethod": "string",
    "IntegrationResponseSelectionExpression": "string",
    "IntegrationSubtype": "string",
    "IntegrationType": "AWS|HTTP|MOCK|HTTP_PROXY|AWS_PROXY",
    "IntegrationUri": "string",
    "PassthroughBehavior": "WHEN_NO_MATCH|NEVER|WHEN_NO_TEMPLATES",
    "PayloadFormatVersion": "string",
    "RequestParameters": {},
    "RequestTemplates": {},
    "ResponseParameters": {},
    "TemplateSelectionExpression": "string",
    "TimeoutInMillis": "integer",
    "TlsConfig": {
        "ServerNameToVerify": "string"
    }
}
```

---

### 10.12 `delete-integration`

Deletes an integration.

**Synopsis:**
```bash
aws apigatewayv2 delete-integration \
    --api-id <value> \
    --integration-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | API ID |
| `--integration-id` | **Yes** | string | -- | Integration ID |

**Output:** None

---

### 10.13 `get-integration`

Gets information about an integration.

**Synopsis:**
```bash
aws apigatewayv2 get-integration \
    --api-id <value> \
    --integration-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | API ID |
| `--integration-id` | **Yes** | string | -- | Integration ID |

**Output Schema:** Same as `create-integration`.

---

### 10.14 `get-integrations`

Lists integrations for an API. **Paginated operation.**

**Synopsis:**
```bash
aws apigatewayv2 get-integrations \
    --api-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | API ID |
| `--max-results` | No | string | None | Maximum items |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Items": [
        {
            "IntegrationId": "string",
            "IntegrationType": "string",
            "IntegrationUri": "string",
            "Description": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 10.15 `update-integration`

Updates an integration.

**Synopsis:**
```bash
aws apigatewayv2 update-integration \
    --api-id <value> \
    --integration-id <value> \
    [--connection-id <value>] \
    [--connection-type <value>] \
    [--content-handling-strategy <value>] \
    [--credentials-arn <value>] \
    [--description <value>] \
    [--integration-method <value>] \
    [--integration-subtype <value>] \
    [--integration-type <value>] \
    [--integration-uri <value>] \
    [--passthrough-behavior <value>] \
    [--payload-format-version <value>] \
    [--request-parameters <value>] \
    [--request-templates <value>] \
    [--response-parameters <value>] \
    [--template-selection-expression <value>] \
    [--timeout-in-millis <value>] \
    [--tls-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | API ID |
| `--integration-id` | **Yes** | string | -- | Integration ID |

All other parameters are the same as `create-integration` and are optional for updates.

**Output Schema:** Same as `create-integration`.

---

## Stages (v2)

### 10.16 `create-stage` (v2)

Creates a stage for an HTTP or WebSocket API.

**Synopsis:**
```bash
aws apigatewayv2 create-stage \
    --api-id <value> \
    --stage-name <value> \
    [--access-log-settings <value>] \
    [--auto-deploy | --no-auto-deploy] \
    [--client-certificate-id <value>] \
    [--default-route-settings <value>] \
    [--deployment-id <value>] \
    [--description <value>] \
    [--route-settings <value>] \
    [--stage-variables <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | API ID |
| `--stage-name` | **Yes** | string | -- | Stage name (e.g., `prod`, `$default`) |
| `--access-log-settings` | No | structure | None | Access log settings. Shorthand: `DestinationArn=string,Format=string` |
| `--auto-deploy` | No | boolean | false | Enable automatic deployments on changes |
| `--client-certificate-id` | No | string | None | Client certificate ID |
| `--default-route-settings` | No | structure | None | Default route settings. Shorthand: `DataTraceEnabled=boolean,DetailedMetricsEnabled=boolean,LoggingLevel=ERROR\|INFO\|OFF,ThrottlingBurstLimit=integer,ThrottlingRateLimit=double` |
| `--deployment-id` | No | string | None | Deployment ID to associate |
| `--description` | No | string | None | Description |
| `--route-settings` | No | map | None | Route-specific settings by route key |
| `--stage-variables` | No | map | None | Stage variables |
| `--tags` | No | map | None | Key-value tags |

**Output Schema:**
```json
{
    "AccessLogSettings": {
        "DestinationArn": "string",
        "Format": "string"
    },
    "ApiGatewayManaged": "boolean",
    "AutoDeploy": "boolean",
    "ClientCertificateId": "string",
    "CreatedDate": "timestamp",
    "DefaultRouteSettings": {
        "DataTraceEnabled": "boolean",
        "DetailedMetricsEnabled": "boolean",
        "LoggingLevel": "ERROR|INFO|OFF",
        "ThrottlingBurstLimit": "integer",
        "ThrottlingRateLimit": "double"
    },
    "DeploymentId": "string",
    "Description": "string",
    "LastDeploymentStatusMessage": "string",
    "LastUpdatedDate": "timestamp",
    "RouteSettings": {},
    "StageName": "string",
    "StageVariables": {},
    "Tags": {}
}
```

---

### 10.17 `delete-stage` (v2)

Deletes a stage.

**Synopsis:**
```bash
aws apigatewayv2 delete-stage \
    --api-id <value> \
    --stage-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | API ID |
| `--stage-name` | **Yes** | string | -- | Stage name |

**Output:** None

---

### 10.18 `get-stage` (v2)

Gets information about a stage.

**Synopsis:**
```bash
aws apigatewayv2 get-stage \
    --api-id <value> \
    --stage-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | API ID |
| `--stage-name` | **Yes** | string | -- | Stage name |

**Output Schema:** Same as `create-stage` (v2).

---

### 10.19 `get-stages` (v2)

Lists stages for an API. **Paginated operation.**

**Synopsis:**
```bash
aws apigatewayv2 get-stages \
    --api-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | API ID |
| `--max-results` | No | string | None | Maximum items |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Items": [
        {
            "StageName": "string",
            "DeploymentId": "string",
            "AutoDeploy": "boolean",
            "Description": "string",
            "Tags": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 10.20 `update-stage` (v2)

Updates a stage.

**Synopsis:**
```bash
aws apigatewayv2 update-stage \
    --api-id <value> \
    --stage-name <value> \
    [--access-log-settings <value>] \
    [--auto-deploy | --no-auto-deploy] \
    [--client-certificate-id <value>] \
    [--default-route-settings <value>] \
    [--deployment-id <value>] \
    [--description <value>] \
    [--route-settings <value>] \
    [--stage-variables <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | API ID |
| `--stage-name` | **Yes** | string | -- | Stage name |

All other parameters are the same as `create-stage` (v2) and are optional for updates.

**Output Schema:** Same as `create-stage` (v2).

---

## Authorizers (v2)

### 10.21 `create-authorizer` (v2)

Creates an authorizer for an HTTP or WebSocket API.

**Synopsis:**
```bash
aws apigatewayv2 create-authorizer \
    --api-id <value> \
    --authorizer-type <value> \
    --identity-source <value> \
    --name <value> \
    [--authorizer-credentials-arn <value>] \
    [--authorizer-payload-format-version <value>] \
    [--authorizer-result-ttl-in-seconds <value>] \
    [--authorizer-uri <value>] \
    [--enable-simple-responses | --no-enable-simple-responses] \
    [--jwt-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | API ID |
| `--authorizer-type` | **Yes** | string | -- | Type: `REQUEST` or `JWT` |
| `--identity-source` | **Yes** | string | -- | Identity source (e.g., `$request.header.Authorization`) |
| `--name` | **Yes** | string | -- | Authorizer name |
| `--authorizer-credentials-arn` | No | string | None | IAM role ARN for Lambda authorizer |
| `--authorizer-payload-format-version` | No | string | None | Payload format: `1.0` or `2.0` |
| `--authorizer-result-ttl-in-seconds` | No | integer | 300 | Cache TTL (0-3600 seconds) |
| `--authorizer-uri` | Cond. | string | None | Lambda function URI (required for `REQUEST` type) |
| `--enable-simple-responses` | No | boolean | false | Enable simple boolean responses for Lambda authorizers |
| `--jwt-configuration` | Cond. | structure | None | JWT config (required for `JWT` type). Shorthand: `Audience=string,string,Issuer=string` |

**Output Schema:**
```json
{
    "AuthorizerId": "string",
    "AuthorizerCredentialsArn": "string",
    "AuthorizerPayloadFormatVersion": "string",
    "AuthorizerResultTtlInSeconds": "integer",
    "AuthorizerType": "REQUEST|JWT",
    "AuthorizerUri": "string",
    "EnableSimpleResponses": "boolean",
    "IdentitySource": "string",
    "JwtConfiguration": {
        "Audience": ["string"],
        "Issuer": "string"
    },
    "Name": "string"
}
```

---

### 10.22 `delete-authorizer` (v2)

Deletes an authorizer.

**Synopsis:**
```bash
aws apigatewayv2 delete-authorizer \
    --api-id <value> \
    --authorizer-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | API ID |
| `--authorizer-id` | **Yes** | string | -- | Authorizer ID |

**Output:** None

---

### 10.23 `get-authorizer` (v2)

Gets information about an authorizer.

**Synopsis:**
```bash
aws apigatewayv2 get-authorizer \
    --api-id <value> \
    --authorizer-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | API ID |
| `--authorizer-id` | **Yes** | string | -- | Authorizer ID |

**Output Schema:** Same as `create-authorizer` (v2).

---

### 10.24 `get-authorizers` (v2)

Lists authorizers for an API. **Paginated operation.**

**Synopsis:**
```bash
aws apigatewayv2 get-authorizers \
    --api-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | API ID |
| `--max-results` | No | string | None | Maximum items |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Items": [
        {
            "AuthorizerId": "string",
            "AuthorizerType": "REQUEST|JWT",
            "Name": "string",
            "IdentitySource": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 10.25 `update-authorizer` (v2)

Updates an authorizer.

**Synopsis:**
```bash
aws apigatewayv2 update-authorizer \
    --api-id <value> \
    --authorizer-id <value> \
    [--authorizer-credentials-arn <value>] \
    [--authorizer-payload-format-version <value>] \
    [--authorizer-result-ttl-in-seconds <value>] \
    [--authorizer-type <value>] \
    [--authorizer-uri <value>] \
    [--enable-simple-responses | --no-enable-simple-responses] \
    [--identity-source <value>] \
    [--jwt-configuration <value>] \
    [--name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | API ID |
| `--authorizer-id` | **Yes** | string | -- | Authorizer ID |

All other parameters are the same as `create-authorizer` (v2) and are optional for updates.

**Output Schema:** Same as `create-authorizer` (v2).

---

## Deployments (v2)

### 10.26 `create-deployment` (v2)

Creates a deployment for an API.

**Synopsis:**
```bash
aws apigatewayv2 create-deployment \
    --api-id <value> \
    [--description <value>] \
    [--stage-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | API ID |
| `--description` | No | string | None | Description |
| `--stage-name` | No | string | None | Stage name to deploy to |

**Output Schema:**
```json
{
    "AutoDeployed": "boolean",
    "CreatedDate": "timestamp",
    "DeploymentId": "string",
    "DeploymentStatus": "PENDING|FAILED|DEPLOYED",
    "DeploymentStatusMessage": "string",
    "Description": "string"
}
```

---

### 10.27 `delete-deployment` (v2)

Deletes a deployment.

**Synopsis:**
```bash
aws apigatewayv2 delete-deployment \
    --api-id <value> \
    --deployment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | API ID |
| `--deployment-id` | **Yes** | string | -- | Deployment ID |

**Output:** None

---

### 10.28 `get-deployment` (v2)

Gets information about a deployment.

**Synopsis:**
```bash
aws apigatewayv2 get-deployment \
    --api-id <value> \
    --deployment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | API ID |
| `--deployment-id` | **Yes** | string | -- | Deployment ID |

**Output Schema:** Same as `create-deployment` (v2).

---

### 10.29 `get-deployments` (v2)

Lists deployments for an API. **Paginated operation.**

**Synopsis:**
```bash
aws apigatewayv2 get-deployments \
    --api-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | API ID |
| `--max-results` | No | string | None | Maximum items |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Items": [
        {
            "DeploymentId": "string",
            "DeploymentStatus": "PENDING|FAILED|DEPLOYED",
            "Description": "string",
            "CreatedDate": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
