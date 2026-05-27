# Function URLs

### 8.1 `create-function-url-config`

Creates an HTTP(S) endpoint for a Lambda function. The URL is unique and immutable.

**Synopsis:**
```bash
aws lambda create-function-url-config \
    --function-name <value> \
    --auth-type <value> \
    [--qualifier <value>] \
    [--cors <value>] \
    [--invoke-mode <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |
| `--auth-type` | **Yes** | string | -- | Values: `NONE` (public), `AWS_IAM` (IAM auth required) |
| `--qualifier` | No | string | -- | Alias name (1-128 chars) |
| `--cors` | No | structure | -- | CORS config. Shorthand: `AllowCredentials=boolean,AllowHeaders=string,string,AllowMethods=string,string,AllowOrigins=string,string,ExposeHeaders=string,string,MaxAge=integer` |
| `--invoke-mode` | No | string | `BUFFERED` | Values: `BUFFERED` (6 MB max), `RESPONSE_STREAM` (20 MB max) |

**Output Schema:**
```json
{
    "FunctionUrl": "string",
    "FunctionArn": "string",
    "AuthType": "NONE|AWS_IAM",
    "Cors": {
        "AllowCredentials": true|false,
        "AllowHeaders": ["string"],
        "AllowMethods": ["string"],
        "AllowOrigins": ["string"],
        "ExposeHeaders": ["string"],
        "MaxAge": "integer"
    },
    "CreationTime": "string",
    "InvokeMode": "BUFFERED|RESPONSE_STREAM"
}
```

---

### 8.2 `get-function-url-config`

Returns the function URL configuration.

**Synopsis:**
```bash
aws lambda get-function-url-config \
    --function-name <value> \
    [--qualifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |
| `--qualifier` | No | string | -- | Alias name (1-128 chars) |

**Output Schema:** Same as `create-function-url-config` plus `LastModifiedTime`.

---

### 8.3 `update-function-url-config`

Updates the function URL configuration.

**Synopsis:**
```bash
aws lambda update-function-url-config \
    --function-name <value> \
    [--qualifier <value>] \
    [--auth-type <value>] \
    [--cors <value>] \
    [--invoke-mode <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |
| `--qualifier` | No | string | -- | Alias name (1-128 chars) |
| `--auth-type` | No | string | -- | Values: `NONE`, `AWS_IAM` |
| `--cors` | No | structure | -- | CORS configuration |
| `--invoke-mode` | No | string | -- | Values: `BUFFERED`, `RESPONSE_STREAM` |

**Output Schema:** Same as `create-function-url-config` plus `LastModifiedTime`.

---

### 8.4 `delete-function-url-config`

Deletes a function URL configuration.

**Synopsis:**
```bash
aws lambda delete-function-url-config \
    --function-name <value> \
    [--qualifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |
| `--qualifier` | No | string | -- | Alias name (1-128 chars) |

**Output:** None on success.

---

### 8.5 `list-function-url-configs`

Lists function URL configurations for a function. **Paginated operation.**

**Synopsis:**
```bash
aws lambda list-function-url-configs \
    --function-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "FunctionUrlConfigs": [
        {
            "FunctionUrl": "string",
            "FunctionArn": "string",
            "AuthType": "NONE|AWS_IAM",
            "Cors": {"..."},
            "CreationTime": "string",
            "LastModifiedTime": "string",
            "InvokeMode": "BUFFERED|RESPONSE_STREAM"
        }
    ],
    "NextMarker": "string"
}
```

---
