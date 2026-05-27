# Mailbox

### 7.1 `get-mailbox-details`

Gets mailbox size and quota details for a user.

**Synopsis:**
```bash
aws workmail get-mailbox-details \
    --organization-id <value> \
    --user-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--user-id` | **Yes** | string | -- | User ID, username, or email |

**Output Schema:**
```json
{
    "MailboxQuota": "integer",
    "MailboxSize": "double"
}
```

---

### 7.2 `update-mailbox-quota`

Updates the maximum mailbox size for a user.

**Synopsis:**
```bash
aws workmail update-mailbox-quota \
    --organization-id <value> \
    --user-id <value> \
    --mailbox-quota <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--user-id` | **Yes** | string | -- | User ID, username, or email |
| `--mailbox-quota` | **Yes** | integer | -- | New mailbox quota in MB (min 1) |

**Output:** None

---

### 7.3 `put-mailbox-permissions`

Sets mailbox permissions (full access, send-as, send-on-behalf).

**Synopsis:**
```bash
aws workmail put-mailbox-permissions \
    --organization-id <value> \
    --entity-id <value> \
    --grantee-id <value> \
    --permission-values <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--entity-id` | **Yes** | string | -- | Entity ID (mailbox owner) |
| `--grantee-id` | **Yes** | string | -- | Grantee entity ID |
| `--permission-values` | **Yes** | list | -- | Permissions: `FULL_ACCESS`, `SEND_AS`, `SEND_ON_BEHALF` |

**Output:** None

---

### 7.4 `delete-mailbox-permissions`

Deletes mailbox permissions granted to a grantee.

**Synopsis:**
```bash
aws workmail delete-mailbox-permissions \
    --organization-id <value> \
    --entity-id <value> \
    --grantee-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--entity-id` | **Yes** | string | -- | Entity ID (mailbox owner) |
| `--grantee-id` | **Yes** | string | -- | Grantee entity ID |

**Output:** None

---

### 7.5 `list-mailbox-permissions`

Lists mailbox permissions for an entity. **Paginated operation.**

**Synopsis:**
```bash
aws workmail list-mailbox-permissions \
    --organization-id <value> \
    --entity-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--entity-id` | **Yes** | string | -- | Entity ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "Permissions": [
        {
            "GranteeId": "string",
            "GranteeType": "GROUP|USER",
            "PermissionValues": ["FULL_ACCESS|SEND_AS|SEND_ON_BEHALF"]
        }
    ],
    "NextToken": "string"
}
```

---

### 7.6 `start-mailbox-export-job`

Starts a mailbox export job to export mailbox contents to S3.

**Synopsis:**
```bash
aws workmail start-mailbox-export-job \
    --organization-id <value> \
    --entity-id <value> \
    --role-arn <value> \
    --kms-key-arn <value> \
    --s3-bucket-name <value> \
    --s3-prefix <value> \
    [--client-token <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--entity-id` | **Yes** | string | -- | Entity ID (user or resource) |
| `--role-arn` | **Yes** | string | -- | IAM role ARN with S3 write access |
| `--kms-key-arn` | **Yes** | string | -- | KMS key ARN for encryption |
| `--s3-bucket-name` | **Yes** | string | -- | S3 bucket name (1-63 chars) |
| `--s3-prefix` | **Yes** | string | -- | S3 key prefix (1-1023 chars) |
| `--client-token` | No | string | Auto | Idempotency token |
| `--description` | No | string | None | Job description (0-1023 chars) |

**Output Schema:**
```json
{
    "JobId": "string"
}
```

---

### 7.7 `describe-mailbox-export-job`

Describes a mailbox export job including status and progress.

**Synopsis:**
```bash
aws workmail describe-mailbox-export-job \
    --organization-id <value> \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--job-id` | **Yes** | string | -- | Export job ID |

**Output Schema:**
```json
{
    "EntityId": "string",
    "Description": "string",
    "RoleArn": "string",
    "KmsKeyArn": "string",
    "S3BucketName": "string",
    "S3Prefix": "string",
    "S3Path": "string",
    "EstimatedProgress": "integer",
    "State": "RUNNING|COMPLETED|FAILED|CANCELLED",
    "ErrorInfo": "string",
    "StartTime": "timestamp",
    "EndTime": "timestamp"
}
```

---

### 7.8 `cancel-mailbox-export-job`

Cancels a running mailbox export job.

**Synopsis:**
```bash
aws workmail cancel-mailbox-export-job \
    --organization-id <value> \
    --job-id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--job-id` | **Yes** | string | -- | Export job ID to cancel |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None

---

### 7.9 `list-mailbox-export-jobs`

Lists mailbox export jobs for an organization. **Paginated operation.**

**Synopsis:**
```bash
aws workmail list-mailbox-export-jobs \
    --organization-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "Jobs": [
        {
            "JobId": "string",
            "EntityId": "string",
            "Description": "string",
            "S3BucketName": "string",
            "S3Path": "string",
            "EstimatedProgress": "integer",
            "State": "RUNNING|COMPLETED|FAILED|CANCELLED",
            "StartTime": "timestamp",
            "EndTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
