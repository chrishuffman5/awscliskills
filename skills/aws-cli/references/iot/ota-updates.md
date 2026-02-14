# OTA Updates

## 13.1 `create-ota-update`

Creates an OTA (Over-The-Air) update for devices.

**Synopsis:**
```bash
aws iot create-ota-update \
    --ota-update-id <value> \
    --targets <value> \
    --files <value> \
    --role-arn <value> \
    [--description <value>] \
    [--protocols <value>] \
    [--target-selection <value>] \
    [--aws-job-executions-rollout-config <value>] \
    [--aws-job-presigned-url-config <value>] \
    [--aws-job-abort-config <value>] \
    [--aws-job-timeout-config <value>] \
    [--additional-parameters <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ota-update-id` | **Yes** | string | -- | OTA update ID (1-128 chars) |
| `--targets` | **Yes** | list | -- | Thing/group ARNs (min 1) |
| `--files` | **Yes** | list | -- | Files to stream (min 1). See file structure below |
| `--role-arn` | **Yes** | string | -- | IAM role ARN for S3/Jobs/CodeSigning |
| `--description` | No | string | None | Description (max 2028 chars) |
| `--protocols` | No | list | None | `MQTT`, `HTTP`, or both (1-2) |
| `--target-selection` | No | string | None | `CONTINUOUS` or `SNAPSHOT` |
| `--aws-job-executions-rollout-config` | No | structure | None | Rollout config |
| `--aws-job-presigned-url-config` | No | structure | None | Pre-signed URL config (60-3600 seconds) |
| `--aws-job-abort-config` | No | structure | None | Job abort criteria |
| `--aws-job-timeout-config` | No | structure | None | Timeout in minutes (1-10080) |
| `--additional-parameters` | No | map | None | Extra parameters (not sent to devices) |
| `--tags` | No | list | None | Tags |

**File structure:**
```json
{
    "fileName": "string",
    "fileType": 0-255,
    "fileVersion": "string",
    "fileLocation": {
        "stream": {"streamId": "string", "fileId": 0-255},
        "s3Location": {"bucket": "string", "key": "string", "version": "string"}
    },
    "codeSigning": {
        "awsSignerJobId": "string",
        "startSigningJobParameter": {},
        "customCodeSigning": {}
    },
    "attributes": {"string": "string"}
}
```

**Output Schema:**
```json
{
    "otaUpdateId": "string",
    "awsIotJobId": "string",
    "otaUpdateArn": "string",
    "awsIotJobArn": "string",
    "otaUpdateStatus": "CREATE_PENDING|CREATE_IN_PROGRESS|CREATE_COMPLETE|CREATE_FAILED|DELETE_IN_PROGRESS|DELETE_FAILED"
}
```

---

## 13.2 `get-ota-update`

Gets an OTA update.

**Synopsis:**
```bash
aws iot get-ota-update \
    --ota-update-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ota-update-id` | **Yes** | string | -- | OTA update ID |

**Output Schema:**
```json
{
    "otaUpdateInfo": {
        "otaUpdateId": "string",
        "otaUpdateArn": "string",
        "creationDate": "timestamp",
        "lastModifiedDate": "timestamp",
        "description": "string",
        "targets": ["string"],
        "protocols": ["string"],
        "awsJobExecutionsRolloutConfig": {},
        "awsJobPresignedUrlConfig": {},
        "targetSelection": "CONTINUOUS|SNAPSHOT",
        "otaUpdateFiles": [],
        "otaUpdateStatus": "string",
        "awsIotJobId": "string",
        "awsIotJobArn": "string",
        "errorInfo": {"code": "string", "message": "string"},
        "additionalParameters": {}
    }
}
```

---

## 13.3 `list-ota-updates`

Lists OTA updates. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-ota-updates \
    [--max-results <value>] \
    [--next-token <value>] \
    [--ota-update-status <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Max results (1-250) |
| `--next-token` | No | string | None | Pagination token |
| `--ota-update-status` | No | string | None | Filter by status |

**Output Schema:**
```json
{
    "otaUpdates": [
        {
            "otaUpdateId": "string",
            "otaUpdateArn": "string",
            "creationDate": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

## 13.4 `delete-ota-update`

Deletes an OTA update.

**Synopsis:**
```bash
aws iot delete-ota-update \
    --ota-update-id <value> \
    [--delete-stream | --no-delete-stream] \
    [--force-delete-aws-job | --no-force-delete-aws-job] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ota-update-id` | **Yes** | string | -- | OTA update ID |
| `--delete-stream` | No | boolean | false | Also delete the stream |
| `--force-delete-aws-job` | No | boolean | false | Force delete the AWS job |

**Output:** None

---

## 13.5 `create-stream`

Creates a stream for OTA updates from S3 files.

**Synopsis:**
```bash
aws iot create-stream \
    --stream-id <value> \
    --files <value> \
    --role-arn <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-id` | **Yes** | string | -- | Stream ID (1-128 chars) |
| `--files` | **Yes** | list | -- | Files to stream (1-50). Each: `{fileId: 0-255, s3Location: {bucket, key, version}}` |
| `--role-arn` | **Yes** | string | -- | IAM role ARN for S3 access (20-2048 chars) |
| `--description` | No | string | None | Description (max 2028 chars) |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "streamId": "string",
    "streamArn": "string",
    "description": "string",
    "streamVersion": "integer"
}
```

---

## 13.6 `describe-stream`

Describes a stream.

**Synopsis:**
```bash
aws iot describe-stream \
    --stream-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-id` | **Yes** | string | -- | Stream ID |

**Output Schema:**
```json
{
    "streamInfo": {
        "streamId": "string",
        "streamArn": "string",
        "streamVersion": "integer",
        "description": "string",
        "files": [{"fileId": "integer", "s3Location": {"bucket": "string", "key": "string", "version": "string"}}],
        "createdAt": "timestamp",
        "lastUpdatedAt": "timestamp",
        "roleArn": "string"
    }
}
```

---

## 13.7 `list-streams`

Lists streams. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-streams \
    [--max-results <value>] \
    [--next-token <value>] \
    [--ascending-order | --no-ascending-order] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Max results (1-250) |
| `--next-token` | No | string | None | Pagination token |
| `--ascending-order` | No | boolean | false | Sort ascending |

**Output Schema:**
```json
{
    "streams": [
        {
            "streamId": "string",
            "streamArn": "string",
            "streamVersion": "integer",
            "description": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 13.8 `update-stream`

Updates a stream.

**Synopsis:**
```bash
aws iot update-stream \
    --stream-id <value> \
    [--description <value>] \
    [--files <value>] \
    [--role-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-id` | **Yes** | string | -- | Stream ID |
| `--description` | No | string | None | Updated description |
| `--files` | No | list | None | Updated files |
| `--role-arn` | No | string | None | Updated IAM role ARN |

**Output Schema:**
```json
{
    "streamId": "string",
    "streamArn": "string",
    "description": "string",
    "streamVersion": "integer"
}
```

---

## 13.9 `delete-stream`

Deletes a stream.

**Synopsis:**
```bash
aws iot delete-stream \
    --stream-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-id` | **Yes** | string | -- | Stream ID |

**Output:** None
