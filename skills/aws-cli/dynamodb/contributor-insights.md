# Contributor Insights

### 13.1 `describe-contributor-insights`

Returns information about contributor insights for a table or GSI.

**Synopsis:**
```bash
aws dynamodb describe-contributor-insights \
    --table-name <value> \
    [--index-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-name` | **Yes** | string | -- | Table name or ARN (1-1024 chars) |
| `--index-name` | No | string | -- | GSI name (3-255 chars) |

**Output Schema:**
```json
{
    "TableName": "string",
    "IndexName": "string",
    "ContributorInsightsRuleList": ["string"],
    "ContributorInsightsStatus": "ENABLING|ENABLED|DISABLING|DISABLED|FAILED",
    "LastUpdateDateTime": "timestamp",
    "FailureException": {
        "ExceptionName": "string",
        "ExceptionDescription": "string"
    }
}
```

---

### 13.2 `update-contributor-insights`

Enables or disables contributor insights on a table or GSI.

**Synopsis:**
```bash
aws dynamodb update-contributor-insights \
    --table-name <value> \
    --contributor-insights-action <value> \
    [--index-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-name` | **Yes** | string | -- | Table name or ARN (1-1024 chars) |
| `--contributor-insights-action` | **Yes** | string | -- | `ENABLE` or `DISABLE` |
| `--index-name` | No | string | -- | GSI name (3-255 chars) |

**Output Schema:**
```json
{
    "TableName": "string",
    "IndexName": "string",
    "ContributorInsightsStatus": "ENABLING|ENABLED|DISABLING|DISABLED|FAILED"
}
```

---

### 13.3 `list-contributor-insights`

Lists contributor insights summaries. **Paginated operation.**

**Synopsis:**
```bash
aws dynamodb list-contributor-insights \
    [--table-name <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-name` | No | string | -- | Filter by table name (1-1024 chars) |
| `--next-token` | No | string | -- | Pagination token |
| `--max-results` | No | integer | -- | Max results (0-100) |

**Output Schema:**
```json
{
    "ContributorInsightsSummaries": [
        {
            "TableName": "string",
            "IndexName": "string",
            "ContributorInsightsStatus": "ENABLING|ENABLED|DISABLING|DISABLED|FAILED"
        }
    ],
    "NextToken": "string"
}
```

---
