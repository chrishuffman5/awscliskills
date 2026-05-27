# Functions

### 3.1 `create-function`

Creates a CloudFront function.

**Synopsis:**
```bash
aws cloudfront create-function \
    --name <value> \
    --function-config <value> \
    --function-code <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--name` | **Yes** | string | Function name (1-64 chars). Pattern: `[a-zA-Z0-9-_]{1,64}` |
| `--function-config` | **Yes** | structure | Function configuration (Comment, Runtime) |
| `--function-code` | **Yes** | blob | Function code (1-40,960 bytes). Use `fileb://function.js` |

**Function Config structure:**

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `Comment` | **Yes** | string | Description of the function |
| `Runtime` | **Yes** | string | `cloudfront-js-1.0` or `cloudfront-js-2.0` |
| `KeyValueStoreAssociations` | No | structure | Key value store associations |

**Output Schema:**
```json
{
    "FunctionSummary": {
        "Name": "string",
        "Status": "string",
        "FunctionConfig": {
            "Comment": "string",
            "Runtime": "cloudfront-js-1.0|cloudfront-js-2.0",
            "KeyValueStoreAssociations": {
                "Quantity": "integer",
                "Items": [{"KeyValueStoreARN": "string"}]
            }
        },
        "FunctionMetadata": {
            "FunctionARN": "string",
            "Stage": "DEVELOPMENT|LIVE",
            "CreatedTime": "timestamp",
            "LastModifiedTime": "timestamp"
        }
    },
    "Location": "string",
    "ETag": "string"
}
```

---

### 3.2 `delete-function`

Deletes a CloudFront function. Function must not be associated with any cache behavior.

**Synopsis:**
```bash
aws cloudfront delete-function \
    --name <value> \
    --if-match <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--name` | **Yes** | string | Function name |
| `--if-match` | **Yes** | string | ETag from `describe-function` |

**Output:** None.

---

### 3.3 `describe-function`

Gets summary information about a function (without the code).

**Synopsis:**
```bash
aws cloudfront describe-function \
    --name <value> \
    [--stage <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Function name |
| `--stage` | No | string | `DEVELOPMENT` | `DEVELOPMENT` or `LIVE` |

**Output Schema:**
```json
{
    "FunctionSummary": {
        "Name": "string",
        "Status": "string",
        "FunctionConfig": { "..." },
        "FunctionMetadata": {
            "FunctionARN": "string",
            "Stage": "DEVELOPMENT|LIVE",
            "CreatedTime": "timestamp",
            "LastModifiedTime": "timestamp"
        }
    },
    "ETag": "string"
}
```

---

### 3.4 `get-function`

Gets the function code and configuration.

**Synopsis:**
```bash
aws cloudfront get-function \
    --name <value> \
    [--stage <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Function name |
| `--stage` | No | string | `DEVELOPMENT` | `DEVELOPMENT` or `LIVE` |

**Output Schema:**
```json
{
    "FunctionCode": "blob",
    "ContentType": "string",
    "ETag": "string"
}
```

---

### 3.5 `list-functions`

Lists CloudFront functions.

**Synopsis:**
```bash
aws cloudfront list-functions \
    [--marker <value>] \
    [--max-items <value>] \
    [--stage <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--marker` | No | string | None | Pagination marker |
| `--max-items` | No | string | None | Maximum items to return |
| `--stage` | No | string | `DEVELOPMENT` | `DEVELOPMENT` or `LIVE` |

**Output Schema:**
```json
{
    "FunctionList": {
        "MaxItems": "integer",
        "Quantity": "integer",
        "NextMarker": "string",
        "Items": [
            {
                "Name": "string",
                "Status": "string",
                "FunctionConfig": { "..." },
                "FunctionMetadata": { "..." }
            }
        ]
    }
}
```

---

### 3.6 `publish-function`

Publishes a CloudFront function from DEVELOPMENT to LIVE stage.

**Synopsis:**
```bash
aws cloudfront publish-function \
    --name <value> \
    --if-match <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--name` | **Yes** | string | Function name |
| `--if-match` | **Yes** | string | ETag from `describe-function` (DEVELOPMENT stage) |

**Output Schema:**
```json
{
    "FunctionSummary": {
        "Name": "string",
        "Status": "string",
        "FunctionConfig": { "..." },
        "FunctionMetadata": {
            "FunctionARN": "string",
            "Stage": "LIVE",
            "CreatedTime": "timestamp",
            "LastModifiedTime": "timestamp"
        }
    }
}
```

---

### 3.7 `test-function`

Tests a CloudFront function with a provided event object.

**Synopsis:**
```bash
aws cloudfront test-function \
    --name <value> \
    --if-match <value> \
    --event-object <value> \
    [--stage <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Function name |
| `--if-match` | **Yes** | string | -- | ETag from `describe-function` |
| `--event-object` | **Yes** | blob | -- | Event object to test with. Use `fileb://event.json` |
| `--stage` | No | string | `DEVELOPMENT` | `DEVELOPMENT` or `LIVE` |

**Output Schema:**
```json
{
    "TestResult": {
        "FunctionSummary": { "..." },
        "ComputeUtilization": "string",
        "FunctionExecutionLogs": ["string"],
        "FunctionErrorMessage": "string",
        "FunctionOutput": "string"
    }
}
```

---

### 3.8 `update-function`

Updates a CloudFront function's code and/or configuration.

**Synopsis:**
```bash
aws cloudfront update-function \
    --name <value> \
    --if-match <value> \
    --function-config <value> \
    --function-code <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--name` | **Yes** | string | Function name |
| `--if-match` | **Yes** | string | ETag from `describe-function` |
| `--function-config` | **Yes** | structure | Updated function configuration |
| `--function-code` | **Yes** | blob | Updated function code. Use `fileb://function.js` |

**Output Schema:** Same as `create-function`.

---
