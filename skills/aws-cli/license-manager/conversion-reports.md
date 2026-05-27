# Conversion Tasks & Report Generators

### 6.1 `create-license-conversion-task-for-resource`

Creates a license type conversion task for a resource (e.g., converting an EC2 instance between license types).

**Synopsis:**
```bash
aws license-manager create-license-conversion-task-for-resource \
    --resource-arn <value> \
    --source-license-context <value> \
    --destination-license-context <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to convert (max 2048 chars) |
| `--source-license-context` | **Yes** | structure | -- | Source license type info (`UsageOperation`, `ProductCodes`) |
| `--destination-license-context` | **Yes** | structure | -- | Destination license type info (`UsageOperation`, `ProductCodes`) |

**License Context Structure:**
```json
{
    "UsageOperation": "string",
    "ProductCodes": [
        {
            "ProductCodeId": "string",
            "ProductCodeType": "marketplace"
        }
    ]
}
```

**Output Schema:**
```json
{
    "LicenseConversionTaskId": "string"
}
```

---

### 6.2 `get-license-conversion-task`

Gets details of a license conversion task.

**Synopsis:**
```bash
aws license-manager get-license-conversion-task \
    --license-conversion-task-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--license-conversion-task-id` | **Yes** | string | -- | ID of the conversion task |

**Output Schema:**
```json
{
    "LicenseConversionTaskId": "string",
    "ResourceArn": "string",
    "SourceLicenseContext": {
        "UsageOperation": "string",
        "ProductCodes": []
    },
    "DestinationLicenseContext": {
        "UsageOperation": "string",
        "ProductCodes": []
    },
    "StatusMessage": "string",
    "Status": "IN_PROGRESS|SUCCEEDED|FAILED",
    "StartTime": "timestamp",
    "LicenseConversionTime": "timestamp",
    "EndTime": "timestamp"
}
```

---

### 6.3 `list-license-conversion-tasks`

Lists license conversion tasks. **Paginated operation.**

**Synopsis:**
```bash
aws license-manager list-license-conversion-tasks \
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
| `--filters` | No | list | None | Filters: `ResourceArn`, `Status` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "LicenseConversionTasks": [
        {
            "LicenseConversionTaskId": "string",
            "ResourceArn": "string",
            "SourceLicenseContext": {},
            "DestinationLicenseContext": {},
            "Status": "IN_PROGRESS|SUCCEEDED|FAILED",
            "StatusMessage": "string",
            "StartTime": "timestamp",
            "LicenseConversionTime": "timestamp",
            "EndTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.4 `create-license-manager-report-generator`

Creates a report generator for license configuration or asset group usage reports.

**Synopsis:**
```bash
aws license-manager create-license-manager-report-generator \
    --report-generator-name <value> \
    --type <value> \
    --report-context <value> \
    --report-frequency <value> \
    --client-token <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--report-generator-name` | **Yes** | string | -- | Report generator name (1-100 chars) |
| `--type` | **Yes** | list(string) | -- | Report types: `LicenseConfigurationSummaryReport`, `LicenseConfigurationUsageReport`, `LicenseAssetGroupUsageReport` |
| `--report-context` | **Yes** | structure | -- | License configuration or asset group ARNs plus date range |
| `--report-frequency` | **Yes** | structure | -- | Frequency: `value=1, period=DAY\|WEEK\|MONTH\|ONE_TIME` |
| `--client-token` | **Yes** | string | -- | Idempotency token (1-36 chars) |
| `--description` | No | string | None | Description |
| `--tags` | No | list | None | Tags (Key/Value pairs) |

**Report Context Structure:**
```json
{
    "licenseConfigurationArns": ["string"],
    "licenseAssetGroupArns": ["string"],
    "reportStartDate": "timestamp",
    "reportEndDate": "timestamp"
}
```

**Output Schema:**
```json
{
    "LicenseManagerReportGeneratorArn": "string"
}
```

---

### 6.5 `delete-license-manager-report-generator`

Deletes a report generator.

**Synopsis:**
```bash
aws license-manager delete-license-manager-report-generator \
    --license-manager-report-generator-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--license-manager-report-generator-arn` | **Yes** | string | -- | ARN of the report generator |

**Output:** None

---

### 6.6 `get-license-manager-report-generator`

Gets details of a report generator.

**Synopsis:**
```bash
aws license-manager get-license-manager-report-generator \
    --license-manager-report-generator-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--license-manager-report-generator-arn` | **Yes** | string | -- | ARN of the report generator |

**Output Schema:**
```json
{
    "ReportGenerator": {
        "ReportGeneratorName": "string",
        "ReportType": ["string"],
        "ReportContext": {
            "licenseConfigurationArns": ["string"],
            "licenseAssetGroupArns": ["string"]
        },
        "ReportFrequency": {
            "value": "integer",
            "period": "DAY|WEEK|MONTH|ONE_TIME"
        },
        "LicenseManagerReportGeneratorArn": "string",
        "LastRunStatus": "string",
        "LastRunFailureReason": "string",
        "LastReportGenerationTime": "string",
        "ReportCreatorAccount": "string",
        "Description": "string",
        "S3Location": {
            "bucket": "string",
            "keyPrefix": "string"
        },
        "CreateTime": "string",
        "Tags": []
    }
}
```

---

### 6.7 `list-license-manager-report-generators`

Lists report generators. **Paginated operation.**

**Synopsis:**
```bash
aws license-manager list-license-manager-report-generators \
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
| `--filters` | No | list | None | Filters: `LicenseConfigurationArn` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ReportGenerators": [],
    "NextToken": "string"
}
```

---

### 6.8 `update-license-manager-report-generator`

Updates a report generator.

**Synopsis:**
```bash
aws license-manager update-license-manager-report-generator \
    --license-manager-report-generator-arn <value> \
    --report-generator-name <value> \
    --type <value> \
    --report-context <value> \
    --report-frequency <value> \
    --client-token <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--license-manager-report-generator-arn` | **Yes** | string | -- | ARN of the report generator |
| `--report-generator-name` | **Yes** | string | -- | Report generator name |
| `--type` | **Yes** | list(string) | -- | Report types |
| `--report-context` | **Yes** | structure | -- | Report context |
| `--report-frequency` | **Yes** | structure | -- | Report frequency |
| `--client-token` | **Yes** | string | -- | Idempotency token |
| `--description` | No | string | None | Description |

**Output:** None
