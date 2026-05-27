# API Keys & Usage Plans

### 6.1 `create-api-key`

Creates a new API key.

**Synopsis:**
```bash
aws apigateway create-api-key \
    [--name <value>] \
    [--description <value>] \
    [--enabled | --no-enabled] \
    [--generate-distinct-id | --no-generate-distinct-id] \
    [--value <value>] \
    [--stage-keys <value>] \
    [--customer-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | No | string | None | Name of the API key |
| `--description` | No | string | None | Description |
| `--enabled` | No | boolean | false | Whether the API key is active |
| `--generate-distinct-id` | No | boolean | false | Generate a unique ID for the key |
| `--value` | No | string | None | Specify the API key value (auto-generated if omitted) |
| `--stage-keys` | No | list | None | Associated stages. Shorthand: `restApiId=string,stageName=string` |
| `--customer-id` | No | string | None | Customer identifier (from external system) |
| `--tags` | No | map | None | Key-value tags |

**Output Schema:**
```json
{
    "id": "string",
    "value": "string",
    "name": "string",
    "customerId": "string",
    "description": "string",
    "enabled": "boolean",
    "createdDate": "timestamp",
    "lastUpdatedDate": "timestamp",
    "stageKeys": ["string"],
    "tags": {}
}
```

---

### 6.2 `delete-api-key`

Deletes an API key.

**Synopsis:**
```bash
aws apigateway delete-api-key \
    --api-key <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-key` | **Yes** | string | -- | ID of the API key to delete |

**Output:** None

---

### 6.3 `get-api-key`

Gets information about an API key.

**Synopsis:**
```bash
aws apigateway get-api-key \
    --api-key <value> \
    [--include-value | --no-include-value] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-key` | **Yes** | string | -- | ID of the API key |
| `--include-value` | No | boolean | false | Include the API key value in the response |

**Output Schema:** Same as `create-api-key`.

---

### 6.4 `get-api-keys`

Lists API keys. **Paginated operation.**

**Synopsis:**
```bash
aws apigateway get-api-keys \
    [--name-query <value>] \
    [--customer-id <value>] \
    [--include-values | --no-include-values] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name-query` | No | string | None | Filter by name prefix |
| `--customer-id` | No | string | None | Filter by customer ID |
| `--include-values` | No | boolean | false | Include key values in results |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 500) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "warnings": ["string"],
    "items": [
        {
            "id": "string",
            "value": "string",
            "name": "string",
            "customerId": "string",
            "description": "string",
            "enabled": "boolean",
            "createdDate": "timestamp",
            "lastUpdatedDate": "timestamp",
            "stageKeys": ["string"],
            "tags": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 6.5 `update-api-key`

Updates an API key using patch operations.

**Synopsis:**
```bash
aws apigateway update-api-key \
    --api-key <value> \
    [--patch-operations <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-key` | **Yes** | string | -- | ID of the API key |
| `--patch-operations` | No | list | None | Patch operations |

**Supported Patch Paths:** `/name`, `/description`, `/enabled`, `/customerId`

**Output Schema:** Same as `create-api-key`.

---

### 6.6 `create-usage-plan`

Creates a usage plan with throttle and quota limits.

**Synopsis:**
```bash
aws apigateway create-usage-plan \
    --name <value> \
    [--description <value>] \
    [--api-stages <value>] \
    [--throttle <value>] \
    [--quota <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the usage plan |
| `--description` | No | string | None | Description |
| `--api-stages` | No | list | None | Associated API stages. Shorthand: `apiId=string,stage=string,throttle={path1={burstLimit=integer,rateLimit=double}}` |
| `--throttle` | No | structure | None | Throttle settings. Shorthand: `burstLimit=integer,rateLimit=double` |
| `--quota` | No | structure | None | Quota settings. Shorthand: `limit=integer,offset=integer,period=DAY\|WEEK\|MONTH` |
| `--tags` | No | map | None | Key-value tags |

**Output Schema:**
```json
{
    "id": "string",
    "name": "string",
    "description": "string",
    "apiStages": [
        {
            "apiId": "string",
            "stage": "string",
            "throttle": {
                "string": {
                    "burstLimit": "integer",
                    "rateLimit": "double"
                }
            }
        }
    ],
    "throttle": {
        "burstLimit": "integer",
        "rateLimit": "double"
    },
    "quota": {
        "limit": "integer",
        "offset": "integer",
        "period": "DAY|WEEK|MONTH"
    },
    "productCode": "string",
    "tags": {}
}
```

---

### 6.7 `delete-usage-plan`

Deletes a usage plan.

**Synopsis:**
```bash
aws apigateway delete-usage-plan \
    --usage-plan-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--usage-plan-id` | **Yes** | string | -- | ID of the usage plan |

**Output:** None

---

### 6.8 `get-usage-plan`

Gets information about a usage plan.

**Synopsis:**
```bash
aws apigateway get-usage-plan \
    --usage-plan-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--usage-plan-id` | **Yes** | string | -- | ID of the usage plan |

**Output Schema:** Same as `create-usage-plan`.

---

### 6.9 `get-usage-plans`

Lists usage plans. **Paginated operation.**

**Synopsis:**
```bash
aws apigateway get-usage-plans \
    [--key-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | No | string | None | Filter by API key ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "items": [
        {
            "id": "string",
            "name": "string",
            "description": "string",
            "apiStages": [],
            "throttle": {},
            "quota": {},
            "tags": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 6.10 `update-usage-plan`

Updates a usage plan using patch operations.

**Synopsis:**
```bash
aws apigateway update-usage-plan \
    --usage-plan-id <value> \
    [--patch-operations <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--usage-plan-id` | **Yes** | string | -- | ID of the usage plan |
| `--patch-operations` | No | list | None | Patch operations |

**Supported Patch Paths:** `/name`, `/description`, `/apiStages`, `/throttle/burstLimit`, `/throttle/rateLimit`, `/quota/limit`, `/quota/offset`, `/quota/period`, `/productCode`

**Output Schema:** Same as `create-usage-plan`.

---

### 6.11 `create-usage-plan-key`

Adds an API key to a usage plan.

**Synopsis:**
```bash
aws apigateway create-usage-plan-key \
    --usage-plan-id <value> \
    --key-id <value> \
    --key-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--usage-plan-id` | **Yes** | string | -- | ID of the usage plan |
| `--key-id` | **Yes** | string | -- | ID of the API key |
| `--key-type` | **Yes** | string | -- | Key type: `API_KEY` |

**Output Schema:**
```json
{
    "id": "string",
    "type": "API_KEY",
    "value": "string",
    "name": "string"
}
```

---

### 6.12 `delete-usage-plan-key`

Removes an API key from a usage plan.

**Synopsis:**
```bash
aws apigateway delete-usage-plan-key \
    --usage-plan-id <value> \
    --key-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--usage-plan-id` | **Yes** | string | -- | ID of the usage plan |
| `--key-id` | **Yes** | string | -- | ID of the API key |

**Output:** None

---

### 6.13 `get-usage-plan-key`

Gets a usage plan key.

**Synopsis:**
```bash
aws apigateway get-usage-plan-key \
    --usage-plan-id <value> \
    --key-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--usage-plan-id` | **Yes** | string | -- | ID of the usage plan |
| `--key-id` | **Yes** | string | -- | ID of the API key |

**Output Schema:** Same as `create-usage-plan-key`.

---

### 6.14 `get-usage-plan-keys`

Lists keys in a usage plan. **Paginated operation.**

**Synopsis:**
```bash
aws apigateway get-usage-plan-keys \
    --usage-plan-id <value> \
    [--name-query <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--usage-plan-id` | **Yes** | string | -- | ID of the usage plan |
| `--name-query` | No | string | None | Filter by name prefix |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "items": [
        {
            "id": "string",
            "type": "API_KEY",
            "value": "string",
            "name": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.15 `get-usage`

Gets the usage data of a usage plan for a specified time period. **Paginated operation.**

**Synopsis:**
```bash
aws apigateway get-usage \
    --usage-plan-id <value> \
    --start-date <value> \
    --end-date <value> \
    [--key-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--usage-plan-id` | **Yes** | string | -- | ID of the usage plan |
| `--start-date` | **Yes** | string | -- | Start date (format: `YYYY-MM-DD`) |
| `--end-date` | **Yes** | string | -- | End date (format: `YYYY-MM-DD`) |
| `--key-id` | No | string | None | Filter by API key ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "usagePlanId": "string",
    "startDate": "string",
    "endDate": "string",
    "items": {
        "string": [
            [
                "long (used)",
                "long (remaining)"
            ]
        ]
    },
    "NextToken": "string"
}
```
