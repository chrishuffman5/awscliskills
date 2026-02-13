# AWS CLI v2 — SNS (Simple Notification Service) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/sns/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `add-permission` | Permissions | Add permissions to a topic access policy |
| `check-if-phone-number-is-opted-out` | SMS | Check if a phone number is opted out of SMS |
| `confirm-subscription` | Subscriptions | Confirm a pending subscription |
| `create-platform-application` | Platform Apps | Create a mobile push platform application |
| `create-platform-endpoint` | Platform Endpoints | Create an endpoint for a device on a platform |
| `create-sms-sandbox-phone-number` | SMS Sandbox | Add a phone number to SMS sandbox |
| `create-topic` | Topics | Create an SNS topic |
| `delete-endpoint` | Platform Endpoints | Delete a platform endpoint |
| `delete-platform-application` | Platform Apps | Delete a platform application |
| `delete-sms-sandbox-phone-number` | SMS Sandbox | Remove a phone number from SMS sandbox |
| `delete-topic` | Topics | Delete an SNS topic |
| `get-data-protection-policy` | Data Protection | Get data protection policy for a topic |
| `get-endpoint-attributes` | Platform Endpoints | Get endpoint attributes |
| `get-platform-application-attributes` | Platform Apps | Get platform application attributes |
| `get-sms-attributes` | SMS | Get default SMS sending attributes |
| `get-sms-sandbox-account-status` | SMS Sandbox | Check if account is in SMS sandbox |
| `get-subscription-attributes` | Subscriptions | Get subscription attributes |
| `get-topic-attributes` | Topics | Get topic attributes |
| `list-endpoints-by-platform-application` | Platform Endpoints | List endpoints for a platform application |
| `list-origination-numbers` | Origination | List dedicated origination numbers |
| `list-phone-numbers-opted-out` | SMS | List opted-out phone numbers |
| `list-platform-applications` | Platform Apps | List platform applications |
| `list-sms-sandbox-phone-numbers` | SMS Sandbox | List sandbox phone numbers |
| `list-subscriptions` | Subscriptions | List all subscriptions |
| `list-subscriptions-by-topic` | Subscriptions | List subscriptions for a topic |
| `list-tags-for-resource` | Tags | List tags for a resource |
| `list-topics` | Topics | List all topics |
| `opt-in-phone-number` | SMS | Opt in a phone number for SMS |
| `publish` | Publishing | Publish a message to a topic or endpoint |
| `publish-batch` | Publishing | Publish up to 10 messages in a batch |
| `put-data-protection-policy` | Data Protection | Set data protection policy for a topic |
| `remove-permission` | Permissions | Remove permissions from a topic access policy |
| `set-endpoint-attributes` | Platform Endpoints | Set endpoint attributes |
| `set-platform-application-attributes` | Platform Apps | Set platform application attributes |
| `set-sms-attributes` | SMS | Set default SMS sending attributes |
| `set-subscription-attributes` | Subscriptions | Set subscription attributes |
| `set-topic-attributes` | Topics | Set topic attributes |
| `subscribe` | Subscriptions | Subscribe an endpoint to a topic |
| `tag-resource` | Tags | Add tags to a resource |
| `unsubscribe` | Subscriptions | Unsubscribe from a topic |
| `untag-resource` | Tags | Remove tags from a resource |
| `verify-sms-sandbox-phone-number` | SMS Sandbox | Verify a sandbox phone number with OTP |

---

## Global Options Reference

These options are available on all `aws sns` subcommands:

| Option | Type | Description |
|--------|------|-------------|
| `--debug` | boolean | Turn on debug logging |
| `--endpoint-url` | string | Override default service URL |
| `--no-verify-ssl` | boolean | Disable SSL certificate verification |
| `--no-paginate` | boolean | Disable automatic pagination |
| `--output` | string | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | JMESPath query for filtering response data |
| `--profile` | string | Use a specific AWS credential profile |
| `--region` | string | AWS region to use |
| `--version` | string | Display the tool version |
| `--color` | string | Color output: `on`, `off`, `auto` |
| `--no-sign-request` | boolean | Do not sign requests |
| `--ca-bundle` | string | CA certificate bundle for SSL verification |
| `--cli-read-timeout` | integer | Socket read timeout in seconds (default: 60) |
| `--cli-connect-timeout` | integer | Socket connect timeout in seconds (default: 60) |
| `--cli-binary-format` | string | Binary blob format: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | Disable CLI pager for output |
| `--cli-auto-prompt` | boolean | Automatically prompt for CLI input parameters |
| `--no-cli-auto-prompt` | boolean | Disable automatic prompting |
| `--cli-input-json` | string | Read arguments from JSON string |
| `--cli-input-yaml` | string | Read arguments from YAML string |
| `--generate-cli-skeleton` | string | Print JSON/YAML skeleton without sending request. Values: `input`, `yaml-input`, `output` |
