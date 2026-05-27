# Reports

### 1.1 `put-report-definition`

Creates a new Cost and Usage Report definition. The report will be delivered to the specified S3 bucket.

**Synopsis:**
```bash
aws cur put-report-definition \
    --report-definition <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--report-definition` | **Yes** | structure | -- | Report definition object (JSON or `file://`). See structure below |
| `--tags` | No | list | None | Tags for the report (max 200) |

**ReportDefinition Structure:**
```json
{
    "ReportName": "string",
    "TimeUnit": "HOURLY|DAILY|MONTHLY",
    "Format": "textORcsv|Parquet",
    "Compression": "ZIP|GZIP|Parquet",
    "AdditionalSchemaElements": ["RESOURCES|SPLIT_COST_ALLOCATION_DATA|MANUAL_DISCOUNT_COMPATIBILITY"],
    "S3Bucket": "string",
    "S3Prefix": "string",
    "S3Region": "string",
    "AdditionalArtifacts": ["REDSHIFT|QUICKSIGHT|ATHENA"],
    "RefreshClosedReports": true|false,
    "ReportVersioning": "CREATE_NEW_REPORT|OVERWRITE_REPORT",
    "BillingViewArn": "string"
}
```

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `ReportName` | **Yes** | string | Unique report name (max 256 chars) |
| `TimeUnit` | **Yes** | string | `HOURLY`, `DAILY`, or `MONTHLY` |
| `Format` | **Yes** | string | `textORcsv` or `Parquet` |
| `Compression` | **Yes** | string | `ZIP`, `GZIP`, or `Parquet` |
| `AdditionalSchemaElements` | **Yes** | list(string) | Content: `RESOURCES`, `SPLIT_COST_ALLOCATION_DATA`, `MANUAL_DISCOUNT_COMPATIBILITY` |
| `S3Bucket` | **Yes** | string | S3 bucket name (max 256 chars) |
| `S3Prefix` | **Yes** | string | S3 key prefix (max 256 chars) |
| `S3Region` | **Yes** | string | AWS region of the S3 bucket |
| `AdditionalArtifacts` | No | list(string) | `REDSHIFT`, `QUICKSIGHT`, `ATHENA` |
| `RefreshClosedReports` | No | boolean | Refresh reports with retroactive charges |
| `ReportVersioning` | No | string | `CREATE_NEW_REPORT` or `OVERWRITE_REPORT` |
| `BillingViewArn` | No | string | ARN of billing view (max 128 chars) |

**Output Schema:**
```json
{}
```

---

### 1.2 `delete-report-definition`

Deletes a Cost and Usage Report definition.

**Synopsis:**
```bash
aws cur delete-report-definition \
    --report-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--report-name` | **Yes** | string | -- | Name of the report to delete (max 256 chars) |

**Output Schema:**
```json
{
    "ResponseMessage": "string"
}
```

---

### 1.3 `describe-report-definitions`

Lists all Cost and Usage Report definitions in the account. **Paginated.**

**Synopsis:**
```bash
aws cur describe-report-definitions \
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
| `--page-size` | No | integer | None | Items per API call (max 5) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ReportDefinitions": [
        {
            "ReportName": "string",
            "TimeUnit": "HOURLY|DAILY|MONTHLY",
            "Format": "textORcsv|Parquet",
            "Compression": "ZIP|GZIP|Parquet",
            "AdditionalSchemaElements": ["string"],
            "S3Bucket": "string",
            "S3Prefix": "string",
            "S3Region": "string",
            "AdditionalArtifacts": ["string"],
            "RefreshClosedReports": "boolean",
            "ReportVersioning": "CREATE_NEW_REPORT|OVERWRITE_REPORT",
            "BillingViewArn": "string",
            "ReportStatus": {
                "lastDelivery": "string",
                "lastStatus": "SUCCESS|ERROR_PERMISSIONS|ERROR_NO_BUCKET"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 1.4 `modify-report-definition`

Modifies an existing Cost and Usage Report definition. You must provide the full updated report definition.

**Synopsis:**
```bash
aws cur modify-report-definition \
    --report-name <value> \
    --report-definition <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--report-name` | **Yes** | string | -- | Name of the report to modify (max 256 chars) |
| `--report-definition` | **Yes** | structure | -- | Complete updated report definition |

**Output Schema:**
```json
{}
```
