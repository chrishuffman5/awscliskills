# Stages & Deployments

### 4.1 `create-deployment`

Creates a deployment for a REST API. A deployment makes the API callable at a stage.

**Synopsis:**
```bash
aws apigateway create-deployment \
    --rest-api-id <value> \
    [--stage-name <value>] \
    [--stage-description <value>] \
    [--description <value>] \
    [--cache-cluster-enabled | --no-cache-cluster-enabled] \
    [--cache-cluster-size <value>] \
    [--variables <value>] \
    [--canary-settings <value>] \
    [--tracing-enabled | --no-tracing-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--stage-name` | No | string | None | Name of the stage to deploy to (creates stage if it does not exist) |
| `--stage-description` | No | string | None | Description for the stage |
| `--description` | No | string | None | Description for the deployment |
| `--cache-cluster-enabled` | No | boolean | false | Enable API cache for the stage |
| `--cache-cluster-size` | No | string | None | Cache size: `0.5`, `1.6`, `6.1`, `13.5`, `28.4`, `58.2`, `118`, `237` (GB) |
| `--variables` | No | map | None | Stage variables. Shorthand: `key1=value1,key2=value2` |
| `--canary-settings` | No | structure | None | Canary deployment settings |
| `--tracing-enabled` | No | boolean | false | Enable X-Ray tracing |

**Output Schema:**
```json
{
    "id": "string",
    "description": "string",
    "createdDate": "timestamp",
    "apiSummary": {
        "string": {
            "string": {
                "authorizationType": "string",
                "apiKeyRequired": "boolean"
            }
        }
    }
}
```

---

### 4.2 `delete-deployment`

Deletes a deployment.

**Synopsis:**
```bash
aws apigateway delete-deployment \
    --rest-api-id <value> \
    --deployment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--deployment-id` | **Yes** | string | -- | ID of the deployment to delete |

**Output:** None

---

### 4.3 `get-deployment`

Gets information about a deployment.

**Synopsis:**
```bash
aws apigateway get-deployment \
    --rest-api-id <value> \
    --deployment-id <value> \
    [--embed <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--deployment-id` | **Yes** | string | -- | ID of the deployment |
| `--embed` | No | list(string) | None | Embed additional info: `apiSummary` |

**Output Schema:**
```json
{
    "id": "string",
    "description": "string",
    "createdDate": "timestamp",
    "apiSummary": {}
}
```

---

### 4.4 `get-deployments`

Lists deployments for a REST API. **Paginated operation.**

**Synopsis:**
```bash
aws apigateway get-deployments \
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
| `--page-size` | No | integer | None | Items per API call (max 500) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "items": [
        {
            "id": "string",
            "description": "string",
            "createdDate": "timestamp",
            "apiSummary": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 4.5 `create-stage`

Creates a new stage for a deployment.

**Synopsis:**
```bash
aws apigateway create-stage \
    --rest-api-id <value> \
    --stage-name <value> \
    --deployment-id <value> \
    [--description <value>] \
    [--cache-cluster-enabled | --no-cache-cluster-enabled] \
    [--cache-cluster-size <value>] \
    [--variables <value>] \
    [--documentation-version <value>] \
    [--canary-settings <value>] \
    [--tracing-enabled | --no-tracing-enabled] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--stage-name` | **Yes** | string | -- | Name of the stage |
| `--deployment-id` | **Yes** | string | -- | ID of the deployment to associate |
| `--description` | No | string | None | Stage description |
| `--cache-cluster-enabled` | No | boolean | false | Enable API cache |
| `--cache-cluster-size` | No | string | None | Cache cluster size |
| `--variables` | No | map | None | Stage variables |
| `--documentation-version` | No | string | None | Documentation version |
| `--canary-settings` | No | structure | None | Canary settings |
| `--tracing-enabled` | No | boolean | false | Enable X-Ray tracing |
| `--tags` | No | map | None | Key-value tags |

**Output Schema:**
```json
{
    "deploymentId": "string",
    "clientCertificateId": "string",
    "stageName": "string",
    "description": "string",
    "cacheClusterEnabled": "boolean",
    "cacheClusterSize": "0.5|1.6|6.1|13.5|28.4|58.2|118|237",
    "cacheClusterStatus": "CREATE_IN_PROGRESS|AVAILABLE|DELETE_IN_PROGRESS|NOT_AVAILABLE|FLUSH_IN_PROGRESS",
    "methodSettings": {
        "string": {
            "metricsEnabled": "boolean",
            "loggingLevel": "OFF|ERROR|INFO",
            "dataTraceEnabled": "boolean",
            "throttlingBurstLimit": "integer",
            "throttlingRateLimit": "double",
            "cachingEnabled": "boolean",
            "cacheTtlInSeconds": "integer",
            "cacheDataEncrypted": "boolean",
            "requireAuthorizationForCacheControl": "boolean",
            "unauthorizedCacheControlHeaderStrategy": "FAIL_WITH_403|SUCCEED_WITH_RESPONSE_HEADER|SUCCEED_WITHOUT_RESPONSE_HEADER"
        }
    },
    "variables": {
        "string": "string"
    },
    "documentationVersion": "string",
    "accessLogSettings": {
        "format": "string",
        "destinationArn": "string"
    },
    "canarySettings": {
        "percentTraffic": "double",
        "deploymentId": "string",
        "stageVariableOverrides": {},
        "useStageCache": "boolean"
    },
    "tracingEnabled": "boolean",
    "webAclArn": "string",
    "tags": {},
    "createdDate": "timestamp",
    "lastUpdatedDate": "timestamp"
}
```

---

### 4.6 `delete-stage`

Deletes a stage.

**Synopsis:**
```bash
aws apigateway delete-stage \
    --rest-api-id <value> \
    --stage-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--stage-name` | **Yes** | string | -- | Name of the stage to delete |

**Output:** None

---

### 4.7 `get-stage`

Gets information about a stage.

**Synopsis:**
```bash
aws apigateway get-stage \
    --rest-api-id <value> \
    --stage-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--stage-name` | **Yes** | string | -- | Name of the stage |

**Output Schema:** Same as `create-stage`.

---

### 4.8 `get-stages`

Lists all stages for a REST API.

**Synopsis:**
```bash
aws apigateway get-stages \
    --rest-api-id <value> \
    [--deployment-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--deployment-id` | No | string | None | Filter by deployment ID |

**Output Schema:**
```json
{
    "item": [
        {
            "deploymentId": "string",
            "stageName": "string",
            "description": "string",
            "cacheClusterEnabled": "boolean",
            "cacheClusterSize": "string",
            "cacheClusterStatus": "string",
            "methodSettings": {},
            "variables": {},
            "tracingEnabled": "boolean",
            "tags": {},
            "createdDate": "timestamp",
            "lastUpdatedDate": "timestamp"
        }
    ]
}
```

---

### 4.9 `update-stage`

Updates a stage using patch operations.

**Synopsis:**
```bash
aws apigateway update-stage \
    --rest-api-id <value> \
    --stage-name <value> \
    [--patch-operations <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--stage-name` | **Yes** | string | -- | Name of the stage |
| `--patch-operations` | No | list | None | Patch operations |

**Common Patch Paths:**
- `/description` — Stage description
- `/deploymentId` — Associated deployment
- `/variables/variableName` — Stage variable
- `/cacheClusterEnabled` — Cache toggle
- `/cacheClusterSize` — Cache size
- `/*/*/logging/loglevel` — Logging level (OFF, ERROR, INFO)
- `/*/*/logging/dataTrace` — Data trace toggle
- `/*/*/throttling/burstLimit` — Throttle burst
- `/*/*/throttling/rateLimit` — Throttle rate
- `/*/*/caching/enabled` — Method cache toggle
- `/*/*/caching/ttlInSeconds` — Cache TTL
- `/tracingEnabled` — X-Ray tracing
- `/accessLogSettings/destinationArn` — Access log destination
- `/accessLogSettings/format` — Access log format

**Output Schema:** Same as `create-stage`.

---

### 4.10 `flush-stage-cache`

Flushes the API stage cache.

**Synopsis:**
```bash
aws apigateway flush-stage-cache \
    --rest-api-id <value> \
    --stage-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--stage-name` | **Yes** | string | -- | Name of the stage |

**Output:** None

---

### 4.11 `flush-stage-authorizers-cache`

Flushes all authorizer cache entries for a stage.

**Synopsis:**
```bash
aws apigateway flush-stage-authorizers-cache \
    --rest-api-id <value> \
    --stage-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--stage-name` | **Yes** | string | -- | Name of the stage |

**Output:** None
