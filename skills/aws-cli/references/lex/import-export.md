# Import/Export

### 7.1 `create-export`

Creates a zip archive export of a bot, bot locale, or custom vocabulary.

**Synopsis:**
```bash
aws lexv2-models create-export \
    --resource-specification <value> \
    --file-format <value> \
    [--file-password <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-specification` | **Yes** | structure | -- | Resource to export (bot, bot locale, or custom vocabulary) |
| `--file-format` | **Yes** | string | -- | File format: `LexJson` or `TSV` |
| `--file-password` | No | string | None | Password to encrypt the archive (1-1024 chars) |

**ResourceSpecification Structure:**
```json
{
    "botExportSpecification": {
        "botId": "string",
        "botVersion": "string"
    }
}
```
Or:
```json
{
    "botLocaleExportSpecification": {
        "botId": "string",
        "botVersion": "string",
        "localeId": "string"
    }
}
```
Or:
```json
{
    "customVocabularyExportSpecification": {
        "botId": "string",
        "botVersion": "string",
        "localeId": "string"
    }
}
```

**Output Schema:**
```json
{
    "exportId": "string",
    "resourceSpecification": {},
    "fileFormat": "LexJson|TSV",
    "exportStatus": "InProgress|Completed|Failed|Deleting",
    "creationDateTime": "timestamp"
}
```

---

### 7.2 `delete-export`

Deletes an export.

**Synopsis:**
```bash
aws lexv2-models delete-export \
    --export-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--export-id` | **Yes** | string | -- | Export identifier (10 chars) |

**Output Schema:**
```json
{
    "exportId": "string",
    "exportStatus": "InProgress|Completed|Failed|Deleting"
}
```

---

### 7.3 `describe-export`

Gets metadata for an export, including download URL when the export is complete.

**Synopsis:**
```bash
aws lexv2-models describe-export \
    --export-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--export-id` | **Yes** | string | -- | Export identifier (10 chars) |

**Output Schema:**
```json
{
    "exportId": "string",
    "resourceSpecification": {},
    "fileFormat": "LexJson|TSV",
    "exportStatus": "InProgress|Completed|Failed|Deleting",
    "failureReasons": ["string"],
    "downloadUrl": "string",
    "creationDateTime": "timestamp",
    "lastUpdatedDateTime": "timestamp"
}
```

---

### 7.4 `list-exports`

Lists all exports for a bot, bot locale, or custom vocabulary.

**Synopsis:**
```bash
aws lexv2-models list-exports \
    [--bot-id <value>] \
    [--bot-version <value>] \
    [--sort-by <value>] \
    [--filters <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--locale-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | No | string | None | Bot identifier |
| `--bot-version` | No | string | None | Bot version |
| `--sort-by` | No | structure | None | Sort field and order |
| `--filters` | No | list | None | Filter criteria |
| `--max-results` | No | integer | None | Maximum exports to return (1-1000) |
| `--next-token` | No | string | None | Pagination token |
| `--locale-id` | No | string | None | Locale identifier |

**Output Schema:**
```json
{
    "botId": "string",
    "botVersion": "string",
    "exportSummaries": [
        {
            "exportId": "string",
            "resourceSpecification": {},
            "fileFormat": "LexJson|TSV",
            "exportStatus": "string",
            "creationDateTime": "timestamp",
            "lastUpdatedDateTime": "timestamp"
        }
    ],
    "nextToken": "string",
    "localeId": "string"
}
```

---

### 7.5 `update-export`

Updates the password for an existing export.

**Synopsis:**
```bash
aws lexv2-models update-export \
    --export-id <value> \
    [--file-password <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--export-id` | **Yes** | string | -- | Export identifier (10 chars) |
| `--file-password` | No | string | None | New password for the archive |

**Output Schema:**
```json
{
    "exportId": "string",
    "resourceSpecification": {},
    "fileFormat": "LexJson|TSV",
    "exportStatus": "string",
    "creationDateTime": "timestamp",
    "lastUpdatedDateTime": "timestamp"
}
```

---

### 7.6 `start-import`

Starts importing a bot, bot locale, or custom vocabulary from a zip archive.

**Synopsis:**
```bash
aws lexv2-models start-import \
    --import-id <value> \
    --resource-specification <value> \
    --merge-strategy <value> \
    [--file-password <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--import-id` | **Yes** | string | -- | Import identifier from `create-upload-url` (10 chars) |
| `--resource-specification` | **Yes** | structure | -- | Parameters for the resource being imported |
| `--merge-strategy` | **Yes** | string | -- | Strategy for conflicts: `Overwrite`, `FailOnConflict`, `Append` |
| `--file-password` | No | string | None | Password to decrypt the archive (1-1024 chars) |

**Output Schema:**
```json
{
    "importId": "string",
    "resourceSpecification": {},
    "mergeStrategy": "Overwrite|FailOnConflict|Append",
    "importStatus": "InProgress|Completed|Failed|Deleting",
    "creationDateTime": "timestamp"
}
```

---

### 7.7 `delete-import`

Deletes an import record.

**Synopsis:**
```bash
aws lexv2-models delete-import \
    --import-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--import-id` | **Yes** | string | -- | Import identifier (10 chars) |

**Output Schema:**
```json
{
    "importId": "string",
    "importStatus": "InProgress|Completed|Failed|Deleting"
}
```

---

### 7.8 `describe-import`

Gets metadata for an import.

**Synopsis:**
```bash
aws lexv2-models describe-import \
    --import-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--import-id` | **Yes** | string | -- | Import identifier (10 chars) |

**Output Schema:**
```json
{
    "importId": "string",
    "resourceSpecification": {},
    "importedResourceId": "string",
    "importedResourceName": "string",
    "mergeStrategy": "Overwrite|FailOnConflict|Append",
    "importStatus": "InProgress|Completed|Failed|Deleting",
    "failureReasons": ["string"],
    "creationDateTime": "timestamp",
    "lastUpdatedDateTime": "timestamp"
}
```

---

### 7.9 `list-imports`

Lists all imports.

**Synopsis:**
```bash
aws lexv2-models list-imports \
    [--bot-id <value>] \
    [--bot-version <value>] \
    [--sort-by <value>] \
    [--filters <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--locale-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | No | string | None | Bot identifier |
| `--bot-version` | No | string | None | Bot version |
| `--sort-by` | No | structure | None | Sort field and order |
| `--filters` | No | list | None | Filter criteria |
| `--max-results` | No | integer | None | Maximum imports to return (1-1000) |
| `--next-token` | No | string | None | Pagination token |
| `--locale-id` | No | string | None | Locale identifier |

**Output Schema:**
```json
{
    "botId": "string",
    "botVersion": "string",
    "importSummaries": [
        {
            "importId": "string",
            "importedResourceId": "string",
            "importedResourceName": "string",
            "importStatus": "string",
            "mergeStrategy": "string",
            "creationDateTime": "timestamp",
            "lastUpdatedDateTime": "timestamp",
            "importedResourceType": "Bot|BotLocale|CustomVocabulary|TestSet"
        }
    ],
    "nextToken": "string",
    "localeId": "string"
}
```

---

### 7.10 `create-upload-url`

Creates a presigned S3 URL for uploading a zip archive for import.

**Synopsis:**
```bash
aws lexv2-models create-upload-url \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "importId": "string",
    "uploadUrl": "string"
}
```
