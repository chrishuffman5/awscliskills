# Findings Reports

### 4.1 `create-findings-report`

Creates a findings report and exports it to an S3 bucket.

**Synopsis:**
```bash
aws inspector2 create-findings-report \
    --report-format <value> \
    --s3-destination <value> \
    [--filter-criteria <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--report-format` | **Yes** | string | -- | Report format: `CSV`, `JSON` |
| `--s3-destination` | **Yes** | structure | -- | S3 destination. Shorthand: `bucketName=string,keyPrefix=string,kmsKeyArn=string` |
| `--filter-criteria` | No | structure | None | Filter criteria (same as `list-findings`). Only `ACTIVE` findings by default |

**S3 Destination Structure:**
```json
{
    "bucketName": "string",
    "keyPrefix": "string",
    "kmsKeyArn": "string"
}
```

**Output Schema:**
```json
{
    "reportId": "string"
}
```

---

### 4.2 `cancel-findings-report`

Cancels a findings report generation.

**Synopsis:**
```bash
aws inspector2 cancel-findings-report \
    --report-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--report-id` | **Yes** | string | -- | ID of the report to cancel |

**Output Schema:**
```json
{
    "reportId": "string"
}
```

---

### 4.3 `get-findings-report-status`

Gets the status of a findings report.

**Synopsis:**
```bash
aws inspector2 get-findings-report-status \
    [--report-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--report-id` | No | string | None | ID of the report to check |

**Output Schema:**
```json
{
    "reportId": "string",
    "status": "SUCCEEDED|IN_PROGRESS|CANCELLED|FAILED",
    "errorCode": "INTERNAL_ERROR|INVALID_PERMISSIONS|NO_FINDINGS_FOUND|BUCKET_NOT_FOUND|INCOMPATIBLE_BUCKET_REGION|MALFORMED_KMS_KEY",
    "errorMessage": "string",
    "destination": {
        "bucketName": "string",
        "keyPrefix": "string",
        "kmsKeyArn": "string"
    },
    "filterCriteria": {}
}
```

---

### 4.4 `create-sbom-export`

Creates an SBOM (Software Bill of Materials) export and sends it to an S3 bucket.

**Synopsis:**
```bash
aws inspector2 create-sbom-export \
    --report-format <value> \
    --s3-destination <value> \
    [--resource-filter-criteria <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--report-format` | **Yes** | string | -- | SBOM format: `CYCLONEDX_1_4`, `SPDX_2_3` |
| `--s3-destination` | **Yes** | structure | -- | S3 destination. Shorthand: `bucketName=string,keyPrefix=string,kmsKeyArn=string` |
| `--resource-filter-criteria` | No | structure | None | Filter criteria for resources to include |

**Output Schema:**
```json
{
    "reportId": "string"
}
```

---

### 4.5 `cancel-sbom-export`

Cancels an SBOM export.

**Synopsis:**
```bash
aws inspector2 cancel-sbom-export \
    --report-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--report-id` | **Yes** | string | -- | ID of the SBOM export to cancel |

**Output Schema:**
```json
{
    "reportId": "string"
}
```

---

### 4.6 `get-sbom-export`

Gets the status of an SBOM export.

**Synopsis:**
```bash
aws inspector2 get-sbom-export \
    --report-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--report-id` | **Yes** | string | -- | ID of the SBOM export to check |

**Output Schema:**
```json
{
    "reportId": "string",
    "status": "SUCCEEDED|IN_PROGRESS|CANCELLED|FAILED",
    "errorCode": "INTERNAL_ERROR|INVALID_PERMISSIONS|NO_FINDINGS_FOUND|BUCKET_NOT_FOUND|INCOMPATIBLE_BUCKET_REGION|MALFORMED_KMS_KEY",
    "errorMessage": "string",
    "s3Destination": {
        "bucketName": "string",
        "keyPrefix": "string",
        "kmsKeyArn": "string"
    },
    "filterCriteria": {},
    "format": "CYCLONEDX_1_4|SPDX_2_3"
}
```
