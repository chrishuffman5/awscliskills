# Classifiers

### 7.1 `create-classifier`

Creates a classifier. Specify exactly one of the classifier types.

**Synopsis:**
```bash
aws glue create-classifier \
    [--grok-classifier <value>] \
    [--xml-classifier <value>] \
    [--json-classifier <value>] \
    [--csv-classifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--grok-classifier` | No* | structure | -- | Grok classifier. Shorthand: `Classification=string,Name=string,GrokPattern=string,CustomPatterns=string` |
| `--xml-classifier` | No* | structure | -- | XML classifier. Shorthand: `Classification=string,Name=string,RowTag=string` |
| `--json-classifier` | No* | structure | -- | JSON classifier. Shorthand: `Name=string,JsonPath=string` |
| `--csv-classifier` | No* | structure | -- | CSV classifier. Shorthand: `Name=string,Delimiter=string,QuoteSymbol=string,ContainsHeader=UNKNOWN|PRESENT|ABSENT,Header=string,string,DisableValueTrimming=boolean,AllowSingleColumn=boolean,CustomDatatypeConfigured=boolean,CustomDatatypes=string,string,Serde=OpenCSVSerDe|LazySimpleSerDe|None` |

*Exactly one classifier type is required.

No output on success.

---

### 7.2 `delete-classifier`

Deletes a classifier.

**Synopsis:**
```bash
aws glue delete-classifier \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Classifier name |

No output on success.

---

### 7.3 `get-classifier`

Retrieves a classifier.

**Synopsis:**
```bash
aws glue get-classifier \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Classifier name |

**Output Schema:**
```json
{
    "Classifier": {
        "GrokClassifier": {
            "Name": "string",
            "Classification": "string",
            "CreationTime": "timestamp",
            "LastUpdated": "timestamp",
            "Version": "long",
            "GrokPattern": "string",
            "CustomPatterns": "string"
        },
        "XMLClassifier": {
            "Name": "string",
            "Classification": "string",
            "CreationTime": "timestamp",
            "LastUpdated": "timestamp",
            "Version": "long",
            "RowTag": "string"
        },
        "JsonClassifier": {
            "Name": "string",
            "JsonPath": "string",
            "CreationTime": "timestamp",
            "LastUpdated": "timestamp",
            "Version": "long"
        },
        "CsvClassifier": {
            "Name": "string",
            "CreationTime": "timestamp",
            "LastUpdated": "timestamp",
            "Version": "long",
            "Delimiter": "string",
            "QuoteSymbol": "string",
            "ContainsHeader": "UNKNOWN|PRESENT|ABSENT",
            "Header": ["string"],
            "DisableValueTrimming": "boolean",
            "AllowSingleColumn": "boolean",
            "CustomDatatypeConfigured": "boolean",
            "CustomDatatypes": ["string"],
            "Serde": "OpenCSVSerDe|LazySimpleSerDe|None"
        }
    }
}
```

---

### 7.4 `get-classifiers`

Retrieves all classifiers. **Paginated operation.**

**Synopsis:**
```bash
aws glue get-classifiers \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "Classifiers": ["<Classifier structure>"],
    "NextToken": "string"
}
```

---

### 7.5 `update-classifier`

Updates a classifier. Specify the same classifier type as the original.

**Synopsis:**
```bash
aws glue update-classifier \
    [--grok-classifier <value>] \
    [--xml-classifier <value>] \
    [--json-classifier <value>] \
    [--csv-classifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--grok-classifier` | No* | structure | -- | Updated grok classifier. Shorthand: `Name=string,Classification=string,GrokPattern=string,CustomPatterns=string` |
| `--xml-classifier` | No* | structure | -- | Updated XML classifier. Shorthand: `Name=string,Classification=string,RowTag=string` |
| `--json-classifier` | No* | structure | -- | Updated JSON classifier. Shorthand: `Name=string,JsonPath=string` |
| `--csv-classifier` | No* | structure | -- | Updated CSV classifier |

*Exactly one classifier type is required.

No output on success.
