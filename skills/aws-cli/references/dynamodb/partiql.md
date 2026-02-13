# PartiQL (SQL-Compatible Access)

### 6.1 `execute-statement`

Executes a single PartiQL statement against a DynamoDB table.

**Synopsis:**
```bash
aws dynamodb execute-statement \
    --statement <value> \
    [--parameters <value>] \
    [--consistent-read | --no-consistent-read] \
    [--next-token <value>] \
    [--return-consumed-capacity <value>] \
    [--limit <value>] \
    [--return-values-on-condition-check-failure <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--statement` | **Yes** | string | -- | PartiQL statement (1-8192 chars). Supports SELECT, INSERT, UPDATE, DELETE |
| `--parameters` | No | list | -- | List of AttributeValue objects for parameterized statements |
| `--consistent-read` | No | boolean | false | Strongly consistent read |
| `--next-token` | No | string | -- | Pagination token (1-32768 chars) |
| `--return-consumed-capacity` | No | string | `NONE` | `INDEXES`, `TOTAL`, or `NONE` |
| `--limit` | No | integer | -- | Maximum items to evaluate (min: 1) |
| `--return-values-on-condition-check-failure` | No | string | `NONE` | `ALL_OLD` or `NONE` |

**Output Schema:**
```json
{
    "Items": [
        { "string": {} }
    ],
    "NextToken": "string",
    "ConsumedCapacity": {
        "TableName": "string",
        "CapacityUnits": "double",
        "Table": {},
        "LocalSecondaryIndexes": {},
        "GlobalSecondaryIndexes": {}
    },
    "LastEvaluatedKey": { "string": {} }
}
```

---

### 6.2 `batch-execute-statement`

Executes multiple PartiQL statements in a batch. Max 25 statements.

**Synopsis:**
```bash
aws dynamodb batch-execute-statement \
    --statements <value> \
    [--return-consumed-capacity <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--statements` | **Yes** | list | -- | 1-25 PartiQL statements. Each has `Statement` (string), optional `Parameters`, `ConsistentRead`, `ReturnValuesOnConditionCheckFailure` |
| `--return-consumed-capacity` | No | string | `NONE` | `INDEXES`, `TOTAL`, or `NONE` |

**Output Schema:**
```json
{
    "Responses": [
        {
            "Error": {
                "Code": "ConditionalCheckFailed|ItemCollectionSizeLimitExceeded|RequestLimitExceeded|ValidationError|ProvisionedThroughputExceeded|TransactionConflict|ThrottlingError|InternalServerError|ResourceNotFound|AccessDenied|DuplicateItem",
                "Message": "string",
                "Item": {}
            },
            "TableName": "string",
            "Item": { "string": {} }
        }
    ],
    "ConsumedCapacity": [
        { "TableName": "string", "CapacityUnits": "double" }
    ]
}
```

---

### 6.3 `execute-transaction`

Executes multiple PartiQL statements atomically as a transaction. Max 100 statements.

**Synopsis:**
```bash
aws dynamodb execute-transaction \
    --transact-statements <value> \
    [--client-request-token <value>] \
    [--return-consumed-capacity <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--transact-statements` | **Yes** | list | -- | 1-100 ParameterizedStatement objects. Each has `Statement`, optional `Parameters`, `ReturnValuesOnConditionCheckFailure` |
| `--client-request-token` | No | string | -- | Idempotency token |
| `--return-consumed-capacity` | No | string | `NONE` | `INDEXES`, `TOTAL`, or `NONE` |

**Output Schema:**
```json
{
    "Responses": [
        {
            "Item": { "string": {} }
        }
    ],
    "ConsumedCapacity": [
        { "TableName": "string", "CapacityUnits": "double" }
    ]
}
```

---
