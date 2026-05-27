# Terminologies

### 2.1 `import-terminology`

Creates or updates a custom terminology resource. Custom terminologies ensure that specific terms are translated consistently.

**Synopsis:**
```bash
aws translate import-terminology \
    --name <value> \
    --merge-strategy <value> \
    --data-file <value> \
    [--description <value>] \
    [--terminology-data <value>] \
    [--encryption-key <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the custom terminology (1-256 chars, pattern: `^([A-Za-z0-9-]_?)+$`) |
| `--merge-strategy` | **Yes** | string | -- | Merge strategy for importing. Only value: `OVERWRITE` |
| `--data-file` | **Yes** | blob | -- | Path to terminology file: `fileb://terms.csv` |
| `--description` | No | string | None | Description of the custom terminology (max 256 chars) |
| `--terminology-data` | No | structure | None | Terminology data format and directionality |
| `--encryption-key` | No | structure | None | KMS encryption key for the terminology |
| `--tags` | No | list | None | Key-value pairs for resource metadata (max 200 tags) |

**TerminologyData Structure:**
```json
{
    "Format": "CSV|TMX|TSV",
    "Directionality": "UNI|MULTI"
}
```

**EncryptionKey Structure:**
```json
{
    "Type": "KMS",
    "Id": "arn:aws:kms:region:account-id:key/key-id"
}
```

**Output Schema:**
```json
{
    "TerminologyProperties": {
        "Name": "string",
        "Description": "string",
        "Arn": "string",
        "SourceLanguageCode": "string",
        "TargetLanguageCodes": ["string"],
        "EncryptionKey": {
            "Type": "KMS",
            "Id": "string"
        },
        "SizeBytes": "integer",
        "TermCount": "integer",
        "SkippedTermCount": "integer",
        "CreatedAt": "timestamp",
        "LastUpdatedAt": "timestamp",
        "Directionality": "UNI|MULTI",
        "Format": "CSV|TMX|TSV",
        "Message": "string"
    },
    "AuxiliaryDataLocation": {
        "RepositoryType": "string",
        "Location": "string"
    }
}
```

---

### 2.2 `get-terminology`

Retrieves a custom terminology resource including its properties and a presigned S3 URL to download the terminology data.

**Synopsis:**
```bash
aws translate get-terminology \
    --name <value> \
    [--terminology-data-format <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the custom terminology to retrieve (1-256 chars) |
| `--terminology-data-format` | No | string | None | Output format: `CSV`, `TMX`, `TSV`. Defaults to original import format |

**Output Schema:**
```json
{
    "TerminologyProperties": {
        "Name": "string",
        "Description": "string",
        "Arn": "string",
        "SourceLanguageCode": "string",
        "TargetLanguageCodes": ["string"],
        "EncryptionKey": {
            "Type": "KMS",
            "Id": "string"
        },
        "SizeBytes": "integer",
        "TermCount": "integer",
        "SkippedTermCount": "integer",
        "CreatedAt": "timestamp",
        "LastUpdatedAt": "timestamp",
        "Directionality": "UNI|MULTI",
        "Message": "string",
        "Format": "CSV|TMX|TSV"
    },
    "TerminologyDataLocation": {
        "RepositoryType": "string",
        "Location": "string"
    },
    "AuxiliaryDataLocation": {
        "RepositoryType": "string",
        "Location": "string"
    }
}
```

---

### 2.3 `list-terminologies`

Lists all custom terminologies associated with the AWS account. **Paginated operation.**

**Synopsis:**
```bash
aws translate list-terminologies \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "TerminologyPropertiesList": [
        {
            "Name": "string",
            "Description": "string",
            "Arn": "string",
            "SourceLanguageCode": "string",
            "TargetLanguageCodes": ["string"],
            "EncryptionKey": {
                "Type": "KMS",
                "Id": "string"
            },
            "SizeBytes": "integer",
            "TermCount": "integer",
            "SkippedTermCount": "integer",
            "CreatedAt": "timestamp",
            "LastUpdatedAt": "timestamp",
            "Directionality": "UNI|MULTI",
            "Message": "string",
            "Format": "CSV|TMX|TSV"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.4 `delete-terminology`

Deletes a custom terminology resource.

**Synopsis:**
```bash
aws translate delete-terminology \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the custom terminology to delete (1-256 chars) |

**Output:** None
