# Model Import & Copy

### `create-model-import-job`

Creates a job to import a model from an S3 data source into Amazon Bedrock.

**Synopsis:**
```bash
aws bedrock create-model-import-job \
    --job-name <value> \
    --imported-model-name <value> \
    --role-arn <value> \
    --model-data-source <value> \
    [--job-tags <value>] \
    [--imported-model-tags <value>] \
    [--client-request-token <value>] \
    [--vpc-config <value>] \
    [--imported-model-kms-key-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-name` | **Yes** | string | -- | Import job name (1-63 chars) |
| `--imported-model-name` | **Yes** | string | -- | Name for the imported model (1-63 chars) |
| `--role-arn` | **Yes** | string | -- | IAM role ARN for Bedrock to assume |
| `--model-data-source` | **Yes** | structure | -- | S3 source for the model data |
| `--job-tags` | No | list | None | Tags for the import job (max 200) |
| `--imported-model-tags` | No | list | None | Tags for the imported model (max 200) |
| `--client-request-token` | No | string | None | Idempotency token (1-256 chars) |
| `--vpc-config` | No | structure | None | VPC config: `subnetIds`, `securityGroupIds` |
| `--imported-model-kms-key-id` | No | string | None | KMS key for encryption (1-2048 chars) |

**Model Data Source Structure:**
```json
{
    "s3DataSource": {
        "s3Uri": "s3://bucket/model-artifacts/"
    }
}
```

**Output Schema:**
```json
{
    "jobArn": "string"
}
```

---

### `get-model-import-job`

Gets details of a model import job.

**Synopsis:**
```bash
aws bedrock get-model-import-job \
    --job-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-identifier` | **Yes** | string | -- | Job name or ARN |

**Output Schema:**
```json
{
    "jobArn": "string",
    "jobName": "string",
    "importedModelName": "string",
    "importedModelArn": "string",
    "roleArn": "string",
    "modelDataSource": {
        "s3DataSource": {
            "s3Uri": "string"
        }
    },
    "status": "InProgress|Completed|Failed",
    "failureMessage": "string",
    "creationTime": "timestamp",
    "lastModifiedTime": "timestamp",
    "endTime": "timestamp",
    "vpcConfig": {
        "subnetIds": ["string"],
        "securityGroupIds": ["string"]
    },
    "importedModelKmsKeyArn": "string"
}
```

---

### `list-model-import-jobs`

Lists model import jobs. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock list-model-import-jobs \
    [--creation-time-after <value>] \
    [--creation-time-before <value>] \
    [--status-equals <value>] \
    [--name-contains <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--creation-time-after` | No | timestamp | None | Filter by creation time |
| `--creation-time-before` | No | timestamp | None | Filter by creation time |
| `--status-equals` | No | string | None | Filter: `InProgress`, `Completed`, `Failed` |
| `--name-contains` | No | string | None | Filter by name substring |
| `--sort-by` | No | string | None | Sort field: `CreationTime` |
| `--sort-order` | No | string | None | `Ascending`, `Descending` |

**Output Schema:**
```json
{
    "nextToken": "string",
    "modelImportJobSummaries": [
        {
            "jobArn": "string",
            "jobName": "string",
            "status": "InProgress|Completed|Failed",
            "importedModelName": "string",
            "importedModelArn": "string",
            "creationTime": "timestamp",
            "lastModifiedTime": "timestamp",
            "endTime": "timestamp"
        }
    ]
}
```

---

### `create-model-copy-job`

Copies a model to another region to make it available there.

**Synopsis:**
```bash
aws bedrock create-model-copy-job \
    --source-model-arn <value> \
    --target-model-name <value> \
    [--model-kms-key-id <value>] \
    [--target-model-tags <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-model-arn` | **Yes** | string | -- | ARN of the model to copy (20-1011 chars) |
| `--target-model-name` | **Yes** | string | -- | Name for the copied model (1-63 chars) |
| `--model-kms-key-id` | No | string | None | KMS key for encryption (1-2048 chars) |
| `--target-model-tags` | No | list | None | Tags for the copied model (max 200) |
| `--client-request-token` | No | string | None | Idempotency token (1-256 chars) |

**Output Schema:**
```json
{
    "jobArn": "string"
}
```

---

### `get-model-copy-job`

Gets details of a model copy job.

**Synopsis:**
```bash
aws bedrock get-model-copy-job \
    --job-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-arn` | **Yes** | string | -- | ARN of the copy job |

**Output Schema:**
```json
{
    "jobArn": "string",
    "status": "InProgress|Completed|Failed",
    "creationTime": "timestamp",
    "targetModelArn": "string",
    "targetModelName": "string",
    "sourceAccountId": "string",
    "sourceModelArn": "string",
    "targetModelKmsKeyArn": "string",
    "failureMessage": "string"
}
```

---

### `list-model-copy-jobs`

Lists model copy jobs. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock list-model-copy-jobs \
    [--creation-time-after <value>] \
    [--creation-time-before <value>] \
    [--status-equals <value>] \
    [--source-account-equals <value>] \
    [--source-model-arn-equals <value>] \
    [--target-model-name-contains <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--creation-time-after` | No | timestamp | None | Filter by creation time |
| `--creation-time-before` | No | timestamp | None | Filter by creation time |
| `--status-equals` | No | string | None | Filter: `InProgress`, `Completed`, `Failed` |
| `--source-account-equals` | No | string | None | Filter by source account ID |
| `--source-model-arn-equals` | No | string | None | Filter by source model ARN |
| `--target-model-name-contains` | No | string | None | Filter by target model name |
| `--sort-by` | No | string | None | Sort field: `CreationTime` |
| `--sort-order` | No | string | None | `Ascending`, `Descending` |

**Output Schema:**
```json
{
    "nextToken": "string",
    "modelCopyJobSummaries": [
        {
            "jobArn": "string",
            "status": "InProgress|Completed|Failed",
            "creationTime": "timestamp",
            "targetModelArn": "string",
            "targetModelName": "string",
            "sourceAccountId": "string",
            "sourceModelArn": "string",
            "sourceModelName": "string",
            "failureMessage": "string"
        }
    ]
}
```

---

### `get-imported-model`

Gets details of an imported model.

**Synopsis:**
```bash
aws bedrock get-imported-model \
    --model-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-identifier` | **Yes** | string | -- | Model name or ARN |

**Output Schema:**
```json
{
    "modelArn": "string",
    "modelName": "string",
    "jobName": "string",
    "jobArn": "string",
    "modelDataSource": {
        "s3DataSource": {
            "s3Uri": "string"
        }
    },
    "creationTime": "timestamp",
    "modelArchitecture": "string",
    "modelKmsKeyArn": "string"
}
```

---

### `list-imported-models`

Lists imported models. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock list-imported-models \
    [--creation-time-before <value>] \
    [--creation-time-after <value>] \
    [--name-contains <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "nextToken": "string",
    "modelSummaries": [
        {
            "modelArn": "string",
            "modelName": "string",
            "creationTime": "timestamp"
        }
    ]
}
```

---

### `delete-imported-model`

Deletes an imported model.

**Synopsis:**
```bash
aws bedrock delete-imported-model \
    --model-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-identifier` | **Yes** | string | -- | Model name or ARN |

**Output:** None (HTTP 200 on success)
