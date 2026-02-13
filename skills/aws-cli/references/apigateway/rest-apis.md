# REST APIs

### 1.1 `create-rest-api`

Creates a new REST API.

**Synopsis:**
```bash
aws apigateway create-rest-api \
    --name <value> \
    [--description <value>] \
    [--version <value>] \
    [--clone-from <value>] \
    [--binary-media-types <value>] \
    [--minimum-compression-size <value>] \
    [--api-key-source <value>] \
    [--endpoint-configuration <value>] \
    [--policy <value>] \
    [--tags <value>] \
    [--disable-execute-api-endpoint | --no-disable-execute-api-endpoint] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the REST API |
| `--description` | No | string | None | Description of the REST API |
| `--version` | No | string | None | Version identifier for the API |
| `--clone-from` | No | string | None | ID of the REST API to clone from |
| `--binary-media-types` | No | list(string) | None | Binary media types (e.g., `application/octet-stream`, `image/png`) |
| `--minimum-compression-size` | No | integer | None | Minimum payload size (bytes) for compression (0-10485760) |
| `--api-key-source` | No | string | `HEADER` | Source of the API key: `HEADER` or `AUTHORIZER` |
| `--endpoint-configuration` | No | structure | None | Endpoint config. Shorthand: `types=EDGE\|REGIONAL\|PRIVATE,vpcEndpointIds=string,string` |
| `--policy` | No | string | None | JSON resource policy for the API |
| `--tags` | No | map | None | Key-value tags. Shorthand: `KeyName1=string,KeyName2=string` |
| `--disable-execute-api-endpoint` | No | boolean | false | Disable the default execute-api endpoint |

**Output Schema:**
```json
{
    "id": "string",
    "name": "string",
    "description": "string",
    "createdDate": "timestamp",
    "version": "string",
    "warnings": ["string"],
    "binaryMediaTypes": ["string"],
    "minimumCompressionSize": "integer",
    "apiKeySource": "HEADER|AUTHORIZER",
    "endpointConfiguration": {
        "types": ["EDGE|REGIONAL|PRIVATE"],
        "vpcEndpointIds": ["string"]
    },
    "policy": "string",
    "tags": {
        "string": "string"
    },
    "disableExecuteApiEndpoint": "boolean",
    "rootResourceId": "string"
}
```

---

### 1.2 `delete-rest-api`

Deletes the specified REST API.

**Synopsis:**
```bash
aws apigateway delete-rest-api \
    --rest-api-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API to delete |

**Output:** None

---

### 1.3 `get-rest-api`

Gets information about the specified REST API.

**Synopsis:**
```bash
aws apigateway get-rest-api \
    --rest-api-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |

**Output Schema:**
```json
{
    "id": "string",
    "name": "string",
    "description": "string",
    "createdDate": "timestamp",
    "version": "string",
    "warnings": ["string"],
    "binaryMediaTypes": ["string"],
    "minimumCompressionSize": "integer",
    "apiKeySource": "HEADER|AUTHORIZER",
    "endpointConfiguration": {
        "types": ["EDGE|REGIONAL|PRIVATE"],
        "vpcEndpointIds": ["string"]
    },
    "policy": "string",
    "tags": {
        "string": "string"
    },
    "disableExecuteApiEndpoint": "boolean",
    "rootResourceId": "string"
}
```

---

### 1.4 `get-rest-apis`

Lists all REST APIs. **Paginated operation.**

**Synopsis:**
```bash
aws apigateway get-rest-apis \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call (max 500) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "items": [
        {
            "id": "string",
            "name": "string",
            "description": "string",
            "createdDate": "timestamp",
            "version": "string",
            "warnings": ["string"],
            "binaryMediaTypes": ["string"],
            "minimumCompressionSize": "integer",
            "apiKeySource": "HEADER|AUTHORIZER",
            "endpointConfiguration": {
                "types": ["EDGE|REGIONAL|PRIVATE"],
                "vpcEndpointIds": ["string"]
            },
            "policy": "string",
            "tags": {},
            "disableExecuteApiEndpoint": "boolean",
            "rootResourceId": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `import-rest-api`

Imports a REST API from an external Swagger or OpenAPI 3.0 definition file.

**Synopsis:**
```bash
aws apigateway import-rest-api \
    [--fail-on-warnings | --no-fail-on-warnings] \
    [--parameters <value>] \
    --body <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--body` | **Yes** | blob | -- | API definition body (Swagger/OpenAPI JSON or YAML). Use `fileb://` for file |
| `--fail-on-warnings` | No | boolean | false | Fail if warnings are encountered |
| `--parameters` | No | map | None | Import parameters. Shorthand: `KeyName1=string,KeyName2=string`. Common: `endpointConfigurationTypes=REGIONAL` |

**Output Schema:**
```json
{
    "id": "string",
    "name": "string",
    "description": "string",
    "createdDate": "timestamp",
    "version": "string",
    "warnings": ["string"],
    "binaryMediaTypes": ["string"],
    "minimumCompressionSize": "integer",
    "apiKeySource": "HEADER|AUTHORIZER",
    "endpointConfiguration": {
        "types": ["EDGE|REGIONAL|PRIVATE"],
        "vpcEndpointIds": ["string"]
    },
    "policy": "string",
    "tags": {},
    "disableExecuteApiEndpoint": "boolean",
    "rootResourceId": "string"
}
```

---

### 1.6 `put-rest-api`

Replaces the REST API definition with an external API definition (overwrite or merge).

**Synopsis:**
```bash
aws apigateway put-rest-api \
    --rest-api-id <value> \
    [--mode <value>] \
    [--fail-on-warnings | --no-fail-on-warnings] \
    [--parameters <value>] \
    --body <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--body` | **Yes** | blob | -- | API definition body. Use `fileb://` for file |
| `--mode` | No | string | `overwrite` | Import mode: `merge` or `overwrite` |
| `--fail-on-warnings` | No | boolean | false | Fail if warnings are encountered |
| `--parameters` | No | map | None | Import parameters |

**Output Schema:** Same as `create-rest-api`.

---

### 1.7 `update-rest-api`

Updates REST API properties using patch operations.

**Synopsis:**
```bash
aws apigateway update-rest-api \
    --rest-api-id <value> \
    [--patch-operations <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rest-api-id` | **Yes** | string | -- | ID of the REST API |
| `--patch-operations` | No | list | None | Patch operations. Shorthand: `op=replace,path=/name,value=new-name` |

**Patch Operation Structure:**
```json
[
    {
        "op": "add|remove|replace|move|copy|test",
        "path": "string",
        "value": "string",
        "from": "string"
    }
]
```

Supported paths: `/name`, `/description`, `/version`, `/binaryMediaTypes`, `/minimumCompressionSize`, `/apiKeySource`, `/disableExecuteApiEndpoint`, `/policy`.

**Output Schema:** Same as `create-rest-api`.
