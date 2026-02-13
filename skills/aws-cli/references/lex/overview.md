# AWS CLI v2 — Amazon Lex V2

## Overview

Complete reference for all `aws lexv2-models` and `aws lexv2-runtime` subcommands in AWS CLI v2. Covers bot management, bot aliases, bot locales, intents, slots, slot types, custom vocabulary, import/export, test sets, analytics, bot replicas, bot recommendations, resource policies, runtime interactions, and tagging.

## Quick Reference — Common Workflows

### Create a bot
```bash
aws lexv2-models create-bot \
  --bot-name OrderBot \
  --role-arn arn:aws:iam::123456789012:role/LexBotRole \
  --data-privacy childDirected=false \
  --idle-session-ttl-in-seconds 900
```

### Create a bot locale
```bash
aws lexv2-models create-bot-locale \
  --bot-id ABCDEFGHIJ \
  --bot-version DRAFT \
  --locale-id en_US \
  --nlu-intent-confidence-threshold 0.80 \
  --voice-settings engine=neural,voiceId=Joanna
```

### Create an intent
```bash
aws lexv2-models create-intent \
  --intent-name OrderPizza \
  --bot-id ABCDEFGHIJ \
  --bot-version DRAFT \
  --locale-id en_US \
  --sample-utterances '[{"utterance":"I want to order a pizza"},{"utterance":"Order a pizza"}]'
```

### Create a slot
```bash
aws lexv2-models create-slot \
  --slot-name PizzaSize \
  --bot-id ABCDEFGHIJ \
  --bot-version DRAFT \
  --locale-id en_US \
  --intent-id INTENTID123 \
  --value-elicitation-setting '{"slotConstraint":"Required","promptSpecification":{"messageGroups":[{"message":{"plainTextMessage":{"value":"What size pizza?"}}}],"maxRetries":2}}'
```

### Build a bot locale
```bash
aws lexv2-models build-bot-locale \
  --bot-id ABCDEFGHIJ \
  --bot-version DRAFT \
  --locale-id en_US
```

### Create a bot version and alias
```bash
aws lexv2-models create-bot-version \
  --bot-id ABCDEFGHIJ \
  --bot-version-locale-specification '{"en_US":{"sourceBotVersion":"DRAFT"}}'

aws lexv2-models create-bot-alias \
  --bot-alias-name PROD \
  --bot-id ABCDEFGHIJ \
  --bot-version 1
```

### Send text to a bot (runtime)
```bash
aws lexv2-runtime recognize-text \
  --bot-id ABCDEFGHIJ \
  --bot-alias-id TSTALIASID \
  --locale-id en_US \
  --session-id user-session-123 \
  --text "I want to order a pizza"
```

### Import a bot from a zip archive
```bash
aws lexv2-models create-upload-url
# Upload zip to the returned URL, then:
aws lexv2-models start-import \
  --import-id IMPORTID123 \
  --resource-specification file://spec.json \
  --merge-strategy Overwrite
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Bots | [`bots.md`](bots.md) | create-bot, delete-bot, describe-bot, list-bots, update-bot, create-bot-version, delete-bot-version, describe-bot-version, list-bot-versions |
| Bot Aliases | [`bot-aliases.md`](bot-aliases.md) | create-bot-alias, delete-bot-alias, describe-bot-alias, list-bot-aliases, update-bot-alias |
| Bot Locales | [`bot-locales.md`](bot-locales.md) | create-bot-locale, delete-bot-locale, describe-bot-locale, list-bot-locales, update-bot-locale, build-bot-locale |
| Intents | [`intents.md`](intents.md) | create-intent, delete-intent, describe-intent, list-intents, update-intent, list-built-in-intents, list-recommended-intents |
| Slots | [`slots.md`](slots.md) | create-slot, delete-slot, describe-slot, list-slots, update-slot, create-slot-type, delete-slot-type, describe-slot-type, list-slot-types, update-slot-type, list-built-in-slot-types |
| Custom Vocabulary | [`custom-vocabulary.md`](custom-vocabulary.md) | batch-create-custom-vocabulary-item, batch-delete-custom-vocabulary-item, batch-update-custom-vocabulary-item, delete-custom-vocabulary, describe-custom-vocabulary-metadata, list-custom-vocabulary-items |
| Import/Export | [`import-export.md`](import-export.md) | create-export, delete-export, describe-export, list-exports, update-export, start-import, delete-import, describe-import, list-imports, create-upload-url |
| Test Sets | [`test-sets.md`](test-sets.md) | create-test-set-discrepancy-report, delete-test-set, describe-test-execution, describe-test-set, describe-test-set-discrepancy-report, describe-test-set-generation, get-test-execution-artifacts-url, list-test-execution-result-items, list-test-executions, list-test-set-records, list-test-sets, start-test-execution, start-test-set-generation |
| Analytics | [`analytics.md`](analytics.md) | list-aggregated-utterances, list-intent-metrics, list-intent-paths, list-intent-stage-metrics, list-session-analytics-data, list-session-metrics, list-utterance-analytics-data, list-utterance-metrics, delete-utterances |
| Bot Replicas | [`bot-replicas.md`](bot-replicas.md) | create-bot-replica, delete-bot-replica, describe-bot-replica, list-bot-replicas, list-bot-alias-replicas, list-bot-version-replicas |
| Recommendations | [`recommendations.md`](recommendations.md) | describe-bot-recommendation, list-bot-recommendations, start-bot-recommendation, update-bot-recommendation, stop-bot-recommendation, describe-bot-resource-generation, list-bot-resource-generations, start-bot-resource-generation, generate-bot-element, search-associated-transcripts |
| Resource Policies | [`resource-policies.md`](resource-policies.md) | create-resource-policy, delete-resource-policy, describe-resource-policy, update-resource-policy, create-resource-policy-statement, delete-resource-policy-statement |
| Runtime | [`runtime.md`](runtime.md) | recognize-text, recognize-utterance, get-session, put-session, delete-session |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
| Wait | [`wait.md`](wait.md) | wait bot-available, wait bot-alias-available, wait bot-locale-built, wait bot-locale-express-testing-available, wait bot-version-available, wait bot-export-completed, wait bot-import-completed |
