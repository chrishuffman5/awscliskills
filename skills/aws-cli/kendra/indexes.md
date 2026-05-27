# Indexes

### 1.1 `create-index`

Creates a Kendra index. The index provides search over ingested documents.

**Synopsis:**
```bash
aws kendra create-index \
    --name <value> \
    --role-arn <value> \
    [--edition <value>] \
    [--server-side-encryption-configuration <value>] \
    [--description <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--user-token-configurations <value>] \
    [--user-context-policy <value>] \
    [--user-group-resolution-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Index name (1-1000 chars) |
| `--role-arn` | **Yes** | string | -- | IAM role ARN with CloudWatch access |
| `--edition` | No | string | `ENTERPRISE_EDITION` | `DEVELOPER_EDITION`, `ENTERPRISE_EDITION`, or `GEN_AI_ENTERPRISE_EDITION` |
| `--server-side-encryption-configuration` | No | structure | None | KMS key for encryption: `{KmsKeyId: string}` |
| `--description` | No | string | None | Index description (0-1000 chars) |
| `--client-token` | No | string | None | Idempotency token (1-100 chars) |
| `--tags` | No | list | None | Tags (max 200): `[{Key:string, Value:string}]` |
| `--user-token-configurations` | No | list | None | User token config for access control (max 1) |
| `--user-context-policy` | No | string | None | `ATTRIBUTE_FILTER` or `USER_TOKEN` |
| `--user-group-resolution-configuration` | No | structure | None | IAM Identity Center config |

**Output Schema:**
```json
{
    "Id": "string (36 chars)"
}
```

---

### 1.2 `delete-index`

Deletes a Kendra index. Does not delete associated data source connectors or FAQ resources.

**Synopsis:**
```bash
aws kendra delete-index \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Index ID (36 chars) |

**Output:** None

---

### 1.3 `describe-index`

Gets information about a Kendra index including status, capacity, and configuration.

**Synopsis:**
```bash
aws kendra describe-index \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Index ID (36 chars) |

**Output Schema:**
```json
{
    "Name": "string",
    "Id": "string",
    "Edition": "DEVELOPER_EDITION|ENTERPRISE_EDITION|GEN_AI_ENTERPRISE_EDITION",
    "RoleArn": "string",
    "ServerSideEncryptionConfiguration": {
        "KmsKeyId": "string"
    },
    "Status": "CREATING|ACTIVE|DELETING|FAILED|UPDATING|SYSTEM_UPDATING",
    "Description": "string",
    "CreatedAt": "timestamp",
    "UpdatedAt": "timestamp",
    "DocumentMetadataConfigurations": [
        {
            "Name": "string",
            "Type": "STRING_VALUE|STRING_LIST_VALUE|LONG_VALUE|DATE_VALUE",
            "Relevance": {
                "Freshness": "boolean",
                "Importance": "integer (1-10)",
                "Duration": "string",
                "RankOrder": "ASCENDING|DESCENDING",
                "ValueImportanceMap": {}
            },
            "Search": {
                "Facetable": "boolean",
                "Searchable": "boolean",
                "Displayable": "boolean",
                "Sortable": "boolean"
            }
        }
    ],
    "IndexStatistics": {
        "FaqStatistics": {
            "IndexedQuestionAnswersCount": "integer"
        },
        "TextDocumentStatistics": {
            "IndexedTextDocumentsCount": "integer",
            "IndexedTextBytes": "long"
        }
    },
    "ErrorMessage": "string",
    "CapacityUnits": {
        "StorageCapacityUnits": "integer",
        "QueryCapacityUnits": "integer"
    },
    "UserTokenConfigurations": [],
    "UserContextPolicy": "ATTRIBUTE_FILTER|USER_TOKEN",
    "UserGroupResolutionConfiguration": {
        "UserGroupResolutionMode": "AWS_SSO|NONE"
    }
}
```

---

### 1.4 `list-indices`

Lists Kendra indexes in the account. **Paginated operation.**

**Synopsis:**
```bash
aws kendra list-indices \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "IndexConfigurationSummaryItems": [
        {
            "Name": "string",
            "Id": "string",
            "Edition": "DEVELOPER_EDITION|ENTERPRISE_EDITION|GEN_AI_ENTERPRISE_EDITION",
            "CreatedAt": "timestamp",
            "UpdatedAt": "timestamp",
            "Status": "CREATING|ACTIVE|DELETING|FAILED|UPDATING|SYSTEM_UPDATING"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `update-index`

Updates index settings including capacity, document metadata configurations, and user context policy.

**Synopsis:**
```bash
aws kendra update-index \
    --id <value> \
    [--name <value>] \
    [--role-arn <value>] \
    [--description <value>] \
    [--document-metadata-configuration-updates <value>] \
    [--capacity-units <value>] \
    [--user-token-configurations <value>] \
    [--user-context-policy <value>] \
    [--user-group-resolution-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Index ID (36 chars) |
| `--name` | No | string | None | New index name |
| `--role-arn` | No | string | None | New IAM role ARN |
| `--description` | No | string | None | New description |
| `--document-metadata-configuration-updates` | No | list | None | Document metadata field configurations |
| `--capacity-units` | No | structure | None | `{StorageCapacityUnits: int, QueryCapacityUnits: int}` |
| `--user-token-configurations` | No | list | None | User token configuration |
| `--user-context-policy` | No | string | None | `ATTRIBUTE_FILTER` or `USER_TOKEN` |
| `--user-group-resolution-configuration` | No | structure | None | IAM Identity Center config |

**Output:** None
