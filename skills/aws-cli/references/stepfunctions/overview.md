# AWS CLI v2 — Step Functions (States)

## Overview

Complete reference for all `aws stepfunctions` subcommands in AWS CLI v2. Covers state machine management, execution lifecycle, activities, map runs, and tagging.

## Quick Reference — Common Workflows

### Create a state machine
```bash
aws stepfunctions create-state-machine \
  --name my-state-machine \
  --definition file://definition.json \
  --role-arn arn:aws:iam::123456789012:role/StepFunctionsRole \
  --type STANDARD
```

### Start an execution
```bash
aws stepfunctions start-execution \
  --state-machine-arn arn:aws:states:us-east-1:123456789012:stateMachine:my-state-machine \
  --name my-execution-1 \
  --input '{"key": "value"}'
```

### Check execution status
```bash
aws stepfunctions describe-execution \
  --execution-arn arn:aws:states:us-east-1:123456789012:execution:my-state-machine:my-execution-1
```

### Get execution history
```bash
aws stepfunctions get-execution-history \
  --execution-arn arn:aws:states:us-east-1:123456789012:execution:my-state-machine:my-execution-1 \
  --max-results 100
```

### Stop an execution
```bash
aws stepfunctions stop-execution \
  --execution-arn arn:aws:states:us-east-1:123456789012:execution:my-state-machine:my-execution-1 \
  --cause "Manual stop"
```

### Update a state machine definition
```bash
aws stepfunctions update-state-machine \
  --state-machine-arn arn:aws:states:us-east-1:123456789012:stateMachine:my-state-machine \
  --definition file://new-definition.json
```

### List executions for a state machine
```bash
aws stepfunctions list-executions \
  --state-machine-arn arn:aws:states:us-east-1:123456789012:stateMachine:my-state-machine \
  --status-filter RUNNING
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| State Machines | [`state-machines.md`](state-machines.md) | create-state-machine, delete-state-machine, describe-state-machine, list-state-machines, update-state-machine, describe-state-machine-for-execution, publish-state-machine-version, list-state-machine-versions |
| Executions | [`executions.md`](executions.md) | start-execution, start-sync-execution, stop-execution, describe-execution, list-executions, get-execution-history, redrive-execution |
| Activities | [`activities.md`](activities.md) | create-activity, delete-activity, describe-activity, list-activities, get-activity-task, send-task-success, send-task-failure, send-task-heartbeat |
| Map Runs | [`map-runs.md`](map-runs.md) | describe-map-run, list-map-runs, update-map-run |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
