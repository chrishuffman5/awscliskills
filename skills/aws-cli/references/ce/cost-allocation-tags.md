# Cost Allocation Tags

### 8.1 `list-cost-allocation-tags`

Lists cost allocation tags in the account. All inputs are optional and serve as filters. **Paginated.**

**Synopsis:**
```bash
aws ce list-cost-allocation-tags \
    [--status <value>] \
    [--tag-keys <value>] \
    [--type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--status` | No | string | None | `Active` or `Inactive` |
| `--tag-keys` | No | list(string) | None | Specific tag keys to retrieve (1-100 keys) |
| `--type` | No | string | None | `AWSGenerated` or `UserDefined` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CostAllocationTags": [
        {
            "TagKey": "string",
            "Type": "AWSGenerated|UserDefined",
            "Status": "Active|Inactive",
            "LastUpdatedDate": "string",
            "LastUsedDate": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.2 `update-cost-allocation-tags-status`

Activates or deactivates cost allocation tags. You can activate up to 500 tags.

**Synopsis:**
```bash
aws ce update-cost-allocation-tags-status \
    --cost-allocation-tags-status <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cost-allocation-tags-status` | **Yes** | list | -- | Tag keys and their target status. Shorthand: `TagKey=string,Status=Active\|Inactive ...` |

**Input Structure:**
```json
[
    {
        "TagKey": "string",
        "Status": "Active|Inactive"
    }
]
```

**Output Schema:**
```json
{
    "Errors": [
        {
            "TagKey": "string",
            "Code": "string",
            "Message": "string"
        }
    ]
}
```

---

### 8.3 `list-cost-allocation-tag-backfill-history`

Lists the history of cost allocation tag backfill requests. **Paginated.**

**Synopsis:**
```bash
aws ce list-cost-allocation-tag-backfill-history \
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
    "BackfillRequests": [
        {
            "BackfillFrom": "string",
            "RequestedAt": "string",
            "CompletedAt": "string",
            "BackfillStatus": "SUCCEEDED|PROCESSING|FAILED"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.4 `start-cost-allocation-tag-backfill`

Starts a cost allocation tag backfill request to apply tags retroactively to historical cost data.

**Synopsis:**
```bash
aws ce start-cost-allocation-tag-backfill \
    --backfill-from <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backfill-from` | **Yes** | string | -- | Date to backfill from (format: `YYYY-MM-DD`) |

**Output Schema:**
```json
{
    "BackfillRequest": {
        "BackfillFrom": "string",
        "RequestedAt": "string",
        "CompletedAt": "string",
        "BackfillStatus": "SUCCEEDED|PROCESSING|FAILED"
    }
}
```
