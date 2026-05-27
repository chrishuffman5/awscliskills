# Real-Time Operations

### 1.1 `detect-entities-v2`

Detects medical entities in unstructured clinical text. Returns entities with categories, types, traits, attributes, and confidence scores.

**Synopsis:**
```bash
aws comprehendmedical detect-entities-v2 \
    --text <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--text` | **Yes** | string | -- | Clinical text to analyze (1-20,000 chars, UTF-8) |

**Output Schema:**
```json
{
    "Entities": [
        {
            "Id": "integer",
            "BeginOffset": "integer",
            "EndOffset": "integer",
            "Score": "float (0-1)",
            "Text": "string",
            "Category": "MEDICATION|MEDICAL_CONDITION|PROTECTED_HEALTH_INFORMATION|TEST_TREATMENT_PROCEDURE|ANATOMY|TIME_EXPRESSION|BEHAVIORAL_ENVIRONMENTAL_SOCIAL",
            "Type": "string",
            "Traits": [
                {
                    "Name": "SIGN|SYMPTOM|DIAGNOSIS|NEGATION|PERTAINS_TO_FAMILY|HYPOTHETICAL|LOW_CONFIDENCE|PAST_HISTORY|FUTURE",
                    "Score": "float"
                }
            ],
            "Attributes": [
                {
                    "Type": "string",
                    "Score": "float",
                    "RelationshipScore": "float",
                    "RelationshipType": "string",
                    "Id": "integer",
                    "BeginOffset": "integer",
                    "EndOffset": "integer",
                    "Text": "string",
                    "Category": "string",
                    "Traits": []
                }
            ]
        }
    ],
    "UnmappedAttributes": [
        {
            "Type": "string",
            "Attribute": {}
        }
    ],
    "PaginationToken": "string",
    "ModelVersion": "string"
}
```

---

### 1.2 `detect-phi`

Detects Protected Health Information (PHI) entities in clinical text. PHI includes names, addresses, dates, phone numbers, emails, IDs, and other identifying information.

**Synopsis:**
```bash
aws comprehendmedical detect-phi \
    --text <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--text` | **Yes** | string | -- | Clinical text to analyze (1-20,000 chars, UTF-8) |

**Output Schema:**
```json
{
    "Entities": [
        {
            "Id": "integer",
            "BeginOffset": "integer",
            "EndOffset": "integer",
            "Score": "float (0-1)",
            "Text": "string",
            "Category": "PROTECTED_HEALTH_INFORMATION",
            "Type": "NAME|AGE|DATE|PHONE_OR_FAX|EMAIL|IDENTIFIER|ID|URL|ADDRESS|PROFESSION|CONTACT_POINT",
            "Traits": [
                {
                    "Name": "string",
                    "Score": "float"
                }
            ],
            "Attributes": []
        }
    ],
    "PaginationToken": "string",
    "ModelVersion": "string"
}
```

---

### 1.3 `infer-icd10-cm`

Detects medical conditions in text and maps them to ICD-10-CM codes.

**Synopsis:**
```bash
aws comprehendmedical infer-icd10-cm \
    --text <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--text` | **Yes** | string | -- | Clinical text to analyze (1-10,000 chars) |

**Output Schema:**
```json
{
    "Entities": [
        {
            "Id": "integer",
            "Text": "string",
            "Category": "MEDICAL_CONDITION",
            "Type": "DX_NAME|TIME_EXPRESSION",
            "Score": "float",
            "BeginOffset": "integer",
            "EndOffset": "integer",
            "Attributes": [
                {
                    "Type": "ACUITY|DIRECTION|SYSTEM_ORGAN_SITE|QUALITY|QUANTITY|TIME_TO_DX_NAME|TIME_EXPRESSION",
                    "Score": "float",
                    "RelationshipScore": "float",
                    "Id": "integer",
                    "BeginOffset": "integer",
                    "EndOffset": "integer",
                    "Text": "string",
                    "Traits": [],
                    "Category": "string",
                    "RelationshipType": "string"
                }
            ],
            "Traits": [
                {
                    "Name": "NEGATION|DIAGNOSIS|SIGN|SYMPTOM|PERTAINS_TO_FAMILY|HYPOTHETICAL|LOW_CONFIDENCE",
                    "Score": "float"
                }
            ],
            "ICD10CMConcepts": [
                {
                    "Description": "string",
                    "Code": "string",
                    "Score": "float"
                }
            ]
        }
    ],
    "PaginationToken": "string",
    "ModelVersion": "string"
}
```

---

### 1.4 `infer-rx-norm`

Detects medications in text and maps them to RxNorm concept codes.

**Synopsis:**
```bash
aws comprehendmedical infer-rx-norm \
    --text <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--text` | **Yes** | string | -- | Clinical text to analyze (1-10,000 chars) |

**Output Schema:**
```json
{
    "Entities": [
        {
            "Id": "integer",
            "Text": "string",
            "Category": "MEDICATION",
            "Type": "BRAND_NAME|GENERIC_NAME",
            "Score": "float",
            "BeginOffset": "integer",
            "EndOffset": "integer",
            "Attributes": [
                {
                    "Type": "DOSAGE|DURATION|FORM|FREQUENCY|RATE|ROUTE_OR_MODE|STRENGTH",
                    "Score": "float",
                    "RelationshipScore": "float",
                    "Id": "integer",
                    "BeginOffset": "integer",
                    "EndOffset": "integer",
                    "Text": "string",
                    "Traits": []
                }
            ],
            "Traits": [
                {
                    "Name": "NEGATION|PAST_HISTORY",
                    "Score": "float"
                }
            ],
            "RxNormConcepts": [
                {
                    "Description": "string",
                    "Code": "string",
                    "Score": "float"
                }
            ]
        }
    ],
    "PaginationToken": "string",
    "ModelVersion": "string"
}
```

---

### 1.5 `infer-snomedct`

Detects medical entities in text and maps them to SNOMED CT concepts.

**Synopsis:**
```bash
aws comprehendmedical infer-snomedct \
    --text <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--text` | **Yes** | string | -- | Clinical text to analyze (1-10,000 chars) |

**Output Schema:**
```json
{
    "Entities": [
        {
            "Id": "integer",
            "Text": "string",
            "Category": "MEDICAL_CONDITION|ANATOMY|TEST_TREATMENT_PROCEDURE",
            "Type": "string",
            "Score": "float",
            "BeginOffset": "integer",
            "EndOffset": "integer",
            "Attributes": [],
            "Traits": [
                {
                    "Name": "string",
                    "Score": "float"
                }
            ],
            "SNOMEDCTConcepts": [
                {
                    "Description": "string",
                    "Code": "string",
                    "Score": "float"
                }
            ]
        }
    ],
    "PaginationToken": "string",
    "ModelVersion": "string",
    "SNOMEDCTDetails": {
        "Edition": "string",
        "Language": "string",
        "VersionDate": "string"
    },
    "Characters": {
        "OriginalTextCharacters": "integer"
    }
}
```
