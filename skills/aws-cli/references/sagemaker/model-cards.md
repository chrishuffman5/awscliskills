# Model Cards

## 1. `create-model-card`

Creates a model card to document important details about a model.

**Synopsis:**
```bash
aws sagemaker create-model-card \
    --model-card-name <value> \
    --content <value> \
    --model-card-status <value> \
    [--security-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-card-name` | **Yes** | string | -- | Unique name (1-63 chars) |
| `--content` | **Yes** | string | -- | Model card content as JSON string |
| `--model-card-status` | **Yes** | string | -- | `Draft`, `PendingReview`, `Approved`, `Archived` |
| `--security-config` | No | structure | -- | `KmsKeyId` for encryption |
| `--tags` | No | list | -- | Key-value tags |

**Output Schema:**
```json
{
    "ModelCardArn": "string"
}
```

---

## 2. `describe-model-card`

Returns details about a model card.

**Synopsis:**
```bash
aws sagemaker describe-model-card \
    --model-card-name <value> \
    [--model-card-version <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-card-name` | **Yes** | string | -- | Model card name |
| `--model-card-version` | No | integer | -- | Specific version number |

**Output Schema:**
```json
{
    "ModelCardArn": "string",
    "ModelCardName": "string",
    "ModelCardVersion": "integer",
    "Content": "string",
    "ModelCardStatus": "Draft|PendingReview|Approved|Archived",
    "SecurityConfig": {"KmsKeyId": "string"},
    "CreationTime": "timestamp",
    "CreatedBy": {...},
    "LastModifiedTime": "timestamp",
    "LastModifiedBy": {...},
    "ModelCardProcessingStatus": "DeleteInProgress|DeletePending|ContentDeleted|ExportJobsDeleted|DeleteCompleted|DeleteFailed"
}
```

---

## 3. `list-model-cards`

Lists model cards. **Paginated operation.**

**Synopsis:**
```bash
aws sagemaker list-model-cards \
    [--creation-time-after <value>] \
    [--creation-time-before <value>] \
    [--name-contains <value>] \
    [--model-card-status <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name-contains` | No | string | -- | Filter by name substring |
| `--model-card-status` | No | string | -- | `Draft`, `PendingReview`, `Approved`, `Archived` |
| `--sort-by` | No | string | `Name` | `Name`, `CreationTime` |
| `--sort-order` | No | string | `Ascending` | `Ascending`, `Descending` |

**Output Schema:**
```json
{
    "ModelCardSummaries": [
        {
            "ModelCardName": "string",
            "ModelCardArn": "string",
            "ModelCardStatus": "string",
            "CreationTime": "timestamp",
            "LastModifiedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

## 4. `update-model-card`

Updates a model card.

**Synopsis:**
```bash
aws sagemaker update-model-card \
    --model-card-name <value> \
    [--content <value>] \
    [--model-card-status <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-card-name` | **Yes** | string | -- | Model card name |
| `--content` | No | string | -- | Updated content JSON |
| `--model-card-status` | No | string | -- | Updated status |

**Output Schema:**
```json
{
    "ModelCardArn": "string"
}
```

---

## 5. `delete-model-card`

Deletes a model card.

```bash
aws sagemaker delete-model-card --model-card-name <value>
```

**Output:** None

---

## 6. `list-model-card-versions`

Lists versions of a model card. **Paginated operation.**

**Synopsis:**
```bash
aws sagemaker list-model-card-versions \
    --model-card-name <value> \
    [--creation-time-after <value>] \
    [--creation-time-before <value>] \
    [--model-card-status <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-card-name` | **Yes** | string | -- | Model card name |
| `--model-card-status` | No | string | -- | Filter by status |
| `--sort-by` | No | string | `Version` | `Version` |
| `--sort-order` | No | string | `Descending` | `Ascending`, `Descending` |

**Output Schema:**
```json
{
    "ModelCardVersionSummaryList": [
        {
            "ModelCardName": "string",
            "ModelCardArn": "string",
            "ModelCardStatus": "string",
            "ModelCardVersion": "integer",
            "CreationTime": "timestamp",
            "LastModifiedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

## 7. `create-model-card-export-job`

Exports a model card to PDF.

**Synopsis:**
```bash
aws sagemaker create-model-card-export-job \
    --model-card-name <value> \
    --model-card-export-job-name <value> \
    --output-config <value> \
    [--model-card-version <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-card-name` | **Yes** | string | -- | Model card name |
| `--model-card-export-job-name` | **Yes** | string | -- | Export job name |
| `--output-config` | **Yes** | structure | -- | `S3OutputPath` |
| `--model-card-version` | No | integer | -- | Version to export |

**Output Schema:**
```json
{
    "ModelCardExportJobArn": "string"
}
```

---

## 8. `describe-model-card-export-job`

Returns details about a model card export job.

```bash
aws sagemaker describe-model-card-export-job \
    --model-card-export-job-arn <value>
```

**Output Schema:**
```json
{
    "ModelCardExportJobName": "string",
    "ModelCardExportJobArn": "string",
    "Status": "InProgress|Completed|Failed",
    "ModelCardName": "string",
    "ModelCardVersion": "integer",
    "OutputConfig": {"S3OutputPath": "string"},
    "CreatedAt": "timestamp",
    "LastModifiedAt": "timestamp",
    "FailureReason": "string",
    "ExportArtifacts": {"S3ExportArtifacts": "string"}
}
```

---

## 9. `list-model-card-export-jobs`

Lists model card export jobs. **Paginated operation.**

```bash
aws sagemaker list-model-card-export-jobs \
    --model-card-name <value> \
    [--model-card-version <value>] \
    [--creation-time-after <value>] \
    [--creation-time-before <value>] \
    [--model-card-export-job-name-contains <value>] \
    [--status-equals <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```
