# AWS CLI v2 — Entity Resolution

## Overview

Complete reference for all `aws entityresolution` subcommands in AWS CLI v2. Covers matching workflows, ID mapping workflows, ID namespaces, schema mappings, provider services, and resource policies. Entity Resolution helps link records from multiple sources by matching, linking, and enhancing data using rule-based, ML, or provider-based resolution techniques.

## Quick Reference — Common Workflows

### Create a schema mapping
```bash
aws entityresolution create-schema-mapping \
    --schema-name customer-schema \
    --mapped-input-fields '[
        {"fieldName":"name","type":"NAME","matchKey":"name"},
        {"fieldName":"email","type":"EMAIL_ADDRESS","matchKey":"email"},
        {"fieldName":"phone","type":"PHONE_NUMBER","matchKey":"phone"}
    ]'
```

### Create a rule-based matching workflow
```bash
aws entityresolution create-matching-workflow \
    --workflow-name customer-dedup \
    --input-source-config '[{
        "inputSourceARN":"arn:aws:glue:us-east-1:123456789012:table/mydb/customers",
        "schemaName":"customer-schema",
        "applyNormalization":true
    }]' \
    --output-source-config '[{
        "outputS3Path":"s3://my-bucket/output/",
        "output":[{"name":"name","hashed":false},{"name":"email","hashed":false}]
    }]' \
    --resolution-techniques '{
        "resolutionType":"RULE_MATCHING",
        "ruleBasedProperties":{
            "rules":[{"ruleName":"email-match","matchingKeys":["email"]}],
            "attributeMatchingModel":"ONE_TO_ONE"
        }
    }' \
    --role-arn arn:aws:iam::123456789012:role/EntityResolutionRole
```

### Run a matching job and check status
```bash
aws entityresolution start-matching-job \
    --workflow-name customer-dedup

aws entityresolution get-matching-job \
    --workflow-name customer-dedup \
    --job-id abc123def456
```

### Look up a match ID for a record
```bash
aws entityresolution get-match-id \
    --workflow-name customer-dedup \
    --record name=JohnDoe,email=john@example.com
```

### Create an ID mapping workflow
```bash
aws entityresolution create-id-mapping-workflow \
    --workflow-name cross-system-mapping \
    --input-source-config '[
        {"inputSourceARN":"arn:aws:glue:us-east-1:123456789012:table/db/source","schemaName":"source-schema","type":"SOURCE"},
        {"inputSourceARN":"arn:aws:glue:us-east-1:123456789012:table/db/target","schemaName":"target-schema","type":"TARGET"}
    ]' \
    --id-mapping-techniques '{
        "idMappingType":"RULE_BASED",
        "ruleBasedProperties":{
            "rules":[{"ruleName":"id-rule","matchingKeys":["email"]}],
            "ruleDefinitionType":"SOURCE",
            "attributeMatchingModel":"ONE_TO_ONE",
            "recordMatchingModel":"ONE_SOURCE_TO_ONE_TARGET"
        }
    }' \
    --role-arn arn:aws:iam::123456789012:role/EntityResolutionRole
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Matching Workflows | [matching-workflows.md](matching-workflows.md) | `create-matching-workflow`, `get-matching-workflow`, `list-matching-workflows`, `update-matching-workflow`, `delete-matching-workflow`, `start-matching-job`, `get-matching-job`, `list-matching-jobs`, `get-match-id`, `generate-match-id`, `batch-delete-unique-id` |
| ID Mapping | [id-mapping.md](id-mapping.md) | `create-id-mapping-workflow`, `get-id-mapping-workflow`, `list-id-mapping-workflows`, `update-id-mapping-workflow`, `delete-id-mapping-workflow`, `start-id-mapping-job`, `get-id-mapping-job`, `list-id-mapping-jobs` |
| ID Namespaces | [id-namespaces.md](id-namespaces.md) | `create-id-namespace`, `get-id-namespace`, `list-id-namespaces`, `update-id-namespace`, `delete-id-namespace` |
| Schema Mappings | [schema-mappings.md](schema-mappings.md) | `create-schema-mapping`, `get-schema-mapping`, `list-schema-mappings`, `update-schema-mapping`, `delete-schema-mapping` |
| Providers | [providers.md](providers.md) | `get-provider-service`, `list-provider-services` |
| Policies & Tags | [policies-tags.md](policies-tags.md) | `put-policy`, `get-policy`, `add-policy-statement`, `delete-policy-statement`, `tag-resource`, `untag-resource`, `list-tags-for-resource` |
