# AWS CLI v2 — Athena (Amazon Athena)

## Overview

Complete reference for `aws athena` subcommands in AWS CLI v2. Covers interactive SQL query execution, named queries and prepared statements, workgroup management, data catalog federation, notebook sessions and calculations, capacity reservations, and engine versioning.

## Quick Reference — Common Workflows

### Run a query
```bash
aws athena start-query-execution \
  --query-string "SELECT * FROM my_database.my_table LIMIT 10" \
  --work-group primary \
  --result-configuration OutputLocation=s3://my-bucket/results/
```

### Check query status and get results
```bash
aws athena get-query-execution --query-execution-id <id> \
  --query 'QueryExecution.Status.State'

aws athena get-query-results --query-execution-id <id>
```

### Create a named query
```bash
aws athena create-named-query \
  --name "Top Users" \
  --database mydb \
  --query-string "SELECT user_id, COUNT(*) as cnt FROM events GROUP BY user_id ORDER BY cnt DESC LIMIT 100" \
  --work-group primary
```

### Create a workgroup
```bash
aws athena create-work-group \
  --name analytics-team \
  --configuration ResultConfiguration={OutputLocation=s3://bucket/results/},EnforceWorkGroupConfiguration=true,BytesScannedCutoffPerQuery=10737418240
```

### Create a prepared statement
```bash
aws athena create-prepared-statement \
  --statement-name get_user \
  --work-group primary \
  --query-statement "SELECT * FROM users WHERE user_id = ?"
```

### Execute a prepared statement
```bash
aws athena start-query-execution \
  --query-string "EXECUTE get_user USING '12345'" \
  --work-group primary
```

### Register a data catalog (federated query)
```bash
aws athena create-data-catalog \
  --name my-connector \
  --type LAMBDA \
  --parameters function=arn:aws:lambda:us-east-1:123456789012:function:my-connector
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Queries | [`queries.md`](queries.md) | start-query-execution, stop-query-execution, get-query-execution, get-query-results, batch-get-query-execution, list-query-executions, get-query-runtime-statistics |
| Named Queries | [`named-queries.md`](named-queries.md) | create-named-query, delete-named-query, get-named-query, batch-get-named-query, list-named-queries |
| Prepared Statements | [`prepared-statements.md`](prepared-statements.md) | create-prepared-statement, delete-prepared-statement, get-prepared-statement, update-prepared-statement, list-prepared-statements |
| Workgroups | [`workgroups.md`](workgroups.md) | create-work-group, delete-work-group, get-work-group, update-work-group, list-work-groups |
| Data Catalogs | [`data-catalogs.md`](data-catalogs.md) | create-data-catalog, delete-data-catalog, get-data-catalog, update-data-catalog, list-data-catalogs, get-database, list-databases, get-table-metadata, list-table-metadata |
| Notebooks | [`notebooks.md`](notebooks.md) | create-notebook, delete-notebook, get-notebook-metadata, update-notebook, update-notebook-metadata, list-notebook-metadata, import-notebook, export-notebook |
| Sessions & Calculations | [`sessions-calculations.md`](sessions-calculations.md) | start-session, terminate-session, get-session, get-session-status, list-sessions, start-calculation-execution, stop-calculation-execution, get-calculation-execution, get-calculation-execution-status, list-calculation-executions |
| Capacity | [`capacity.md`](capacity.md) | create-capacity-reservation, cancel-capacity-reservation, get-capacity-reservation, get-capacity-assignment-configuration, put-capacity-assignment-configuration, list-capacity-reservations |
| Engine & Tags | [`engine-tags.md`](engine-tags.md) | list-engine-versions, tag-resource, untag-resource, list-tags-for-resource |
