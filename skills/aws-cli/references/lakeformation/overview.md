# AWS CLI v2 — Lake Formation

## Overview

Complete reference for all `aws lakeformation` subcommands in AWS CLI v2. Covers permissions management (grant/revoke), LF-Tags for tag-based access control, data cells filters for row/column-level security, resource registration, Lake Formation opt-in, governed transactions, temporary credentials, Identity Center integration, and query planning. AWS Lake Formation provides centralized governance and fine-grained access control for data lakes built on Amazon S3 and the AWS Glue Data Catalog.

## Quick Reference — Common Workflows

### Set data lake administrators
```bash
aws lakeformation put-data-lake-settings --catalog-id 123456789012 \
  --data-lake-settings '{
    "DataLakeAdmins": [{"DataLakePrincipalIdentifier": "arn:aws:iam::123456789012:role/LakeFormationAdmin"}],
    "CreateDatabaseDefaultPermissions": [],
    "CreateTableDefaultPermissions": []
  }'
```

### Register an S3 location
```bash
aws lakeformation register-resource \
  --resource-arn arn:aws:s3:::my-data-lake-bucket \
  --use-service-linked-role
```

### Grant database permissions
```bash
aws lakeformation grant-permissions \
  --principal '{"DataLakePrincipalIdentifier":"arn:aws:iam::123456789012:role/AnalystRole"}' \
  --resource '{"Database":{"Name":"analytics_db"}}' \
  --permissions SELECT DESCRIBE
```

### Grant table-level permissions with LF-Tags
```bash
aws lakeformation grant-permissions \
  --principal '{"DataLakePrincipalIdentifier":"arn:aws:iam::123456789012:role/AnalystRole"}' \
  --resource '{"LFTagPolicy":{"ResourceType":"TABLE","Expression":[{"TagKey":"department","TagValues":["analytics"]}]}}' \
  --permissions SELECT
```

### Create an LF-Tag
```bash
aws lakeformation create-lf-tag --tag-key department \
  --tag-values '["analytics","engineering","marketing"]'
```

### Assign LF-Tags to a resource
```bash
aws lakeformation add-lf-tags-to-resource \
  --resource '{"Table":{"DatabaseName":"analytics_db","Name":"users"}}' \
  --lf-tags '[{"TagKey":"department","TagValues":["analytics"]}]'
```

### Create a data cells filter (row/column security)
```bash
aws lakeformation create-data-cells-filter --table-data \
  '{"TableCatalogId":"123456789012","DatabaseName":"analytics_db","TableName":"users","Name":"pii-filter","RowFilter":{"FilterExpression":"country='\''US'\''"},"ColumnNames":["name","email"]}'
```

### List permissions
```bash
aws lakeformation list-permissions \
  --principal '{"DataLakePrincipalIdentifier":"arn:aws:iam::123456789012:role/AnalystRole"}'
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Permissions | [`permissions.md`](permissions.md) | grant-permissions, revoke-permissions, batch-grant-permissions, batch-revoke-permissions, list-permissions, get-effective-permissions-for-path, get-data-lake-settings, put-data-lake-settings, get-data-lake-principal |
| LF-Tags | [`lf-tags.md`](lf-tags.md) | create-lf-tag, get-lf-tag, update-lf-tag, delete-lf-tag, list-lf-tags, add-lf-tags-to-resource, remove-lf-tags-from-resource, get-resource-lf-tags, search-databases-by-lf-tags, search-tables-by-lf-tags, create-lf-tag-expression, get-lf-tag-expression, update-lf-tag-expression, delete-lf-tag-expression, list-lf-tag-expressions |
| Data Cells Filters | [`data-cells-filters.md`](data-cells-filters.md) | create-data-cells-filter, update-data-cells-filter, delete-data-cells-filter, get-data-cells-filter, list-data-cells-filter |
| Resources | [`resources.md`](resources.md) | register-resource, deregister-resource, describe-resource, update-resource, list-resources, list-table-storage-optimizers, update-table-storage-optimizer |
| Opt-In | [`opt-in.md`](opt-in.md) | create-lake-formation-opt-in, delete-lake-formation-opt-in, list-lake-formation-opt-ins |
| Transactions | [`transactions.md`](transactions.md) | start-transaction, commit-transaction, cancel-transaction, describe-transaction, extend-transaction, list-transactions, get-table-objects, update-table-objects, delete-objects-on-cancel |
| Credentials | [`credentials.md`](credentials.md) | get-temporary-glue-table-credentials, get-temporary-glue-partition-credentials, get-temporary-data-location-credentials, assume-decorated-role-with-saml |
| Identity Center | [`identity-center.md`](identity-center.md) | create-lake-formation-identity-center-configuration, describe-lake-formation-identity-center-configuration, update-lake-formation-identity-center-configuration, delete-lake-formation-identity-center-configuration |
| Query | [`query.md`](query.md) | start-query-planning, get-query-state, get-query-statistics, get-work-units, get-work-unit-results |
