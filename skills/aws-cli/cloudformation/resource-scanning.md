# Resource Scanning

### 7.1 `start-resource-scan`

Starts scanning for resources in the account. Used by the IaC generator to discover existing resources that can be added to generated templates.

**Synopsis:**
```bash
aws cloudformation start-resource-scan \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--client-request-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "ResourceScanId": "string"
}
```

---

### 7.2 `describe-resource-scan`

Describes a resource scan, including its status and progress.

**Synopsis:**
```bash
aws cloudformation describe-resource-scan \
    --resource-scan-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-scan-id` | **Yes** | string | -- | Resource scan ID |

**Output Schema:**
```json
{
    "ResourceScanId": "string",
    "Status": "IN_PROGRESS|FAILED|COMPLETE|EXPIRED",
    "StatusReason": "string",
    "StartTime": "timestamp",
    "EndTime": "timestamp",
    "PercentageCompleted": "double",
    "ResourceTypes": ["string"],
    "ResourcesScanned": "integer",
    "ResourcesRead": "integer"
}
```

---

### 7.3 `list-resource-scans`

Lists resource scans in the account. **Paginated operation.**

**Synopsis:**
```bash
aws cloudformation list-resource-scans \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "ResourceScanSummaries": [
        {
            "ResourceScanId": "string",
            "Status": "IN_PROGRESS|FAILED|COMPLETE|EXPIRED",
            "StatusReason": "string",
            "StartTime": "timestamp",
            "EndTime": "timestamp",
            "PercentageCompleted": "double"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.4 `list-resource-scan-resources`

Lists resources discovered by a resource scan. **Paginated operation.**

**Synopsis:**
```bash
aws cloudformation list-resource-scan-resources \
    --resource-scan-id <value> \
    [--resource-identifier <value>] \
    [--resource-type-prefix <value>] \
    [--tag-key <value>] \
    [--tag-value <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-scan-id` | **Yes** | string | -- | Resource scan ID |
| `--resource-identifier` | No | string | None | Filter by resource identifier |
| `--resource-type-prefix` | No | string | None | Filter by resource type prefix (e.g., `AWS::S3`) |
| `--tag-key` | No | string | None | Filter by tag key |
| `--tag-value` | No | string | None | Filter by tag value |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "Resources": [
        {
            "ResourceType": "string",
            "ResourceIdentifier": {
                "key": "value"
            },
            "ManagedByStack": true|false
        }
    ],
    "NextToken": "string"
}
```

---

### 7.5 `list-resource-scan-related-resources`

Lists resources related to a given resource discovered by a resource scan. **Paginated operation.**

**Synopsis:**
```bash
aws cloudformation list-resource-scan-related-resources \
    --resource-scan-id <value> \
    --resources <value> \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-scan-id` | **Yes** | string | -- | Resource scan ID |
| `--resources` | **Yes** | list | -- | Resources to find related resources for. JSON: `[{"ResourceType":"string","ResourceIdentifier":{"key":"value"}}]` |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "RelatedResources": [
        {
            "ResourceType": "string",
            "ResourceIdentifier": {
                "key": "value"
            },
            "ManagedByStack": true|false
        }
    ],
    "NextToken": "string"
}
```
