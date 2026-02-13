# S3 Access Points

S3 access points provide customized access to data stored in S3 through FSx for Lustre file systems.

### 8.1 `create-and-attach-s3-access-point`

Creates an S3 access point and attaches it to an FSx for Lustre file system.

**Synopsis:**
```bash
aws fsx create-and-attach-s3-access-point \
    --file-system-id <value> \
    --s3-access-point-configuration <value> \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-id` | **Yes** | string | -- | Lustre file system ID |
| `--s3-access-point-configuration` | **Yes** | structure | -- | S3 access point config |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "S3AccessPointAttachment": {
        "Lifecycle": "CREATING|AVAILABLE|DELETING|FAILED",
        "S3AccessPointArn": "string",
        "FileSystemId": "string",
        "ResourceARN": "string",
        "Tags": []
    }
}
```

---

### 8.2 `describe-s3-access-point-attachments`

Returns descriptions of S3 access point attachments. **Paginated operation.**

**Synopsis:**
```bash
aws fsx describe-s3-access-point-attachments \
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
| `--filters` | No | list | None | Filters: `file-system-id` |

**Output Schema:**
```json
{
    "S3AccessPointAttachments": [
        {
            "Lifecycle": "string",
            "S3AccessPointArn": "string",
            "FileSystemId": "string",
            "ResourceARN": "string",
            "Tags": []
        }
    ],
    "NextToken": "string"
}
```

---

### 8.3 `detach-and-delete-s3-access-point`

Detaches and deletes an S3 access point from a file system.

**Synopsis:**
```bash
aws fsx detach-and-delete-s3-access-point \
    --s3-access-point-arn <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--s3-access-point-arn` | **Yes** | string | -- | S3 access point ARN |

**Output Schema:**
```json
{
    "Lifecycle": "DELETING",
    "S3AccessPointArn": "string"
}
```
