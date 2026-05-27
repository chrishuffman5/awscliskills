# AppSync — Quick Reference

## All Commands

| Command | Description |
|---------|-------------|
| `associate-api` | Associate an API with a custom domain name |
| `associate-merged-graphql-api` | Associate a source API with a merged API |
| `associate-source-graphql-api` | Associate a source API from the merged API owner account |
| `create-api` | Create an Event API |
| `create-api-cache` | Create caching for a GraphQL API |
| `create-api-key` | Create an API key for a GraphQL API |
| `create-channel-namespace` | Create a channel namespace for an Event API |
| `create-data-source` | Create a data source |
| `create-domain-name` | Create a custom domain name |
| `create-function` | Create a pipeline function |
| `create-graphql-api` | Create a GraphQL API |
| `create-resolver` | Create a resolver |
| `create-type` | Create a GraphQL type |
| `delete-api` | Delete an Event API |
| `delete-api-cache` | Delete an API cache |
| `delete-api-key` | Delete an API key |
| `delete-channel-namespace` | Delete a channel namespace |
| `delete-data-source` | Delete a data source |
| `delete-domain-name` | Delete a custom domain name |
| `delete-function` | Delete a pipeline function |
| `delete-graphql-api` | Delete a GraphQL API |
| `delete-resolver` | Delete a resolver |
| `delete-type` | Delete a GraphQL type |
| `disassociate-api` | Disassociate an API from a custom domain |
| `disassociate-merged-graphql-api` | Disassociate a source API from a merged API |
| `disassociate-source-graphql-api` | Disassociate a source API from the merged API owner side |
| `evaluate-code` | Evaluate JavaScript resolver code |
| `evaluate-mapping-template` | Evaluate a VTL mapping template |
| `flush-api-cache` | Flush an API cache |
| `get-api` | Describe an Event API |
| `get-api-association` | Get API association with a custom domain |
| `get-api-cache` | Describe an API cache |
| `get-channel-namespace` | Describe a channel namespace |
| `get-data-source` | Describe a data source |
| `get-data-source-introspection` | Get data source introspection results |
| `get-domain-name` | Describe a custom domain name |
| `get-function` | Describe a pipeline function |
| `get-graphql-api` | Describe a GraphQL API |
| `get-graphql-api-environment-variables` | Get environment variables for a GraphQL API |
| `get-introspection-schema` | Get the introspection schema for a GraphQL API |
| `get-resolver` | Describe a resolver |
| `get-schema-creation-status` | Get the schema creation status |
| `get-source-api-association` | Describe a source API association |
| `get-type` | Describe a GraphQL type |
| `list-api-keys` | List API keys for a GraphQL API |
| `list-apis` | List Event APIs |
| `list-channel-namespaces` | List channel namespaces for an Event API |
| `list-data-sources` | List data sources for a GraphQL API |
| `list-domain-names` | List custom domain names |
| `list-functions` | List pipeline functions for a GraphQL API |
| `list-graphql-apis` | List GraphQL APIs |
| `list-resolvers` | List resolvers for a GraphQL API type |
| `list-resolvers-by-function` | List resolvers that use a specific function |
| `list-source-api-associations` | List source API associations for a merged API |
| `list-tags-for-resource` | List tags for an AppSync resource |
| `list-types` | List GraphQL types for a GraphQL API |
| `list-types-by-association` | List types by source API association |
| `put-graphql-api-environment-variables` | Set environment variables for a GraphQL API |
| `start-data-source-introspection` | Start introspection of a data source |
| `start-schema-creation` | Upload and create a GraphQL schema |
| `start-schema-merge` | Trigger a schema merge for a merged API |
| `tag-resource` | Add tags to an AppSync resource |
| `untag-resource` | Remove tags from an AppSync resource |
| `update-api` | Update an Event API |
| `update-api-cache` | Update API caching behavior |
| `update-api-key` | Update an API key |
| `update-channel-namespace` | Update a channel namespace |
| `update-data-source` | Update a data source |
| `update-domain-name` | Update a custom domain name |
| `update-function` | Update a pipeline function |
| `update-graphql-api` | Update a GraphQL API |
| `update-resolver` | Update a resolver |
| `update-source-api-association` | Update a source API association |
| `update-type` | Update a GraphQL type |

## Global Options

All commands accept these options:

| Option | Description |
|--------|-------------|
| `--output` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | JMESPath query to filter output |
| `--region` | AWS region |
| `--profile` | Named credential profile |
| `--no-cli-pager` | Disable pager for output |
| `--cli-input-json` | Read parameters from JSON string |
| `--cli-input-yaml` | Read parameters from YAML string |
| `--generate-cli-skeleton` | Print JSON/YAML input skeleton |

## Common Patterns

### List all GraphQL APIs with their endpoints
```bash
aws appsync list-graphql-apis \
    --query 'graphqlApis[].{Name:name,Id:apiId,Auth:authenticationType,Uris:uris}'
```

### Check schema creation status
```bash
aws appsync get-schema-creation-status --api-id abc123 \
    --query '{Status:status,Details:details}'
```

### List all resolvers for a type
```bash
aws appsync list-resolvers --api-id abc123 --type-name Query \
    --query 'resolvers[].{Field:fieldName,DataSource:dataSourceName,Kind:kind}'
```

### List data sources for an API
```bash
aws appsync list-data-sources --api-id abc123 \
    --query 'dataSources[].{Name:name,Type:type}'
```
