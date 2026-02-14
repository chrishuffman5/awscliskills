# AWS CLI v2 — EventBridge Scheduler

## Overview

Complete reference for all `aws scheduler` subcommands in AWS CLI v2. Covers schedule creation and management, schedule groups, and resource tagging. Amazon EventBridge Scheduler is a serverless scheduler that creates, runs, and manages scheduled tasks at scale. It supports one-time and recurring schedules using at, rate, and cron expressions, with built-in retry policies and dead-letter queues. Targets include Lambda, Step Functions, SQS, SNS, ECS, EventBridge, Kinesis, SageMaker, and any AWS API action via universal targets.

## Quick Reference — Common Workflows

### Create a recurring Lambda schedule
```bash
aws scheduler create-schedule \
    --name invoke-lambda-every-hour \
    --schedule-expression "rate(1 hour)" \
    --flexible-time-window Mode=OFF \
    --target '{"Arn":"arn:aws:lambda:us-east-1:123456789012:function:MyFunction","RoleArn":"arn:aws:iam::123456789012:role/SchedulerRole"}'
```

### Create a one-time schedule
```bash
aws scheduler create-schedule \
    --name one-time-task \
    --schedule-expression "at(2026-03-01T08:00:00)" \
    --schedule-expression-timezone "America/New_York" \
    --flexible-time-window Mode=OFF \
    --action-after-completion DELETE \
    --target '{"Arn":"arn:aws:sqs:us-east-1:123456789012:my-queue","RoleArn":"arn:aws:iam::123456789012:role/SchedulerRole","Input":"{\"action\":\"cleanup\"}"}'
```

### Create a cron schedule with retry policy
```bash
aws scheduler create-schedule \
    --name daily-report \
    --schedule-expression "cron(0 9 * * ? *)" \
    --schedule-expression-timezone "US/Eastern" \
    --flexible-time-window Mode=FLEXIBLE,MaximumWindowInMinutes=15 \
    --target '{"Arn":"arn:aws:states:us-east-1:123456789012:stateMachine:ReportGenerator","RoleArn":"arn:aws:iam::123456789012:role/SchedulerRole","RetryPolicy":{"MaximumRetryAttempts":3,"MaximumEventAgeInSeconds":3600},"DeadLetterConfig":{"Arn":"arn:aws:sqs:us-east-1:123456789012:dlq"}}'
```

### Organize schedules with groups
```bash
aws scheduler create-schedule-group \
    --name production-jobs \
    --tags Key=Environment,Value=Production

aws scheduler create-schedule \
    --name nightly-backup \
    --group-name production-jobs \
    --schedule-expression "cron(0 2 * * ? *)" \
    --flexible-time-window Mode=OFF \
    --target '{"Arn":"arn:aws:lambda:us-east-1:123456789012:function:BackupFunction","RoleArn":"arn:aws:iam::123456789012:role/SchedulerRole"}'
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Schedules | [schedules.md](schedules.md) | `create-schedule`, `get-schedule`, `list-schedules`, `update-schedule`, `delete-schedule` |
| Schedule Groups | [schedule-groups.md](schedule-groups.md) | `create-schedule-group`, `get-schedule-group`, `list-schedule-groups`, `delete-schedule-group` |
| Tags | [tags.md](tags.md) | `tag-resource`, `untag-resource`, `list-tags-for-resource` |
