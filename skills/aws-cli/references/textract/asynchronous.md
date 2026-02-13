# Asynchronous Operations

### 2.1 `start-document-analysis`

Starts asynchronous analysis of a document for text, tables, forms, queries, signatures, or layout. Documents must be in S3. Returns a JobId for polling with `get-document-analysis`.

**Synopsis:**
```bash
aws textract start-document-analysis \
    --document-location <value> \
    --feature-types <value> \
    [--client-request-token <value>] \
    [--job-tag <value>] \
    [--notification-channel <value>] \
    [--output-config <value>] \
    [--kms-key-id <value>] \
    [--queries-config <value>] \
    [--adapters-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--document-location` | **Yes** | structure | -- | S3 location of the document |
| `--feature-types` | **Yes** | list(string) | -- | Analysis types: `TABLES`, `FORMS`, `QUERIES`, `SIGNATURES`, `LAYOUT` |
| `--client-request-token` | No | string | None | Idempotent token (1-64 chars) to prevent duplicate jobs |
| `--job-tag` | No | string | None | Identifier included in SNS completion notification (1-64 chars) |
| `--notification-channel` | No | structure | None | SNS topic and IAM role for job completion notifications |
| `--output-config` | No | structure | None | S3 bucket for output results |
| `--kms-key-id` | No | string | SSE-S3 | KMS key for encrypting results (1-2048 chars) |
| `--queries-config` | No | structure | None | Custom queries configuration |
| `--adapters-config` | No | structure | None | Adapter configuration for fine-tuned extraction |

**NotificationChannel Structure:**
```json
{
    "SNSTopicArn": "string (20-1024 chars)",
    "RoleArn": "string (20-2048 chars)"
}
```

**OutputConfig Structure:**
```json
{
    "S3Bucket": "string (3-255 chars)",
    "S3Prefix": "string (1-1024 chars, default: textract_output)"
}
```

**Output Schema:**
```json
{
    "JobId": "string (1-64 chars)"
}
```

---

### 2.2 `start-document-text-detection`

Starts asynchronous text detection in a document stored in S3. Returns a JobId for polling with `get-document-text-detection`.

**Synopsis:**
```bash
aws textract start-document-text-detection \
    --document-location <value> \
    [--client-request-token <value>] \
    [--job-tag <value>] \
    [--notification-channel <value>] \
    [--output-config <value>] \
    [--kms-key-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--document-location` | **Yes** | structure | -- | S3 location of the document |
| `--client-request-token` | No | string | None | Idempotent token (1-64 chars) |
| `--job-tag` | No | string | None | Identifier for SNS notification (1-64 chars) |
| `--notification-channel` | No | structure | None | SNS topic and IAM role for notifications |
| `--output-config` | No | structure | None | S3 bucket for output results |
| `--kms-key-id` | No | string | SSE-S3 | KMS key for encryption |

**Output Schema:**
```json
{
    "JobId": "string (1-64 chars)"
}
```

---

### 2.3 `start-expense-analysis`

Starts asynchronous analysis of invoices and receipts stored in S3. Returns a JobId for polling with `get-expense-analysis`.

**Synopsis:**
```bash
aws textract start-expense-analysis \
    --document-location <value> \
    [--client-request-token <value>] \
    [--job-tag <value>] \
    [--notification-channel <value>] \
    [--output-config <value>] \
    [--kms-key-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--document-location` | **Yes** | structure | -- | S3 location of the document |
| `--client-request-token` | No | string | None | Idempotent token (1-64 chars) |
| `--job-tag` | No | string | None | Identifier for SNS notification (1-64 chars) |
| `--notification-channel` | No | structure | None | SNS topic and IAM role for notifications |
| `--output-config` | No | structure | None | S3 bucket for output results |
| `--kms-key-id` | No | string | SSE-S3 | KMS key for encryption |

**Output Schema:**
```json
{
    "JobId": "string (1-64 chars)"
}
```

---

### 2.4 `start-lending-analysis`

Starts asynchronous analysis of a lending document (mortgage packets, loan applications). Classifies, splits, and extracts information. Returns a JobId for polling with `get-lending-analysis` or `get-lending-analysis-summary`.

**Synopsis:**
```bash
aws textract start-lending-analysis \
    --document-location <value> \
    [--client-request-token <value>] \
    [--job-tag <value>] \
    [--notification-channel <value>] \
    [--output-config <value>] \
    [--kms-key-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--document-location` | **Yes** | structure | -- | S3 location of the document |
| `--client-request-token` | No | string | None | Idempotent token (1-64 chars) |
| `--job-tag` | No | string | None | Identifier for SNS notification (1-64 chars) |
| `--notification-channel` | No | structure | None | SNS topic and IAM role for notifications |
| `--output-config` | No | structure | None | S3 bucket for output results |
| `--kms-key-id` | No | string | None | KMS key for encryption (1-2048 chars) |

**Output Schema:**
```json
{
    "JobId": "string (1-64 chars)"
}
```

---

### 2.5 `get-document-analysis`

Gets the results of an asynchronous document analysis operation. Use the JobId returned by `start-document-analysis`. **Paginated operation.**

**Synopsis:**
```bash
aws textract get-document-analysis \
    --job-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID from `start-document-analysis` (1-64 chars, valid for 7 days) |
| `--max-results` | No | integer | 1000 | Max results per page (1-1000) |
| `--next-token` | No | string | None | Pagination token from previous response (1-1024 chars) |

**Output Schema:**
```json
{
    "DocumentMetadata": {
        "Pages": "integer"
    },
    "JobStatus": "IN_PROGRESS|SUCCEEDED|FAILED|PARTIAL_SUCCESS",
    "NextToken": "string",
    "Blocks": [
        {
            "BlockType": "string",
            "Confidence": "float (0-100)",
            "Text": "string",
            "TextType": "HANDWRITING|PRINTED",
            "RowIndex": "integer",
            "ColumnIndex": "integer",
            "RowSpan": "integer",
            "ColumnSpan": "integer",
            "Geometry": {
                "BoundingBox": {
                    "Width": "float",
                    "Height": "float",
                    "Left": "float",
                    "Top": "float"
                },
                "Polygon": [{"X": "float", "Y": "float"}],
                "RotationAngle": "float"
            },
            "Id": "string",
            "Relationships": [
                {
                    "Type": "VALUE|CHILD|COMPLEX_FEATURES|MERGED_CELL|TITLE|ANSWER|TABLE|TABLE_TITLE|TABLE_FOOTER",
                    "Ids": ["string"]
                }
            ],
            "EntityTypes": ["string"],
            "SelectionStatus": "SELECTED|NOT_SELECTED",
            "Page": "integer",
            "Query": {
                "Text": "string",
                "Alias": "string",
                "Pages": ["string"]
            }
        }
    ],
    "Warnings": [
        {
            "ErrorCode": "string",
            "Pages": ["integer"]
        }
    ],
    "StatusMessage": "string",
    "AnalyzeDocumentModelVersion": "string"
}
```

---

### 2.6 `get-document-text-detection`

Gets the results of an asynchronous text detection operation. Use the JobId returned by `start-document-text-detection`. **Paginated operation.**

**Synopsis:**
```bash
aws textract get-document-text-detection \
    --job-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID from `start-document-text-detection` (1-64 chars, valid for 7 days) |
| `--max-results` | No | integer | 1000 | Max results per page (1-1000) |
| `--next-token` | No | string | None | Pagination token from previous response (1-1024 chars) |

**Output Schema:**
```json
{
    "DocumentMetadata": {
        "Pages": "integer"
    },
    "JobStatus": "IN_PROGRESS|SUCCEEDED|FAILED|PARTIAL_SUCCESS",
    "NextToken": "string",
    "Blocks": [
        {
            "BlockType": "PAGE|LINE|WORD",
            "Confidence": "float (0-100)",
            "Text": "string",
            "TextType": "HANDWRITING|PRINTED",
            "Geometry": {
                "BoundingBox": {
                    "Width": "float",
                    "Height": "float",
                    "Left": "float",
                    "Top": "float"
                },
                "Polygon": [{"X": "float", "Y": "float"}],
                "RotationAngle": "float"
            },
            "Id": "string",
            "Relationships": [
                {
                    "Type": "CHILD|VALUE",
                    "Ids": ["string"]
                }
            ],
            "Page": "integer"
        }
    ],
    "Warnings": [
        {
            "ErrorCode": "string",
            "Pages": ["integer"]
        }
    ],
    "StatusMessage": "string",
    "DetectDocumentTextModelVersion": "string"
}
```

---

### 2.7 `get-expense-analysis`

Gets the results of an asynchronous expense analysis operation. Use the JobId returned by `start-expense-analysis`. **Paginated operation.**

**Synopsis:**
```bash
aws textract get-expense-analysis \
    --job-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID from `start-expense-analysis` (1-64 chars, valid for 7 days) |
| `--max-results` | No | integer | 20 | Max results per page (1-20) |
| `--next-token` | No | string | None | Pagination token from previous response (1-1024 chars) |

**Output Schema:**
```json
{
    "DocumentMetadata": {
        "Pages": "integer"
    },
    "JobStatus": "IN_PROGRESS|SUCCEEDED|FAILED|PARTIAL_SUCCESS",
    "NextToken": "string",
    "ExpenseDocuments": [
        {
            "ExpenseIndex": "integer",
            "SummaryFields": [
                {
                    "Type": {"Text": "string", "Confidence": "float"},
                    "LabelDetection": {"Text": "string", "Geometry": {}, "Confidence": "float"},
                    "ValueDetection": {"Text": "string", "Geometry": {}, "Confidence": "float"},
                    "PageNumber": "integer",
                    "Currency": {"Code": "string", "Confidence": "float"},
                    "GroupProperties": [{"Types": ["string"], "Id": "string"}]
                }
            ],
            "LineItemGroups": [
                {
                    "LineItemGroupIndex": "integer",
                    "LineItems": [
                        {
                            "LineItemExpenseFields": []
                        }
                    ]
                }
            ],
            "Blocks": []
        }
    ],
    "Warnings": [
        {
            "ErrorCode": "string",
            "Pages": ["integer"]
        }
    ],
    "StatusMessage": "string",
    "AnalyzeExpenseModelVersion": "string"
}
```

---

### 2.8 `get-lending-analysis`

Gets the results of an asynchronous lending document analysis. Use the JobId returned by `start-lending-analysis`. **Paginated operation.**

**Synopsis:**
```bash
aws textract get-lending-analysis \
    --job-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID from `start-lending-analysis` (1-64 chars, valid for 7 days) |
| `--max-results` | No | integer | 30 | Max results per page (1-30) |
| `--next-token` | No | string | None | Pagination token from previous response (1-1024 chars) |

**Output Schema:**
```json
{
    "DocumentMetadata": {
        "Pages": "integer"
    },
    "JobStatus": "IN_PROGRESS|SUCCEEDED|FAILED|PARTIAL_SUCCESS",
    "NextToken": "string",
    "Results": [
        {
            "Page": "integer",
            "PageClassification": {
                "PageType": [
                    {"Value": "string", "Confidence": "float"}
                ],
                "PageNumber": [
                    {"Value": "string", "Confidence": "float"}
                ]
            },
            "Extractions": [
                {
                    "LendingDocument": {
                        "LendingFields": [
                            {
                                "Type": "string",
                                "KeyDetection": {
                                    "Text": "string",
                                    "SelectionStatus": "SELECTED|NOT_SELECTED",
                                    "Geometry": {},
                                    "Confidence": "float"
                                },
                                "ValueDetections": [
                                    {
                                        "Text": "string",
                                        "SelectionStatus": "SELECTED|NOT_SELECTED",
                                        "Geometry": {},
                                        "Confidence": "float"
                                    }
                                ]
                            }
                        ],
                        "SignatureDetections": [
                            {"Confidence": "float", "Geometry": {}}
                        ]
                    },
                    "ExpenseDocument": {},
                    "IdentityDocument": {}
                }
            ]
        }
    ],
    "Warnings": [
        {
            "ErrorCode": "string",
            "Pages": ["integer"]
        }
    ],
    "StatusMessage": "string",
    "AnalyzeLendingModelVersion": "string"
}
```

---

### 2.9 `get-lending-analysis-summary`

Gets summary information about a lending document analysis job. Use the JobId returned by `start-lending-analysis`. Returns document classification and split information without full extraction results.

**Synopsis:**
```bash
aws textract get-lending-analysis-summary \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID from `start-lending-analysis` (1-64 chars, valid for 7 days) |

**Output Schema:**
```json
{
    "DocumentMetadata": {
        "Pages": "integer"
    },
    "JobStatus": "IN_PROGRESS|SUCCEEDED|FAILED|PARTIAL_SUCCESS",
    "Summary": {
        "DocumentGroups": [
            {
                "Type": "string",
                "SplitDocuments": [
                    {
                        "Index": "integer",
                        "Pages": ["integer"]
                    }
                ],
                "DetectedSignatures": [
                    {"Page": "integer"}
                ],
                "UndetectedSignatures": [
                    {"Page": "integer"}
                ]
            }
        ],
        "UndetectedDocumentTypes": ["string"]
    },
    "Warnings": [
        {
            "ErrorCode": "string",
            "Pages": ["integer"]
        }
    ],
    "StatusMessage": "string",
    "AnalyzeLendingModelVersion": "string"
}
```
