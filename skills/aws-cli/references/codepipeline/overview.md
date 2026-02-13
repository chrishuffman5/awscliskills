# AWS CLI v2 — CodePipeline

## Overview

Complete reference for all `aws codepipeline` subcommands in AWS CLI v2. Covers pipeline management, stage transitions, action types, approval results, action execution, webhooks, and resource tagging.

## Quick Reference — Common Workflows

### Create a pipeline
```bash
aws codepipeline create-pipeline --cli-input-json file://pipeline.json
```

### Get pipeline details
```bash
aws codepipeline get-pipeline --name my-pipeline
```

### List all pipelines
```bash
aws codepipeline list-pipelines --query 'pipelines[].name'
```

### Start a pipeline execution
```bash
aws codepipeline start-pipeline-execution --name my-pipeline
```

### Get pipeline execution status
```bash
aws codepipeline get-pipeline-state --name my-pipeline
```

### Stop a pipeline execution
```bash
aws codepipeline stop-pipeline-execution --pipeline-name my-pipeline \
  --pipeline-execution-id exec-id --reason "Manual stop"
```

### Approve a manual approval action
```bash
aws codepipeline put-approval-result --pipeline-name my-pipeline \
  --stage-name Approval --action-name ManualApproval \
  --result summary="Approved by admin",status=Approved \
  --token approval-token
```

### Enable/disable a stage transition
```bash
aws codepipeline disable-stage-transition --pipeline-name my-pipeline \
  --stage-name Production --transition-type Inbound \
  --reason "Maintenance window"

aws codepipeline enable-stage-transition --pipeline-name my-pipeline \
  --stage-name Production --transition-type Inbound
```

### Retry a failed stage
```bash
aws codepipeline retry-stage-execution --pipeline-name my-pipeline \
  --stage-name Build --pipeline-execution-id exec-id \
  --retry-mode FAILED_ACTIONS
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Pipelines | [`pipelines.md`](pipelines.md) | create-pipeline, delete-pipeline, get-pipeline, list-pipelines, update-pipeline, start-pipeline-execution, stop-pipeline-execution, get-pipeline-state, get-pipeline-execution, list-pipeline-executions, retry-stage-execution, rollback-stage |
| Stages | [`stages.md`](stages.md) | enable-stage-transition, disable-stage-transition, put-approval-result |
| Actions | [`actions.md`](actions.md) | put-third-party-job-success-result, put-third-party-job-failure-result, put-job-success-result, put-job-failure-result, poll-for-third-party-jobs, poll-for-jobs, acknowledge-third-party-job, acknowledge-job, put-action-revision, list-action-executions |
| Action Types | [`action-types.md`](action-types.md) | get-action-type, list-action-types, update-action-type |
| Webhooks | [`webhooks.md`](webhooks.md) | put-webhook, delete-webhook, deregister-webhook-with-third-party, list-webhooks, register-webhook-with-third-party |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
