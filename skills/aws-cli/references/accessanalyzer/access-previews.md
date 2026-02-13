# Access Previews

### 4.1 `create-access-preview`

Creates an access preview that allows you to preview IAM Access Analyzer findings for your resource before deploying resource permissions. Only for account-level analyzers with `ACTIVE` status.

**Synopsis:**
```bash
aws accessanalyzer create-access-preview \
    --analyzer-arn <value> \
    --configurations <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--analyzer-arn` | **Yes** | string | -- | The ARN of the account analyzer |
| `--configurations` | **Yes** | map | -- | Access control configuration for the resource (must contain exactly one element) |
| `--client-token` | No | string | None | Client token for idempotency |

**Supported Configuration Resource Types:**

| Key | Resource Type |
|-----|---------------|
| `s3Bucket` | Amazon S3 bucket |
| `iamRole` | IAM role |
| `sqsQueue` | Amazon SQS queue |
| `kmsKey` | KMS key |
| `secretsManagerSecret` | Secrets Manager secret |
| `efsFileSystem` | Amazon EFS file system |
| `ecrRepository` | Amazon ECR repository |
| `ebsSnapshot` | Amazon EBS snapshot |
| `rdsDbSnapshot` | Amazon RDS DB snapshot |
| `rdsDbClusterSnapshot` | Amazon RDS DB cluster snapshot |
| `snsTopic` | Amazon SNS topic |
| `s3ExpressDirectoryBucket` | S3 Express directory bucket |
| `dynamodbStream` | DynamoDB stream |
| `dynamodbTable` | DynamoDB table |

**Output Schema:**
```json
{
    "id": "string"
}
```

---

### 4.2 `get-access-preview`

Retrieves information about an access preview.

**Synopsis:**
```bash
aws accessanalyzer get-access-preview \
    --analyzer-arn <value> \
    --access-preview-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--analyzer-arn` | **Yes** | string | -- | The ARN of the analyzer |
| `--access-preview-id` | **Yes** | string | -- | The ID of the access preview |

**Output Schema:**
```json
{
    "accessPreview": {
        "id": "string",
        "analyzerArn": "string",
        "configurations": {
            "string": {}
        },
        "createdAt": "timestamp",
        "status": "COMPLETED|CREATING|FAILED",
        "statusReason": {
            "code": "INTERNAL_ERROR|INVALID_CONFIGURATION"
        }
    }
}
```

---

### 4.3 `list-access-previews`

Lists access previews for the specified analyzer. **Paginated operation.**

**Synopsis:**
```bash
aws accessanalyzer list-access-previews \
    --analyzer-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--analyzer-arn` | **Yes** | string | -- | The ARN of the analyzer |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "accessPreviews": [
        {
            "id": "string",
            "analyzerArn": "string",
            "createdAt": "timestamp",
            "status": "COMPLETED|CREATING|FAILED",
            "statusReason": {
                "code": "INTERNAL_ERROR|INVALID_CONFIGURATION"
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 4.4 `list-access-preview-findings`

Lists findings for the specified access preview. **Paginated operation.**

**Synopsis:**
```bash
aws accessanalyzer list-access-preview-findings \
    --analyzer-arn <value> \
    --access-preview-id <value> \
    [--filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--analyzer-arn` | **Yes** | string | -- | The ARN of the analyzer |
| `--access-preview-id` | **Yes** | string | -- | The ID of the access preview |
| `--filter` | No | map | None | Filter criteria |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "findings": [
        {
            "id": "string",
            "existingFindingId": "string",
            "existingFindingStatus": "ACTIVE|ARCHIVED|RESOLVED",
            "principal": {"string": "string"},
            "action": ["string"],
            "condition": {"string": "string"},
            "resource": "string",
            "isPublic": "boolean",
            "resourceType": "string",
            "createdAt": "timestamp",
            "changeType": "CHANGED|NEW|UNCHANGED",
            "status": "ACTIVE|ARCHIVED|RESOLVED",
            "resourceOwnerAccount": "string",
            "error": "string",
            "sources": [
                {
                    "type": "POLICY|BUCKET_ACL|S3_ACCESS_POINT|S3_ACCESS_POINT_ACCOUNT",
                    "detail": {
                        "accessPointArn": "string",
                        "accessPointAccount": "string"
                    }
                }
            ]
        }
    ],
    "nextToken": "string"
}
```
