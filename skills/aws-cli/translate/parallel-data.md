# Parallel Data

### 3.1 `create-parallel-data`

Creates a parallel data resource used for Active Custom Translation in batch translation jobs. Parallel data consists of example translations that customize the machine translation output.

**Synopsis:**
```bash
aws translate create-parallel-data \
    --name <value> \
    --parallel-data-config <value> \
    [--description <value>] \
    [--encryption-key <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name for the parallel data resource (1-256 chars, pattern: `^([A-Za-z0-9-]_?)+$`) |
| `--parallel-data-config` | **Yes** | structure | -- | Format and S3 location of the parallel data input file |
| `--description` | No | string | None | Description for the resource (max 256 chars) |
| `--encryption-key` | No | structure | None | KMS encryption key details |
| `--client-token` | No | string | None | Unique identifier for idempotency (1-64 chars) |
| `--tags` | No | list | None | Key-value pairs for resource metadata (max 200 tags) |

**ParallelDataConfig Structure:**
```json
{
    "S3Uri": "s3://bucket-name/parallel-data/",
    "Format": "TSV|CSV|TMX"
}
```

**Output Schema:**
```json
{
    "Name": "string",
    "Status": "CREATING|UPDATING|ACTIVE|DELETING|FAILED"
}
```

---

### 3.2 `get-parallel-data`

Retrieves a parallel data resource including its properties and presigned S3 URLs to download the data.

**Synopsis:**
```bash
aws translate get-parallel-data \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the parallel data resource to retrieve (1-256 chars) |

**Output Schema:**
```json
{
    "ParallelDataProperties": {
        "Name": "string",
        "Arn": "string",
        "Description": "string",
        "Status": "CREATING|UPDATING|ACTIVE|DELETING|FAILED",
        "SourceLanguageCode": "string",
        "TargetLanguageCodes": ["string"],
        "ParallelDataConfig": {
            "S3Uri": "string",
            "Format": "TSV|CSV|TMX"
        },
        "Message": "string",
        "ImportedDataSize": "long",
        "ImportedRecordCount": "long",
        "FailedRecordCount": "long",
        "SkippedRecordCount": "long",
        "EncryptionKey": {
            "Type": "KMS",
            "Id": "string"
        },
        "CreatedAt": "timestamp",
        "LastUpdatedAt": "timestamp",
        "LatestUpdateAttemptStatus": "CREATING|UPDATING|ACTIVE|DELETING|FAILED",
        "LatestUpdateAttemptAt": "timestamp"
    },
    "DataLocation": {
        "RepositoryType": "string",
        "Location": "string"
    },
    "AuxiliaryDataLocation": {
        "RepositoryType": "string",
        "Location": "string"
    },
    "LatestUpdateAttemptAuxiliaryDataLocation": {
        "RepositoryType": "string",
        "Location": "string"
    }
}
```

---

### 3.3 `list-parallel-data`

Lists all parallel data resources associated with the AWS account.

**Synopsis:**
```bash
aws translate list-parallel-data \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token (max 8192 chars) |
| `--max-results` | No | integer | None | Maximum results per page (1-500) |

**Output Schema:**
```json
{
    "ParallelDataPropertiesList": [
        {
            "Name": "string",
            "Arn": "string",
            "Description": "string",
            "Status": "CREATING|UPDATING|ACTIVE|DELETING|FAILED",
            "SourceLanguageCode": "string",
            "TargetLanguageCodes": ["string"],
            "ParallelDataConfig": {
                "S3Uri": "string",
                "Format": "TSV|CSV|TMX"
            },
            "Message": "string",
            "ImportedDataSize": "long",
            "ImportedRecordCount": "long",
            "FailedRecordCount": "long",
            "SkippedRecordCount": "long",
            "EncryptionKey": {
                "Type": "KMS",
                "Id": "string"
            },
            "CreatedAt": "timestamp",
            "LastUpdatedAt": "timestamp",
            "LatestUpdateAttemptStatus": "CREATING|UPDATING|ACTIVE|DELETING|FAILED",
            "LatestUpdateAttemptAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.4 `update-parallel-data`

Updates an existing parallel data resource by replacing the input file with a new one.

**Synopsis:**
```bash
aws translate update-parallel-data \
    --name <value> \
    --parallel-data-config <value> \
    [--description <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the parallel data resource to update (1-256 chars) |
| `--parallel-data-config` | **Yes** | structure | -- | New format and S3 location of the parallel data input file |
| `--description` | No | string | None | Updated description (max 256 chars) |
| `--client-token` | No | string | None | Unique identifier for idempotency (1-64 chars) |

**ParallelDataConfig Structure:**
```json
{
    "S3Uri": "s3://bucket-name/parallel-data/",
    "Format": "TSV|CSV|TMX"
}
```

**Output Schema:**
```json
{
    "Name": "string",
    "Status": "CREATING|UPDATING|ACTIVE|DELETING|FAILED",
    "LatestUpdateAttemptStatus": "CREATING|UPDATING|ACTIVE|DELETING|FAILED",
    "LatestUpdateAttemptAt": "timestamp"
}
```

---

### 3.5 `delete-parallel-data`

Deletes a parallel data resource.

**Synopsis:**
```bash
aws translate delete-parallel-data \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the parallel data resource to delete (1-256 chars) |

**Output Schema:**
```json
{
    "Name": "string",
    "Status": "CREATING|UPDATING|ACTIVE|DELETING|FAILED"
}
```
