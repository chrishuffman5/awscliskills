# Invalidations

### 2.1 `create-invalidation`

Creates an invalidation to remove cached objects from edge locations.

**Synopsis:**
```bash
aws cloudfront create-invalidation \
    --distribution-id <value> \
    [--invalidation-batch <value>] \
    [--paths <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--distribution-id` | **Yes** | string | Distribution ID |
| `--invalidation-batch` | No* | structure | Invalidation batch config (*mutually exclusive with `--paths`) |
| `--paths` | No* | string(s) | Space-separated paths to invalidate (*mutually exclusive with `--invalidation-batch`) |

**Invalidation Batch structure:**
```json
{
    "Paths": {
        "Quantity": "integer",
        "Items": ["/path1", "/path2"]
    },
    "CallerReference": "string"
}
```

**Output Schema:**
```json
{
    "Location": "string",
    "Invalidation": {
        "Id": "string",
        "Status": "InProgress|Completed",
        "CreateTime": "timestamp",
        "InvalidationBatch": {
            "Paths": {
                "Quantity": "integer",
                "Items": ["string"]
            },
            "CallerReference": "string"
        }
    }
}
```

---

### 2.2 `get-invalidation`

Gets information about a specific invalidation.

**Synopsis:**
```bash
aws cloudfront get-invalidation \
    --distribution-id <value> \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--distribution-id` | **Yes** | string | Distribution ID |
| `--id` | **Yes** | string | Invalidation ID |

**Output Schema:**
```json
{
    "Invalidation": {
        "Id": "string",
        "Status": "InProgress|Completed",
        "CreateTime": "timestamp",
        "InvalidationBatch": {
            "Paths": {
                "Quantity": "integer",
                "Items": ["string"]
            },
            "CallerReference": "string"
        }
    }
}
```

---

### 2.3 `list-invalidations`

Lists invalidation batches for a distribution. **Paginated operation.**

**Synopsis:**
```bash
aws cloudfront list-invalidations \
    --distribution-id <value> \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--distribution-id` | **Yes** | string | -- | Distribution ID |
| `--max-items` | No | integer | None | Total items to return |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |

**Output Schema:**
```json
{
    "InvalidationList": {
        "Marker": "string",
        "MaxItems": "integer",
        "IsTruncated": "boolean",
        "NextMarker": "string",
        "Quantity": "integer",
        "Items": [
            {
                "Id": "string",
                "CreateTime": "timestamp",
                "Status": "string"
            }
        ]
    }
}
```

---
