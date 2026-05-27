# Assessment Reports

### 4.1 `create-assessment-report`

Creates an assessment report for a specified assessment.

**Synopsis:**
```bash
aws auditmanager create-assessment-report \
    --name <value> \
    --assessment-id <value> \
    [--description <value>] \
    [--query-statement <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Report name (1-300 chars) |
| `--assessment-id` | **Yes** | string | -- | Assessment ID (UUID) |
| `--description` | No | string | None | Report description (max 1000 chars) |
| `--query-statement` | No | string | None | SQL query for evidence finder |

**Output Schema:**
```json
{
    "assessmentReport": {
        "id": "string",
        "name": "string",
        "description": "string",
        "awsAccountId": "string",
        "assessmentId": "string",
        "assessmentName": "string",
        "author": "string",
        "status": "COMPLETE|IN_PROGRESS|FAILED",
        "creationTime": "timestamp"
    }
}
```

---

### 4.2 `delete-assessment-report`

Deletes an assessment report.

**Synopsis:**
```bash
aws auditmanager delete-assessment-report \
    --assessment-id <value> \
    --assessment-report-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-id` | **Yes** | string | -- | Assessment ID |
| `--assessment-report-id` | **Yes** | string | -- | Report ID to delete |

**Output Schema:** Empty on success.

---

### 4.3 `list-assessment-reports`

Returns a list of assessment reports. **Paginated.**

**Synopsis:**
```bash
aws auditmanager list-assessment-reports \
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
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "assessmentReports": [
        {
            "id": "string",
            "name": "string",
            "description": "string",
            "assessmentId": "string",
            "assessmentName": "string",
            "author": "string",
            "status": "COMPLETE|IN_PROGRESS|FAILED",
            "creationTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 4.4 `get-assessment-report-url`

Returns the presigned URL to download an assessment report.

**Synopsis:**
```bash
aws auditmanager get-assessment-report-url \
    --assessment-report-id <value> \
    --assessment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-report-id` | **Yes** | string | -- | Report ID |
| `--assessment-id` | **Yes** | string | -- | Assessment ID |

**Output Schema:**
```json
{
    "preSignedUrl": {
        "hyperlinkName": "string",
        "link": "string"
    }
}
```

---

### 4.5 `associate-assessment-report-evidence-folder`

Associates an evidence folder with an assessment report.

**Synopsis:**
```bash
aws auditmanager associate-assessment-report-evidence-folder \
    --assessment-id <value> \
    --evidence-folder-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-id` | **Yes** | string | -- | Assessment ID |
| `--evidence-folder-id` | **Yes** | string | -- | Evidence folder ID |

**Output Schema:** Empty on success.

---

### 4.6 `disassociate-assessment-report-evidence-folder`

Disassociates an evidence folder from an assessment report.

**Synopsis:**
```bash
aws auditmanager disassociate-assessment-report-evidence-folder \
    --assessment-id <value> \
    --evidence-folder-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-id` | **Yes** | string | -- | Assessment ID |
| `--evidence-folder-id` | **Yes** | string | -- | Evidence folder ID |

**Output Schema:** Empty on success.

---

### 4.7 `batch-associate-assessment-report-evidence`

Associates specific evidence items with an assessment report.

**Synopsis:**
```bash
aws auditmanager batch-associate-assessment-report-evidence \
    --assessment-id <value> \
    --evidence-folder-id <value> \
    --evidence-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-id` | **Yes** | string | -- | Assessment ID |
| `--evidence-folder-id` | **Yes** | string | -- | Evidence folder ID |
| `--evidence-ids` | **Yes** | list(string) | -- | Evidence item IDs to associate |

**Output Schema:**
```json
{
    "evidenceIds": ["string"],
    "errors": [
        {
            "evidenceId": "string",
            "errorCode": "string",
            "errorMessage": "string"
        }
    ]
}
```

---

### 4.8 `batch-disassociate-assessment-report-evidence`

Disassociates specific evidence items from an assessment report.

**Synopsis:**
```bash
aws auditmanager batch-disassociate-assessment-report-evidence \
    --assessment-id <value> \
    --evidence-folder-id <value> \
    --evidence-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-id` | **Yes** | string | -- | Assessment ID |
| `--evidence-folder-id` | **Yes** | string | -- | Evidence folder ID |
| `--evidence-ids` | **Yes** | list(string) | -- | Evidence item IDs to disassociate |

**Output Schema:**
```json
{
    "evidenceIds": ["string"],
    "errors": [
        {
            "evidenceId": "string",
            "errorCode": "string",
            "errorMessage": "string"
        }
    ]
}
```

---

### 4.9 `validate-assessment-report-integrity`

Validates the integrity of an assessment report stored in S3.

**Synopsis:**
```bash
aws auditmanager validate-assessment-report-integrity \
    --s3-relative-path <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--s3-relative-path` | **Yes** | string | -- | S3 path of the assessment report |

**Output Schema:**
```json
{
    "signatureValid": true|false,
    "signatureAlgorithm": "string",
    "signatureDateTime": "string",
    "signatureKeyId": "string",
    "validationErrors": ["string"]
}
```
