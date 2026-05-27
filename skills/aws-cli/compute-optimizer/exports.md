# Exports

### 3.1 `export-ec2-instance-recommendations`

Exports EC2 instance recommendations to an S3 bucket.

**Synopsis:**
```bash
aws compute-optimizer export-ec2-instance-recommendations \
    --s3-destination-config <value> \
    [--account-ids <value>] \
    [--filters <value>] \
    [--fields-to-export <value>] \
    [--file-format <value>] \
    [--include-member-accounts | --no-include-member-accounts] \
    [--recommendation-preferences <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--s3-destination-config` | **Yes** | structure | -- | S3 destination. Shorthand: `bucket=string,keyPrefix=string` |
| `--account-ids` | No | list(string) | None | Account IDs to export |
| `--filters` | No | list | None | Filter results |
| `--fields-to-export` | No | list(string) | None | Fields to include in export |
| `--file-format` | No | string | `Csv` | Output format: `Csv` |
| `--include-member-accounts` | No | boolean | false | Include all member accounts |
| `--recommendation-preferences` | No | structure | None | Preferences override |

**Output Schema:**
```json
{
    "jobId": "string",
    "s3Destination": {
        "bucket": "string",
        "key": "string",
        "metadataKey": "string"
    }
}
```

---

### 3.2 `export-auto-scaling-group-recommendations`

Exports Auto Scaling group recommendations to an S3 bucket.

**Synopsis:**
```bash
aws compute-optimizer export-auto-scaling-group-recommendations \
    --s3-destination-config <value> \
    [--account-ids <value>] \
    [--filters <value>] \
    [--fields-to-export <value>] \
    [--file-format <value>] \
    [--include-member-accounts | --no-include-member-accounts] \
    [--recommendation-preferences <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--s3-destination-config` | **Yes** | structure | -- | S3 destination. Shorthand: `bucket=string,keyPrefix=string` |
| `--account-ids` | No | list(string) | None | Account IDs to export |
| `--filters` | No | list | None | Filter results |
| `--fields-to-export` | No | list(string) | None | Fields to include |
| `--file-format` | No | string | `Csv` | Output format: `Csv` |
| `--include-member-accounts` | No | boolean | false | Include all member accounts |
| `--recommendation-preferences` | No | structure | None | Preferences override |

**Output Schema:**
```json
{
    "jobId": "string",
    "s3Destination": {
        "bucket": "string",
        "key": "string",
        "metadataKey": "string"
    }
}
```

---

### 3.3 `export-ebs-volume-recommendations`

Exports EBS volume recommendations to an S3 bucket.

**Synopsis:**
```bash
aws compute-optimizer export-ebs-volume-recommendations \
    --s3-destination-config <value> \
    [--account-ids <value>] \
    [--filters <value>] \
    [--fields-to-export <value>] \
    [--file-format <value>] \
    [--include-member-accounts | --no-include-member-accounts] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--s3-destination-config` | **Yes** | structure | -- | S3 destination. Shorthand: `bucket=string,keyPrefix=string` |
| `--account-ids` | No | list(string) | None | Account IDs to export |
| `--filters` | No | list | None | Filter results |
| `--fields-to-export` | No | list(string) | None | Fields to include |
| `--file-format` | No | string | `Csv` | Output format: `Csv` |
| `--include-member-accounts` | No | boolean | false | Include all member accounts |

**Output Schema:**
```json
{
    "jobId": "string",
    "s3Destination": {
        "bucket": "string",
        "key": "string",
        "metadataKey": "string"
    }
}
```

---

### 3.4 `export-lambda-function-recommendations`

Exports Lambda function recommendations to an S3 bucket.

**Synopsis:**
```bash
aws compute-optimizer export-lambda-function-recommendations \
    --s3-destination-config <value> \
    [--account-ids <value>] \
    [--filters <value>] \
    [--fields-to-export <value>] \
    [--file-format <value>] \
    [--include-member-accounts | --no-include-member-accounts] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--s3-destination-config` | **Yes** | structure | -- | S3 destination. Shorthand: `bucket=string,keyPrefix=string` |
| `--account-ids` | No | list(string) | None | Account IDs to export |
| `--filters` | No | list | None | Filter results |
| `--fields-to-export` | No | list(string) | None | Fields to include |
| `--file-format` | No | string | `Csv` | Output format: `Csv` |
| `--include-member-accounts` | No | boolean | false | Include all member accounts |

**Output Schema:**
```json
{
    "jobId": "string",
    "s3Destination": {
        "bucket": "string",
        "key": "string",
        "metadataKey": "string"
    }
}
```

---

### 3.5 `export-ecs-service-recommendations`

Exports ECS service recommendations to an S3 bucket.

**Synopsis:**
```bash
aws compute-optimizer export-ecs-service-recommendations \
    --s3-destination-config <value> \
    [--account-ids <value>] \
    [--filters <value>] \
    [--fields-to-export <value>] \
    [--file-format <value>] \
    [--include-member-accounts | --no-include-member-accounts] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--s3-destination-config` | **Yes** | structure | -- | S3 destination. Shorthand: `bucket=string,keyPrefix=string` |
| `--account-ids` | No | list(string) | None | Account IDs to export |
| `--filters` | No | list | None | Filter results |
| `--fields-to-export` | No | list(string) | None | Fields to include |
| `--file-format` | No | string | `Csv` | Output format: `Csv` |
| `--include-member-accounts` | No | boolean | false | Include all member accounts |

**Output Schema:**
```json
{
    "jobId": "string",
    "s3Destination": {
        "bucket": "string",
        "key": "string",
        "metadataKey": "string"
    }
}
```

---

### 3.6 `export-rds-database-recommendations`

Exports RDS database recommendations to an S3 bucket.

**Synopsis:**
```bash
aws compute-optimizer export-rds-database-recommendations \
    --s3-destination-config <value> \
    [--account-ids <value>] \
    [--filters <value>] \
    [--fields-to-export <value>] \
    [--file-format <value>] \
    [--include-member-accounts | --no-include-member-accounts] \
    [--recommendation-preferences <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--s3-destination-config` | **Yes** | structure | -- | S3 destination. Shorthand: `bucket=string,keyPrefix=string` |
| `--account-ids` | No | list(string) | None | Account IDs to export |
| `--filters` | No | list | None | Filter results |
| `--fields-to-export` | No | list(string) | None | Fields to include |
| `--file-format` | No | string | `Csv` | Output format: `Csv` |
| `--include-member-accounts` | No | boolean | false | Include all member accounts |
| `--recommendation-preferences` | No | structure | None | Preferences override |

**Output Schema:**
```json
{
    "jobId": "string",
    "s3Destination": {
        "bucket": "string",
        "key": "string",
        "metadataKey": "string"
    }
}
```

---

### 3.7 `export-idle-recommendations`

Exports idle resource recommendations to an S3 bucket.

**Synopsis:**
```bash
aws compute-optimizer export-idle-recommendations \
    --s3-destination-config <value> \
    [--account-ids <value>] \
    [--filters <value>] \
    [--fields-to-export <value>] \
    [--file-format <value>] \
    [--include-member-accounts | --no-include-member-accounts] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--s3-destination-config` | **Yes** | structure | -- | S3 destination. Shorthand: `bucket=string,keyPrefix=string` |
| `--account-ids` | No | list(string) | None | Account IDs to export |
| `--filters` | No | list | None | Filter results |
| `--fields-to-export` | No | list(string) | None | Fields to include |
| `--file-format` | No | string | `Csv` | Output format: `Csv` |
| `--include-member-accounts` | No | boolean | false | Include all member accounts |

**Output Schema:**
```json
{
    "jobId": "string",
    "s3Destination": {
        "bucket": "string",
        "key": "string",
        "metadataKey": "string"
    }
}
```
