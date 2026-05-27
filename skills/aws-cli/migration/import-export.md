# Import & Export

## Import

### 9.1 `start-import`

Starts a new import task from a CSV file in S3.

**Synopsis:**
```bash
aws mgn start-import \
    --s3-bucket-source <value> \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--s3-bucket-source` | **Yes** | structure | -- | S3 bucket source (see below) |
| `--client-token` | No | string | None | Client token (max 64 chars) |
| `--tags` | No | map | None | Tags (max 50) |

**S3 Bucket Source Structure:**
```json
{
    "s3Bucket": "string",
    "s3Key": "string",
    "s3BucketOwner": "string"
}
```

Shorthand: `s3Bucket=string,s3Key=string,s3BucketOwner=string`

**Output Schema:**
```json
{
    "importTask": {
        "importID": "string",
        "arn": "string",
        "s3BucketSource": {
            "s3Bucket": "string",
            "s3Key": "string",
            "s3BucketOwner": "string"
        },
        "creationDateTime": "string",
        "endDateTime": "string",
        "status": "PENDING|STARTED|FAILED|SUCCEEDED",
        "progressPercentage": "float",
        "summary": {
            "waves": {
                "createdCount": "long",
                "modifiedCount": "long"
            },
            "applications": {
                "createdCount": "long",
                "modifiedCount": "long"
            },
            "servers": {
                "createdCount": "long",
                "modifiedCount": "long"
            }
        },
        "tags": {"key": "value"}
    }
}
```

---

### 9.2 `list-imports`

Lists import tasks. **Paginated.**

**Synopsis:**
```bash
aws mgn list-imports \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | structure | None | Filters: `importIDs=["string"]` (max 10) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "items": [
        {
            "importID": "string",
            "arn": "string",
            "s3BucketSource": {
                "s3Bucket": "string",
                "s3Key": "string",
                "s3BucketOwner": "string"
            },
            "creationDateTime": "string",
            "endDateTime": "string",
            "status": "PENDING|STARTED|FAILED|SUCCEEDED",
            "progressPercentage": "float",
            "summary": {
                "waves": {"createdCount": "long", "modifiedCount": "long"},
                "applications": {"createdCount": "long", "modifiedCount": "long"},
                "servers": {"createdCount": "long", "modifiedCount": "long"}
            },
            "tags": {"key": "value"}
        }
    ],
    "nextToken": "string"
}
```

---

### 9.3 `list-import-errors`

Lists errors for a specific import task. **Paginated.**

**Synopsis:**
```bash
aws mgn list-import-errors \
    --import-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--import-id` | **Yes** | string | -- | Import ID (pattern: `import-[0-9a-zA-Z]{17}`) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "items": [
        {
            "errorDateTime": "string",
            "errorType": "VALIDATION_ERROR|PROCESSING_ERROR",
            "errorData": {
                "sourceServerID": "string",
                "applicationID": "string",
                "waveID": "string",
                "ec2LaunchTemplateID": "string",
                "rowNumber": "long",
                "rawError": "string",
                "accountID": "string"
            }
        }
    ],
    "nextToken": "string"
}
```

---

## Export

### 9.4 `start-export`

Starts a new export task to an S3 bucket.

**Synopsis:**
```bash
aws mgn start-export \
    --s3-bucket <value> \
    --s3-key <value> \
    [--s3-bucket-owner <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--s3-bucket` | **Yes** | string | -- | S3 bucket name |
| `--s3-key` | **Yes** | string | -- | S3 key (must end with `.csv`) |
| `--s3-bucket-owner` | No | string | None | S3 bucket owner account ID (12 digits) |
| `--tags` | No | map | None | Tags (max 50) |

**Output Schema:**
```json
{
    "exportTask": {
        "exportID": "string",
        "arn": "string",
        "s3Bucket": "string",
        "s3Key": "string",
        "s3BucketOwner": "string",
        "creationDateTime": "string",
        "endDateTime": "string",
        "status": "PENDING|STARTED|FAILED|SUCCEEDED",
        "progressPercentage": "float",
        "summary": {
            "serversCount": "long",
            "applicationsCount": "long",
            "wavesCount": "long"
        },
        "tags": {"key": "value"}
    }
}
```

---

### 9.5 `list-exports`

Lists export tasks. **Paginated.**

**Synopsis:**
```bash
aws mgn list-exports \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | structure | None | Filters: `exportIDs=["string"]` (max 10) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "items": [
        {
            "exportID": "string",
            "arn": "string",
            "s3Bucket": "string",
            "s3Key": "string",
            "s3BucketOwner": "string",
            "creationDateTime": "string",
            "endDateTime": "string",
            "status": "PENDING|STARTED|FAILED|SUCCEEDED",
            "progressPercentage": "float",
            "summary": {
                "serversCount": "long",
                "applicationsCount": "long",
                "wavesCount": "long"
            },
            "tags": {"key": "value"}
        }
    ],
    "nextToken": "string"
}
```

---

### 9.6 `list-export-errors`

Lists errors for a specific export task. **Paginated.**

**Synopsis:**
```bash
aws mgn list-export-errors \
    --export-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--export-id` | **Yes** | string | -- | Export ID (pattern: `export-[0-9a-zA-Z]{17}`) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "items": [
        {
            "errorDateTime": "string",
            "errorData": {
                "rawError": "string"
            }
        }
    ],
    "nextToken": "string"
}
```
