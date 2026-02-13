# AWS CLI v2 — EventBridge

## Overview

Complete reference for all `aws events` subcommands in AWS CLI v2. Covers event buses, rules, targets, archives, replays, connections, API destinations, schemas, pipes, and tags. EventBridge also has a separate `aws schemas` service for the Schema Registry and `aws pipes` service for EventBridge Pipes.

## Quick Reference — Common Workflows

### Create a custom event bus
```bash
aws events create-event-bus --name my-app-events
```

### Create a rule matching EC2 state changes
```bash
aws events put-rule --name ec2-state-change \
  --event-pattern '{"source":["aws.ec2"],"detail-type":["EC2 Instance State-change Notification"]}' \
  --state ENABLED
```

### Add a Lambda target to a rule
```bash
aws events put-targets --rule ec2-state-change \
  --targets "Id=lambda-target,Arn=arn:aws:lambda:us-east-1:123456789012:function:my-func"
```

### Put a custom event
```bash
aws events put-events --entries \
  '[{"Source":"my.app","DetailType":"OrderCreated","Detail":"{\"orderId\":\"123\"}","EventBusName":"my-app-events"}]'
```

### Create an archive for event replay
```bash
aws events create-archive --archive-name my-archive \
  --source-arn arn:aws:events:us-east-1:123456789012:event-bus/default \
  --retention-days 30
```

### Start a replay from an archive
```bash
aws events start-replay --replay-name my-replay \
  --event-source-arn arn:aws:events:us-east-1:123456789012:event-bus/default \
  --destination Arn=arn:aws:events:us-east-1:123456789012:event-bus/default \
  --event-start-time 2024-01-01T00:00:00Z \
  --event-end-time 2024-01-02T00:00:00Z
```

### Create an API destination
```bash
aws events create-connection --name my-connection \
  --authorization-type API_KEY \
  --auth-parameters "ApiKeyAuthParameters={ApiKeyName=x-api-key,ApiKeyValue=secret123}"

aws events create-api-destination --name my-api-dest \
  --connection-arn arn:aws:events:us-east-1:123456789012:connection/my-connection \
  --invocation-endpoint https://api.example.com/webhook \
  --http-method POST
```

### Create a pipe (SQS to Step Functions)
```bash
aws pipes create-pipe --name my-pipe \
  --source arn:aws:sqs:us-east-1:123456789012:my-queue \
  --target arn:aws:states:us-east-1:123456789012:stateMachine:my-sm \
  --role-arn arn:aws:iam::123456789012:role/pipe-role
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Event Buses | [`event-buses.md`](event-buses.md) | create-event-bus, delete-event-bus, describe-event-bus, list-event-buses, put-events, put-partner-events |
| Rules | [`rules.md`](rules.md) | put-rule, delete-rule, describe-rule, disable-rule, enable-rule, list-rules, list-rule-names-by-target, test-event-pattern |
| Targets | [`targets.md`](targets.md) | put-targets, remove-targets, list-targets-by-rule |
| Archives | [`archives.md`](archives.md) | create-archive, delete-archive, describe-archive, list-archives, update-archive |
| Replays | [`replays.md`](replays.md) | start-replay, cancel-replay, describe-replay, list-replays |
| Connections | [`connections.md`](connections.md) | create-connection, delete-connection, describe-connection, list-connections, update-connection, deauthorize-connection |
| API Destinations | [`api-destinations.md`](api-destinations.md) | create-api-destination, delete-api-destination, describe-api-destination, list-api-destinations, update-api-destination |
| Schemas | [`schemas.md`](schemas.md) | create-schema, delete-schema, describe-schema, list-schemas, update-schema, search-schemas, export-schema, create-registry, delete-registry, describe-registry, list-registries, update-registry, create-discoverer, delete-discoverer, describe-discoverer, list-discoverers, start-discoverer, stop-discoverer |
| Pipes | [`pipes.md`](pipes.md) | create-pipe, delete-pipe, describe-pipe, list-pipes, start-pipe, stop-pipe, update-pipe |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
