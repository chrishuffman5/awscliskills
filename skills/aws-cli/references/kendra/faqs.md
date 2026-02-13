# FAQs

### 3.1 `create-faq`

Creates an FAQ from a file stored in S3.

**Synopsis:**
```bash
aws kendra create-faq \
    --index-id <value> \
    --name <value> \
    --s3-path <value> \
    --role-arn <value> \
    [--description <value>] \
    [--tags <value>] \
    [--file-format <value>] \
    [--client-token <value>] \
    [--language-code <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |
| `--name` | **Yes** | string | -- | FAQ name (1-100 chars) |
| `--s3-path` | **Yes** | structure | -- | S3 path: `{Bucket: string, Key: string}` |
| `--role-arn` | **Yes** | string | -- | IAM role ARN with S3 access |
| `--description` | No | string | None | FAQ description (0-1000 chars) |
| `--tags` | No | list | None | Tags (max 200) |
| `--file-format` | No | string | `CSV` | File format: `CSV`, `CSV_WITH_HEADER`, `JSON` |
| `--client-token` | No | string | None | Idempotency token (1-100 chars) |
| `--language-code` | No | string | `en` | Language code (2-10 chars) |

**Output Schema:**
```json
{
    "Id": "string"
}
```

---

### 3.2 `delete-faq`

Removes an FAQ from a Kendra index.

**Synopsis:**
```bash
aws kendra delete-faq \
    --id <value> \
    --index-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | FAQ ID |
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |

**Output:** None

---

### 3.3 `describe-faq`

Gets information about a FAQ.

**Synopsis:**
```bash
aws kendra describe-faq \
    --id <value> \
    --index-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | FAQ ID |
| `--index-id` | **Yes** | string | -- | Index ID (36 chars) |

**Output Schema:**
```json
{
    "Id": "string",
    "IndexId": "string",
    "Name": "string",
    "Description": "string",
    "CreatedAt": "timestamp",
    "UpdatedAt": "timestamp",
    "S3Path": {
        "Bucket": "string",
        "Key": "string"
    },
    "Status": "CREATING|UPDATING|ACTIVE|DELETING|FAILED",
    "RoleArn": "string",
    "ErrorMessage": "string",
    "FileFormat": "CSV|CSV_WITH_HEADER|JSON",
    "LanguageCode": "string"
}
```

---

### 3.4 `list-faqs`

Lists FAQs for an index. **Paginated operation.**

**Synopsis:**
```bash
aws kendra list-faqs \
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
    "FaqSummaryItems": [
        {
            "Id": "string",
            "Name": "string",
            "Status": "CREATING|UPDATING|ACTIVE|DELETING|FAILED",
            "CreatedAt": "timestamp",
            "UpdatedAt": "timestamp",
            "FileFormat": "CSV|CSV_WITH_HEADER|JSON",
            "LanguageCode": "string"
        }
    ],
    "NextToken": "string"
}
```
