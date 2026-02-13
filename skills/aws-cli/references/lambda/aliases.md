# Aliases

### 5.1 `create-alias`

Creates an alias for a Lambda function version. Aliases can be used for traffic shifting between versions.

**Synopsis:**
```bash
aws lambda create-alias \
    --function-name <value> \
    --name <value> \
    --function-version <value> \
    [--description <value>] \
    [--routing-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |
| `--name` | **Yes** | string | -- | Alias name (1-128 chars). Cannot be a number-only string |
| `--function-version` | **Yes** | string | -- | Version to route to (e.g., `1`, `$LATEST`) |
| `--description` | No | string | -- | Description (0-256 chars) |
| `--routing-config` | No | structure | -- | Traffic splitting. JSON: `{"AdditionalVersionWeights":{"2":0.1}}` routes 10% to version 2 |

**Output Schema:**
```json
{
    "AliasArn": "string",
    "Name": "string",
    "FunctionVersion": "string",
    "Description": "string",
    "RoutingConfig": {
        "AdditionalVersionWeights": {"string": "double"}
    },
    "RevisionId": "string"
}
```

---

### 5.2 `get-alias`

Returns details about a function alias.

**Synopsis:**
```bash
aws lambda get-alias \
    --function-name <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |
| `--name` | **Yes** | string | -- | Alias name (1-128 chars) |

**Output Schema:** Same as `create-alias`.

---

### 5.3 `list-aliases`

Returns a list of function aliases. **Paginated operation.**

**Synopsis:**
```bash
aws lambda list-aliases \
    --function-name <value> \
    [--function-version <value>] \
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
| `--function-version` | No | string | -- | Filter by version pointed to |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Aliases": [
        {
            "AliasArn": "string",
            "Name": "string",
            "FunctionVersion": "string",
            "Description": "string",
            "RoutingConfig": {
                "AdditionalVersionWeights": {"string": "double"}
            },
            "RevisionId": "string"
        }
    ],
    "NextMarker": "string"
}
```

---

### 5.4 `update-alias`

Updates a function alias to point to a different version or configure traffic splitting.

**Synopsis:**
```bash
aws lambda update-alias \
    --function-name <value> \
    --name <value> \
    [--function-version <value>] \
    [--description <value>] \
    [--routing-config <value>] \
    [--revision-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |
| `--name` | **Yes** | string | -- | Alias name (1-128 chars) |
| `--function-version` | No | string | -- | New version to route to |
| `--description` | No | string | -- | Description (0-256 chars) |
| `--routing-config` | No | structure | -- | Traffic splitting config |
| `--revision-id` | No | string | -- | Only update if revision ID matches |

**Output Schema:** Same as `create-alias`.

---

### 5.5 `delete-alias`

Deletes a function alias.

**Synopsis:**
```bash
aws lambda delete-alias \
    --function-name <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |
| `--name` | **Yes** | string | -- | Alias name (1-128 chars) |

**Output:** None on success.

---
