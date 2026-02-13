# Journal

### 2.1 `export-journal-to-s3`

Exports journal contents within a date and time range from a ledger into a specified Amazon S3 bucket. A maximum of two concurrent export jobs per ledger is allowed.

**Synopsis:**
```bash
aws qldb export-journal-to-s3 \
    --name <value> \
    --inclusive-start-time <value> \
    --exclusive-end-time <value> \
    --s3-export-configuration <value> \
    --role-arn <value> \
    [--output-format <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the ledger |
| `--inclusive-start-time` | **Yes** | timestamp | -- | Start of the time range (inclusive), ISO 8601 format |
| `--exclusive-end-time` | **Yes** | timestamp | -- | End of the time range (exclusive), ISO 8601 format |
| `--s3-export-configuration` | **Yes** | structure | -- | S3 bucket, prefix, and encryption configuration |
| `--role-arn` | **Yes** | string | -- | IAM role ARN with permissions to write to S3 |
| `--output-format` | No | string | `ION_BINARY` | Output format: `ION_BINARY`, `ION_TEXT`, `JSON` |

**S3 Export Configuration Structure:**
```json
{
    "Bucket": "string",
    "Prefix": "string",
    "EncryptionConfiguration": {
        "ObjectEncryptionType": "SSE_KMS|SSE_S3|NO_ENCRYPTION",
        "KmsKeyArn": "string"
    }
}
```

**Output Schema:**
```json
{
    "ExportId": "string"
}
```

---

### 2.2 `describe-journal-s3-export`

Returns information about a journal export job, including its current status, creation time, and the export parameters.

**Synopsis:**
```bash
aws qldb describe-journal-s3-export \
    --name <value> \
    --export-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the ledger |
| `--export-id` | **Yes** | string | -- | Unique ID of the export job |

**Output Schema:**
```json
{
    "ExportDescription": {
        "LedgerName": "string",
        "ExportId": "string",
        "ExportCreationTime": "timestamp",
        "Status": "IN_PROGRESS|COMPLETED|CANCELLED",
        "InclusiveStartTime": "timestamp",
        "ExclusiveEndTime": "timestamp",
        "S3ExportConfiguration": {
            "Bucket": "string",
            "Prefix": "string",
            "EncryptionConfiguration": {
                "ObjectEncryptionType": "SSE_KMS|SSE_S3|NO_ENCRYPTION",
                "KmsKeyArn": "string"
            }
        },
        "RoleArn": "string",
        "OutputFormat": "ION_BINARY|ION_TEXT|JSON"
    }
}
```

---

### 2.3 `list-journal-s3-exports`

Returns a list of all journal S3 export jobs across all ledgers in the current account and region. **Paginated operation.**

**Synopsis:**
```bash
aws qldb list-journal-s3-exports \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Maximum number of results per page (1-100) |
| `--next-token` | No | string | None | Pagination token from previous response |

**Output Schema:**
```json
{
    "JournalS3Exports": [
        {
            "LedgerName": "string",
            "ExportId": "string",
            "ExportCreationTime": "timestamp",
            "Status": "IN_PROGRESS|COMPLETED|CANCELLED",
            "InclusiveStartTime": "timestamp",
            "ExclusiveEndTime": "timestamp",
            "S3ExportConfiguration": {
                "Bucket": "string",
                "Prefix": "string",
                "EncryptionConfiguration": {
                    "ObjectEncryptionType": "SSE_KMS|SSE_S3|NO_ENCRYPTION",
                    "KmsKeyArn": "string"
                }
            },
            "RoleArn": "string",
            "OutputFormat": "ION_BINARY|ION_TEXT|JSON"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.4 `list-journal-s3-exports-for-ledger`

Returns a list of journal S3 export jobs for a specified ledger. **Paginated operation.**

**Synopsis:**
```bash
aws qldb list-journal-s3-exports-for-ledger \
    --name <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the ledger |
| `--max-results` | No | integer | None | Maximum number of results per page (1-100) |
| `--next-token` | No | string | None | Pagination token from previous response |

**Output Schema:**
```json
{
    "JournalS3Exports": [
        {
            "LedgerName": "string",
            "ExportId": "string",
            "ExportCreationTime": "timestamp",
            "Status": "IN_PROGRESS|COMPLETED|CANCELLED",
            "InclusiveStartTime": "timestamp",
            "ExclusiveEndTime": "timestamp",
            "S3ExportConfiguration": {},
            "RoleArn": "string",
            "OutputFormat": "ION_BINARY|ION_TEXT|JSON"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.5 `get-block`

Returns a block object at a specified address in a journal. Also returns a proof of the specified block for verification if `DigestTipAddress` is provided.

**Synopsis:**
```bash
aws qldb get-block \
    --name <value> \
    --block-address <value> \
    [--digest-tip-address <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the ledger |
| `--block-address` | **Yes** | structure | -- | Location of the block. Shorthand: `IonText=string` |
| `--digest-tip-address` | No | structure | None | Latest block location for proof generation. Shorthand: `IonText=string` |

**Block Address Structure:**
```json
{
    "IonText": "{strandId:\"string\",sequenceNo:integer}"
}
```

**Output Schema:**
```json
{
    "Block": {
        "IonText": "string"
    },
    "Proof": {
        "IonText": "string"
    }
}
```

---

### 2.6 `get-digest`

Returns the digest of a ledger at the latest committed block. The digest is a 256-bit hash value that uniquely represents the ledger's journal at that point in time.

**Synopsis:**
```bash
aws qldb get-digest \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the ledger |

**Output Schema:**
```json
{
    "Digest": "blob",
    "DigestTipAddress": {
        "IonText": "string"
    }
}
```

---

### 2.7 `get-revision`

Returns a revision data object for a specified document ID and block address. Also returns a proof if `DigestTipAddress` is provided for verification purposes.

**Synopsis:**
```bash
aws qldb get-revision \
    --name <value> \
    --block-address <value> \
    --document-id <value> \
    [--digest-tip-address <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the ledger |
| `--block-address` | **Yes** | structure | -- | Block address of the document revision. Shorthand: `IonText=string` |
| `--document-id` | **Yes** | string | -- | Unique ID of the document to retrieve |
| `--digest-tip-address` | No | structure | None | Latest block location for proof generation. Shorthand: `IonText=string` |

**Output Schema:**
```json
{
    "Revision": {
        "IonText": "string"
    },
    "Proof": {
        "IonText": "string"
    }
}
```
