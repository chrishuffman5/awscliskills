# Table Management

### 1.1 `create-table`

Creates a new DynamoDB table. The table is not ready until its status becomes `ACTIVE`.

**Synopsis:**
```bash
aws dynamodb create-table \
    --table-name <value> \
    [--attribute-definitions <value>] \
    [--key-schema <value>] \
    [--local-secondary-indexes <value>] \
    [--global-secondary-indexes <value>] \
    [--billing-mode <value>] \
    [--provisioned-throughput <value>] \
    [--stream-specification <value>] \
    [--sse-specification <value>] \
    [--tags <value>] \
    [--table-class <value>] \
    [--deletion-protection-enabled | --no-deletion-protection-enabled] \
    [--warm-throughput <value>] \
    [--resource-policy <value>] \
    [--on-demand-throughput <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-name` | **Yes** | string | -- | Table name or ARN (1-1024 chars) |
| `--attribute-definitions` | No | list | -- | Attributes for key schema. Shorthand: `AttributeName=string,AttributeType=S\|N\|B ...` |
| `--key-schema` | No | list | -- | Primary key schema. Shorthand: `AttributeName=string,KeyType=HASH\|RANGE ...` |
| `--local-secondary-indexes` | No | list | -- | Up to 5 LSIs. Each has `IndexName`, `KeySchema`, `Projection` |
| `--global-secondary-indexes` | No | list | -- | Up to 20 GSIs. Each has `IndexName`, `KeySchema`, `Projection`, optional throughput |
| `--billing-mode` | No | string | `PROVISIONED` | `PROVISIONED` or `PAY_PER_REQUEST` |
| `--provisioned-throughput` | No | structure | -- | Required if PROVISIONED. Shorthand: `ReadCapacityUnits=long,WriteCapacityUnits=long` |
| `--stream-specification` | No | structure | -- | Shorthand: `StreamEnabled=boolean,StreamViewType=NEW_IMAGE\|OLD_IMAGE\|NEW_AND_OLD_IMAGES\|KEYS_ONLY` |
| `--sse-specification` | No | structure | -- | `Enabled=boolean,SSEType=AES256\|KMS,KMSMasterKeyId=string` |
| `--tags` | No | list | -- | Up to 50 tags. Shorthand: `Key=string,Value=string ...` |
| `--table-class` | No | string | `STANDARD` | `STANDARD` or `STANDARD_INFREQUENT_ACCESS` |
| `--deletion-protection-enabled` | No | boolean | false | Enable deletion protection |
| `--warm-throughput` | No | structure | -- | `ReadUnitsPerSecond=long,WriteUnitsPerSecond=long` |
| `--resource-policy` | No | string | -- | JSON resource-based policy (max 20 KB) |
| `--on-demand-throughput` | No | structure | -- | `MaxReadRequestUnits=long,MaxWriteRequestUnits=long` |

**Output Schema:**
```json
{
    "TableDescription": {
        "AttributeDefinitions": [
            { "AttributeName": "string", "AttributeType": "S|N|B" }
        ],
        "TableName": "string",
        "KeySchema": [
            { "AttributeName": "string", "KeyType": "HASH|RANGE" }
        ],
        "TableStatus": "CREATING|UPDATING|DELETING|ACTIVE|INACCESSIBLE_ENCRYPTION_CREDENTIALS|ARCHIVING|ARCHIVED",
        "CreationDateTime": "timestamp",
        "ProvisionedThroughput": {
            "ReadCapacityUnits": "long",
            "WriteCapacityUnits": "long",
            "LastIncreaseDateTime": "timestamp",
            "LastDecreaseDateTime": "timestamp",
            "NumberOfDecreasesToday": "long"
        },
        "TableSizeBytes": "long",
        "ItemCount": "long",
        "TableArn": "string",
        "TableId": "string",
        "BillingModeSummary": {
            "BillingMode": "PROVISIONED|PAY_PER_REQUEST",
            "LastUpdateToPayPerRequestDateTime": "timestamp"
        },
        "LocalSecondaryIndexes": [
            {
                "IndexName": "string",
                "KeySchema": [],
                "Projection": { "ProjectionType": "ALL|KEYS_ONLY|INCLUDE", "NonKeyAttributes": ["string"] },
                "IndexSizeBytes": "long",
                "ItemCount": "long",
                "IndexArn": "string"
            }
        ],
        "GlobalSecondaryIndexes": [
            {
                "IndexName": "string",
                "KeySchema": [],
                "Projection": {},
                "IndexStatus": "CREATING|UPDATING|DELETING|ACTIVE",
                "Backfilling": "boolean",
                "ProvisionedThroughput": {},
                "IndexSizeBytes": "long",
                "ItemCount": "long",
                "IndexArn": "string"
            }
        ],
        "StreamSpecification": {
            "StreamEnabled": "boolean",
            "StreamViewType": "NEW_IMAGE|OLD_IMAGE|NEW_AND_OLD_IMAGES|KEYS_ONLY"
        },
        "LatestStreamLabel": "string",
        "LatestStreamArn": "string",
        "SSEDescription": {
            "Status": "ENABLED|DISABLED",
            "SSEType": "AES256|KMS",
            "KMSMasterKeyArn": "string"
        },
        "TableClassSummary": {
            "TableClass": "STANDARD|STANDARD_INFREQUENT_ACCESS"
        },
        "DeletionProtectionEnabled": "boolean"
    }
}
```

---

### 1.2 `delete-table`

Deletes a table and all of its items. Table must not have deletion protection enabled.

**Synopsis:**
```bash
aws dynamodb delete-table \
    --table-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-name` | **Yes** | string | -- | Table name or ARN (1-1024 chars) |

**Output Schema:**
```json
{
    "TableDescription": {
        "TableName": "string",
        "TableStatus": "DELETING",
        "TableArn": "string",
        "TableId": "string",
        "ProvisionedThroughput": {},
        "TableSizeBytes": "long",
        "ItemCount": "long"
    }
}
```

---

### 1.3 `describe-table`

Returns information about a table including status, schema, throughput, indexes, streams, and encryption.

**Synopsis:**
```bash
aws dynamodb describe-table \
    --table-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-name` | **Yes** | string | -- | Table name or ARN (1-1024 chars) |

**Output Schema:** Same as `create-table` `TableDescription` object with all fields populated.

---

### 1.4 `list-tables`

Lists all table names in the account/region. **Paginated operation.**

**Synopsis:**
```bash
aws dynamodb list-tables \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | -- | Pagination token from previous response |
| `--page-size` | No | integer | -- | Items per API call (1-100) |
| `--max-items` | No | integer | -- | Maximum total items to return |

**Output Schema:**
```json
{
    "TableNames": ["string"],
    "NextToken": "string"
}
```

---

### 1.5 `update-table`

Modifies table settings including provisioned throughput, billing mode, GSI changes, stream specification, encryption, table class, and deletion protection.

**Synopsis:**
```bash
aws dynamodb update-table \
    --table-name <value> \
    [--attribute-definitions <value>] \
    [--billing-mode <value>] \
    [--provisioned-throughput <value>] \
    [--global-secondary-index-updates <value>] \
    [--stream-specification <value>] \
    [--sse-specification <value>] \
    [--replica-updates <value>] \
    [--table-class <value>] \
    [--deletion-protection-enabled | --no-deletion-protection-enabled] \
    [--multi-region-consistency <value>] \
    [--on-demand-throughput <value>] \
    [--warm-throughput <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-name` | **Yes** | string | -- | Table name or ARN (1-1024 chars) |
| `--attribute-definitions` | No | list | -- | Required when adding a GSI. Shorthand: `AttributeName=string,AttributeType=S\|N\|B ...` |
| `--billing-mode` | No | string | -- | `PROVISIONED` or `PAY_PER_REQUEST` |
| `--provisioned-throughput` | No | structure | -- | `ReadCapacityUnits=long,WriteCapacityUnits=long` |
| `--global-secondary-index-updates` | No | list | -- | Create, Update, or Delete GSI operations |
| `--stream-specification` | No | structure | -- | `StreamEnabled=boolean,StreamViewType=...` |
| `--sse-specification` | No | structure | -- | Server-side encryption settings |
| `--replica-updates` | No | list | -- | Create, Update, or Delete replica operations |
| `--table-class` | No | string | -- | `STANDARD` or `STANDARD_INFREQUENT_ACCESS` |
| `--deletion-protection-enabled` | No | boolean | -- | Enable/disable deletion protection |
| `--multi-region-consistency` | No | string | -- | `EVENTUAL` or `STRONG` |
| `--on-demand-throughput` | No | structure | -- | `MaxReadRequestUnits=long,MaxWriteRequestUnits=long` |
| `--warm-throughput` | No | structure | -- | `ReadUnitsPerSecond=long,WriteUnitsPerSecond=long` |

**Output Schema:** Same as `create-table` `TableDescription` object.

---

### 1.6 `describe-table-replica-auto-scaling`

Describes auto-scaling settings across replicas of a global table.

**Synopsis:**
```bash
aws dynamodb describe-table-replica-auto-scaling \
    --table-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-name` | **Yes** | string | -- | Table name (1-255 chars) |

**Output Schema:**
```json
{
    "TableAutoScalingDescription": {
        "TableName": "string",
        "TableStatus": "CREATING|UPDATING|DELETING|ACTIVE",
        "Replicas": [
            {
                "RegionName": "string",
                "GlobalSecondaryIndexes": [
                    {
                        "IndexName": "string",
                        "IndexStatus": "CREATING|UPDATING|DELETING|ACTIVE",
                        "ProvisionedReadCapacityAutoScalingSettings": {},
                        "ProvisionedWriteCapacityAutoScalingSettings": {}
                    }
                ],
                "ReplicaProvisionedReadCapacityAutoScalingSettings": {
                    "MinimumUnits": "long",
                    "MaximumUnits": "long",
                    "AutoScalingDisabled": "boolean",
                    "AutoScalingRoleArn": "string",
                    "ScalingPolicies": []
                },
                "ReplicaProvisionedWriteCapacityAutoScalingSettings": {},
                "ReplicaStatus": "CREATING|CREATION_FAILED|UPDATING|DELETING|ACTIVE"
            }
        ]
    }
}
```

---

### 1.7 `update-table-replica-auto-scaling`

Updates auto-scaling settings on global table replicas.

**Synopsis:**
```bash
aws dynamodb update-table-replica-auto-scaling \
    --table-name <value> \
    [--global-secondary-index-updates <value>] \
    [--provisioned-write-capacity-auto-scaling-update <value>] \
    [--replica-updates <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-name` | **Yes** | string | -- | Table name (1-255 chars) |
| `--global-secondary-index-updates` | No | list | -- | GSI auto-scaling updates |
| `--provisioned-write-capacity-auto-scaling-update` | No | structure | -- | Write capacity auto-scaling settings |
| `--replica-updates` | No | list | -- | Per-replica auto-scaling updates |

**Output Schema:** Same as `describe-table-replica-auto-scaling`.

---
