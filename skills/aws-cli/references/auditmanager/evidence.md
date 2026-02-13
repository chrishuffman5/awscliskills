# Evidence

### 5.1 `get-evidence`

Returns a specific evidence item.

**Synopsis:**
```bash
aws auditmanager get-evidence \
    --assessment-id <value> \
    --control-set-id <value> \
    --evidence-folder-id <value> \
    --evidence-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-id` | **Yes** | string | -- | Assessment ID |
| `--control-set-id` | **Yes** | string | -- | Control set ID |
| `--evidence-folder-id` | **Yes** | string | -- | Evidence folder ID |
| `--evidence-id` | **Yes** | string | -- | Evidence ID |

**Output Schema:**
```json
{
    "evidence": {
        "dataSource": "string",
        "evidenceAwsAccountId": "string",
        "time": "timestamp",
        "eventSource": "string",
        "eventName": "string",
        "evidenceByType": "string",
        "resourcesIncluded": [
            {
                "arn": "string",
                "value": "string",
                "complianceCheck": "string"
            }
        ],
        "attributes": {"key": "value"},
        "iamId": "string",
        "complianceCheck": "string",
        "awsOrganization": "string",
        "awsAccountId": "string",
        "evidenceFolderId": "string",
        "id": "string",
        "assessmentReportSelection": "string"
    }
}
```

---

### 5.2 `get-evidence-by-evidence-folder`

Returns all evidence items within an evidence folder. **Paginated.**

**Synopsis:**
```bash
aws auditmanager get-evidence-by-evidence-folder \
    --assessment-id <value> \
    --control-set-id <value> \
    --evidence-folder-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-id` | **Yes** | string | -- | Assessment ID |
| `--control-set-id` | **Yes** | string | -- | Control set ID |
| `--evidence-folder-id` | **Yes** | string | -- | Evidence folder ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "evidence": [
        {
            "dataSource": "string",
            "evidenceAwsAccountId": "string",
            "time": "timestamp",
            "eventSource": "string",
            "eventName": "string",
            "evidenceByType": "string",
            "resourcesIncluded": [],
            "attributes": {},
            "iamId": "string",
            "complianceCheck": "string",
            "evidenceFolderId": "string",
            "id": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 5.3 `get-evidence-folder`

Returns an evidence folder by ID.

**Synopsis:**
```bash
aws auditmanager get-evidence-folder \
    --assessment-id <value> \
    --control-set-id <value> \
    --evidence-folder-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-id` | **Yes** | string | -- | Assessment ID |
| `--control-set-id` | **Yes** | string | -- | Control set ID |
| `--evidence-folder-id` | **Yes** | string | -- | Evidence folder ID |

**Output Schema:**
```json
{
    "evidenceFolder": {
        "name": "string",
        "date": "timestamp",
        "assessmentId": "string",
        "controlSetId": "string",
        "controlId": "string",
        "id": "string",
        "dataSource": "string",
        "author": "string",
        "totalEvidence": "integer",
        "assessmentReportSelectionCount": "integer",
        "controlName": "string",
        "evidenceResourcesIncludedCount": "integer",
        "evidenceByTypeConfigurationDataCount": "integer",
        "evidenceByTypeManualCount": "integer",
        "evidenceByTypeComplianceCheckCount": "integer",
        "evidenceByTypeComplianceCheckIssuesCount": "integer",
        "evidenceByTypeUserActivityCount": "integer",
        "evidenceAwsServiceSourceCount": "integer"
    }
}
```

---

### 5.4 `get-evidence-folders-by-assessment`

Returns evidence folders for an assessment. **Paginated.**

**Synopsis:**
```bash
aws auditmanager get-evidence-folders-by-assessment \
    --assessment-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-id` | **Yes** | string | -- | Assessment ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "evidenceFolders": [
        {
            "name": "string",
            "date": "timestamp",
            "assessmentId": "string",
            "controlSetId": "string",
            "controlId": "string",
            "id": "string",
            "dataSource": "string",
            "author": "string",
            "totalEvidence": "integer",
            "controlName": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 5.5 `get-evidence-folders-by-assessment-control`

Returns evidence folders for a specific control in an assessment. **Paginated.**

**Synopsis:**
```bash
aws auditmanager get-evidence-folders-by-assessment-control \
    --assessment-id <value> \
    --control-set-id <value> \
    --control-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-id` | **Yes** | string | -- | Assessment ID |
| `--control-set-id` | **Yes** | string | -- | Control set ID |
| `--control-id` | **Yes** | string | -- | Control ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:** Same as `get-evidence-folders-by-assessment`.

---

### 5.6 `batch-import-evidence-to-assessment-control`

Imports manual evidence to a specific control in an assessment.

**Synopsis:**
```bash
aws auditmanager batch-import-evidence-to-assessment-control \
    --assessment-id <value> \
    --control-set-id <value> \
    --control-id <value> \
    --manual-evidence <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-id` | **Yes** | string | -- | Assessment ID |
| `--control-set-id` | **Yes** | string | -- | Control set ID |
| `--control-id` | **Yes** | string | -- | Control ID |
| `--manual-evidence` | **Yes** | list | -- | Evidence items. Shorthand: `s3ResourcePath=string` or `textEvidence=string` or `evidenceFileName=string` |

**Output Schema:**
```json
{
    "errors": [
        {
            "manualEvidence": {
                "s3ResourcePath": "string",
                "textEvidence": "string",
                "evidenceFileName": "string"
            },
            "errorCode": "string",
            "errorMessage": "string"
        }
    ]
}
```

---

### 5.7 `get-evidence-file-upload-url`

Returns a presigned URL for uploading evidence files.

**Synopsis:**
```bash
aws auditmanager get-evidence-file-upload-url \
    --file-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-name` | **Yes** | string | -- | File name for the evidence upload |

**Output Schema:**
```json
{
    "evidenceFileName": "string",
    "uploadUrl": "string"
}
```
