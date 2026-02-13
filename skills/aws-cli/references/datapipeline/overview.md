# AWS CLI v2 — Data Pipeline

> **LEGACY SERVICE NOTICE:** AWS Data Pipeline is a legacy service. For new workloads, AWS recommends using **AWS Step Functions** for workflow orchestration, **AWS Glue** for ETL jobs, or **Amazon Managed Workflows for Apache Airflow (MWAA)** for complex data pipeline orchestration. Data Pipeline is still available but receives only maintenance updates.

## Overview

Complete reference for all `aws datapipeline` subcommands in AWS CLI v2. Covers pipeline management, pipeline definitions, object queries, task runner operations, and tagging.

AWS Data Pipeline is a web service for processing and moving data between different AWS compute and storage services, as well as on-premises data sources, at specified intervals. You define a pipeline (a data-processing workload) composed of data nodes, activities, schedules, and preconditions.

## Quick Reference — Common Workflows

### Create a pipeline

```bash
aws datapipeline create-pipeline \
  --name my-pipeline \
  --unique-id my-pipeline-token
```

### Upload a pipeline definition

```bash
aws datapipeline put-pipeline-definition \
  --pipeline-id df-0123456789ABCDEFG \
  --pipeline-definition file://pipeline-definition.json
```

### Validate a pipeline definition

```bash
aws datapipeline validate-pipeline-definition \
  --pipeline-id df-0123456789ABCDEFG \
  --pipeline-definition file://pipeline-definition.json
```

### Activate a pipeline

```bash
aws datapipeline activate-pipeline \
  --pipeline-id df-0123456789ABCDEFG
```

### List all pipelines

```bash
aws datapipeline list-pipelines --query 'pipelineIdList[].{ID:id,Name:name}' --output table
```

### Describe a pipeline

```bash
aws datapipeline describe-pipelines \
  --pipeline-ids df-0123456789ABCDEFG
```

### Get the pipeline definition

```bash
aws datapipeline get-pipeline-definition \
  --pipeline-id df-0123456789ABCDEFG
```

### Deactivate a pipeline

```bash
aws datapipeline deactivate-pipeline \
  --pipeline-id df-0123456789ABCDEFG
```

### Delete a pipeline

```bash
aws datapipeline delete-pipeline \
  --pipeline-id df-0123456789ABCDEFG
```

### Tag a pipeline

```bash
aws datapipeline add-tags \
  --pipeline-id df-0123456789ABCDEFG \
  --tags key=Environment,value=Production key=Project,value=MyETL
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Pipelines | [`pipelines.md`](pipelines.md) | create-pipeline, delete-pipeline, describe-pipelines, list-pipelines, activate-pipeline, deactivate-pipeline |
| Definitions | [`definitions.md`](definitions.md) | put-pipeline-definition, get-pipeline-definition, validate-pipeline-definition |
| Objects & Runs | [`objects-runs.md`](objects-runs.md) | describe-objects, query-objects, evaluate-expression, set-status |
| Tasks & Tags | [`tasks-tags.md`](tasks-tags.md) | poll-for-task, report-task-progress, report-task-runner-heartbeat, set-task-status, add-tags, remove-tags |
