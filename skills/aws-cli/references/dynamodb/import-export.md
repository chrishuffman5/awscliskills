# Import / Export

### 12.1 `export-table-to-point-in-time`

Exports table data to an S3 bucket. Supports full and incremental exports.

**Synopsis:**
```bash
aws dynamodb export-table-to-point-in-time \
    --table-arn <value> \
    --s3-bucket <value> \
    [--export-time <value>] \
    [--client-token <value>] \
    [--s3-bucket-owner <value>] \
    [--s3-prefix <value>] \
    [--s3-sse-algorithm <value>] \
    [--s3-sse-kms-key-id <value>] \
    [--export-format <value>] \
    [--export-type <value>] \
    [--incremental-export-specification <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-arn` | **Yes** | string | -- | Table ARN (1-1024 chars) |
| `--s3-bucket` | **Yes** | string | -- | S3 bucket name (max 255 chars) |
| `--export-time` | No | timestamp | -- | Point in time to export from |
| `--client-token` | No | string | -- | Idempotency token (valid 8 hours) |
| `--s3-bucket-owner` | No | string | -- | S3 bucket owner account ID (12 digits) |
| `--s3-prefix` | No | string | -- | S3 key prefix (max 1024 chars) |
| `--s3-sse-algorithm` | No | string | -- | `AES256` or `KMS` |
| `--s3-sse-kms-key-id` | No | string | -- | KMS key ID (1-2048 chars) |
| `--export-format` | No | string | `DYNAMODB_JSON` | `DYNAMODB_JSON` or `ION` |
| `--export-type` | No | string | `FULL_EXPORT` | `FULL_EXPORT` or `INCREMENTAL_EXPORT` |
| `--incremental-export-specification` | No | structure | -- | `ExportFromTime`, `ExportToTime`, `ExportViewType` (NEW_IMAGE or NEW_AND_OLD_IMAGES) |

**Output Schema:**
```json
{
    "ExportDescription": {
        "ExportArn": "string",
        "ExportStatus": "IN_PROGRESS|COMPLETED|FAILED",
        "StartTime": "timestamp",
        "EndTime": "timestamp",
        "ExportManifest": "string",
        "TableArn": "string",
        "TableId": "string",
        "ExportTime": "timestamp",
        "ClientToken": "string",
        "S3Bucket": "string",
        "S3BucketOwner": "string",
        "S3Prefix": "string",
        "S3SseAlgorithm": "AES256|KMS",
        "S3SseKmsKeyId": "string",
        "FailureCode": "string",
        "FailureMessage": "string",
        "ExportFormat": "DYNAMODB_JSON|ION",
        "BilledSizeBytes": "long",
        "ItemCount": "long",
        "ExportType": "FULL_EXPORT|INCREMENTAL_EXPORT",
        "IncrementalExportSpecification": {}
    }
}
```

---

### 12.2 `describe-export`

Describes an existing table export.

**Synopsis:**
```bash
aws dynamodb describe-export \
    --export-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--export-arn` | **Yes** | string | -- | Export ARN (37-1024 chars) |

**Output Schema:** Same as `export-table-to-point-in-time`.

---

### 12.3 `list-exports`

Lists completed and in-progress table exports. **Paginated operation.**

**Synopsis:**
```bash
aws dynamodb list-exports \
    [--table-arn <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-arn` | No | string | -- | Filter by table ARN |
| `--max-results` | No | integer | -- | Max results per page (1-25) |
| `--next-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{
    "ExportSummaries": [
        {
            "ExportArn": "string",
            "ExportStatus": "IN_PROGRESS|COMPLETED|FAILED",
            "ExportType": "FULL_EXPORT|INCREMENTAL_EXPORT"
        }
    ],
    "NextToken": "string"
}
```

---

### 12.4 `import-table`

Imports data from S3 into a new DynamoDB table. Supports DynamoDB JSON, ION, and CSV formats.

**Synopsis:**
```bash
aws dynamodb import-table \
    --s3-bucket-source <value> \
    --input-format <value> \
    --table-creation-parameters <value> \
    [--client-token <value>] \
    [--input-format-options <value>] \
    [--input-compression-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--s3-bucket-source` | **Yes** | structure | -- | `S3Bucket` (required), optional `S3BucketOwner`, `S3KeyPrefix` |
| `--input-format` | **Yes** | string | -- | `DYNAMODB_JSON`, `ION`, or `CSV` |
| `--table-creation-parameters` | **Yes** | structure | -- | `TableName`, `AttributeDefinitions`, `KeySchema` (required), optional billing/throughput/encryption/GSI settings |
| `--client-token` | No | string | -- | Idempotency token |
| `--input-format-options` | No | structure | -- | CSV options: `Csv={Delimiter=string,HeaderList=[string,...]}` |
| `--input-compression-type` | No | string | `NONE` | `GZIP`, `ZSTD`, or `NONE` |

**Output Schema:**
```json
{
    "ImportTableDescription": {
        "ImportArn": "string",
        "ImportStatus": "IN_PROGRESS|COMPLETED|CANCELLING|CANCELLED|FAILED",
        "TableArn": "string",
        "TableId": "string",
        "ClientToken": "string",
        "S3BucketSource": {},
        "ErrorCount": "long",
        "CloudWatchLogGroupArn": "string",
        "InputFormat": "DYNAMODB_JSON|ION|CSV",
        "InputFormatOptions": {},
        "InputCompressionType": "GZIP|ZSTD|NONE",
        "TableCreationParameters": {},
        "StartTime": "timestamp",
        "EndTime": "timestamp",
        "ProcessedSizeBytes": "long",
        "ProcessedItemCount": "long",
        "ImportedItemCount": "long",
        "FailureCode": "string",
        "FailureMessage": "string"
    }
}
```

---

### 12.5 `describe-import`

Describes an existing table import.

**Synopsis:**
```bash
aws dynamodb describe-import \
    --import-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--import-arn` | **Yes** | string | -- | Import ARN (37-1024 chars) |

**Output Schema:** Same as `import-table`.

---

### 12.6 `list-imports`

Lists completed and in-progress table imports. **Paginated operation.**

**Synopsis:**
```bash
aws dynamodb list-imports \
    [--table-arn <value>] \
    [--page-size <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-arn` | No | string | -- | Filter by table ARN |
| `--page-size` | No | integer | -- | Max results per page (1-25) |
| `--next-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{
    "ImportSummaryList": [
        {
            "ImportArn": "string",
            "ImportStatus": "IN_PROGRESS|COMPLETED|CANCELLING|CANCELLED|FAILED",
            "TableArn": "string",
            "S3BucketSource": {},
            "CloudWatchLogGroupArn": "string",
            "InputFormat": "DYNAMODB_JSON|ION|CSV",
            "StartTime": "timestamp",
            "EndTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---
