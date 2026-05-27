# Security Configuration

### 18.1 `create-security-configuration`

Creates a security configuration for encryption settings.

**Synopsis:**
```bash
aws glue create-security-configuration \
    --name <value> \
    --encryption-configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Security configuration name |
| `--encryption-configuration` | **Yes** | structure | -- | Encryption config (JSON). Includes S3Encryption, CloudWatchEncryption, JobBookmarksEncryption |

**Encryption Configuration JSON Example:**
```json
{
    "S3Encryption": [
        {
            "S3EncryptionMode": "SSE-KMS|SSE-S3|DISABLED",
            "KmsKeyArn": "arn:aws:kms:..."
        }
    ],
    "CloudWatchEncryption": {
        "CloudWatchEncryptionMode": "SSE-KMS|DISABLED",
        "KmsKeyArn": "arn:aws:kms:..."
    },
    "JobBookmarksEncryption": {
        "JobBookmarksEncryptionMode": "CSE-KMS|DISABLED",
        "KmsKeyArn": "arn:aws:kms:..."
    }
}
```

**Output Schema:**
```json
{
    "Name": "string",
    "CreatedTimestamp": "timestamp"
}
```

---

### 18.2 `delete-security-configuration`

Deletes a security configuration.

**Synopsis:**
```bash
aws glue delete-security-configuration \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Security configuration name |

No output on success.

---

### 18.3 `get-security-configuration`

Retrieves a security configuration.

**Synopsis:**
```bash
aws glue get-security-configuration \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Security configuration name |

**Output Schema:**
```json
{
    "SecurityConfiguration": {
        "Name": "string",
        "CreatedTimeStamp": "timestamp",
        "EncryptionConfiguration": {
            "S3Encryption": [
                {
                    "S3EncryptionMode": "SSE-KMS|SSE-S3|DISABLED",
                    "KmsKeyArn": "string"
                }
            ],
            "CloudWatchEncryption": {
                "CloudWatchEncryptionMode": "SSE-KMS|DISABLED",
                "KmsKeyArn": "string"
            },
            "JobBookmarksEncryption": {
                "JobBookmarksEncryptionMode": "CSE-KMS|DISABLED",
                "KmsKeyArn": "string"
            }
        }
    }
}
```

---

### 18.4 `get-security-configurations`

Lists all security configurations. **Paginated operation.**

**Synopsis:**
```bash
aws glue get-security-configurations \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "SecurityConfigurations": [
        {
            "Name": "string",
            "CreatedTimeStamp": "timestamp",
            "EncryptionConfiguration": {}
        }
    ],
    "NextToken": "string"
}
```
