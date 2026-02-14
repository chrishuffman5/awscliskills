# Queries

### 13.1 `execute-query`

Runs a SQL-like query against IoT SiteWise metadata and data. **Paginated operation.**

**Synopsis:**
```bash
aws iotsitewise execute-query \
    --query-statement <value> \
    [--client-token <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-statement` | **Yes** | string | -- | IoT SiteWise SQL query statement |
| `--client-token` | No | string | Auto | Idempotency token |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "columns": [
        {
            "name": "string",
            "type": {
                "scalarType": "BOOLEAN|INT|DOUBLE|TIMESTAMP|STRING"
            }
        }
    ],
    "rows": [
        {
            "data": [
                {
                    "scalarValue": "string",
                    "arrayValue": [],
                    "rowValue": {"data": []},
                    "nullValue": "boolean"
                }
            ]
        }
    ],
    "nextToken": "string"
}
```
