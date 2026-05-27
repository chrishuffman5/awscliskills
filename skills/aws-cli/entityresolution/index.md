# Entity Resolution — Quick Reference

## All Commands

| Command | Description |
|---------|-------------|
| `create-matching-workflow` | Create a matching workflow |
| `get-matching-workflow` | Get details of a matching workflow |
| `list-matching-workflows` | List matching workflows |
| `update-matching-workflow` | Update a matching workflow |
| `delete-matching-workflow` | Delete a matching workflow |
| `start-matching-job` | Start a matching job |
| `get-matching-job` | Get matching job status and metrics |
| `list-matching-jobs` | List matching jobs |
| `get-match-id` | Get match ID for a single record |
| `generate-match-id` | Generate match ID with processing options |
| `batch-delete-unique-id` | Batch delete unique IDs |
| `create-id-mapping-workflow` | Create an ID mapping workflow |
| `get-id-mapping-workflow` | Get details of an ID mapping workflow |
| `list-id-mapping-workflows` | List ID mapping workflows |
| `update-id-mapping-workflow` | Update an ID mapping workflow |
| `delete-id-mapping-workflow` | Delete an ID mapping workflow |
| `start-id-mapping-job` | Start an ID mapping job |
| `get-id-mapping-job` | Get ID mapping job status |
| `list-id-mapping-jobs` | List ID mapping jobs |
| `create-id-namespace` | Create an ID namespace |
| `get-id-namespace` | Get details of an ID namespace |
| `list-id-namespaces` | List ID namespaces |
| `update-id-namespace` | Update an ID namespace |
| `delete-id-namespace` | Delete an ID namespace |
| `create-schema-mapping` | Create a schema mapping |
| `get-schema-mapping` | Get details of a schema mapping |
| `list-schema-mappings` | List schema mappings |
| `update-schema-mapping` | Update a schema mapping |
| `delete-schema-mapping` | Delete a schema mapping |
| `get-provider-service` | Get details of a provider service |
| `list-provider-services` | List available provider services |
| `put-policy` | Create/replace a resource policy |
| `get-policy` | Get a resource policy |
| `add-policy-statement` | Add a statement to a resource policy |
| `delete-policy-statement` | Delete a statement from a resource policy |
| `tag-resource` | Add tags to a resource |
| `untag-resource` | Remove tags from a resource |
| `list-tags-for-resource` | List tags for a resource |

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

### Check matching job results
```bash
aws entityresolution get-matching-job \
    --workflow-name my-workflow \
    --job-id abc123 \
    --query '{Status:status,Records:metrics.inputRecords,Matches:metrics.matchIDs}'
```

### List all active matching workflows
```bash
aws entityresolution list-matching-workflows \
    --query 'workflowSummaries[].{Name:workflowName,Created:createdAt}'
```

### Look up match ID with normalization
```bash
aws entityresolution get-match-id \
    --workflow-name my-workflow \
    --record name="John Doe",email=john@example.com \
    --apply-normalization
```
