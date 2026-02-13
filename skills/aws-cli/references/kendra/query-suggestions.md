# Query Suggestions

### 5.1 `get-query-suggestions`

Gets query suggestions as the user types, based on past queries and document content.

**Synopsis:**
```bash
aws kendra get-query-suggestions \
    --index-id <value> \
    --query-text <value> \
    [--max-suggestions-count <value>] \
    [--suggestion-types <value>] \
    [--attribute-suggestions-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--query-text` | **Yes** | string | -- | Partial query text to get suggestions for |
| `--max-suggestions-count` | No | integer | None | Max suggestions to return |
| `--suggestion-types` | No | list | None | Suggestion types: `QUERY`, `DOCUMENT_ATTRIBUTES` |
| `--attribute-suggestions-config` | No | structure | None | Config for attribute-based suggestions |

**Output Schema:**
```json
{
    "QuerySuggestionsId": "string",
    "Suggestions": [
        {
            "Id": "string",
            "Value": {
                "Text": {
                    "Text": "string",
                    "Highlights": [
                        {
                            "BeginOffset": "integer",
                            "EndOffset": "integer"
                        }
                    ]
                }
            },
            "SourceDocuments": [
                {
                    "DocumentId": "string",
                    "SuggestionAttributes": ["string"],
                    "AdditionalAttributes": []
                }
            ]
        }
    ]
}
```

---

### 5.2 `describe-query-suggestions-config`

Gets the query suggestions configuration for an index.

**Synopsis:**
```bash
aws kendra describe-query-suggestions-config \
    --index-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |

**Output Schema:**
```json
{
    "Mode": "ENABLED|LEARN_ONLY",
    "Status": "ACTIVE|UPDATING",
    "QueryLogLookBackWindowInDays": "integer",
    "IncludeQueriesWithoutUserInformation": "boolean",
    "MinimumNumberOfQueryingUsers": "integer",
    "MinimumQueryCount": "integer",
    "LastSuggestionsBuildTime": "timestamp",
    "LastClearTime": "timestamp",
    "TotalSuggestionsCount": "integer",
    "AttributeSuggestionsConfig": {}
}
```

---

### 5.3 `update-query-suggestions-config`

Updates the query suggestions configuration.

**Synopsis:**
```bash
aws kendra update-query-suggestions-config \
    --index-id <value> \
    [--mode <value>] \
    [--query-log-look-back-window-in-days <value>] \
    [--include-queries-without-user-information | --no-include-queries-without-user-information] \
    [--minimum-number-of-querying-users <value>] \
    [--minimum-query-count <value>] \
    [--attribute-suggestions-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--mode` | No | string | None | `ENABLED` or `LEARN_ONLY` |
| `--query-log-look-back-window-in-days` | No | integer | None | Days of query logs to use (1-180) |
| `--include-queries-without-user-information` | No | boolean | None | Include anonymous queries |
| `--minimum-number-of-querying-users` | No | integer | None | Min unique users for a suggestion |
| `--minimum-query-count` | No | integer | None | Min times a query must appear |
| `--attribute-suggestions-config` | No | structure | None | Attribute suggestions config |

**Output:** None

---

### 5.4 `clear-query-suggestions`

Clears all query suggestion history from an index.

**Synopsis:**
```bash
aws kendra clear-query-suggestions \
    --index-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |

**Output:** None

---

### 5.5 `create-query-suggestions-block-list`

Creates a block list to prevent specific queries from appearing as suggestions.

**Synopsis:**
```bash
aws kendra create-query-suggestions-block-list \
    --index-id <value> \
    --name <value> \
    --source-s3-path <value> \
    --role-arn <value> \
    [--description <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--name` | **Yes** | string | -- | Block list name (1-100 chars) |
| `--source-s3-path` | **Yes** | structure | -- | S3 path: `{Bucket: string, Key: string}` |
| `--role-arn` | **Yes** | string | -- | IAM role ARN with S3 access |
| `--description` | No | string | None | Description (0-1000 chars) |
| `--client-token` | No | string | None | Idempotency token |
| `--tags` | No | list | None | Tags (max 200) |

**Output Schema:**
```json
{
    "Id": "string"
}
```

---

### 5.6 `delete-query-suggestions-block-list`

Deletes a block list.

**Synopsis:**
```bash
aws kendra delete-query-suggestions-block-list \
    --index-id <value> \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--id` | **Yes** | string | -- | Block list ID |

**Output:** None

---

### 5.7 `describe-query-suggestions-block-list`

Gets information about a block list.

**Synopsis:**
```bash
aws kendra describe-query-suggestions-block-list \
    --index-id <value> \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--id` | **Yes** | string | -- | Block list ID |

**Output Schema:**
```json
{
    "IndexId": "string",
    "Id": "string",
    "Name": "string",
    "Description": "string",
    "Status": "ACTIVE|CREATING|DELETING|UPDATING|ACTIVE_BUT_UPDATE_FAILED|FAILED",
    "ErrorMessage": "string",
    "CreatedAt": "timestamp",
    "UpdatedAt": "timestamp",
    "SourceS3Path": {"Bucket": "string", "Key": "string"},
    "ItemCount": "integer",
    "FileSizeBytes": "long",
    "RoleArn": "string"
}
```

---

### 5.8 `list-query-suggestions-block-lists`

Lists block lists for an index. **Paginated operation.**

**Synopsis:**
```bash
aws kendra list-query-suggestions-block-lists \
    --index-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "BlockListSummaryItems": [
        {
            "Id": "string",
            "Name": "string",
            "Status": "string",
            "CreatedAt": "timestamp",
            "UpdatedAt": "timestamp",
            "ItemCount": "integer"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.9 `update-query-suggestions-block-list`

Updates a block list.

**Synopsis:**
```bash
aws kendra update-query-suggestions-block-list \
    --index-id <value> \
    --id <value> \
    [--name <value>] \
    [--description <value>] \
    [--source-s3-path <value>] \
    [--role-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--id` | **Yes** | string | -- | Block list ID |
| `--name` | No | string | None | New name |
| `--description` | No | string | None | New description |
| `--source-s3-path` | No | structure | None | New S3 path |
| `--role-arn` | No | string | None | New IAM role ARN |

**Output:** None
