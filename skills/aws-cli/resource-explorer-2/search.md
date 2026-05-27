# Search

### 3.1 `search`

Searches for resources using a query string. Returns up to 1,000 results. Uses the default view unless a specific view ARN is provided. **Paginated.**

**Synopsis:**
```bash
aws resource-explorer-2 search \
    --query-string <value> \
    [--view-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-string` | **Yes** | string | -- | Search keywords and filters (0-1280 chars, case-insensitive). Empty string returns all results |
| `--view-arn` | No | string | None | View to use. Defaults to Region's default view (0-1000 chars) |

**Query Syntax:**

| Prefix | Example | Description |
|--------|---------|-------------|
| (none) | `my-bucket` | Free-text search across all fields |
| `service:` | `service:ec2` | Filter by AWS service |
| `resourcetype:` | `resourcetype:ec2:instance` | Filter by resource type |
| `region:` | `region:us-east-1` | Filter by Region |
| `tag:` | `tag:Env=Prod` | Filter by tag key=value |
| `id:` | `id:i-0123456789` | Filter by resource identifier |
| `-` | `-service:s3` | Negate a filter |

**Output Schema:**
```json
{
    "Resources": [
        {
            "Arn": "string",
            "OwningAccountId": "string",
            "Region": "string",
            "ResourceType": "string",
            "Service": "string",
            "LastReportedAt": "timestamp",
            "Properties": [
                {
                    "Name": "string",
                    "LastReportedAt": "timestamp",
                    "Data": {}
                }
            ]
        }
    ],
    "NextToken": "string",
    "ViewArn": "string",
    "Count": {
        "TotalResources": "long",
        "Complete": "boolean"
    }
}
```

> `Count.Complete` indicates whether the count is exact (`true`) or a lower bound (`false`, capped at 1,000).

---

### 3.2 `list-resources`

Lists resources matching filter criteria. Similar to `search` but uses filter structure instead of query string. **Paginated.**

**Synopsis:**
```bash
aws resource-explorer-2 list-resources \
    [--filters <value>] \
    [--view-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | structure | None | Filter criteria. Shorthand: `FilterString="service:ec2 region:us-east-1"` (0-2048 chars) |
| `--view-arn` | No | string | None | View to use. Defaults to Region's default view (0-1000 chars) |

**Output Schema:**
```json
{
    "Resources": [
        {
            "Arn": "string",
            "OwningAccountId": "string",
            "Region": "string",
            "ResourceType": "string",
            "Service": "string",
            "LastReportedAt": "timestamp",
            "Properties": [
                {
                    "Name": "string",
                    "LastReportedAt": "timestamp",
                    "Data": {}
                }
            ]
        }
    ],
    "NextToken": "string",
    "ViewArn": "string"
}
```

---

### 3.3 `list-supported-resource-types`

Lists all resource types that Resource Explorer can discover and index. **Paginated.**

**Synopsis:**
```bash
aws resource-explorer-2 list-supported-resource-types \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:** Pagination only.

**Output Schema:**
```json
{
    "ResourceTypes": [
        {
            "ResourceType": "string",
            "Service": "string"
        }
    ],
    "NextToken": "string"
}
```
