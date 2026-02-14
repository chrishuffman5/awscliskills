# AWS CLI v2 — EventBridge Pipes

## Overview

Complete reference for all `aws pipes` subcommands in AWS CLI v2. Covers pipe creation, management, lifecycle control, and tagging. Amazon EventBridge Pipes connects event sources to targets with optional filtering, enrichment, and transformation. Supported sources include SQS, Kinesis, DynamoDB Streams, Amazon MQ, MSK, and self-managed Kafka. Targets include Lambda, Step Functions, ECS, Batch, API Gateway, EventBridge, CloudWatch Logs, Kinesis, SQS, Redshift, SageMaker, and Timestream.

## Quick Reference — Common Workflows

### Create a pipe from SQS to Lambda
```bash
aws pipes create-pipe \
    --name sqs-to-lambda \
    --source arn:aws:sqs:us-east-1:123456789012:my-queue \
    --target arn:aws:lambda:us-east-1:123456789012:function:my-processor \
    --role-arn arn:aws:iam::123456789012:role/PipeRole \
    --source-parameters '{"SqsQueueParameters":{"BatchSize":10,"MaximumBatchingWindowInSeconds":5}}' \
    --target-parameters '{"LambdaFunctionParameters":{"InvocationType":"REQUEST_RESPONSE"}}' \
    --desired-state RUNNING
```

### Create a pipe with filtering and enrichment
```bash
aws pipes create-pipe \
    --name filtered-pipe \
    --source arn:aws:sqs:us-east-1:123456789012:orders-queue \
    --target arn:aws:states:us-east-1:123456789012:stateMachine:order-processor \
    --role-arn arn:aws:iam::123456789012:role/PipeRole \
    --source-parameters '{"FilterCriteria":{"Filters":[{"Pattern":"{\"body\":{\"orderType\":[\"premium\"]}}"}]},"SqsQueueParameters":{"BatchSize":1}}' \
    --enrichment arn:aws:lambda:us-east-1:123456789012:function:enrich-order \
    --enrichment-parameters '{"InputTemplate":"{\"orderId\":<$.body.orderId>,\"customer\":<$.body.customer>}"}' \
    --target-parameters '{"StepFunctionStateMachineParameters":{"InvocationType":"FIRE_AND_FORGET"}}' \
    --desired-state RUNNING
```

### Create a pipe from Kinesis to ECS with logging
```bash
aws pipes create-pipe \
    --name kinesis-to-ecs \
    --source arn:aws:kinesis:us-east-1:123456789012:stream/my-stream \
    --target arn:aws:ecs:us-east-1:123456789012:cluster/my-cluster \
    --role-arn arn:aws:iam::123456789012:role/PipeRole \
    --source-parameters '{"KinesisStreamParameters":{"StartingPosition":"LATEST","BatchSize":100,"MaximumBatchingWindowInSeconds":10}}' \
    --target-parameters '{"EcsTaskParameters":{"TaskDefinitionArn":"arn:aws:ecs:us-east-1:123456789012:task-definition/processor:1","TaskCount":1,"LaunchType":"FARGATE","NetworkConfiguration":{"awsvpcConfiguration":{"Subnets":["subnet-abc123"],"AssignPublicIp":"ENABLED"}}}}' \
    --log-configuration '{"CloudwatchLogsLogDestination":{"LogGroupArn":"arn:aws:logs:us-east-1:123456789012:log-group:/aws/pipes/kinesis-to-ecs"},"Level":"ERROR"}' \
    --desired-state RUNNING
```

### Stop and restart a pipe
```bash
aws pipes stop-pipe --name my-pipe

aws pipes start-pipe --name my-pipe
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Pipes | [pipes.md](pipes.md) | `create-pipe`, `describe-pipe`, `list-pipes`, `update-pipe`, `delete-pipe`, `start-pipe`, `stop-pipe` |
| Tags | [tags.md](tags.md) | `tag-resource`, `untag-resource`, `list-tags-for-resource` |
