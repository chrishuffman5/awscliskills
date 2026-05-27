# Thesauri

### 4.1 `create-thesaurus`

Creates a thesaurus for synonym matching in search queries.

**Synopsis:**
```bash
aws kendra create-thesaurus \
    --index-id <value> \
    --name <value> \
    --role-arn <value> \
    --source-s3-path <value> \
    [--description <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--name` | **Yes** | string | -- | Thesaurus name (1-100 chars) |
| `--role-arn` | **Yes** | string | -- | IAM role ARN with S3 access |
| `--source-s3-path` | **Yes** | structure | -- | S3 path: `{Bucket: string, Key: string}` |
| `--description` | No | string | None | Description (0-1000 chars) |
| `--tags` | No | list | None | Tags (max 200) |
| `--client-token` | No | string | None | Idempotency token (1-100 chars) |

**Output Schema:**
```json
{
    "Id": "string"
}
```

---

### 4.2 `delete-thesaurus`

Deletes a thesaurus from an index.

**Synopsis:**
```bash
aws kendra delete-thesaurus \
    --id <value> \
    --index-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Thesaurus ID |
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |

**Output:** None

---

### 4.3 `describe-thesaurus`

Gets information about a thesaurus.

**Synopsis:**
```bash
aws kendra describe-thesaurus \
    --id <value> \
    --index-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Thesaurus ID |
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |

**Output Schema:**
```json
{
    "Id": "string",
    "IndexId": "string",
    "Name": "string",
    "Description": "string",
    "Status": "CREATING|ACTIVE|DELETING|UPDATING|ACTIVE_BUT_UPDATE_FAILED|FAILED",
    "ErrorMessage": "string",
    "CreatedAt": "timestamp",
    "UpdatedAt": "timestamp",
    "RoleArn": "string",
    "SourceS3Path": {
        "Bucket": "string",
        "Key": "string"
    },
    "FileSizeBytes": "long",
    "TermCount": "long",
    "SynonymRuleCount": "long"
}
```

---

### 4.4 `list-thesauri`

Lists thesauri for an index. **Paginated operation.**

**Synopsis:**
```bash
aws kendra list-thesauri \
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
    "ThesaurusSummaryItems": [
        {
            "Id": "string",
            "Name": "string",
            "Status": "string",
            "CreatedAt": "timestamp",
            "UpdatedAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.5 `update-thesaurus`

Updates a thesaurus.

**Synopsis:**
```bash
aws kendra update-thesaurus \
    --id <value> \
    --index-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--role-arn <value>] \
    [--source-s3-path <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Thesaurus ID |
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--name` | No | string | None | New name |
| `--description` | No | string | None | New description |
| `--role-arn` | No | string | None | New IAM role ARN |
| `--source-s3-path` | No | structure | None | New S3 path |

**Output:** None
