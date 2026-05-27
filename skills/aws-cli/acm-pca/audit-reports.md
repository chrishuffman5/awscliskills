# Audit Reports

### 3.1 `create-certificate-authority-audit-report`

Creates an audit report that lists every time a certificate is issued or revoked. The report is saved to an S3 bucket.

**Synopsis:**
```bash
aws acm-pca create-certificate-authority-audit-report \
    --certificate-authority-arn <value> \
    --s3-bucket-name <value> \
    --audit-report-response-format <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-authority-arn` | **Yes** | string | -- | ARN of the CA to audit |
| `--s3-bucket-name` | **Yes** | string | -- | S3 bucket name for the report (3-255 chars) |
| `--audit-report-response-format` | **Yes** | string | -- | Report format: `JSON` or `CSV` |

**Output Schema:**
```json
{
    "AuditReportId": "string",
    "S3Key": "string"
}
```

---

### 3.2 `describe-certificate-authority-audit-report`

Returns information about the specified audit report.

**Synopsis:**
```bash
aws acm-pca describe-certificate-authority-audit-report \
    --certificate-authority-arn <value> \
    --audit-report-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-authority-arn` | **Yes** | string | -- | ARN of the CA |
| `--audit-report-id` | **Yes** | string | -- | ID of the audit report |

**Output Schema:**
```json
{
    "AuditReportStatus": "CREATING|SUCCESS|FAILED",
    "S3BucketName": "string",
    "S3Key": "string",
    "CreatedAt": "timestamp"
}
```
