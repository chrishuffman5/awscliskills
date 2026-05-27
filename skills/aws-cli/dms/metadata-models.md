# Metadata Models

Metadata model operations support schema conversion workflows within migration projects. These commands manage the assessment, conversion, creation, import, and export of metadata models.

### 8.1 `start-metadata-model-assessment`

Starts an assessment of a metadata model.

**Synopsis:**
```bash
aws dms start-metadata-model-assessment \
    --migration-project-identifier <value> \
    --selection-rules <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--migration-project-identifier` | **Yes** | string | -- | Migration project identifier or ARN |
| `--selection-rules` | **Yes** | string | -- | JSON selection rules specifying schemas/tables |

**Output Schema:**
```json
{
    "RequestIdentifier": "string"
}
```

---

### 8.2 `start-metadata-model-conversion`

Starts the conversion of a metadata model.

**Synopsis:**
```bash
aws dms start-metadata-model-conversion \
    --migration-project-identifier <value> \
    --selection-rules <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--migration-project-identifier` | **Yes** | string | -- | Migration project identifier or ARN |
| `--selection-rules` | **Yes** | string | -- | JSON selection rules |

**Output Schema:**
```json
{
    "RequestIdentifier": "string"
}
```

---

### 8.3 `cancel-metadata-model-conversion`

Cancels a metadata model conversion that is in progress.

**Synopsis:**
```bash
aws dms cancel-metadata-model-conversion \
    --migration-project-identifier <value> \
    --selection-rules <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--migration-project-identifier` | **Yes** | string | -- | Migration project identifier or ARN |
| `--selection-rules` | **Yes** | string | -- | JSON selection rules |

**Output Schema:**
```json
{
    "RequestIdentifier": "string"
}
```

---

### 8.4 `start-metadata-model-creation`

Starts the creation of a metadata model.

**Synopsis:**
```bash
aws dms start-metadata-model-creation \
    --migration-project-identifier <value> \
    --selection-rules <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--migration-project-identifier` | **Yes** | string | -- | Migration project identifier or ARN |
| `--selection-rules` | **Yes** | string | -- | JSON selection rules |

**Output Schema:**
```json
{
    "RequestIdentifier": "string"
}
```

---

### 8.5 `cancel-metadata-model-creation`

Cancels a metadata model creation that is in progress.

**Synopsis:**
```bash
aws dms cancel-metadata-model-creation \
    --migration-project-identifier <value> \
    --selection-rules <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--migration-project-identifier` | **Yes** | string | -- | Migration project identifier or ARN |
| `--selection-rules` | **Yes** | string | -- | JSON selection rules |

**Output Schema:**
```json
{
    "RequestIdentifier": "string"
}
```

---

### 8.6 `start-metadata-model-import`

Starts the import of a metadata model.

**Synopsis:**
```bash
aws dms start-metadata-model-import \
    --migration-project-identifier <value> \
    --selection-rules <value> \
    --origin <value> \
    [--refresh | --no-refresh] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--migration-project-identifier` | **Yes** | string | -- | Migration project identifier or ARN |
| `--selection-rules` | **Yes** | string | -- | JSON selection rules |
| `--origin` | **Yes** | string | -- | Import origin: `SOURCE` or `TARGET` |
| `--refresh` | No | boolean | -- | Refresh the metadata model |

**Output Schema:**
```json
{
    "RequestIdentifier": "string"
}
```

---

### 8.7 `start-metadata-model-export-as-script`

Exports the metadata model as a SQL script.

**Synopsis:**
```bash
aws dms start-metadata-model-export-as-script \
    --migration-project-identifier <value> \
    --selection-rules <value> \
    --origin <value> \
    [--file-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--migration-project-identifier` | **Yes** | string | -- | Migration project identifier or ARN |
| `--selection-rules` | **Yes** | string | -- | JSON selection rules |
| `--origin` | **Yes** | string | -- | Export origin: `SOURCE` or `TARGET` |
| `--file-name` | No | string | -- | Output file name |

**Output Schema:**
```json
{
    "RequestIdentifier": "string"
}
```

---

### 8.8 `start-metadata-model-export-to-target`

Exports the metadata model to the target database.

**Synopsis:**
```bash
aws dms start-metadata-model-export-to-target \
    --migration-project-identifier <value> \
    --selection-rules <value> \
    [--overwrite-extension-pack | --no-overwrite-extension-pack] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--migration-project-identifier` | **Yes** | string | -- | Migration project identifier or ARN |
| `--selection-rules` | **Yes** | string | -- | JSON selection rules |
| `--overwrite-extension-pack` | No | boolean | -- | Overwrite existing extension pack |

**Output Schema:**
```json
{
    "RequestIdentifier": "string"
}
```

---

### 8.9 `export-metadata-model-assessment`

Exports the metadata model assessment report to S3.

**Synopsis:**
```bash
aws dms export-metadata-model-assessment \
    --migration-project-identifier <value> \
    --selection-rules <value> \
    [--file-name <value>] \
    [--assessment-report-types <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--migration-project-identifier` | **Yes** | string | -- | Migration project identifier or ARN |
| `--selection-rules` | **Yes** | string | -- | JSON selection rules |
| `--file-name` | No | string | -- | Output file name |
| `--assessment-report-types` | No | list(string) | -- | Report types: `pdf`, `csv` |

**Output Schema:**
```json
{
    "PdfReport": {
        "S3ObjectKey": "string",
        "ObjectUrl": "string"
    },
    "CsvReport": {
        "S3ObjectKey": "string",
        "ObjectUrl": "string"
    }
}
```

---

### 8.10 `describe-metadata-model-assessments`

Describes the metadata model assessments for a migration project. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-metadata-model-assessments \
    --migration-project-identifier <value> \
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
| `--migration-project-identifier` | **Yes** | string | -- | Migration project identifier or ARN |
| `--filters` | No | list | -- | Filters |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Marker": "string",
    "Requests": [
        {
            "Status": "string",
            "RequestIdentifier": "string"
        }
    ]
}
```

---

### 8.11–8.15 `describe-metadata-model-conversions`, `describe-metadata-model-creations`, `describe-metadata-model-exports-as-script`, `describe-metadata-model-exports-to-target`, `describe-metadata-model-imports`

All share the same synopsis and parameters as `describe-metadata-model-assessments` (section 8.10). Each returns a paginated list of requests for their respective operation type.

**Synopsis:** Same as section 8.10 — requires `--migration-project-identifier` and optional `--filters` and pagination parameters.

**Output Schema:** Same as section 8.10.
