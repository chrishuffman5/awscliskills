# Query & Scan

### 3.1 `query`

Retrieves items from a table or index using a key condition expression. Results are sorted by sort key. **Paginated operation.**

**Synopsis:**
```bash
aws dynamodb query \
    --table-name <value> \
    --key-condition-expression <value> \
    [--index-name <value>] \
    [--select <value>] \
    [--projection-expression <value>] \
    [--filter-expression <value>] \
    [--expression-attribute-names <value>] \
    [--expression-attribute-values <value>] \
    [--consistent-read | --no-consistent-read] \
    [--scan-index-forward | --no-scan-index-forward] \
    [--return-consumed-capacity <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-name` | **Yes** | string | -- | Table name or ARN (1-1024 chars) |
| `--key-condition-expression` | **Yes** | string | -- | Key condition. Partition key must use `=`. Sort key can use `=`, `<`, `<=`, `>`, `>=`, `BETWEEN`, `begins_with` |
| `--index-name` | No | string | -- | Name of GSI or LSI to query (3-255 chars) |
| `--select` | No | string | `ALL_ATTRIBUTES` | `ALL_ATTRIBUTES`, `ALL_PROJECTED_ATTRIBUTES`, `SPECIFIC_ATTRIBUTES`, `COUNT` |
| `--projection-expression` | No | string | -- | Comma-separated attributes to return |
| `--filter-expression` | No | string | -- | Applied after query, before returning. Does not reduce consumed capacity |
| `--expression-attribute-names` | No | map | -- | `#name` substitution tokens |
| `--expression-attribute-values` | No | map | -- | `:value` substitution tokens |
| `--consistent-read` | No | boolean | false | Strongly consistent read. Not supported on GSI |
| `--scan-index-forward` | No | boolean | true | `true` = ascending, `false` = descending sort by sort key |
| `--return-consumed-capacity` | No | string | `NONE` | `INDEXES`, `TOTAL`, or `NONE` |
| `--starting-token` | No | string | -- | Pagination token from previous response |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Maximum total items to return |

**Output Schema:**
```json
{
    "Items": [
        {
            "string": { "S": "string", "N": "string", "B": "blob", "M": {}, "L": [], "NULL": "boolean", "BOOL": "boolean" }
        }
    ],
    "Count": "integer",
    "ScannedCount": "integer",
    "LastEvaluatedKey": {
        "string": {}
    },
    "ConsumedCapacity": {
        "TableName": "string",
        "CapacityUnits": "double",
        "Table": {},
        "LocalSecondaryIndexes": {},
        "GlobalSecondaryIndexes": {}
    }
}
```

---

### 3.2 `scan`

Reads every item in a table or secondary index. Supports parallel scan. **Paginated operation.**

**Synopsis:**
```bash
aws dynamodb scan \
    --table-name <value> \
    [--index-name <value>] \
    [--select <value>] \
    [--projection-expression <value>] \
    [--filter-expression <value>] \
    [--expression-attribute-names <value>] \
    [--expression-attribute-values <value>] \
    [--consistent-read | --no-consistent-read] \
    [--total-segments <value>] \
    [--segment <value>] \
    [--return-consumed-capacity <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-name` | **Yes** | string | -- | Table name or ARN (1-1024 chars) |
| `--index-name` | No | string | -- | Name of GSI or LSI to scan |
| `--select` | No | string | `ALL_ATTRIBUTES` | `ALL_ATTRIBUTES`, `ALL_PROJECTED_ATTRIBUTES`, `SPECIFIC_ATTRIBUTES`, `COUNT` |
| `--projection-expression` | No | string | -- | Comma-separated attributes to return |
| `--filter-expression` | No | string | -- | Applied after scan, before returning |
| `--expression-attribute-names` | No | map | -- | `#name` substitution tokens |
| `--expression-attribute-values` | No | map | -- | `:value` substitution tokens |
| `--consistent-read` | No | boolean | false | Strongly consistent read |
| `--total-segments` | No | integer | -- | Total segments for parallel scan (1-1000000). Must pair with `--segment` |
| `--segment` | No | integer | -- | Segment ID for parallel scan (0-based). Must pair with `--total-segments` |
| `--return-consumed-capacity` | No | string | `NONE` | `INDEXES`, `TOTAL`, or `NONE` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:** Same as `query` output.

---
