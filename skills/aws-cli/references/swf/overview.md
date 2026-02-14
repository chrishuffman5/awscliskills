# AWS CLI v2 — SWF (Simple Workflow Service)

## Overview

Complete reference for all `aws swf` subcommands in AWS CLI v2. Covers domain management, workflow type and activity type registration, workflow execution lifecycle, activity and decision task polling and responses, counting operations, and resource tagging. SWF enables building applications that coordinate work across distributed components using asynchronous task-based workflows.

## Quick Reference — Common Workflows

### Register a domain
```bash
aws swf register-domain \
    --name my-domain \
    --workflow-execution-retention-period-in-days 30 \
    --description "Production workflow domain"
```

### Register a workflow type and activity type
```bash
aws swf register-workflow-type \
    --domain my-domain \
    --name "OrderProcessing" \
    --workflow-version "v1" \
    --default-execution-start-to-close-timeout 3600 \
    --default-task-start-to-close-timeout 300 \
    --default-task-list name=order-decisions \
    --default-child-policy TERMINATE

aws swf register-activity-type \
    --domain my-domain \
    --name "ProcessPayment" \
    --activity-version "v1" \
    --default-task-start-to-close-timeout 120 \
    --default-task-heartbeat-timeout 30 \
    --default-task-list name=payment-tasks
```

### Start a workflow execution
```bash
aws swf start-workflow-execution \
    --domain my-domain \
    --workflow-id "order-12345" \
    --workflow-type name=OrderProcessing,version=v1 \
    --input '{"orderId":"12345","amount":99.99}' \
    --execution-start-to-close-timeout 3600 \
    --task-start-to-close-timeout 300
```

### Describe a workflow execution
```bash
aws swf describe-workflow-execution \
    --domain my-domain \
    --execution workflowId=order-12345,runId=abc123 \
    --query '{Status:executionInfo.executionStatus,Open:openCounts}'
```

### Terminate a workflow execution
```bash
aws swf terminate-workflow-execution \
    --domain my-domain \
    --workflow-id "order-12345" \
    --reason "Cancelled by administrator" \
    --child-policy TERMINATE
```

### Count open workflow executions
```bash
aws swf count-open-workflow-executions \
    --domain my-domain \
    --start-time-filter oldestDate=1609459200
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Domains | [`domains.md`](domains.md) | `register-domain`, `describe-domain`, `list-domains`, `deprecate-domain`, `undeprecate-domain` |
| Workflow Types | [`workflow-types.md`](workflow-types.md) | `register-workflow-type`, `describe-workflow-type`, `list-workflow-types`, `deprecate-workflow-type`, `undeprecate-workflow-type`, `delete-workflow-type` |
| Activity Types | [`activity-types.md`](activity-types.md) | `register-activity-type`, `describe-activity-type`, `list-activity-types`, `deprecate-activity-type`, `undeprecate-activity-type`, `delete-activity-type` |
| Workflow Executions | [`workflow-executions.md`](workflow-executions.md) | `start-workflow-execution`, `describe-workflow-execution`, `get-workflow-execution-history`, `list-open-workflow-executions`, `list-closed-workflow-executions`, `request-cancel-workflow-execution`, `signal-workflow-execution`, `terminate-workflow-execution` |
| Activity Tasks | [`activity-tasks.md`](activity-tasks.md) | `poll-for-activity-task`, `record-activity-task-heartbeat`, `respond-activity-task-completed`, `respond-activity-task-failed`, `respond-activity-task-canceled` |
| Decision Tasks | [`decision-tasks.md`](decision-tasks.md) | `poll-for-decision-task`, `respond-decision-task-completed` |
| Counting | [`counting.md`](counting.md) | `count-open-workflow-executions`, `count-closed-workflow-executions`, `count-pending-activity-tasks`, `count-pending-decision-tasks` |
| Tags | [`tags.md`](tags.md) | `tag-resource`, `untag-resource`, `list-tags-for-resource` |
