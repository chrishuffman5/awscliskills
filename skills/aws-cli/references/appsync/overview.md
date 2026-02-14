# AWS CLI v2 — AppSync

## Overview

Complete reference for all `aws appsync` subcommands in AWS CLI v2. Covers GraphQL API management, Event API management, data sources, resolvers, pipeline functions, type definitions, API keys, caching, custom domain names, merged API associations, channel namespaces, and resource tagging. AWS AppSync is a fully managed service for building scalable GraphQL and real-time Event APIs backed by multiple data sources including DynamoDB, Lambda, HTTP endpoints, OpenSearch, RDS, and EventBridge.

## Quick Reference — Common Workflows

### Create a GraphQL API with API key authentication
```bash
aws appsync create-graphql-api \
    --name my-graphql-api \
    --authentication-type API_KEY

aws appsync create-api-key \
    --api-id abc123 \
    --description "Development key" \
    --expires 1735689600
```

### Upload a GraphQL schema
```bash
aws appsync start-schema-creation \
    --api-id abc123 \
    --definition fileb://schema.graphql

aws appsync get-schema-creation-status \
    --api-id abc123
```

### Add a DynamoDB data source and resolver
```bash
aws appsync create-data-source \
    --api-id abc123 \
    --name PostsTable \
    --type AMAZON_DYNAMODB \
    --service-role-arn arn:aws:iam::123456789012:role/AppSyncDDBRole \
    --dynamodb-config '{"tableName":"Posts","awsRegion":"us-east-1"}'

aws appsync create-resolver \
    --api-id abc123 \
    --type-name Query \
    --field-name getPost \
    --data-source-name PostsTable \
    --runtime '{"name":"APPSYNC_JS","runtimeVersion":"1.0.0"}' \
    --code 'export function request(ctx) { return { operation: "GetItem", key: util.dynamodb.toMapValues({id: ctx.args.id}) }; } export function response(ctx) { return ctx.result; }'
```

### Create a pipeline resolver with functions
```bash
aws appsync create-function \
    --api-id abc123 \
    --name validateInput \
    --data-source-name NONE_DS \
    --runtime '{"name":"APPSYNC_JS","runtimeVersion":"1.0.0"}' \
    --code 'export function request(ctx) { return {}; } export function response(ctx) { return ctx.result; }'

aws appsync create-resolver \
    --api-id abc123 \
    --type-name Mutation \
    --field-name createPost \
    --kind PIPELINE \
    --pipeline-config '{"functions":["func1id","func2id"]}' \
    --runtime '{"name":"APPSYNC_JS","runtimeVersion":"1.0.0"}' \
    --code 'export function request(ctx) { return {}; } export function response(ctx) { return ctx.result; }'
```

### Create an Event API with channel namespaces
```bash
aws appsync create-api \
    --name my-event-api \
    --event-config '{"authProviders":[{"authType":"API_KEY"}],"connectionAuthModes":[{"authType":"API_KEY"}],"defaultPublishAuthModes":[{"authType":"API_KEY"}],"defaultSubscribeAuthModes":[{"authType":"API_KEY"}]}'

aws appsync create-channel-namespace \
    --api-id evt123 \
    --name chat-messages
```

### Set up a custom domain
```bash
aws appsync create-domain-name \
    --domain-name api.example.com \
    --certificate-arn arn:aws:acm:us-east-1:123456789012:certificate/abc-123

aws appsync associate-api \
    --domain-name api.example.com \
    --api-id abc123
```

### Create a merged API from source APIs
```bash
aws appsync create-graphql-api \
    --name my-merged-api \
    --authentication-type API_KEY \
    --api-type MERGED \
    --merged-api-execution-role-arn arn:aws:iam::123456789012:role/MergedApiRole

aws appsync associate-merged-graphql-api \
    --source-api-identifier source-api-id \
    --merged-api-identifier merged-api-id \
    --source-api-association-config '{"mergeType":"AUTO_MERGE"}'
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| GraphQL APIs | [graphql-apis.md](graphql-apis.md) | `create-graphql-api`, `get-graphql-api`, `list-graphql-apis`, `update-graphql-api`, `delete-graphql-api`, `get-graphql-api-environment-variables`, `put-graphql-api-environment-variables`, `get-introspection-schema`, `start-schema-creation`, `get-schema-creation-status` |
| Event APIs | [event-apis.md](event-apis.md) | `create-api`, `get-api`, `list-apis`, `update-api`, `delete-api`, `create-channel-namespace`, `get-channel-namespace`, `list-channel-namespaces`, `update-channel-namespace`, `delete-channel-namespace` |
| Data Sources | [data-sources.md](data-sources.md) | `create-data-source`, `get-data-source`, `list-data-sources`, `update-data-source`, `delete-data-source`, `start-data-source-introspection`, `get-data-source-introspection` |
| Resolvers | [resolvers.md](resolvers.md) | `create-resolver`, `get-resolver`, `list-resolvers`, `update-resolver`, `delete-resolver`, `list-resolvers-by-function`, `evaluate-code`, `evaluate-mapping-template` |
| Functions | [functions.md](functions.md) | `create-function`, `get-function`, `list-functions`, `update-function`, `delete-function` |
| Types | [types.md](types.md) | `create-type`, `get-type`, `list-types`, `update-type`, `delete-type`, `list-types-by-association` |
| API Keys & Cache | [api-keys-cache.md](api-keys-cache.md) | `create-api-key`, `list-api-keys`, `update-api-key`, `delete-api-key`, `create-api-cache`, `get-api-cache`, `update-api-cache`, `delete-api-cache`, `flush-api-cache` |
| Domain Names | [domain-names.md](domain-names.md) | `create-domain-name`, `get-domain-name`, `list-domain-names`, `update-domain-name`, `delete-domain-name`, `associate-api`, `get-api-association`, `disassociate-api` |
| Merged APIs | [merged-apis.md](merged-apis.md) | `associate-merged-graphql-api`, `disassociate-merged-graphql-api`, `associate-source-graphql-api`, `disassociate-source-graphql-api`, `get-source-api-association`, `list-source-api-associations`, `update-source-api-association`, `start-schema-merge` |
| Tags | [tags.md](tags.md) | `tag-resource`, `untag-resource`, `list-tags-for-resource` |
