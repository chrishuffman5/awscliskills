# Readiness Checks

Commands for managing Route 53 ARC readiness checks via `aws route53-recovery-readiness`.

### 5.1 `create-readiness-check`

Creates a readiness check that monitors a resource set for recovery readiness. Audits run once every minute.

**Synopsis:**
```bash
aws route53-recovery-readiness create-readiness-check \
    --readiness-check-name <value> \
    --resource-set-name <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--readiness-check-name` | **Yes** | string | -- | Name of the readiness check |
| `--resource-set-name` | **Yes** | string | -- | Name of the resource set to monitor |
| `--tags` | No | map | None | Tags as key-value pairs |

**Output Schema:**
```json
{
    "ReadinessCheckArn": "string",
    "ReadinessCheckName": "string",
    "ResourceSet": "string",
    "Tags": {
        "string": "string"
    }
}
```

---

### 5.2 `get-readiness-check`

Gets details about a readiness check.

**Synopsis:**
```bash
aws route53-recovery-readiness get-readiness-check \
    --readiness-check-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--readiness-check-name` | **Yes** | string | -- | Name of the readiness check |

**Output Schema:**
```json
{
    "ReadinessCheckArn": "string",
    "ReadinessCheckName": "string",
    "ResourceSet": "string",
    "Tags": {
        "string": "string"
    }
}
```

---

### 5.3 `update-readiness-check`

Updates a readiness check to point to a different resource set.

**Synopsis:**
```bash
aws route53-recovery-readiness update-readiness-check \
    --readiness-check-name <value> \
    --resource-set-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--readiness-check-name` | **Yes** | string | -- | Name of the readiness check |
| `--resource-set-name` | **Yes** | string | -- | New resource set name |

**Output Schema:**
```json
{
    "ReadinessCheckArn": "string",
    "ReadinessCheckName": "string",
    "ResourceSet": "string",
    "Tags": {
        "string": "string"
    }
}
```

---

### 5.4 `delete-readiness-check`

Deletes a readiness check.

**Synopsis:**
```bash
aws route53-recovery-readiness delete-readiness-check \
    --readiness-check-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--readiness-check-name` | **Yes** | string | -- | Name of the readiness check to delete |

**Output:** None on success.

---

### 5.5 `list-readiness-checks`

Lists all readiness checks. **Paginated operation.**

**Synopsis:**
```bash
aws route53-recovery-readiness list-readiness-checks \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ReadinessChecks": [
        {
            "ReadinessCheckArn": "string",
            "ReadinessCheckName": "string",
            "ResourceSet": "string",
            "Tags": {
                "string": "string"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 5.6 `get-readiness-check-status`

Gets the readiness status for a readiness check, including per-resource status. **Paginated operation.**

**Synopsis:**
```bash
aws route53-recovery-readiness get-readiness-check-status \
    --readiness-check-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--readiness-check-name` | **Yes** | string | -- | Name of the readiness check |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Readiness": "READY|NOT_READY|UNKNOWN|NOT_AUTHORIZED",
    "Resources": [
        {
            "ComponentId": "string",
            "LastCheckedTimestamp": "timestamp",
            "Readiness": "READY|NOT_READY|UNKNOWN|NOT_AUTHORIZED",
            "ResourceArn": "string"
        }
    ],
    "Messages": [
        {
            "MessageText": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.7 `get-readiness-check-resource-status`

Gets the readiness status for a specific resource within a readiness check, including per-rule results. **Paginated operation.**

**Synopsis:**
```bash
aws route53-recovery-readiness get-readiness-check-resource-status \
    --readiness-check-name <value> \
    --resource-identifier <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--readiness-check-name` | **Yes** | string | -- | Name of the readiness check |
| `--resource-identifier` | **Yes** | string | -- | Resource ARN or ARC-generated identifier |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Readiness": "READY|NOT_READY|UNKNOWN|NOT_AUTHORIZED",
    "Rules": [
        {
            "LastCheckedTimestamp": "timestamp",
            "Messages": [
                {
                    "MessageText": "string"
                }
            ],
            "Readiness": "READY|NOT_READY|UNKNOWN|NOT_AUTHORIZED",
            "RuleId": "string"
        }
    ],
    "NextToken": "string"
}
```
