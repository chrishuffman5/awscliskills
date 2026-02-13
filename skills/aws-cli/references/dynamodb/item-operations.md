# Item Operations

### 2.1 `put-item`

Creates a new item, or replaces an old item with a new item. If an item with the same primary key exists, the entire item is replaced.

**Synopsis:**
```bash
aws dynamodb put-item \
    --table-name <value> \
    --item <value> \
    [--condition-expression <value>] \
    [--expression-attribute-names <value>] \
    [--expression-attribute-values <value>] \
    [--return-values <value>] \
    [--return-consumed-capacity <value>] \
    [--return-item-collection-metrics <value>] \
    [--return-values-on-condition-check-failure <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-name` | **Yes** | string | -- | Table name or ARN (1-1024 chars) |
| `--item` | **Yes** | map | -- | Map of attribute name to AttributeValue. Must include all primary key attributes |
| `--condition-expression` | No | string | -- | Condition for the put to succeed. Supports `attribute_exists`, `attribute_not_exists`, `begins_with`, `contains`, `size` |
| `--expression-attribute-names` | No | map | -- | Substitution tokens for attribute names (`#name` syntax) |
| `--expression-attribute-values` | No | map | -- | Substitution tokens for attribute values (`:value` syntax) |
| `--return-values` | No | string | `NONE` | `NONE` or `ALL_OLD` (returns previous item if replaced) |
| `--return-consumed-capacity` | No | string | `NONE` | `INDEXES`, `TOTAL`, or `NONE` |
| `--return-item-collection-metrics` | No | string | `NONE` | `SIZE` or `NONE` |
| `--return-values-on-condition-check-failure` | No | string | `NONE` | `ALL_OLD` or `NONE` |

**Output Schema:**
```json
{
    "Attributes": {
        "string": {
            "S": "string", "N": "string", "B": "blob",
            "SS": ["string"], "NS": ["string"], "BS": ["blob"],
            "M": {}, "L": [], "NULL": "boolean", "BOOL": "boolean"
        }
    },
    "ConsumedCapacity": {
        "TableName": "string",
        "CapacityUnits": "double",
        "ReadCapacityUnits": "double",
        "WriteCapacityUnits": "double",
        "Table": { "CapacityUnits": "double" },
        "LocalSecondaryIndexes": { "string": { "CapacityUnits": "double" } },
        "GlobalSecondaryIndexes": { "string": { "CapacityUnits": "double" } }
    },
    "ItemCollectionMetrics": {
        "ItemCollectionKey": { "string": {} },
        "SizeEstimateRangeGB": ["double", "double"]
    }
}
```

---

### 2.2 `get-item`

Returns a set of attributes for the item with the given primary key.

**Synopsis:**
```bash
aws dynamodb get-item \
    --table-name <value> \
    --key <value> \
    [--consistent-read | --no-consistent-read] \
    [--projection-expression <value>] \
    [--expression-attribute-names <value>] \
    [--return-consumed-capacity <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-name` | **Yes** | string | -- | Table name or ARN (1-1024 chars) |
| `--key` | **Yes** | map | -- | Primary key attribute map. Must include all key attributes |
| `--consistent-read` | No | boolean | false | Use strongly consistent read |
| `--projection-expression` | No | string | -- | Comma-separated attributes to retrieve |
| `--expression-attribute-names` | No | map | -- | Substitution tokens for attribute names |
| `--return-consumed-capacity` | No | string | `NONE` | `INDEXES`, `TOTAL`, or `NONE` |

**Output Schema:**
```json
{
    "Item": {
        "string": {
            "S": "string", "N": "string", "B": "blob",
            "SS": ["string"], "NS": ["string"], "BS": ["blob"],
            "M": {}, "L": [], "NULL": "boolean", "BOOL": "boolean"
        }
    },
    "ConsumedCapacity": {
        "TableName": "string",
        "CapacityUnits": "double",
        "ReadCapacityUnits": "double",
        "WriteCapacityUnits": "double",
        "Table": {},
        "LocalSecondaryIndexes": {},
        "GlobalSecondaryIndexes": {}
    }
}
```

---

### 2.3 `update-item`

Edits an existing item's attributes or adds a new item if it does not exist.

**Synopsis:**
```bash
aws dynamodb update-item \
    --table-name <value> \
    --key <value> \
    [--update-expression <value>] \
    [--condition-expression <value>] \
    [--expression-attribute-names <value>] \
    [--expression-attribute-values <value>] \
    [--return-values <value>] \
    [--return-consumed-capacity <value>] \
    [--return-item-collection-metrics <value>] \
    [--return-values-on-condition-check-failure <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-name` | **Yes** | string | -- | Table name or ARN (1-1024 chars) |
| `--key` | **Yes** | map | -- | Primary key attribute map |
| `--update-expression` | No | string | -- | Actions: `SET`, `REMOVE`, `ADD`, `DELETE`. Example: `SET #a = :val, REMOVE #b` |
| `--condition-expression` | No | string | -- | Condition that must be satisfied for the update to occur |
| `--expression-attribute-names` | No | map | -- | `#name` substitution tokens |
| `--expression-attribute-values` | No | map | -- | `:value` substitution tokens |
| `--return-values` | No | string | `NONE` | `NONE`, `ALL_OLD`, `UPDATED_OLD`, `ALL_NEW`, `UPDATED_NEW` |
| `--return-consumed-capacity` | No | string | `NONE` | `INDEXES`, `TOTAL`, or `NONE` |
| `--return-item-collection-metrics` | No | string | `NONE` | `SIZE` or `NONE` |
| `--return-values-on-condition-check-failure` | No | string | `NONE` | `ALL_OLD` or `NONE` |

**Output Schema:**
```json
{
    "Attributes": {
        "string": { "S": "string", "N": "string", "B": "blob", "SS": [], "NS": [], "BS": [], "M": {}, "L": [], "NULL": "boolean", "BOOL": "boolean" }
    },
    "ConsumedCapacity": {
        "TableName": "string",
        "CapacityUnits": "double",
        "ReadCapacityUnits": "double",
        "WriteCapacityUnits": "double",
        "Table": {},
        "LocalSecondaryIndexes": {},
        "GlobalSecondaryIndexes": {}
    },
    "ItemCollectionMetrics": {
        "ItemCollectionKey": {},
        "SizeEstimateRangeGB": ["double", "double"]
    }
}
```

---

### 2.4 `delete-item`

Deletes a single item from a table by primary key.

**Synopsis:**
```bash
aws dynamodb delete-item \
    --table-name <value> \
    --key <value> \
    [--condition-expression <value>] \
    [--expression-attribute-names <value>] \
    [--expression-attribute-values <value>] \
    [--return-values <value>] \
    [--return-consumed-capacity <value>] \
    [--return-item-collection-metrics <value>] \
    [--return-values-on-condition-check-failure <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-name` | **Yes** | string | -- | Table name or ARN (1-1024 chars) |
| `--key` | **Yes** | map | -- | Primary key attribute map |
| `--condition-expression` | No | string | -- | Condition for the delete to succeed |
| `--expression-attribute-names` | No | map | -- | `#name` substitution tokens |
| `--expression-attribute-values` | No | map | -- | `:value` substitution tokens |
| `--return-values` | No | string | `NONE` | `NONE` or `ALL_OLD` (returns deleted item) |
| `--return-consumed-capacity` | No | string | `NONE` | `INDEXES`, `TOTAL`, or `NONE` |
| `--return-item-collection-metrics` | No | string | `NONE` | `SIZE` or `NONE` |
| `--return-values-on-condition-check-failure` | No | string | `NONE` | `ALL_OLD` or `NONE` |

**Output Schema:** Same structure as `put-item` output (`Attributes`, `ConsumedCapacity`, `ItemCollectionMetrics`).

---
