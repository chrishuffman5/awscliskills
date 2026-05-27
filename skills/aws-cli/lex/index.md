# AWS CLI v2 -- Amazon Lex V2 Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/lexv2-models/ and https://docs.aws.amazon.com/cli/latest/reference/lexv2-runtime/

---

## Quick Reference — lexv2-models

| Command | Category | Description |
|---------|----------|-------------|
| `create-bot` | Bot | Create a new bot |
| `delete-bot` | Bot | Delete a bot and all associated resources |
| `describe-bot` | Bot | Get metadata for a bot |
| `list-bots` | Bot | List all bots in the account |
| `update-bot` | Bot | Update an existing bot |
| `create-bot-version` | Bot | Create an immutable snapshot of a bot |
| `delete-bot-version` | Bot | Delete a specific bot version |
| `describe-bot-version` | Bot | Get metadata for a bot version |
| `list-bot-versions` | Bot | List all versions of a bot |
| `create-bot-alias` | Bot Alias | Create an alias for a bot |
| `delete-bot-alias` | Bot Alias | Delete a bot alias |
| `describe-bot-alias` | Bot Alias | Get metadata for a bot alias |
| `list-bot-aliases` | Bot Alias | List all aliases for a bot |
| `update-bot-alias` | Bot Alias | Update an existing bot alias |
| `create-bot-locale` | Bot Locale | Create a locale for a bot |
| `delete-bot-locale` | Bot Locale | Delete a bot locale |
| `describe-bot-locale` | Bot Locale | Get metadata for a bot locale |
| `list-bot-locales` | Bot Locale | List all locales for a bot version |
| `update-bot-locale` | Bot Locale | Update a bot locale configuration |
| `build-bot-locale` | Bot Locale | Build a bot locale for testing |
| `create-intent` | Intent | Create an intent in a bot locale |
| `delete-intent` | Intent | Delete an intent |
| `describe-intent` | Intent | Get metadata for an intent |
| `list-intents` | Intent | List all intents in a bot locale |
| `update-intent` | Intent | Update an existing intent |
| `list-built-in-intents` | Intent | List built-in intents for a locale |
| `list-recommended-intents` | Intent | List recommended intents from bot recommendation |
| `create-slot` | Slot | Create a slot in an intent |
| `delete-slot` | Slot | Delete a slot |
| `describe-slot` | Slot | Get metadata for a slot |
| `list-slots` | Slot | List all slots in an intent |
| `update-slot` | Slot | Update an existing slot |
| `create-slot-type` | Slot Type | Create a custom slot type |
| `delete-slot-type` | Slot Type | Delete a slot type |
| `describe-slot-type` | Slot Type | Get metadata for a slot type |
| `list-slot-types` | Slot Type | List all slot types in a bot locale |
| `update-slot-type` | Slot Type | Update an existing slot type |
| `list-built-in-slot-types` | Slot Type | List built-in slot types for a locale |
| `batch-create-custom-vocabulary-item` | Custom Vocabulary | Create multiple custom vocabulary items |
| `batch-delete-custom-vocabulary-item` | Custom Vocabulary | Delete multiple custom vocabulary items |
| `batch-update-custom-vocabulary-item` | Custom Vocabulary | Update multiple custom vocabulary items |
| `delete-custom-vocabulary` | Custom Vocabulary | Delete custom vocabulary for a locale |
| `describe-custom-vocabulary-metadata` | Custom Vocabulary | Get custom vocabulary metadata |
| `list-custom-vocabulary-items` | Custom Vocabulary | List custom vocabulary items |
| `create-export` | Import/Export | Create a zip archive export of a bot or locale |
| `delete-export` | Import/Export | Delete an export |
| `describe-export` | Import/Export | Get metadata for an export |
| `list-exports` | Import/Export | List all exports for a bot or locale |
| `update-export` | Import/Export | Update export file password |
| `start-import` | Import/Export | Start importing from a zip archive |
| `delete-import` | Import/Export | Delete an import |
| `describe-import` | Import/Export | Get metadata for an import |
| `list-imports` | Import/Export | List all imports |
| `create-upload-url` | Import/Export | Create a presigned URL for uploading import archive |
| `create-test-set-discrepancy-report` | Test Sets | Create a test set discrepancy report |
| `delete-test-set` | Test Sets | Delete a test set |
| `describe-test-execution` | Test Sets | Get metadata for a test execution |
| `describe-test-set` | Test Sets | Get metadata for a test set |
| `describe-test-set-discrepancy-report` | Test Sets | Get discrepancy report details |
| `describe-test-set-generation` | Test Sets | Get test set generation details |
| `get-test-execution-artifacts-url` | Test Sets | Get URL for test execution artifacts |
| `list-test-execution-result-items` | Test Sets | List test execution result items |
| `list-test-executions` | Test Sets | List all test executions |
| `list-test-set-records` | Test Sets | List records in a test set |
| `list-test-sets` | Test Sets | List all test sets |
| `start-test-execution` | Test Sets | Start a test execution |
| `start-test-set-generation` | Test Sets | Start generating a test set |
| `list-aggregated-utterances` | Analytics | List aggregated utterance data |
| `list-intent-metrics` | Analytics | List intent-level metrics |
| `list-intent-paths` | Analytics | List intent paths |
| `list-intent-stage-metrics` | Analytics | List intent stage metrics |
| `list-session-analytics-data` | Analytics | List session analytics data |
| `list-session-metrics` | Analytics | List session-level metrics |
| `list-utterance-analytics-data` | Analytics | List utterance analytics data |
| `list-utterance-metrics` | Analytics | List utterance-level metrics |
| `delete-utterances` | Analytics | Delete stored utterances |
| `create-bot-replica` | Bot Replica | Create a bot replica in another region |
| `delete-bot-replica` | Bot Replica | Delete a bot replica |
| `describe-bot-replica` | Bot Replica | Get metadata for a bot replica |
| `list-bot-replicas` | Bot Replica | List all bot replicas |
| `list-bot-alias-replicas` | Bot Replica | List alias replicas for a bot |
| `list-bot-version-replicas` | Bot Replica | List version replicas for a bot |
| `describe-bot-recommendation` | Recommendation | Get bot recommendation details |
| `list-bot-recommendations` | Recommendation | List bot recommendations |
| `start-bot-recommendation` | Recommendation | Start a bot recommendation |
| `update-bot-recommendation` | Recommendation | Update a bot recommendation |
| `stop-bot-recommendation` | Recommendation | Stop a bot recommendation |
| `describe-bot-resource-generation` | Recommendation | Get resource generation details |
| `list-bot-resource-generations` | Recommendation | List resource generations |
| `start-bot-resource-generation` | Recommendation | Start a resource generation |
| `generate-bot-element` | Recommendation | Generate a bot element |
| `search-associated-transcripts` | Recommendation | Search transcripts associated with a recommendation |
| `create-resource-policy` | Resource Policy | Create a resource-based policy |
| `delete-resource-policy` | Resource Policy | Delete a resource policy |
| `describe-resource-policy` | Resource Policy | Get a resource policy |
| `update-resource-policy` | Resource Policy | Update a resource policy |
| `create-resource-policy-statement` | Resource Policy | Add a statement to a resource policy |
| `delete-resource-policy-statement` | Resource Policy | Remove a statement from a resource policy |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

## Quick Reference — lexv2-runtime

| Command | Category | Description |
|---------|----------|-------------|
| `recognize-text` | Runtime | Send text input to a bot for processing |
| `recognize-utterance` | Runtime | Send audio or text input to a bot |
| `get-session` | Runtime | Get the current session state |
| `put-session` | Runtime | Create or update a session |
| `delete-session` | Runtime | Delete a session |

---

## Global Options

These options are available on ALL `aws lexv2-models` and `aws lexv2-runtime` commands.

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `--debug` | boolean | false | Enable debug logging to stderr |
| `--endpoint-url` | string | -- | Override the default service endpoint URL |
| `--no-verify-ssl` | boolean | false | Disable SSL certificate verification |
| `--no-paginate` | boolean | false | Disable automatic pagination |
| `--output` | string | `json` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | -- | JMESPath query to filter output |
| `--profile` | string | `default` | Named AWS credential profile |
| `--region` | string | from config | AWS region to send requests to |
| `--version` | string | -- | Display the CLI version |
| `--color` | string | `auto` | Toggle color output: `on`, `off`, `auto` |
| `--no-sign-request` | boolean | false | Do not sign requests |
| `--ca-bundle` | string | -- | Path to custom CA certificate bundle for SSL |
| `--cli-read-timeout` | integer | 60 | Socket read timeout in seconds |
| `--cli-connect-timeout` | integer | 60 | Socket connect timeout in seconds |
| `--cli-binary-format` | string | `base64` | Format for binary blob input: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from a JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from a YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton: `input`, `yaml-input`, `output` |

---

## Common Patterns

### Bot Status Values
| Status | Description |
|--------|-------------|
| `Creating` | Bot is being created |
| `Available` | Bot is ready to use |
| `Inactive` | Bot is inactive |
| `Deleting` | Bot is being deleted |
| `Failed` | Bot creation failed |
| `Versioning` | A new version is being created |
| `Importing` | Bot is being imported |
| `Updating` | Bot is being updated |

### Bot Locale Status Values
| Status | Description |
|--------|-------------|
| `Creating` | Locale is being created |
| `Building` | Locale is being built |
| `Built` | Locale is built and ready for testing |
| `ReadyExpressTesting` | Ready for express testing |
| `Failed` | Build failed |
| `Deleting` | Locale is being deleted |
| `NotBuilt` | Locale has not been built |
| `Importing` | Locale is being imported |
| `Processing` | Locale is processing |

### Bot Alias Status Values
| Status | Description |
|--------|-------------|
| `Creating` | Alias is being created |
| `Available` | Alias is ready to use |
| `Deleting` | Alias is being deleted |
| `Failed` | Alias creation failed |

### Import Status Values
| Status | Description |
|--------|-------------|
| `InProgress` | Import is in progress |
| `Completed` | Import completed successfully |
| `Failed` | Import failed |
| `Deleting` | Import is being deleted |

### Intent State Values
| State | Description |
|-------|-------------|
| `Failed` | Intent fulfillment failed |
| `Fulfilled` | Intent was fulfilled |
| `InProgress` | Intent is in progress |
| `ReadyForFulfillment` | All slots filled, ready for fulfillment |
| `Waiting` | Waiting for user input |
| `FulfillmentInProgress` | Fulfillment Lambda is executing |

### Dialog Action Types
| Type | Description |
|------|-------------|
| `Close` | Close the dialog |
| `ConfirmIntent` | Ask user to confirm intent |
| `Delegate` | Let Lex decide next action |
| `ElicitIntent` | Ask user for their intent |
| `ElicitSlot` | Ask user for a slot value |
| `None` | No specific action |

### Wait Commands
```bash
aws lexv2-models wait bot-available --bot-id ABCDEFGHIJ
aws lexv2-models wait bot-alias-available --bot-id ABCDEFGHIJ --bot-alias-id ALIASID123
aws lexv2-models wait bot-locale-built --bot-id ABCDEFGHIJ --bot-version DRAFT --locale-id en_US
aws lexv2-models wait bot-export-completed --export-id EXPORTID12
aws lexv2-models wait bot-import-completed --import-id IMPORTID12
```
