# Synchronous Operations

### 1.1 `detect-document-text`

Detects text in a document. Returns PAGE, LINE, and WORD blocks with confidence scores and geometry data.

**Synopsis:**
```bash
aws textract detect-document-text \
    --document <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--document` | **Yes** | structure | -- | Input document as bytes or S3 object. Supports JPEG, PNG, PDF (single-page), TIFF. Max 5 MB |

**Document Structure:**
```json
{
    "Bytes": "blob (max 10485760)",
    "S3Object": {
        "Bucket": "string (3-255 chars)",
        "Name": "string (1-1024 chars)",
        "Version": "string (1-1024 chars, optional)"
    }
}
```

**Output Schema:**
```json
{
    "DocumentMetadata": {
        "Pages": "integer"
    },
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
                "Polygon": [
                    {
                        "X": "float",
                        "Y": "float"
                    }
                ],
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
    "DetectDocumentTextModelVersion": "string"
}
```

---

### 1.2 `analyze-document`

Analyzes a document for relationships between detected items. Supports tables, forms, queries, signatures, and layout detection.

**Synopsis:**
```bash
aws textract analyze-document \
    --document <value> \
    --feature-types <value> \
    [--human-loop-config <value>] \
    [--queries-config <value>] \
    [--adapters-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--document` | **Yes** | structure | -- | Input document as bytes or S3 object. Max 5 MB |
| `--feature-types` | **Yes** | list(string) | -- | Analysis types: `TABLES`, `FORMS`, `QUERIES`, `SIGNATURES`, `LAYOUT` |
| `--human-loop-config` | No | structure | None | Human-in-the-loop workflow config for Amazon A2I |
| `--queries-config` | No | structure | None | Custom queries to run against the document |
| `--adapters-config` | No | structure | None | Custom adapter configuration for fine-tuned extraction |

**HumanLoopConfig Structure:**
```json
{
    "HumanLoopName": "string (1-63 chars)",
    "FlowDefinitionArn": "string (max 256 chars)",
    "DataAttributes": {
        "ContentClassifiers": ["FreeOfPersonallyIdentifiableInformation|FreeOfAdultContent"]
    }
}
```

**QueriesConfig Structure:**
```json
{
    "Queries": [
        {
            "Text": "string (1-200 chars)",
            "Alias": "string (1-200 chars)",
            "Pages": ["string (e.g., '1-3', '4-*')"]
        }
    ]
}
```

**AdaptersConfig Structure:**
```json
{
    "Adapters": [
        {
            "AdapterId": "string (12-1011 chars)",
            "Version": "string (1-128 chars)",
            "Pages": ["string"]
        }
    ]
}
```

**Output Schema:**
```json
{
    "DocumentMetadata": {
        "Pages": "integer"
    },
    "Blocks": [
        {
            "BlockType": "PAGE|LINE|WORD|KEY_VALUE_SET|TABLE|CELL|MERGED_CELL|SELECTION_ELEMENT|SIGNATURE|QUERY|QUERY_RESULT|LAYOUT_TEXT|LAYOUT_TITLE|LAYOUT_HEADER|LAYOUT_FOOTER|LAYOUT_SECTION_HEADER|LAYOUT_PAGE_NUMBER|LAYOUT_LIST|LAYOUT_FIGURE|LAYOUT_TABLE|LAYOUT_KEY_VALUE",
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
                "Polygon": [
                    {
                        "X": "float",
                        "Y": "float"
                    }
                ],
                "RotationAngle": "float"
            },
            "Id": "string",
            "Relationships": [
                {
                    "Type": "VALUE|CHILD|COMPLEX_FEATURES|MERGED_CELL|TITLE|ANSWER|TABLE|TABLE_TITLE|TABLE_FOOTER",
                    "Ids": ["string"]
                }
            ],
            "EntityTypes": ["KEY|VALUE|COLUMN_HEADER|TABLE_TITLE|TABLE_FOOTER|TABLE_SECTION_TITLE|TABLE_SUMMARY|STRUCTURED_TABLE|SEMI_STRUCTURED_TABLE"],
            "SelectionStatus": "SELECTED|NOT_SELECTED",
            "Page": "integer",
            "Query": {
                "Text": "string",
                "Alias": "string",
                "Pages": ["string"]
            }
        }
    ],
    "HumanLoopActivationOutput": {
        "HumanLoopArn": "string",
        "HumanLoopActivationReasons": ["string"],
        "HumanLoopActivationConditionsEvaluationResults": "string"
    },
    "AnalyzeDocumentModelVersion": "string"
}
```

---

### 1.3 `analyze-expense`

Analyzes an invoice or receipt document. Extracts vendor name, receipt items, prices, and other expense-related data.

**Synopsis:**
```bash
aws textract analyze-expense \
    --document <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--document` | **Yes** | structure | -- | Input document as bytes or S3 object. Supports JPEG, PNG, PDF, TIFF. Max 5 MB |

**Output Schema:**
```json
{
    "DocumentMetadata": {
        "Pages": "integer"
    },
    "ExpenseDocuments": [
        {
            "ExpenseIndex": "integer",
            "SummaryFields": [
                {
                    "Type": {
                        "Text": "string",
                        "Confidence": "float (0-100)"
                    },
                    "LabelDetection": {
                        "Text": "string",
                        "Geometry": {
                            "BoundingBox": {},
                            "Polygon": [],
                            "RotationAngle": "float"
                        },
                        "Confidence": "float (0-100)"
                    },
                    "ValueDetection": {
                        "Text": "string",
                        "Geometry": {},
                        "Confidence": "float (0-100)"
                    },
                    "PageNumber": "integer",
                    "Currency": {
                        "Code": "USD|EUR|GBP|CAD|INR|JPY|CHF|AUD|CNY|BZR|SEK|HKD",
                        "Confidence": "float (0-100)"
                    },
                    "GroupProperties": [
                        {
                            "Types": ["string"],
                            "Id": "string"
                        }
                    ]
                }
            ],
            "LineItemGroups": [
                {
                    "LineItemGroupIndex": "integer",
                    "LineItems": [
                        {
                            "LineItemExpenseFields": [
                                {
                                    "Type": {},
                                    "LabelDetection": {},
                                    "ValueDetection": {},
                                    "PageNumber": "integer",
                                    "Currency": {},
                                    "GroupProperties": []
                                }
                            ]
                        }
                    ]
                }
            ],
            "Blocks": []
        }
    ]
}
```

---

### 1.4 `analyze-id`

Analyzes identity documents (driver licenses, passports). Extracts specific fields such as first name, last name, date of birth, and document number.

**Synopsis:**
```bash
aws textract analyze-id \
    --document-pages <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--document-pages` | **Yes** | list | -- | List of document pages (1-2 items). Each item is a Document structure with Bytes or S3Object |

**Output Schema:**
```json
{
    "IdentityDocuments": [
        {
            "DocumentIndex": "integer",
            "IdentityDocumentFields": [
                {
                    "Type": {
                        "Text": "string",
                        "NormalizedValue": {
                            "Value": "string",
                            "ValueType": "DATE"
                        },
                        "Confidence": "float (0-100)"
                    },
                    "ValueDetection": {
                        "Text": "string",
                        "NormalizedValue": {
                            "Value": "string",
                            "ValueType": "DATE"
                        },
                        "Confidence": "float (0-100)"
                    }
                }
            ],
            "Blocks": [
                {
                    "BlockType": "PAGE|LINE|WORD",
                    "Confidence": "float",
                    "Text": "string",
                    "TextType": "PRINTED|HANDWRITING",
                    "Geometry": {},
                    "Id": "string",
                    "Relationships": [],
                    "Page": "integer"
                }
            ]
        }
    ],
    "DocumentMetadata": {
        "Pages": "integer"
    },
    "AnalyzeIDModelVersion": "string"
}
```
