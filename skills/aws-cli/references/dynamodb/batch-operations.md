# Batch Operations

### 4.1 `batch-write-item`

Puts or deletes multiple items across one or more tables. Max 25 requests per call, 16 MB total.

**Synopsis:**
```bash
aws dynamodb batch-write-item \
    --request-items <value> \
    [--return-consumed-capacity <value>] \
    [--return-item-collection-metrics <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--request-items` | **Yes** | map | -- | Map of table name to list of `PutRequest` and/or `DeleteRequest` objects. Max 25 requests, 400 KB per item, 16 MB total |
| `--return-consumed-capacity` | No | string | `NONE` | `INDEXES`, `TOTAL`, or `NONE` |
| `--return-item-collection-metrics` | No | string | `NONE` | `SIZE` or `NONE` |

**Output Schema:**
```json
{
    "UnprocessedItems": {
        "string": [
            {
                "PutRequest": { "Item": {} },
                "DeleteRequest": { "Key": {} }
            }
        ]
    },
    "ItemCollectionMetrics": {
        "string": [
            {
                "ItemCollectionKey": {},
                "SizeEstimateRangeGB": ["double", "double"]
            }
        ]
    },
    "ConsumedCapacity": [
        {
            "TableName": "string",
            "CapacityUnits": "double",
            "Table": {},
            "LocalSecondaryIndexes": {},
            "GlobalSecondaryIndexes": {}
        }
    ]
}
```

---

### 4.2 `batch-get-item`

Returns attributes of one or more items from one or more tables. Max 100 items per call, 16 MB total.

**Synopsis:**
```bash
aws dynamodb batch-get-item \
    --request-items <value> \
    [--return-consumed-capacity <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--request-items` | **Yes** | map | -- | Map of table name to `Keys` (list of key maps), optional `ConsistentRead`, `ProjectionExpression`, `ExpressionAttributeNames`. Max 100 items, 16 MB total |
| `--return-consumed-capacity` | No | string | `NONE` | `INDEXES`, `TOTAL`, or `NONE` |

**Output Schema:**
```json
{
    "Responses": {
        "string": [
            { "string": {} }
        ]
    },
    "UnprocessedKeys": {
        "string": {
            "Keys": [],
            "ConsistentRead": "boolean",
            "ProjectionExpression": "string",
            "ExpressionAttributeNames": {}
        }
    },
    "ConsumedCapacity": [
        {
            "TableName": "string",
            "CapacityUnits": "double",
            "Table": {},
            "LocalSecondaryIndexes": {},
            "GlobalSecondaryIndexes": {}
        }
    ]
}
```

---
