# Secret Lifecycle

### 1.1 `create-secret`

Creates a new secret. You can store text or binary data. Optionally replicate to other regions at creation time.

**Synopsis:**
```bash
aws secretsmanager create-secret \
    --name <value> \
    [--client-request-token <value>] \
    [--description <value>] \
    [--kms-key-id <value>] \
    [--secret-binary <value>] \
    [--secret-string <value>] \
    [--tags <value>] \
    [--add-replica-regions <value>] \
    [--force-overwrite-replica-secret | --no-force-overwrite-replica-secret] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Secret name (1-512 chars). Pattern: ASCII letters, numbers, `/_+=.@-`. Do not end with hyphen + 6 characters |
| `--client-request-token` | No | string | auto-generated UUID | Idempotency token (32-64 chars) |
| `--description` | No | string | None | Description of the secret (max 2048 chars) |
| `--kms-key-id` | No | string | `aws/secretsmanager` | ARN, key ID, or alias of KMS key for encryption (max 2048 chars) |
| `--secret-binary` | No | blob | None | Binary data to encrypt (1-65536 bytes). Either `--secret-binary` or `--secret-string` required, not both |
| `--secret-string` | No | string | None | Text data to encrypt (1-65536 chars). JSON key/value pairs recommended |
| `--tags` | No | list | None | Tags: `[{"Key":"name","Value":"value"}]`. Key max 128, Value max 256 chars |
| `--add-replica-regions` | No | list | None | Regions and KMS keys for replicas. Structure: `Region=string,KmsKeyId=string` |
| `--force-overwrite-replica-secret` | No | boolean | false | Overwrite existing secret with same name in destination region |

**Output Schema:**
```json
{
    "ARN": "string",
    "Name": "string",
    "VersionId": "string",
    "ReplicationStatus": [
        {
            "Region": "string",
            "KmsKeyId": "string",
            "Status": "InSync|Failed|InProgress",
            "StatusMessage": "string",
            "LastAccessedDate": "timestamp"
        }
    ]
}
```

---

### 1.2 `delete-secret`

Schedules a secret for deletion. The secret enters a recovery window before permanent deletion.

**Synopsis:**
```bash
aws secretsmanager delete-secret \
    --secret-id <value> \
    [--recovery-window-in-days <value>] \
    [--force-delete-without-recovery | --no-force-delete-without-recovery] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--secret-id` | **Yes** | string | -- | ARN or name of the secret (1-2048 chars) |
| `--recovery-window-in-days` | No | long | 30 | Days before permanent deletion (7-30). Cannot combine with `--force-delete-without-recovery` |
| `--force-delete-without-recovery` | No | boolean | false | Delete immediately with no recovery. Cannot combine with `--recovery-window-in-days` |

**Output Schema:**
```json
{
    "ARN": "string",
    "Name": "string",
    "DeletionDate": "timestamp"
}
```

---

### 1.3 `describe-secret`

Retrieves metadata about a secret. Does **not** return the secret value itself.

**Synopsis:**
```bash
aws secretsmanager describe-secret \
    --secret-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--secret-id` | **Yes** | string | -- | ARN or name of the secret (1-2048 chars) |

**Output Schema:**
```json
{
    "ARN": "string",
    "Name": "string",
    "Description": "string",
    "KmsKeyId": "string",
    "RotationEnabled": true|false,
    "RotationLambdaARN": "string",
    "RotationRules": {
        "AutomaticallyAfterDays": long,
        "Duration": "string",
        "ScheduleExpression": "string"
    },
    "LastRotatedDate": "timestamp",
    "LastChangedDate": "timestamp",
    "LastAccessedDate": "timestamp",
    "DeletedDate": "timestamp",
    "NextRotationDate": "timestamp",
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ],
    "VersionIdsToStages": {
        "string": ["string"]
    },
    "OwningService": "string",
    "CreatedDate": "timestamp",
    "PrimaryRegion": "string",
    "ReplicationStatus": [
        {
            "Region": "string",
            "KmsKeyId": "string",
            "Status": "InSync|Failed|InProgress",
            "StatusMessage": "string",
            "LastAccessedDate": "timestamp"
        }
    ]
}
```

---

### 1.4 `list-secrets`

Lists the secrets stored in the account. **Paginated operation.**

**Synopsis:**
```bash
aws secretsmanager list-secrets \
    [--include-planned-deletion | --no-include-planned-deletion] \
    [--filters <value>] \
    [--sort-order <value>] \
    [--sort-by <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--include-planned-deletion` | No | boolean | false | Include secrets scheduled for deletion |
| `--filters` | No | list | None | Filters to apply (max 10). Keys: `description`, `name`, `tag-key`, `tag-value`, `primary-region`, `owning-service`, `all` |
| `--sort-order` | No | string | `asc` | Sort order: `asc` or `desc` |
| `--sort-by` | No | string | `created-date` | Sort field: `created-date`, `last-accessed-date`, `last-changed-date`, `name` |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Structure:**
```json
[
    {
        "Key": "description|name|tag-key|tag-value|primary-region|owning-service|all",
        "Values": ["string"]
    }
]
```

**Output Schema:**
```json
{
    "SecretList": [
        {
            "ARN": "string",
            "Name": "string",
            "Description": "string",
            "KmsKeyId": "string",
            "RotationEnabled": true|false,
            "RotationLambdaARN": "string",
            "RotationRules": {
                "AutomaticallyAfterDays": long,
                "Duration": "string",
                "ScheduleExpression": "string"
            },
            "LastRotatedDate": "timestamp",
            "LastChangedDate": "timestamp",
            "LastAccessedDate": "timestamp",
            "DeletedDate": "timestamp",
            "NextRotationDate": "timestamp",
            "Tags": [
                {
                    "Key": "string",
                    "Value": "string"
                }
            ],
            "SecretVersionsToStages": {
                "string": ["string"]
            },
            "OwningService": "string",
            "CreatedDate": "timestamp",
            "PrimaryRegion": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `update-secret`

Updates the metadata or value of an existing secret. Creates a new version if `--secret-string` or `--secret-binary` is provided.

**Synopsis:**
```bash
aws secretsmanager update-secret \
    --secret-id <value> \
    [--client-request-token <value>] \
    [--description <value>] \
    [--kms-key-id <value>] \
    [--secret-binary <value>] \
    [--secret-string <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--secret-id` | **Yes** | string | -- | ARN or name of the secret (1-2048 chars) |
| `--client-request-token` | No | string | auto-generated | Idempotency token (32-64 chars) |
| `--description` | No | string | None | Updated description (max 2048 chars) |
| `--kms-key-id` | No | string | existing key | ARN, key ID, or alias for KMS encryption (max 2048 chars) |
| `--secret-binary` | No | blob | None | New binary value (1-65536 bytes). Cannot combine with `--secret-string` |
| `--secret-string` | No | string | None | New text value (1-65536 chars). Cannot combine with `--secret-binary` |

**Output Schema:**
```json
{
    "ARN": "string",
    "Name": "string",
    "VersionId": "string"
}
```

---

### 1.6 `restore-secret`

Cancels the scheduled deletion of a secret by removing the `DeletedDate` timestamp.

**Synopsis:**
```bash
aws secretsmanager restore-secret \
    --secret-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--secret-id` | **Yes** | string | -- | ARN or name of the secret to restore (1-2048 chars) |

**Output Schema:**
```json
{
    "ARN": "string",
    "Name": "string"
}
```

---

### 1.7 `put-secret-value`

Stores a new version of a secret value. Creates a new version with the `AWSCURRENT` staging label.

**Synopsis:**
```bash
aws secretsmanager put-secret-value \
    --secret-id <value> \
    [--client-request-token <value>] \
    [--secret-binary <value>] \
    [--secret-string <value>] \
    [--version-stages <value>] \
    [--rotation-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--secret-id` | **Yes** | string | -- | ARN or name of the secret (1-2048 chars) |
| `--client-request-token` | No | string | auto-generated | Idempotency token (32-64 chars) |
| `--secret-binary` | No | blob | None | Binary data to encrypt (1-65536 bytes). Cannot combine with `--secret-string` |
| `--secret-string` | No | string | None | Text data to encrypt (1-65536 chars). Cannot combine with `--secret-binary` |
| `--version-stages` | No | list(string) | `["AWSCURRENT"]` | Staging labels to attach (1-20 labels, each 1-256 chars) |
| `--rotation-token` | No | string | None | Token for rotation via assumed role or cross-account (36-256 chars) |

**Output Schema:**
```json
{
    "ARN": "string",
    "Name": "string",
    "VersionId": "string",
    "VersionStages": ["string"]
}
```

---
