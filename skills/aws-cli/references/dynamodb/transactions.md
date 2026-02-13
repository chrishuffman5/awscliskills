# Transactions

### 5.1 `transact-write-items`

Synchronous write operation that groups up to 100 actions (Put, Update, Delete, ConditionCheck). All actions succeed or all fail atomically.

**Synopsis:**
```bash
aws dynamodb transact-write-items \
    --transact-items <value> \
    [--return-consumed-capacity <value>] \
    [--return-item-collection-metrics <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--transact-items` | **Yes** | list | -- | 1-100 TransactWriteItem objects. Each contains one of: `ConditionCheck`, `Put`, `Update`, `Delete` |
| `--return-consumed-capacity` | No | string | `NONE` | `INDEXES`, `TOTAL`, or `NONE` |
| `--return-item-collection-metrics` | No | string | `NONE` | `SIZE` or `NONE` |
| `--client-request-token` | No | string | -- | Idempotency token (valid 10 minutes) |

**TransactWriteItem actions:**

Each action is a structure with `TableName`, `Key` (for Update/Delete/ConditionCheck) or `Item` (for Put), optional `ConditionExpression`, `ExpressionAttributeNames`, `ExpressionAttributeValues`, `ReturnValuesOnConditionCheckFailure`. Update also requires `UpdateExpression`.

**Output Schema:**
```json
{
    "ConsumedCapacity": [
        {
            "TableName": "string",
            "CapacityUnits": "double",
            "Table": {},
            "LocalSecondaryIndexes": {},
            "GlobalSecondaryIndexes": {}
        }
    ],
    "ItemCollectionMetrics": {
        "string": [
            {
                "ItemCollectionKey": {},
                "SizeEstimateRangeGB": ["double", "double"]
            }
        ]
    }
}
```

**Constraints:**
- Max 100 actions per transaction
- Max 4 MB aggregate size
- No two actions can target the same item
- All tables must be in the same AWS account and Region

---

### 5.2 `transact-get-items`

Synchronous read of up to 100 items from one or more tables as an atomic operation.

**Synopsis:**
```bash
aws dynamodb transact-get-items \
    --transact-items <value> \
    [--return-consumed-capacity <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--transact-items` | **Yes** | list | -- | 1-100 TransactGetItem objects. Each contains a `Get` with `TableName`, `Key`, optional `ProjectionExpression`, `ExpressionAttributeNames` |
| `--return-consumed-capacity` | No | string | `NONE` | `INDEXES`, `TOTAL`, or `NONE` |

**Output Schema:**
```json
{
    "ConsumedCapacity": [
        {
            "TableName": "string",
            "CapacityUnits": "double",
            "Table": {},
            "LocalSecondaryIndexes": {},
            "GlobalSecondaryIndexes": {}
        }
    ],
    "Responses": [
        {
            "Item": {
                "string": { "S": "string", "N": "string", "B": "blob", "M": {}, "L": [], "NULL": "boolean", "BOOL": "boolean" }
            }
        }
    ]
}
```

---
