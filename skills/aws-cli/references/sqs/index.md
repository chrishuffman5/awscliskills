# AWS CLI v2 — SQS (Simple Queue Service) Command Reference Index

> Based on AWS CLI v2.33.20 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/sqs/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `add-permission` | Permissions | Add permissions to a queue |
| `cancel-message-move-task` | DLQ Redrive | Cancel a message move task |
| `change-message-visibility` | Messages | Change visibility timeout of a message |
| `change-message-visibility-batch` | Messages | Change visibility timeout for up to 10 messages |
| `create-queue` | Queue | Create a new standard or FIFO queue |
| `delete-message` | Messages | Delete a message from a queue |
| `delete-message-batch` | Messages | Delete up to 10 messages in a batch |
| `delete-queue` | Queue | Delete a queue |
| `get-queue-attributes` | Queue | Get attributes of a queue |
| `get-queue-url` | Queue | Get the URL of a queue by name |
| `list-dead-letter-source-queues` | DLQ Redrive | List queues that send messages to a DLQ |
| `list-message-move-tasks` | DLQ Redrive | List message move tasks for a queue |
| `list-queue-tags` | Tags | List tags applied to a queue |
| `list-queues` | Queue | List all queues |
| `purge-queue` | Queue | Delete all messages from a queue |
| `receive-message` | Messages | Receive messages from a queue |
| `remove-permission` | Permissions | Remove permissions from a queue |
| `send-message` | Messages | Send a message to a queue |
| `send-message-batch` | Messages | Send up to 10 messages in a batch |
| `set-queue-attributes` | Queue | Set attributes for a queue |
| `start-message-move-task` | DLQ Redrive | Start a message move task (DLQ redrive) |
| `tag-queue` | Tags | Add tags to a queue |
| `untag-queue` | Tags | Remove tags from a queue |

---

## Global Options Reference

These options are available on all `aws sqs` commands:

| Option | Type | Description |
|--------|------|-------------|
| `--debug` | boolean | Enable debug logging |
| `--endpoint-url` | string | Override default service URL |
| `--no-verify-ssl` | boolean | Disable SSL certificate verification |
| `--no-paginate` | boolean | Disable automatic pagination |
| `--output` | string | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | JMESPath query to filter output |
| `--profile` | string | Named credential profile |
| `--region` | string | AWS region override |
| `--version` | string | Display CLI version |
| `--color` | string | Color output: `on`, `off`, `auto` |
| `--no-sign-request` | boolean | Do not sign requests |
| `--ca-bundle` | string | CA certificate bundle for SSL verification |
| `--cli-read-timeout` | integer | Socket read timeout in seconds (default: 60) |
| `--cli-connect-timeout` | integer | Socket connect timeout in seconds (default: 60) |
| `--cli-binary-format` | string | Binary format: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | Disable output pager |
| `--cli-auto-prompt` | boolean | Enable auto-prompt for parameters |
| `--no-cli-auto-prompt` | boolean | Disable auto-prompt |
| `--cli-input-json` | string | Read arguments from JSON string |
| `--cli-input-yaml` | string | Read arguments from YAML string |
| `--generate-cli-skeleton` | string | Print JSON/YAML skeleton without making API call. Values: `input`, `yaml-input`, `output` |
