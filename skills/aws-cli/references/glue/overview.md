# AWS CLI v2 — Glue (AWS Glue)

## Overview

Complete reference for `aws glue` subcommands in AWS CLI v2. Covers ETL jobs, crawlers, Data Catalog (databases, tables, partitions), connections, classifiers, triggers, workflows, blueprints, development endpoints, ML transforms, data quality rules, schema registry, interactive sessions, zero-ETL integrations, column statistics, materialized views, security configurations, custom entity types, and resource-level tagging.

## Quick Reference — Common Workflows

### Create and start a crawler
```bash
aws glue create-crawler --name my-crawler \
  --role arn:aws:iam::123456789012:role/GlueCrawlerRole \
  --database-name mydb \
  --targets S3Targets=[{Path=s3://my-bucket/data/}]

aws glue start-crawler --name my-crawler
```

### Create and run an ETL job
```bash
aws glue create-job --name my-etl-job \
  --role arn:aws:iam::123456789012:role/GlueJobRole \
  --command Name=glueetl,ScriptLocation=s3://bucket/scripts/etl.py,PythonVersion=3 \
  --default-arguments '{"--TempDir":"s3://bucket/temp/","--job-language":"python"}'

aws glue start-job-run --job-name my-etl-job
```

### Check job run status
```bash
aws glue get-job-run --job-name my-etl-job --run-id jr_xxxxx \
  --query 'JobRun.{State:JobRunState,Error:ErrorMessage}'
```

### List databases and tables
```bash
aws glue get-databases --query 'DatabaseList[].Name'
aws glue get-tables --database-name mydb --query 'TableList[].Name'
```

### Create a schema in Schema Registry
```bash
aws glue create-schema --schema-name my-schema \
  --registry-id RegistryName=my-registry \
  --data-format AVRO --compatibility BACKWARD \
  --schema-definition file://schema.avsc
```

### Create a workflow
```bash
aws glue create-workflow --name my-pipeline
aws glue create-trigger --name start-trigger --type ON_DEMAND \
  --workflow-name my-pipeline \
  --actions JobName=my-etl-job
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Jobs | [`jobs.md`](jobs.md) | create-job, delete-job, get-job, get-jobs, update-job, batch-get-jobs, start-job-run, batch-stop-job-run, get-job-run, get-job-runs, get-job-bookmark, reset-job-bookmark |
| Crawlers | [`crawlers.md`](crawlers.md) | create-crawler, delete-crawler, get-crawler, get-crawlers, update-crawler, start-crawler, stop-crawler, batch-get-crawlers, get-crawler-metrics, start-crawler-schedule, stop-crawler-schedule, list-crawlers |
| Databases | [`databases.md`](databases.md) | create-database, delete-database, get-database, get-databases, update-database |
| Tables | [`tables.md`](tables.md) | create-table, delete-table, get-table, get-tables, update-table, batch-delete-table, get-table-version, get-table-versions, delete-table-version, batch-delete-table-version, search-tables |
| Partitions | [`partitions.md`](partitions.md) | create-partition, delete-partition, get-partition, get-partitions, update-partition, batch-create-partition, batch-delete-partition, batch-get-partition, batch-update-partition, get-partition-indexes, create-partition-index, delete-partition-index |
| Connections | [`connections.md`](connections.md) | create-connection, delete-connection, get-connection, get-connections, update-connection, batch-delete-connection |
| Classifiers | [`classifiers.md`](classifiers.md) | create-classifier, delete-classifier, get-classifier, get-classifiers, update-classifier |
| Triggers | [`triggers.md`](triggers.md) | create-trigger, delete-trigger, get-trigger, get-triggers, update-trigger, start-trigger, stop-trigger, batch-get-triggers, list-triggers |
| Workflows | [`workflows.md`](workflows.md) | create-workflow, delete-workflow, get-workflow, get-workflows, update-workflow, start-workflow-run, stop-workflow-run, get-workflow-run, get-workflow-runs, get-workflow-run-properties, put-workflow-run-properties, batch-get-workflows, list-workflows, resume-workflow-run |
| Blueprints | [`blueprints.md`](blueprints.md) | create-blueprint, delete-blueprint, get-blueprint, get-blueprint-run, get-blueprint-runs, list-blueprints, start-blueprint-run, update-blueprint, batch-get-blueprints |
| Dev Endpoints | [`dev-endpoints.md`](dev-endpoints.md) | create-dev-endpoint, delete-dev-endpoint, get-dev-endpoint, get-dev-endpoints, update-dev-endpoint, batch-get-dev-endpoints, list-dev-endpoints |
| ML Transforms | [`ml-transforms.md`](ml-transforms.md) | create-ml-transform, delete-ml-transform, get-ml-transform, get-ml-transforms, update-ml-transform, start-ml-evaluation-task-run, start-ml-labeling-set-generation-task-run, cancel-ml-task-run, get-ml-task-run, get-ml-task-runs, list-ml-transforms |
| Data Quality | [`data-quality.md`](data-quality.md) | create-data-quality-ruleset, delete-data-quality-ruleset, get-data-quality-ruleset, get-data-quality-result, list-data-quality-rulesets, list-data-quality-results, start-data-quality-ruleset-evaluation-run, start-data-quality-rule-recommendation-run, cancel-data-quality-ruleset-evaluation-run, get-data-quality-ruleset-evaluation-run, list-data-quality-ruleset-evaluation-runs, batch-get-data-quality-result, update-data-quality-ruleset |
| Schema Registry | [`schema-registry.md`](schema-registry.md) | create-registry, delete-registry, get-registry, update-registry, list-registries, create-schema, delete-schema, get-schema, get-schema-version, update-schema, list-schemas, list-schema-versions, register-schema-version, get-schema-by-definition, get-schema-versions-diff, put-schema-version-metadata, remove-schema-version-metadata, query-schema-version-metadata, delete-schema-versions, check-schema-version-validity |
| Sessions | [`sessions.md`](sessions.md) | create-session, delete-session, get-session, list-sessions, stop-session, run-statement, cancel-statement, get-statement, list-statements |
| Integrations | [`integrations.md`](integrations.md) | create-integration, delete-integration, get-integration, describe-integrations, modify-integration, create-integration-resource-property, get-integration-resource-property, update-integration-resource-property, create-integration-table-properties, get-integration-table-properties, update-integration-table-properties, describe-inbound-integrations |
| Column Statistics | [`column-statistics.md`](column-statistics.md) | get-column-statistics-for-table, update-column-statistics-for-table, delete-column-statistics-for-table, get-column-statistics-for-partition, update-column-statistics-for-partition, delete-column-statistics-for-partition, get-column-statistics-task-run, get-column-statistics-task-runs, start-column-statistics-task-run, stop-column-statistics-task-run |
| Materialized Views | [`materialized-views.md`](materialized-views.md) | get-table (materialized views use the table API with specific properties) |
| Security Config | [`security-config.md`](security-config.md) | create-security-configuration, delete-security-configuration, get-security-configuration, get-security-configurations |
| Custom Entity Types | [`custom-entity-types.md`](custom-entity-types.md) | create-custom-entity-type, delete-custom-entity-type, get-custom-entity-type, batch-get-custom-entity-types, list-custom-entity-types |
| Usage, UDFs & Tags | [`usage-udfs-tags.md`](usage-udfs-tags.md) | get-resource-policies, get-resource-policy, put-resource-policy, delete-resource-policy, get-user-defined-function, get-user-defined-functions, create-user-defined-function, update-user-defined-function, delete-user-defined-function, tag-resource, untag-resource, get-tags |
