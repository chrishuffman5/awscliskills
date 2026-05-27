# Attached Files

### 27.1 `start-attached-file-upload`

Starts an attached file upload.

**Synopsis:**
```bash
aws connect start-attached-file-upload \
    --instance-id <value> \
    --file-name <value> \
    --file-size-in-bytes <value> \
    --file-use-case-type <value> \
    --associated-resource-arn <value> \
    [--client-token <value>] \
    [--url-expiry-in-seconds <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--file-name` | **Yes** | string | -- | File name (1-256 chars) |
| `--file-size-in-bytes` | **Yes** | long | -- | File size in bytes |
| `--file-use-case-type` | **Yes** | string | -- | `ATTACHMENT`, `EMAIL_MESSAGE` |
| `--associated-resource-arn` | **Yes** | string | -- | Resource ARN to associate file with |
| `--client-token` | No | string | Auto | Idempotency token |
| `--url-expiry-in-seconds` | No | integer | None | Upload URL expiry (5-300 seconds) |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "FileArn": "string",
    "FileId": "string",
    "CreationTime": "string",
    "FileStatus": "APPROVED|REJECTED|PROCESSING|FAILED",
    "CreatedBy": {},
    "UploadUrlMetadata": {
        "Url": "string",
        "UrlExpiry": "string",
        "HeadersToInclude": { "key": "value" }
    }
}
```

---

### 27.2 `complete-attached-file-upload`

Completes an attached file upload.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--file-id` | **Yes** | string | -- | File ID |
| `--associated-resource-arn` | **Yes** | string | -- | Associated resource ARN |

**Output:** None

---

### 27.3 `get-attached-file`

Gets an attached file with a download URL.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--file-id` | **Yes** | string | -- | File ID |
| `--associated-resource-arn` | **Yes** | string | -- | Associated resource ARN |
| `--url-expiry-in-seconds` | No | integer | None | Download URL expiry (5-300) |

**Output Schema:**
```json
{
    "FileArn": "string",
    "FileId": "string",
    "CreationTime": "string",
    "FileStatus": "string",
    "FileName": "string",
    "FileSizeInBytes": "long",
    "AssociatedResourceArn": "string",
    "FileUseCaseType": "string",
    "CreatedBy": {},
    "DownloadUrlMetadata": {
        "Url": "string",
        "UrlExpiry": "string"
    },
    "Tags": { "key": "value" }
}
```

---

### 27.4 `delete-attached-file`

Deletes an attached file.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--file-id` | **Yes** | string | -- | File ID |
| `--associated-resource-arn` | **Yes** | string | -- | Associated resource ARN |

**Output:** None

---

### 27.5 `batch-get-attached-file-metadata`

Batch gets metadata for attached files.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--file-ids` | **Yes** | list | -- | File IDs (1-5) |
| `--associated-resource-arn` | **Yes** | string | -- | Associated resource ARN |

**Output Schema:**
```json
{
    "Files": [ { "CreationTime": "string", "FileArn": "string", "FileId": "string", "FileName": "string", "FileSizeInBytes": "long", "FileStatus": "string", "CreatedBy": {}, "FileUseCaseType": "string", "AssociatedResourceArn": "string", "Tags": {} } ],
    "Errors": [ { "ErrorCode": "string", "ErrorMessage": "string", "FileId": "string" } ]
}
```
