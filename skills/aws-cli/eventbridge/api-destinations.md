# API Destinations

### 7.1 `create-api-destination`

Creates an API destination, which is an HTTP endpoint that can be used as a target for EventBridge rules.

**Synopsis:**
```bash
aws events create-api-destination \
    --name <value> \
    --connection-arn <value> \
    --invocation-endpoint <value> \
    --http-method <value> \
    [--description <value>] \
    [--invocation-rate-limit-per-second <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | API destination name |
| `--connection-arn` | **Yes** | string | -- | ARN of the connection to use for authorization |
| `--invocation-endpoint` | **Yes** | string | -- | URL of the HTTP endpoint (supports `*` wildcard for path parameters) |
| `--http-method` | **Yes** | string | -- | HTTP method: `GET`, `POST`, `PUT`, `DELETE`, `PATCH`, `HEAD`, `OPTIONS` |
| `--description` | No | string | None | Description |
| `--invocation-rate-limit-per-second` | No | integer | 300 | Max invocations per second |

**Output Schema:**
```json
{
    "ApiDestinationArn": "string",
    "ApiDestinationState": "ACTIVE|INACTIVE",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp"
}
```

---

### 7.2 `delete-api-destination`

Deletes an API destination.

**Synopsis:**
```bash
aws events delete-api-destination \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | API destination name to delete |

**Output Schema:**
```json
{}
```

---

### 7.3 `describe-api-destination`

Retrieves details about an API destination.

**Synopsis:**
```bash
aws events describe-api-destination \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | API destination name |

**Output Schema:**
```json
{
    "ApiDestinationArn": "string",
    "Name": "string",
    "Description": "string",
    "ApiDestinationState": "ACTIVE|INACTIVE",
    "ConnectionArn": "string",
    "InvocationEndpoint": "string",
    "HttpMethod": "GET|POST|PUT|DELETE|PATCH|HEAD|OPTIONS",
    "InvocationRateLimitPerSecond": "integer",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp"
}
```

---

### 7.4 `list-api-destinations`

Lists all API destinations. Supports filtering by name prefix or connection ARN. **Paginated operation.**

**Synopsis:**
```bash
aws events list-api-destinations \
    [--name-prefix <value>] \
    [--connection-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name-prefix` | No | string | None | Filter by name prefix |
| `--connection-arn` | No | string | None | Filter by connection ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ApiDestinations": [
        {
            "ApiDestinationArn": "string",
            "Name": "string",
            "ApiDestinationState": "ACTIVE|INACTIVE",
            "ConnectionArn": "string",
            "InvocationEndpoint": "string",
            "HttpMethod": "string",
            "InvocationRateLimitPerSecond": "integer",
            "CreationTime": "timestamp",
            "LastModifiedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.5 `update-api-destination`

Updates an API destination.

**Synopsis:**
```bash
aws events update-api-destination \
    --name <value> \
    [--description <value>] \
    [--connection-arn <value>] \
    [--invocation-endpoint <value>] \
    [--http-method <value>] \
    [--invocation-rate-limit-per-second <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | API destination name |
| `--description` | No | string | None | Updated description |
| `--connection-arn` | No | string | None | Updated connection ARN |
| `--invocation-endpoint` | No | string | None | Updated endpoint URL |
| `--http-method` | No | string | None | Updated HTTP method |
| `--invocation-rate-limit-per-second` | No | integer | None | Updated rate limit |

**Output Schema:**
```json
{
    "ApiDestinationArn": "string",
    "ApiDestinationState": "ACTIVE|INACTIVE",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp"
}
```
