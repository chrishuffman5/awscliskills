
# AWS CLI v2 — Lambda (Serverless Compute)

## Overview

Complete reference for all `aws lambda` subcommands in AWS CLI v2. Covers function creation and management, deployment packages, layers, event source mappings, aliases, versions, provisioned concurrency, function URLs, code signing, and permissions.

## Quick Reference — Common Workflows

### Create a function from zip
```bash
aws lambda create-function --function-name my-func \
  --runtime python3.12 --handler index.handler \
  --role arn:aws:iam::123456789012:role/lambda-role \
  --zip-file fileb://function.zip
```

### Create a function from container image
```bash
aws lambda create-function --function-name my-func \
  --package-type Image \
  --code ImageUri=123456789012.dkr.ecr.us-east-1.amazonaws.com/my-app:latest \
  --role arn:aws:iam::123456789012:role/lambda-role
```

### Update function code
```bash
aws lambda update-function-code --function-name my-func --zip-file fileb://function.zip
aws lambda wait function-updated --function-name my-func
```

### Invoke a function
```bash
aws lambda invoke --function-name my-func --payload '{"key":"value"}' output.json
cat output.json
```

### Add an SQS event source
```bash
aws lambda create-event-source-mapping --function-name my-func \
  --event-source-arn arn:aws:sqs:us-east-1:123456789012:my-queue \
  --batch-size 10
```

### Publish version and create alias
```bash
aws lambda publish-version --function-name my-func --description "v1"
aws lambda create-alias --function-name my-func --name prod --function-version 1
```

## Covered Command Groups

| Group | Commands | Description |
|-------|----------|-------------|
| Functions | create, delete, get, list, update-code, update-configuration, wait | Function lifecycle |
| Invocation | invoke | Running functions |
| Layers | publish, get, list, delete, list-versions, get-policy, add/remove-permission | Shared code layers |
| Event Source Mappings | create, delete, get, list, update | Trigger configuration |
| Aliases | create, delete, get, list, update | Traffic routing |
| Versions | publish-version, list-versions-by-function | Immutable snapshots |
| Concurrency | put/get/delete provisioned-concurrency, put/get/delete function-concurrency | Scaling config |
| Function URLs | create, delete, get, update, list | HTTP endpoints |
| Permissions | add-permission, remove-permission, get-policy | Resource policies |
| Code Signing | create/update/get/list/delete code-signing-config | Signing configuration |
| Tags | tag-resource, untag-resource, list-tags | Resource tagging |

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Functions | [`functions.md`](functions.md) | create-function, delete-function, get-function, get-function-configuration, get-function-event-invoke-config, get-function-recursion-config, list-functions, list-function-event-invoke-configs, update-function-code, update-function-configuration, delete-function-event-invoke-config, put-function-event-invoke-config, update-function-event-invoke-config, put-function-recursion-config |
| Invocation | [`invocation.md`](invocation.md) | invoke |
| Layers | [`layers.md`](layers.md) | publish-layer-version, get-layer-version, get-layer-version-by-arn, get-layer-version-policy, list-layers, list-layer-versions, delete-layer-version, add-layer-version-permission, remove-layer-version-permission |
| Event Source Mappings | [`event-source-mappings.md`](event-source-mappings.md) | create-event-source-mapping, delete-event-source-mapping, get-event-source-mapping, list-event-source-mappings, update-event-source-mapping |
| Aliases | [`aliases.md`](aliases.md) | create-alias, delete-alias, get-alias, list-aliases, update-alias |
| Versions | [`versions.md`](versions.md) | publish-version, list-versions-by-function |
| Concurrency | [`concurrency.md`](concurrency.md) | put-function-concurrency, get-function-concurrency, delete-function-concurrency, put-provisioned-concurrency-config, get-provisioned-concurrency-config, delete-provisioned-concurrency-config, list-provisioned-concurrency-configs |
| Function URLs | [`function-urls.md`](function-urls.md) | create-function-url-config, delete-function-url-config, get-function-url-config, list-function-url-configs, update-function-url-config |
| Permissions | [`permissions.md`](permissions.md) | add-permission, remove-permission, get-policy |
| Code Signing | [`code-signing.md`](code-signing.md) | create-code-signing-config, delete-code-signing-config, get-code-signing-config, list-code-signing-configs, update-code-signing-config, get-function-code-signing-config, put-function-code-signing-config, delete-function-code-signing-config, list-functions-by-code-signing-config |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags |
| Account | [`account.md`](account.md) | get-account-settings |
| Runtime Management | [`runtime-management.md`](runtime-management.md) | get-runtime-management-config, put-runtime-management-config |
| Wait Commands | [`wait-commands.md`](wait-commands.md) | wait function-active, wait function-active-v2, wait function-exists, wait function-updated, wait function-updated-v2, wait published-version-active |
