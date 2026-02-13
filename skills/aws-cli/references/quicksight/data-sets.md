# Data Sets

### 7.1 `create-data-set`

Creates a data set. Data sets define the data used by analyses and dashboards.

**Synopsis:**
```bash
aws quicksight create-data-set \
    --aws-account-id <value> \
    --data-set-id <value> \
    --name <value> \
    --physical-table-map <value> \
    --import-mode <value> \
    [--logical-table-map <value>] \
    [--column-groups <value>] \
    [--field-folders <value>] \
    [--permissions <value>] \
    [--row-level-permission-data-set <value>] \
    [--row-level-permission-tag-configuration <value>] \
    [--column-level-permission-rules <value>] \
    [--tags <value>] \
    [--data-set-usage-configuration <value>] \
    [--data-set-refresh-properties <value>] \
    [--folder-arns <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--data-set-id` | **Yes** | string | -- | Data set ID |
| `--name` | **Yes** | string | -- | Display name (1-128 chars) |
| `--physical-table-map` | **Yes** | map | -- | Physical tables from data source (relational, custom SQL, S3) |
| `--import-mode` | **Yes** | string | -- | `SPICE` or `DIRECT_QUERY` |
| `--logical-table-map` | No | map | None | Logical tables with joins and transformations |
| `--column-groups` | No | list | None | Column groupings |
| `--field-folders` | No | map | None | Field folder organization |
| `--permissions` | No | list | None | Resource permissions |
| `--row-level-permission-data-set` | No | structure | None | Row-level security data set |
| `--row-level-permission-tag-configuration` | No | structure | None | Tag-based RLS |
| `--column-level-permission-rules` | No | list | None | Column-level permission rules |
| `--tags` | No | list | None | Resource tags |
| `--data-set-usage-configuration` | No | structure | None | Usage configuration |
| `--folder-arns` | No | list(string) | None | Folders to add to |

**Physical Table Map (Relational):**
```json
{
    "my-table": {
        "RelationalTable": {
            "DataSourceArn": "string",
            "Catalog": "string",
            "Schema": "string",
            "Name": "string",
            "InputColumns": [
                {
                    "Name": "string",
                    "Type": "STRING|INTEGER|DECIMAL|DATETIME|BIT|BOOLEAN|JSON"
                }
            ]
        }
    }
}
```

**Physical Table Map (Custom SQL):**
```json
{
    "my-query": {
        "CustomSql": {
            "DataSourceArn": "string",
            "Name": "string",
            "SqlQuery": "string",
            "Columns": [
                {
                    "Name": "string",
                    "Type": "STRING|INTEGER|DECIMAL|DATETIME|BIT|BOOLEAN|JSON"
                }
            ]
        }
    }
}
```

**Physical Table Map (S3):**
```json
{
    "my-s3": {
        "S3Source": {
            "DataSourceArn": "string",
            "UploadSettings": {
                "Format": "CSV|TSV|CLF|ELF|XLSX|JSON",
                "StartFromRow": "integer",
                "ContainsHeader": "boolean",
                "TextQualifier": "DOUBLE_QUOTE|SINGLE_QUOTE",
                "Delimiter": "string"
            },
            "InputColumns": []
        }
    }
}
```

**Output Schema:**
```json
{
    "Arn": "string",
    "DataSetId": "string",
    "IngestionArn": "string",
    "IngestionId": "string",
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 7.2 `describe-data-set`

Describes a data set.

**Synopsis:**
```bash
aws quicksight describe-data-set \
    --aws-account-id <value> \
    --data-set-id <value>
```

**Output Schema:**
```json
{
    "DataSet": {
        "Arn": "string",
        "DataSetId": "string",
        "Name": "string",
        "CreatedTime": "timestamp",
        "LastUpdatedTime": "timestamp",
        "PhysicalTableMap": {},
        "LogicalTableMap": {},
        "OutputColumns": [
            {
                "Name": "string",
                "Description": "string",
                "Type": "string",
                "SubType": "string"
            }
        ],
        "ImportMode": "SPICE|DIRECT_QUERY",
        "ConsumedSpiceCapacityInBytes": "long",
        "ColumnGroups": [],
        "FieldFolders": {},
        "RowLevelPermissionDataSet": {},
        "RowLevelPermissionTagConfiguration": {},
        "ColumnLevelPermissionRules": [],
        "DataSetUsageConfiguration": {},
        "DatasetParameters": []
    },
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 7.3 `update-data-set`

Updates a data set. Same parameters as `create-data-set`.

---

### 7.4 `delete-data-set`

Deletes a data set.

**Synopsis:**
```bash
aws quicksight delete-data-set \
    --aws-account-id <value> \
    --data-set-id <value>
```

---

### 7.5 `list-data-sets`

Lists data sets. **Paginated operation.**

**Synopsis:**
```bash
aws quicksight list-data-sets \
    --aws-account-id <value> \
    [--starting-token <value>] [--page-size <value>] [--max-items <value>]
```

**Output Schema:**
```json
{
    "DataSetSummaries": [
        {
            "Arn": "string",
            "DataSetId": "string",
            "Name": "string",
            "CreatedTime": "timestamp",
            "LastUpdatedTime": "timestamp",
            "ImportMode": "SPICE|DIRECT_QUERY",
            "RowLevelPermissionDataSet": {},
            "RowLevelPermissionTagConfigurationApplied": "boolean",
            "ColumnLevelPermissionRulesApplied": "boolean"
        }
    ],
    "NextToken": "string",
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 7.6 `search-data-sets`

Searches data sets using filters. **Paginated operation.**

**Synopsis:**
```bash
aws quicksight search-data-sets \
    --aws-account-id <value> \
    --filters <value> \
    [--starting-token <value>] [--page-size <value>] [--max-items <value>]
```

---

### 7.7 `describe-data-set-permissions` / `update-data-set-permissions`

Manage data set permissions.

**Synopsis:**
```bash
aws quicksight describe-data-set-permissions \
    --aws-account-id <value> --data-set-id <value>

aws quicksight update-data-set-permissions \
    --aws-account-id <value> --data-set-id <value> \
    [--grant-permissions <value>] [--revoke-permissions <value>]
```

---

### 7.8 `describe-data-set-refresh-properties` / `put-data-set-refresh-properties` / `delete-data-set-refresh-properties`

Manage incremental refresh properties for SPICE data sets.

**Synopsis:**
```bash
aws quicksight describe-data-set-refresh-properties \
    --aws-account-id <value> --data-set-id <value>

aws quicksight put-data-set-refresh-properties \
    --aws-account-id <value> --data-set-id <value> \
    --data-set-refresh-properties <value>

aws quicksight delete-data-set-refresh-properties \
    --aws-account-id <value> --data-set-id <value>
```

**Refresh Properties Structure:**
```json
{
    "RefreshConfiguration": {
        "IncrementalRefresh": {
            "LookbackWindow": {
                "ColumnName": "string",
                "Size": "long",
                "SizeUnit": "HOUR|DAY|WEEK"
            }
        }
    }
}
```
