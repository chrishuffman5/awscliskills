# AWS CLI v2 — DMS (Database Migration Service)

## Overview

Complete reference for all `aws dms` subcommands in AWS CLI v2. Covers replication instance management, endpoint configuration, replication task orchestration, serverless replication, data migrations, migration projects, Fleet Advisor, schema conversion, event subscriptions, certificates, and maintenance operations.

## Quick Reference — Common Workflows

### Create a replication subnet group
```bash
aws dms create-replication-subnet-group \
  --replication-subnet-group-identifier my-subnet-group \
  --replication-subnet-group-description "My subnet group" \
  --subnet-ids subnet-0123456789abcdef0 subnet-0abcdef1234567890
```

### Create a replication instance
```bash
aws dms create-replication-instance \
  --replication-instance-identifier my-repl-instance \
  --replication-instance-class dms.r5.large \
  --allocated-storage 100 \
  --replication-subnet-group-identifier my-subnet-group \
  --no-publicly-accessible
aws dms wait replication-instance-available \
  --filters Name=replication-instance-id,Values=my-repl-instance
```

### Create source and target endpoints
```bash
aws dms create-endpoint \
  --endpoint-identifier my-source \
  --endpoint-type source \
  --engine-name mysql \
  --server-name mydb.example.com \
  --port 3306 \
  --username admin \
  --password 'secret' \
  --database-name mydb

aws dms create-endpoint \
  --endpoint-identifier my-target \
  --endpoint-type target \
  --engine-name postgres \
  --server-name targetdb.example.com \
  --port 5432 \
  --username admin \
  --password 'secret' \
  --database-name targetdb
```

### Test endpoint connections
```bash
aws dms test-connection \
  --replication-instance-arn arn:aws:dms:us-east-1:123456789012:rep:ABCDEFG \
  --endpoint-arn arn:aws:dms:us-east-1:123456789012:endpoint:HIJKLMN
```

### Create and start a replication task
```bash
aws dms create-replication-task \
  --replication-task-identifier my-task \
  --source-endpoint-arn arn:aws:dms:us-east-1:123456789012:endpoint:SRC \
  --target-endpoint-arn arn:aws:dms:us-east-1:123456789012:endpoint:TGT \
  --replication-instance-arn arn:aws:dms:us-east-1:123456789012:rep:INST \
  --migration-type full-load-and-cdc \
  --table-mappings file://table-mappings.json
aws dms wait replication-task-ready \
  --filters Name=replication-task-id,Values=my-task

aws dms start-replication-task \
  --replication-task-arn arn:aws:dms:us-east-1:123456789012:task:TASKID \
  --start-replication-task-type start-replication
```

### Monitor replication task progress
```bash
aws dms describe-table-statistics \
  --replication-task-arn arn:aws:dms:us-east-1:123456789012:task:TASKID \
  --query 'TableStatistics[*].[SchemaName,TableName,FullLoadRows,Inserts,Deletes,Updates]' \
  --output table
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Replication Instances | [`replication-instances.md`](replication-instances.md) | create-replication-instance, delete-replication-instance, describe-replication-instances, modify-replication-instance, reboot-replication-instance, describe-orderable-replication-instances, describe-replication-instance-task-logs |
| Endpoints | [`endpoints.md`](endpoints.md) | create-endpoint, delete-endpoint, describe-endpoints, modify-endpoint, describe-endpoint-settings, describe-endpoint-types, test-connection, describe-connections, delete-connection |
| Replication Tasks | [`replication-tasks.md`](replication-tasks.md) | create-replication-task, delete-replication-task, describe-replication-tasks, modify-replication-task, move-replication-task, start-replication-task, stop-replication-task, reload-tables, describe-table-statistics, start-replication-task-assessment, start-replication-task-assessment-run, cancel-replication-task-assessment-run, delete-replication-task-assessment-run, describe-replication-task-assessment-results, describe-replication-task-assessment-runs, describe-replication-task-individual-assessments, describe-applicable-individual-assessments |
| Replication Subnet Groups | [`replication-subnet-groups.md`](replication-subnet-groups.md) | create-replication-subnet-group, delete-replication-subnet-group, describe-replication-subnet-groups, modify-replication-subnet-group |
| Serverless Replication | [`serverless-replication.md`](serverless-replication.md) | create-replication-config, delete-replication-config, describe-replication-configs, modify-replication-config, start-replication, stop-replication, describe-replications, reload-replication-tables, describe-replication-table-statistics |
| Data Migrations | [`data-migrations.md`](data-migrations.md) | create-data-migration, delete-data-migration, describe-data-migrations, modify-data-migration, start-data-migration, stop-data-migration |
| Migration Projects | [`migration-projects.md`](migration-projects.md) | create-migration-project, delete-migration-project, describe-migration-projects, modify-migration-project, create-data-provider, delete-data-provider, describe-data-providers, modify-data-provider, create-instance-profile, delete-instance-profile, describe-instance-profiles, modify-instance-profile |
| Metadata Models | [`metadata-models.md`](metadata-models.md) | describe-metadata-model-assessments, describe-metadata-model-conversions, describe-metadata-model-creations, start-metadata-model-assessment, start-metadata-model-conversion, start-metadata-model-creation, cancel-metadata-model-conversion, cancel-metadata-model-creation, start-metadata-model-export-as-script, start-metadata-model-export-to-target, start-metadata-model-import, describe-metadata-model-exports-as-script, describe-metadata-model-exports-to-target, describe-metadata-model-imports, export-metadata-model-assessment |
| Fleet Advisor | [`fleet-advisor.md`](fleet-advisor.md) | create-fleet-advisor-collector, delete-fleet-advisor-collector, describe-fleet-advisor-collectors, delete-fleet-advisor-databases, describe-fleet-advisor-databases, describe-fleet-advisor-lsa-analysis, describe-fleet-advisor-schema-object-summary, describe-fleet-advisor-schemas, run-fleet-advisor-lsa-analysis |
| Events | [`events.md`](events.md) | create-event-subscription, delete-event-subscription, describe-event-subscriptions, modify-event-subscription, describe-event-categories, describe-events, update-subscriptions-to-event-bridge |
| Schemas & Certificates | [`schemas-certificates.md`](schemas-certificates.md) | describe-schemas, refresh-schemas, describe-refresh-schemas-status, import-certificate, delete-certificate, describe-certificates |
| Recommendations | [`recommendations.md`](recommendations.md) | batch-start-recommendations, start-recommendations, describe-recommendations, describe-recommendation-limitations |
| Maintenance | [`maintenance.md`](maintenance.md) | apply-pending-maintenance-action, describe-pending-maintenance-actions, describe-account-attributes, describe-engine-versions, describe-conversion-configuration, modify-conversion-configuration, describe-extension-pack-associations, start-extension-pack-association |
| Tags | [`tags.md`](tags.md) | add-tags-to-resource, remove-tags-from-resource, list-tags-for-resource |
| Wait | [`wait.md`](wait.md) | replication-instance-available, replication-instance-deleted, replication-task-ready, replication-task-stopped, replication-task-running, replication-task-deleted, endpoint-deleted, test-connection-succeeds |
