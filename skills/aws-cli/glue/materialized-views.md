# Materialized Views

Materialized views in AWS Glue use the Data Catalog table APIs with specific properties. There are no dedicated materialized view commands -- they are managed through the table API with materialized-view-specific parameters.

### Using Tables as Materialized Views

Materialized views are represented as tables in the Data Catalog with `TableType` set to indicate a materialized view. Use the following table commands to manage them:

**Create a materialized view:**
```bash
aws glue create-table \
    --database-name mydb \
    --table-input '{
        "Name": "my_materialized_view",
        "TableType": "VIRTUAL_VIEW",
        "ViewOriginalText": "SELECT ...",
        "ViewExpandedText": "SELECT ...",
        "StorageDescriptor": {
            "Columns": [
                {"Name": "col1", "Type": "string"},
                {"Name": "col2", "Type": "int"}
            ],
            "Location": "",
            "InputFormat": "",
            "OutputFormat": "",
            "SerdeInfo": {}
        },
        "Parameters": {
            "presto_view": "true"
        }
    }'
```

**Retrieve a materialized view:**
```bash
aws glue get-table \
    --database-name mydb \
    --name my_materialized_view
```

**Update a materialized view:**
```bash
aws glue update-table \
    --database-name mydb \
    --table-input '{
        "Name": "my_materialized_view",
        "TableType": "VIRTUAL_VIEW",
        "ViewOriginalText": "SELECT ... (updated)",
        "ViewExpandedText": "SELECT ... (updated)",
        "StorageDescriptor": { ... }
    }'
```

**Delete a materialized view:**
```bash
aws glue delete-table \
    --database-name mydb \
    --name my_materialized_view
```

**List materialized views in a database:**
```bash
aws glue get-tables \
    --database-name mydb \
    --query 'TableList[?TableType==`VIRTUAL_VIEW`].Name'
```

See [`tables.md`](tables.md) for complete table API documentation.
