# Face Liveness

### 4.1 `create-face-liveness-session`

Creates a session for a face liveness check. The session ID expires 3 minutes after creation.

**Synopsis:**
```bash
aws rekognition create-face-liveness-session \
    [--kms-key-id <value>] \
    [--settings <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--kms-key-id` | No | string | -- | KMS key for encrypting audit and reference images |
| `--settings` | No | structure | -- | Session settings (output config, audit images limit, challenge preferences) |
| `--client-request-token` | No | string | auto | Idempotency token (1-64 chars) |

**Settings Structure:**
```json
{
    "OutputConfig": {
        "S3Bucket": "string",
        "S3KeyPrefix": "string"
    },
    "AuditImagesLimit": "integer (0-4, default 0)",
    "ChallengePreferences": [
        {
            "Type": "FaceMovementAndLightChallenge|FaceMovementChallenge",
            "Versions": {
                "Minimum": "string",
                "Maximum": "string"
            }
        }
    ]
}
```

**Output Schema:**
```json
{
    "SessionId": "string"
}
```

---

### 4.2 `get-face-liveness-session-results`

Gets the results of a face liveness session.

**Synopsis:**
```bash
aws rekognition get-face-liveness-session-results \
    --session-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--session-id` | **Yes** | string | -- | Session ID (UUID format) |

**Output Schema:**
```json
{
    "SessionId": "string",
    "Status": "CREATED|IN_PROGRESS|SUCCEEDED|FAILED|EXPIRED",
    "Confidence": "float",
    "ReferenceImage": {
        "Bytes": "blob",
        "S3Object": {
            "Bucket": "string",
            "Name": "string",
            "Version": "string"
        },
        "BoundingBox": {
            "Width": "float",
            "Height": "float",
            "Left": "float",
            "Top": "float"
        }
    },
    "AuditImages": [
        {
            "Bytes": "blob",
            "S3Object": {
                "Bucket": "string",
                "Name": "string",
                "Version": "string"
            },
            "BoundingBox": {}
        }
    ]
}
```
