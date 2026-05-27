# Pipelines

### 1.1 `create-pipeline`

Creates a transcoding pipeline that manages transcoding jobs and connects input/output S3 buckets.

**Synopsis:**
```bash
aws elastictranscoder create-pipeline \
    --name <value> \
    --input-bucket <value> \
    --role <value> \
    [--aws-kms-key-arn <value>] \
    [--notifications <value>] \
    [--content-config <value>] \
    [--thumbnail-config <value>] \
    [--output-bucket <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Pipeline name (1-40 chars) |
| `--input-bucket` | **Yes** | string | -- | S3 bucket for input files |
| `--role` | **Yes** | string | -- | IAM role ARN for S3 and SNS access |
| `--output-bucket` | No | string | None | S3 bucket for output files (use this or ContentConfig+ThumbnailConfig) |
| `--aws-kms-key-arn` | No | string | None | KMS key ARN for output encryption |
| `--notifications` | No | structure | None | SNS notification topics |
| `--content-config` | No | structure | None | Output file storage config (overrides output-bucket) |
| `--thumbnail-config` | No | structure | None | Thumbnail storage config |

**Notifications:**
```json
{
    "Progressing": "arn:aws:sns:us-east-1:123456789012:progressing",
    "Completed": "arn:aws:sns:us-east-1:123456789012:completed",
    "Warning": "arn:aws:sns:us-east-1:123456789012:warning",
    "Error": "arn:aws:sns:us-east-1:123456789012:error"
}
```

**ContentConfig / ThumbnailConfig:**
```json
{
    "Bucket": "string",
    "StorageClass": "Standard|ReducedRedundancy",
    "Permissions": [
        {
            "GranteeType": "Canonical|Email|Group",
            "Grantee": "string",
            "Access": ["Read", "ReadAcp", "WriteAcp", "FullControl"]
        }
    ]
}
```

**Output Schema:**
```json
{
    "Pipeline": {
        "Id": "string",
        "Arn": "string",
        "Name": "string",
        "Status": "Active|Paused",
        "InputBucket": "string",
        "OutputBucket": "string",
        "Role": "string",
        "AwsKmsKeyArn": "string",
        "Notifications": {
            "Progressing": "string",
            "Completed": "string",
            "Warning": "string",
            "Error": "string"
        },
        "ContentConfig": {
            "Bucket": "string",
            "StorageClass": "string",
            "Permissions": []
        },
        "ThumbnailConfig": {
            "Bucket": "string",
            "StorageClass": "string",
            "Permissions": []
        }
    },
    "Warnings": [
        {
            "Code": "string",
            "Message": "string"
        }
    ]
}
```

---

### 1.2 `read-pipeline`

Reads the settings for a pipeline.

**Synopsis:**
```bash
aws elastictranscoder read-pipeline \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Pipeline ID |

**Output Schema:**
```json
{
    "Pipeline": {
        "Id": "string",
        "Arn": "string",
        "Name": "string",
        "Status": "Active|Paused",
        "InputBucket": "string",
        "OutputBucket": "string",
        "Role": "string",
        "AwsKmsKeyArn": "string",
        "Notifications": {},
        "ContentConfig": {},
        "ThumbnailConfig": {}
    },
    "Warnings": []
}
```

---

### 1.3 `update-pipeline`

Updates pipeline settings including name, buckets, role, and encryption.

**Synopsis:**
```bash
aws elastictranscoder update-pipeline \
    --id <value> \
    [--name <value>] \
    [--input-bucket <value>] \
    [--role <value>] \
    [--aws-kms-key-arn <value>] \
    [--notifications <value>] \
    [--content-config <value>] \
    [--thumbnail-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Pipeline ID to update |
| `--name` | No | string | None | Updated name |
| `--input-bucket` | No | string | None | Updated input bucket |
| `--role` | No | string | None | Updated IAM role ARN |
| `--aws-kms-key-arn` | No | string | None | Updated KMS key ARN |
| `--notifications` | No | structure | None | Updated SNS notifications |
| `--content-config` | No | structure | None | Updated output config |
| `--thumbnail-config` | No | structure | None | Updated thumbnail config |

**Output Schema:**
```json
{
    "Pipeline": {
        "Id": "string",
        "Arn": "string",
        "Name": "string",
        "Status": "string",
        "InputBucket": "string",
        "Role": "string",
        "Notifications": {},
        "ContentConfig": {},
        "ThumbnailConfig": {}
    },
    "Warnings": []
}
```

---

### 1.4 `update-pipeline-notifications`

Updates only the notification settings for a pipeline.

**Synopsis:**
```bash
aws elastictranscoder update-pipeline-notifications \
    --id <value> \
    --notifications <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Pipeline ID |
| `--notifications` | **Yes** | structure | -- | SNS topic ARNs for Progressing, Completed, Warning, Error |

**Output Schema:**
```json
{
    "Pipeline": {
        "Id": "string",
        "Notifications": {
            "Progressing": "string",
            "Completed": "string",
            "Warning": "string",
            "Error": "string"
        }
    }
}
```

---

### 1.5 `update-pipeline-status`

Pauses or activates a pipeline.

**Synopsis:**
```bash
aws elastictranscoder update-pipeline-status \
    --id <value> \
    --status <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Pipeline ID |
| `--status` | **Yes** | string | -- | `Active` or `Paused` |

**Output Schema:**
```json
{
    "Pipeline": {
        "Id": "string",
        "Status": "Active|Paused"
    }
}
```

---

### 1.6 `delete-pipeline`

Deletes a pipeline. Pipeline must have no active jobs.

**Synopsis:**
```bash
aws elastictranscoder delete-pipeline \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Pipeline ID to delete |

**Output:** None

---

### 1.7 `list-pipelines`

Lists pipelines. **Paginated operation.**

**Synopsis:**
```bash
aws elastictranscoder list-pipelines \
    [--ascending <value>] \
    [--page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ascending` | No | string | None | `true` for ascending, `false` for descending |
| `--page-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "NextPageToken": "string",
    "Pipelines": [
        {
            "Id": "string",
            "Arn": "string",
            "Name": "string",
            "Status": "Active|Paused",
            "InputBucket": "string",
            "OutputBucket": "string",
            "Role": "string",
            "AwsKmsKeyArn": "string",
            "Notifications": {},
            "ContentConfig": {},
            "ThumbnailConfig": {}
        }
    ]
}
```
