# Configured Tables

## 3.1 `create-configured-table`

Creates a configured table referencing an AWS Glue table.

**Synopsis:**
```bash
aws cleanrooms create-configured-table \
    --name <value> \
    --table-reference <value> \
    --allowed-columns <value> \
    --analysis-method <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Configured table name |
| `--table-reference` | **Yes** | structure | -- | Glue table reference. Shorthand: `Glue={TableName=string,DatabaseName=string}` |
| `--allowed-columns` | **Yes** | list(string) | -- | Columns visible in the collaboration |
| `--analysis-method` | **Yes** | string | -- | Analysis method: `DIRECT_QUERY` |
| `--description` | No | string | None | Description |
| `--tags` | No | map | None | Key-value tags |

**Output Schema:**
```json
{
    "configuredTable": {
        "id": "string",
        "arn": "string",
        "name": "string",
        "description": "string",
        "tableReference": {
            "glue": {
                "tableName": "string",
                "databaseName": "string"
            }
        },
        "createTime": "timestamp",
        "updateTime": "timestamp",
        "analysisRuleTypes": ["AGGREGATION|LIST|CUSTOM"],
        "analysisMethod": "DIRECT_QUERY",
        "allowedColumns": ["string"]
    }
}
```

---

## 3.2 `delete-configured-table`

Deletes a configured table.

**Synopsis:**
```bash
aws cleanrooms delete-configured-table \
    --configured-table-identifier <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configured-table-identifier` | **Yes** | string | -- | Configured table ID or ARN |

**Output Schema:**

None (HTTP 204 on success).

---

## 3.3 `get-configured-table`

Returns details for a configured table.

**Synopsis:**
```bash
aws cleanrooms get-configured-table \
    --configured-table-identifier <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configured-table-identifier` | **Yes** | string | -- | Configured table ID or ARN |

**Output Schema:**
```json
{
    "configuredTable": {
        "id": "string",
        "arn": "string",
        "name": "string",
        "description": "string",
        "tableReference": {},
        "createTime": "timestamp",
        "updateTime": "timestamp",
        "analysisRuleTypes": ["string"],
        "analysisMethod": "string",
        "allowedColumns": ["string"]
    }
}
```

---

## 3.4 `list-configured-tables`

Lists configured tables. **Paginated operation.**

**Synopsis:**
```bash
aws cleanrooms list-configured-tables \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "configuredTableSummaries": [
        {
            "id": "string",
            "arn": "string",
            "name": "string",
            "createTime": "timestamp",
            "updateTime": "timestamp",
            "analysisRuleTypes": ["string"],
            "analysisMethod": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 3.5 `update-configured-table`

Updates a configured table name or description.

**Synopsis:**
```bash
aws cleanrooms update-configured-table \
    --configured-table-identifier <value> \
    [--name <value>] \
    [--description <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configured-table-identifier` | **Yes** | string | -- | Configured table ID or ARN |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |

**Output Schema:**
```json
{
    "configuredTable": {
        "id": "string",
        "arn": "string",
        "name": "string",
        "description": "string",
        "updateTime": "timestamp"
    }
}
```

---

## 3.6 `create-configured-table-analysis-rule`

Creates an analysis rule for a configured table (AGGREGATION, LIST, or CUSTOM).

**Synopsis:**
```bash
aws cleanrooms create-configured-table-analysis-rule \
    --configured-table-identifier <value> \
    --analysis-rule-type <value> \
    --analysis-rule-policy <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configured-table-identifier` | **Yes** | string | -- | Configured table ID or ARN |
| `--analysis-rule-type` | **Yes** | string | -- | Rule type: `AGGREGATION`, `LIST`, or `CUSTOM` |
| `--analysis-rule-policy` | **Yes** | structure | -- | Policy configuration |

**Aggregation Policy Example:**
```json
{
    "v1": {
        "aggregation": {
            "aggregateColumns": [
                {
                    "columnNames": ["purchase_amount"],
                    "function": "SUM|AVG|COUNT|COUNT_DISTINCT|MAX|MIN"
                }
            ],
            "joinColumns": ["customer_id"],
            "joinRequired": "QUERY_RUNNER",
            "dimensionColumns": ["category"],
            "scalarFunctions": ["COALESCE", "CAST"],
            "outputConstraints": [
                {
                    "columnName": "customer_id",
                    "minimum": 100,
                    "type": "COUNT_DISTINCT"
                }
            ]
        }
    }
}
```

**Output Schema:**
```json
{
    "analysisRule": {
        "configuredTableId": "string",
        "configuredTableArn": "string",
        "policy": {},
        "type": "AGGREGATION|LIST|CUSTOM",
        "createTime": "timestamp",
        "updateTime": "timestamp"
    }
}
```

---

## 3.7 `delete-configured-table-analysis-rule`

Deletes an analysis rule from a configured table.

**Synopsis:**
```bash
aws cleanrooms delete-configured-table-analysis-rule \
    --configured-table-identifier <value> \
    --analysis-rule-type <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configured-table-identifier` | **Yes** | string | -- | Configured table ID or ARN |
| `--analysis-rule-type` | **Yes** | string | -- | Rule type: `AGGREGATION`, `LIST`, or `CUSTOM` |

**Output Schema:**

None (HTTP 204 on success).

---

## 3.8 `get-configured-table-analysis-rule`

Gets an analysis rule for a configured table.

**Synopsis:**
```bash
aws cleanrooms get-configured-table-analysis-rule \
    --configured-table-identifier <value> \
    --analysis-rule-type <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configured-table-identifier` | **Yes** | string | -- | Configured table ID or ARN |
| `--analysis-rule-type` | **Yes** | string | -- | Rule type: `AGGREGATION`, `LIST`, or `CUSTOM` |

**Output Schema:**
```json
{
    "analysisRule": {
        "configuredTableId": "string",
        "configuredTableArn": "string",
        "policy": {},
        "type": "string",
        "createTime": "timestamp",
        "updateTime": "timestamp"
    }
}
```

---

## 3.9 `update-configured-table-analysis-rule`

Updates an analysis rule for a configured table.

**Synopsis:**
```bash
aws cleanrooms update-configured-table-analysis-rule \
    --configured-table-identifier <value> \
    --analysis-rule-type <value> \
    --analysis-rule-policy <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configured-table-identifier` | **Yes** | string | -- | Configured table ID or ARN |
| `--analysis-rule-type` | **Yes** | string | -- | Rule type |
| `--analysis-rule-policy` | **Yes** | structure | -- | Updated policy |

**Output Schema:**
```json
{
    "analysisRule": {
        "configuredTableId": "string",
        "configuredTableArn": "string",
        "policy": {},
        "type": "string",
        "updateTime": "timestamp"
    }
}
```

---

## 3.10 `create-configured-table-association`

Associates a configured table with a membership.

**Synopsis:**
```bash
aws cleanrooms create-configured-table-association \
    --membership-identifier <value> \
    --configured-table-identifier <value> \
    --name <value> \
    --role-arn <value> \
    [--description <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID or ARN |
| `--configured-table-identifier` | **Yes** | string | -- | Configured table ID or ARN |
| `--name` | **Yes** | string | -- | Association name |
| `--role-arn` | **Yes** | string | -- | IAM role ARN for data access |
| `--description` | No | string | None | Description |
| `--tags` | No | map | None | Key-value tags |

**Output Schema:**
```json
{
    "configuredTableAssociation": {
        "arn": "string",
        "id": "string",
        "configuredTableId": "string",
        "configuredTableArn": "string",
        "membershipId": "string",
        "membershipArn": "string",
        "roleArn": "string",
        "name": "string",
        "description": "string",
        "createTime": "timestamp",
        "updateTime": "timestamp"
    }
}
```

---

## 3.11 `delete-configured-table-association`

Deletes a configured table association.

**Synopsis:**
```bash
aws cleanrooms delete-configured-table-association \
    --membership-identifier <value> \
    --configured-table-association-identifier <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--configured-table-association-identifier` | **Yes** | string | -- | Association ID |

**Output Schema:**

None (HTTP 204 on success).

---

## 3.12 `get-configured-table-association`

Gets a configured table association.

**Synopsis:**
```bash
aws cleanrooms get-configured-table-association \
    --membership-identifier <value> \
    --configured-table-association-identifier <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--configured-table-association-identifier` | **Yes** | string | -- | Association ID |

**Output Schema:**
```json
{
    "configuredTableAssociation": {
        "arn": "string",
        "id": "string",
        "configuredTableId": "string",
        "configuredTableArn": "string",
        "membershipId": "string",
        "membershipArn": "string",
        "roleArn": "string",
        "name": "string",
        "description": "string",
        "createTime": "timestamp",
        "updateTime": "timestamp"
    }
}
```

---

## 3.13 `list-configured-table-associations`

Lists configured table associations for a membership. **Paginated operation.**

**Synopsis:**
```bash
aws cleanrooms list-configured-table-associations \
    --membership-identifier <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "configuredTableAssociationSummaries": [
        {
            "configuredTableId": "string",
            "membershipId": "string",
            "membershipArn": "string",
            "name": "string",
            "createTime": "timestamp",
            "updateTime": "timestamp",
            "id": "string",
            "arn": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 3.14-3.17 Configured Table Association Analysis Rules

`create-configured-table-association-analysis-rule`, `delete-configured-table-association-analysis-rule`, `get-configured-table-association-analysis-rule`, and `update-configured-table-association-analysis-rule` follow the same pattern as configured table analysis rules (sections 3.6-3.9) but operate on table associations within a membership.

**Synopsis (create):**
```bash
aws cleanrooms create-configured-table-association-analysis-rule \
    --membership-identifier <value> \
    --configured-table-association-identifier <value> \
    --analysis-rule-type <value> \
    --analysis-rule-policy <value>
```

**Required Parameters:** `--membership-identifier`, `--configured-table-association-identifier`, `--analysis-rule-type`, `--analysis-rule-policy`

**Output:** Returns the analysis rule object with type, policy, and timestamps.
