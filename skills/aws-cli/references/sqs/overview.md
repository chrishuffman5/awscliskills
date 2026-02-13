
# AWS CLI v2 — SQS (Simple Queue Service)

## Overview

Complete reference for all `aws sqs` subcommands in AWS CLI v2. Covers standard and FIFO queue management, sending and receiving messages, dead-letter queues, visibility timeout configuration, long polling, message attributes, queue policies, and purging.

## Quick Reference — Common Workflows

### Create a standard queue
```bash
aws sqs create-queue --queue-name my-queue \
  --attributes VisibilityTimeout=60,MessageRetentionPeriod=345600
```

### Create a FIFO queue
```bash
aws sqs create-queue --queue-name my-queue.fifo \
  --attributes FifoQueue=true,ContentBasedDeduplication=true
```

### Send and receive messages
```bash
aws sqs send-message --queue-url https://sqs.us-east-1.amazonaws.com/123456789012/my-queue \
  --message-body '{"task":"process-order","id":42}'
aws sqs receive-message --queue-url https://sqs.us-east-1.amazonaws.com/123456789012/my-queue \
  --max-number-of-messages 10 --wait-time-seconds 20
```

### Delete a message after processing
```bash
aws sqs delete-message --queue-url https://sqs... --receipt-handle <handle>
```

### Configure dead-letter queue
```bash
aws sqs set-queue-attributes --queue-url https://sqs... \
  --attributes '{"RedrivePolicy":"{\"deadLetterTargetArn\":\"arn:aws:sqs:us-east-1:123456789012:my-dlq\",\"maxReceiveCount\":\"3\"}"}'
```

## Covered Command Groups

| Group | Commands | Description |
|-------|----------|-------------|
| Queues | create, delete, list, get-url, get/set-attributes, purge | Queue lifecycle |
| Messages | send, send-batch, receive, delete, delete-batch, change-visibility, change-visibility-batch | Message operations |
| Dead-Letter | list-dead-letter-source-queues, start/cancel-message-move-task, list-message-move-tasks | DLQ redrive |
| Permissions | add-permission, remove-permission | Access control |
| Tags | tag-queue, untag-queue, list-queue-tags | Resource tagging |

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Queue Management | [`queue-management.md`](queue-management.md) | create-queue, delete-queue, list-queues, get-queue-url, get-queue-attributes, set-queue-attributes, purge-queue |
| Messages | [`messages.md`](messages.md) | send-message, send-message-batch, receive-message, delete-message, delete-message-batch, change-message-visibility, change-message-visibility-batch |
| Dead-Letter Queue Redrive | [`dead-letter-queue-redrive.md`](dead-letter-queue-redrive.md) | list-dead-letter-source-queues, start-message-move-task, cancel-message-move-task, list-message-move-tasks |
| Permissions | [`permissions.md`](permissions.md) | add-permission, remove-permission |
| Tags | [`tags.md`](tags.md) | tag-queue, untag-queue, list-queue-tags |
