# Usage & Tags

### 13.1 `get-usage-statistics`

Retrieves usage statistics for the account. **Paginated operation.**

**Synopsis:**
```bash
aws macie2 get-usage-statistics \
    [--filter-by <value>] \
    [--sort-by <value>] \
    [--time-range <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter-by` | No | list | None | Filter criteria |
| `--sort-by` | No | structure | None | Sort criteria |
| `--time-range` | No | string | None | Time range: `MONTH_TO_DATE` or `PAST_30_DAYS` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Structure:**
```json
[
    {
        "comparator": "GT|GTE|LT|LTE|EQ|NE|CONTAINS",
        "key": "accountId|serviceLimit|freeTrialStartDate|total",
        "values": ["string"]
    }
]
```

**Output Schema:**
```json
{
    "records": [
        {
            "accountId": "string",
            "automatedDiscoveryFreeTrialStartDate": "timestamp",
            "freeTrialStartDate": "timestamp",
            "usage": [
                {
                    "currency": "USD",
                    "estimatedCost": "string",
                    "serviceLimit": {
                        "isServiceLimited": "boolean",
                        "unit": "TERABYTES",
                        "value": "long"
                    },
                    "type": "DATA_INVENTORY_EVALUATION|SENSITIVE_DATA_DISCOVERY|AUTOMATED_SENSITIVE_DATA_DISCOVERY|AUTOMATED_OBJECT_MONITORING",
                    "usageCategory": "string"
                }
            ]
        }
    ],
    "nextToken": "string",
    "timeRange": "MONTH_TO_DATE|PAST_30_DAYS"
}
```

---

### 13.2 `get-usage-totals`

Retrieves aggregated usage totals for the account.

**Synopsis:**
```bash
aws macie2 get-usage-totals \
    [--time-range <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--time-range` | No | string | None | Time range: `MONTH_TO_DATE` or `PAST_30_DAYS` |

**Output Schema:**
```json
{
    "timeRange": "MONTH_TO_DATE|PAST_30_DAYS",
    "usageTotals": [
        {
            "currency": "USD",
            "estimatedCost": "string",
            "type": "DATA_INVENTORY_EVALUATION|SENSITIVE_DATA_DISCOVERY|AUTOMATED_SENSITIVE_DATA_DISCOVERY|AUTOMATED_OBJECT_MONITORING"
        }
    ]
}
```

---

### 13.3 `tag-resource`

Adds tags to a Macie resource.

**Synopsis:**
```bash
aws macie2 tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | map | -- | Tags to add (max 50) |

**Output:** None (HTTP 200 on success)

---

### 13.4 `untag-resource`

Removes tags from a Macie resource.

**Synopsis:**
```bash
aws macie2 untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to untag |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output:** None (HTTP 200 on success)

---

### 13.5 `list-tags-for-resource`

Lists tags for a Macie resource.

**Synopsis:**
```bash
aws macie2 list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |

**Output Schema:**
```json
{
    "tags": {
        "string": "string"
    }
}
```
