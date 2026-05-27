# Concurrency

### 7.1 `put-function-concurrency`

Sets the maximum number of concurrent executions reserved for a function.

**Synopsis:**
```bash
aws lambda put-function-concurrency \
    --function-name <value> \
    --reserved-concurrent-executions <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |
| `--reserved-concurrent-executions` | **Yes** | integer | -- | Concurrent executions to reserve (min 0). Set to 0 to throttle the function |

**Output Schema:**
```json
{
    "ReservedConcurrentExecutions": "integer"
}
```

---

### 7.2 `get-function-concurrency`

Returns the reserved concurrency setting for a function.

**Synopsis:**
```bash
aws lambda get-function-concurrency \
    --function-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |

**Output Schema:**
```json
{
    "ReservedConcurrentExecutions": "integer"
}
```

---

### 7.3 `delete-function-concurrency`

Removes the reserved concurrency setting, returning the function to the unreserved pool.

**Synopsis:**
```bash
aws lambda delete-function-concurrency \
    --function-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |

**Output:** None on success.

---

### 7.4 `put-provisioned-concurrency-config`

Allocates provisioned concurrency for a function version or alias. Pre-initializes execution environments to reduce cold starts.

**Synopsis:**
```bash
aws lambda put-provisioned-concurrency-config \
    --function-name <value> \
    --qualifier <value> \
    --provisioned-concurrent-executions <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |
| `--qualifier` | **Yes** | string | -- | Version number or alias name (1-128 chars). Cannot use `$LATEST` |
| `--provisioned-concurrent-executions` | **Yes** | integer | -- | Amount of provisioned concurrency (min 1) |

**Output Schema:**
```json
{
    "RequestedProvisionedConcurrentExecutions": "integer",
    "AvailableProvisionedConcurrentExecutions": "integer",
    "AllocatedProvisionedConcurrentExecutions": "integer",
    "Status": "IN_PROGRESS|READY|FAILED",
    "StatusReason": "string",
    "LastModified": "string"
}
```

---

### 7.5 `get-provisioned-concurrency-config`

Returns the provisioned concurrency configuration for a function version or alias.

**Synopsis:**
```bash
aws lambda get-provisioned-concurrency-config \
    --function-name <value> \
    --qualifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |
| `--qualifier` | **Yes** | string | -- | Version number or alias name (1-128 chars) |

**Output Schema:** Same as `put-provisioned-concurrency-config`.

---

### 7.6 `delete-provisioned-concurrency-config`

Deletes the provisioned concurrency configuration for a function version or alias.

**Synopsis:**
```bash
aws lambda delete-provisioned-concurrency-config \
    --function-name <value> \
    --qualifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |
| `--qualifier` | **Yes** | string | -- | Version number or alias name (1-128 chars) |

**Output:** None on success.

---

### 7.7 `list-provisioned-concurrency-configs`

Lists provisioned concurrency configurations for a function. **Paginated operation.**

**Synopsis:**
```bash
aws lambda list-provisioned-concurrency-configs \
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
    "ProvisionedConcurrencyConfigs": [
        {
            "FunctionArn": "string",
            "RequestedProvisionedConcurrentExecutions": "integer",
            "AvailableProvisionedConcurrentExecutions": "integer",
            "AllocatedProvisionedConcurrentExecutions": "integer",
            "Status": "IN_PROGRESS|READY|FAILED",
            "StatusReason": "string",
            "LastModified": "string"
        }
    ],
    "NextMarker": "string"
}
```

---
