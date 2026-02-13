# Other Jobs

This file covers asynchronous detection jobs for dominant language, key phrases, sentiment, targeted sentiment, PII entities, events, and topics.

All job-start commands share a common pattern of required parameters: `--input-data-config`, `--output-data-config`, `--data-access-role-arn`, and `--language-code` (except topics detection). All return `JobId`, `JobArn`, and `JobStatus`.

---

### 5.1 `start-dominant-language-detection-job`

Starts an asynchronous dominant language detection job.

**Synopsis:**
```bash
aws comprehend start-dominant-language-detection-job \
    --input-data-config <value> \
    --output-data-config <value> \
    --data-access-role-arn <value> \
    [--job-name <value>] \
    [--client-request-token <value>] \
    [--volume-kms-key-id <value>] \
    [--vpc-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-data-config` | **Yes** | structure | -- | Input data location. Shorthand: `S3Uri=string,InputFormat=ONE_DOC_PER_FILE\|ONE_DOC_PER_LINE` |
| `--output-data-config` | **Yes** | structure | -- | Output location. Shorthand: `S3Uri=string,KmsKeyId=string` |
| `--data-access-role-arn` | **Yes** | string | -- | IAM role ARN |
| `--job-name` | No | string | -- | Job identifier |
| `--client-request-token` | No | string | auto | Idempotency token |
| `--volume-kms-key-id` | No | string | -- | KMS key for storage volume |
| `--vpc-config` | No | structure | -- | VPC configuration |
| `--tags` | No | list | -- | Tags |

**Output Schema:**
```json
{
    "JobId": "string",
    "JobArn": "string",
    "JobStatus": "SUBMITTED|IN_PROGRESS|COMPLETED|FAILED|STOP_REQUESTED|STOPPED"
}
```

---

### 5.2 `describe-dominant-language-detection-job`

Gets properties of a dominant language detection job.

**Synopsis:**
```bash
aws comprehend describe-dominant-language-detection-job \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | The identifier of the job |

**Output Schema:**
```json
{
    "DominantLanguageDetectionJobProperties": {
        "JobId": "string",
        "JobArn": "string",
        "JobName": "string",
        "JobStatus": "string",
        "Message": "string",
        "SubmitTime": "timestamp",
        "EndTime": "timestamp",
        "InputDataConfig": {},
        "OutputDataConfig": {},
        "DataAccessRoleArn": "string",
        "VolumeKmsKeyId": "string",
        "VpcConfig": {}
    }
}
```

---

### 5.3 `list-dominant-language-detection-jobs`

Gets a list of dominant language detection jobs. **Paginated.**

**Synopsis:**
```bash
aws comprehend list-dominant-language-detection-jobs \
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
| `--filter` | No | structure | -- | Filter by JobName, JobStatus, SubmitTimeBefore, SubmitTimeAfter |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

---

### 5.4 `stop-dominant-language-detection-job`

Stops a dominant language detection job in progress.

**Synopsis:**
```bash
aws comprehend stop-dominant-language-detection-job \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | The identifier of the job |

**Output Schema:**
```json
{
    "JobId": "string",
    "JobStatus": "string"
}
```

---

### 5.5 `start-key-phrases-detection-job`

Starts an asynchronous key phrases detection job.

**Synopsis:**
```bash
aws comprehend start-key-phrases-detection-job \
    --input-data-config <value> \
    --output-data-config <value> \
    --data-access-role-arn <value> \
    --language-code <value> \
    [--job-name <value>] \
    [--client-request-token <value>] \
    [--volume-kms-key-id <value>] \
    [--vpc-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-data-config` | **Yes** | structure | -- | Input data location and format |
| `--output-data-config` | **Yes** | structure | -- | Output location |
| `--data-access-role-arn` | **Yes** | string | -- | IAM role ARN |
| `--language-code` | **Yes** | string | -- | Language code |
| `--job-name` | No | string | -- | Job identifier |
| `--client-request-token` | No | string | auto | Idempotency token |
| `--volume-kms-key-id` | No | string | -- | KMS key for storage volume |
| `--vpc-config` | No | structure | -- | VPC configuration |
| `--tags` | No | list | -- | Tags |

**Output Schema:**
```json
{
    "JobId": "string",
    "JobArn": "string",
    "JobStatus": "SUBMITTED|IN_PROGRESS|COMPLETED|FAILED|STOP_REQUESTED|STOPPED"
}
```

---

### 5.6 `describe-key-phrases-detection-job`

Gets properties of a key phrases detection job.

**Synopsis:**
```bash
aws comprehend describe-key-phrases-detection-job \
    --job-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | The identifier of the job |

---

### 5.7 `list-key-phrases-detection-jobs`

Gets a list of key phrases detection jobs. **Paginated.**

**Synopsis:**
```bash
aws comprehend list-key-phrases-detection-jobs \
    [--filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

---

### 5.8 `stop-key-phrases-detection-job`

Stops a key phrases detection job in progress.

**Synopsis:**
```bash
aws comprehend stop-key-phrases-detection-job \
    --job-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | The identifier of the job |

---

### 5.9 `start-sentiment-detection-job`

Starts an asynchronous sentiment detection job.

**Synopsis:**
```bash
aws comprehend start-sentiment-detection-job \
    --input-data-config <value> \
    --output-data-config <value> \
    --data-access-role-arn <value> \
    --language-code <value> \
    [--job-name <value>] \
    [--client-request-token <value>] \
    [--volume-kms-key-id <value>] \
    [--vpc-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-data-config` | **Yes** | structure | -- | Input data location and format |
| `--output-data-config` | **Yes** | structure | -- | Output location |
| `--data-access-role-arn` | **Yes** | string | -- | IAM role ARN |
| `--language-code` | **Yes** | string | -- | Language code |
| `--job-name` | No | string | -- | Job identifier |
| `--client-request-token` | No | string | auto | Idempotency token |
| `--volume-kms-key-id` | No | string | -- | KMS key for storage volume |
| `--vpc-config` | No | structure | -- | VPC configuration |
| `--tags` | No | list | -- | Tags |

**Output Schema:**
```json
{
    "JobId": "string",
    "JobArn": "string",
    "JobStatus": "SUBMITTED|IN_PROGRESS|COMPLETED|FAILED|STOP_REQUESTED|STOPPED"
}
```

---

### 5.10 `describe-sentiment-detection-job`

Gets properties of a sentiment detection job.

**Synopsis:**
```bash
aws comprehend describe-sentiment-detection-job \
    --job-id <value>
```

---

### 5.11 `list-sentiment-detection-jobs`

Gets a list of sentiment detection jobs. **Paginated.**

**Synopsis:**
```bash
aws comprehend list-sentiment-detection-jobs \
    [--filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

---

### 5.12 `stop-sentiment-detection-job`

Stops a sentiment detection job in progress.

**Synopsis:**
```bash
aws comprehend stop-sentiment-detection-job \
    --job-id <value>
```

---

### 5.13 `start-targeted-sentiment-detection-job`

Starts an asynchronous targeted sentiment detection job.

**Synopsis:**
```bash
aws comprehend start-targeted-sentiment-detection-job \
    --input-data-config <value> \
    --output-data-config <value> \
    --data-access-role-arn <value> \
    --language-code <value> \
    [--job-name <value>] \
    [--client-request-token <value>] \
    [--volume-kms-key-id <value>] \
    [--vpc-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-data-config` | **Yes** | structure | -- | Input data location and format |
| `--output-data-config` | **Yes** | structure | -- | Output location |
| `--data-access-role-arn` | **Yes** | string | -- | IAM role ARN |
| `--language-code` | **Yes** | string | -- | Language code |
| `--job-name` | No | string | -- | Job identifier |
| `--client-request-token` | No | string | auto | Idempotency token |
| `--volume-kms-key-id` | No | string | -- | KMS key for storage volume |
| `--vpc-config` | No | structure | -- | VPC configuration |
| `--tags` | No | list | -- | Tags |

**Output Schema:**
```json
{
    "JobId": "string",
    "JobArn": "string",
    "JobStatus": "SUBMITTED|IN_PROGRESS|COMPLETED|FAILED|STOP_REQUESTED|STOPPED"
}
```

---

### 5.14 `describe-targeted-sentiment-detection-job`

Gets properties of a targeted sentiment detection job.

**Synopsis:**
```bash
aws comprehend describe-targeted-sentiment-detection-job \
    --job-id <value>
```

---

### 5.15 `list-targeted-sentiment-detection-jobs`

Gets a list of targeted sentiment detection jobs. **Paginated.**

**Synopsis:**
```bash
aws comprehend list-targeted-sentiment-detection-jobs \
    [--filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

---

### 5.16 `stop-targeted-sentiment-detection-job`

Stops a targeted sentiment detection job in progress.

**Synopsis:**
```bash
aws comprehend stop-targeted-sentiment-detection-job \
    --job-id <value>
```

---

### 5.17 `start-pii-entities-detection-job`

Starts an asynchronous PII entities detection job.

**Synopsis:**
```bash
aws comprehend start-pii-entities-detection-job \
    --input-data-config <value> \
    --output-data-config <value> \
    --mode <value> \
    --data-access-role-arn <value> \
    --language-code <value> \
    [--redaction-config <value>] \
    [--job-name <value>] \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-data-config` | **Yes** | structure | -- | Input data location and format |
| `--output-data-config` | **Yes** | structure | -- | Output location |
| `--mode` | **Yes** | string | -- | Output type: `ONLY_REDACTION` or `ONLY_OFFSETS` |
| `--data-access-role-arn` | **Yes** | string | -- | IAM role ARN |
| `--language-code` | **Yes** | string | -- | Language code |
| `--redaction-config` | No | structure | -- | PII redaction config (required if mode is `ONLY_REDACTION`). Shorthand: `PiiEntityTypes=NAME\|SSN\|...,MaskMode=MASK\|REPLACE_WITH_PII_ENTITY_TYPE,MaskCharacter=string` |
| `--job-name` | No | string | -- | Job identifier |
| `--client-request-token` | No | string | auto | Idempotency token |
| `--tags` | No | list | -- | Tags |

**Output Schema:**
```json
{
    "JobId": "string",
    "JobArn": "string",
    "JobStatus": "SUBMITTED|IN_PROGRESS|COMPLETED|FAILED|STOP_REQUESTED|STOPPED"
}
```

---

### 5.18 `describe-pii-entities-detection-job`

Gets properties of a PII entities detection job.

**Synopsis:**
```bash
aws comprehend describe-pii-entities-detection-job \
    --job-id <value>
```

---

### 5.19 `list-pii-entities-detection-jobs`

Gets a list of PII entities detection jobs. **Paginated.**

**Synopsis:**
```bash
aws comprehend list-pii-entities-detection-jobs \
    [--filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

---

### 5.20 `stop-pii-entities-detection-job`

Stops a PII entities detection job in progress.

**Synopsis:**
```bash
aws comprehend stop-pii-entities-detection-job \
    --job-id <value>
```

---

### 5.21 `start-events-detection-job`

Starts an asynchronous events detection job.

**Synopsis:**
```bash
aws comprehend start-events-detection-job \
    --input-data-config <value> \
    --output-data-config <value> \
    --data-access-role-arn <value> \
    --language-code <value> \
    --target-event-types <value> \
    [--job-name <value>] \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-data-config` | **Yes** | structure | -- | Input data location and format |
| `--output-data-config` | **Yes** | structure | -- | Output location |
| `--data-access-role-arn` | **Yes** | string | -- | IAM role ARN |
| `--language-code` | **Yes** | string | -- | Language code (currently `en` only) |
| `--target-event-types` | **Yes** | list(string) | -- | Event types to detect (e.g., `BANKRUPTCY`, `EMPLOYMENT`, `CORPORATE_ACQUISITION`, `INVESTMENT_GENERAL`, `CORPORATE_MERGER`, `IPO`, `RIGHTS_ISSUE`, `SECONDARY_OFFERING`, `SHELF_OFFERING`, `TENDER_OFFERING`, `STOCK_SPLIT`) |
| `--job-name` | No | string | -- | Job identifier |
| `--client-request-token` | No | string | auto | Idempotency token |
| `--tags` | No | list | -- | Tags |

**Output Schema:**
```json
{
    "JobId": "string",
    "JobArn": "string",
    "JobStatus": "SUBMITTED|IN_PROGRESS|COMPLETED|FAILED|STOP_REQUESTED|STOPPED"
}
```

---

### 5.22 `describe-events-detection-job`

Gets properties of an events detection job.

**Synopsis:**
```bash
aws comprehend describe-events-detection-job \
    --job-id <value>
```

---

### 5.23 `list-events-detection-jobs`

Gets a list of events detection jobs. **Paginated.**

**Synopsis:**
```bash
aws comprehend list-events-detection-jobs \
    [--filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

---

### 5.24 `stop-events-detection-job`

Stops an events detection job in progress.

**Synopsis:**
```bash
aws comprehend stop-events-detection-job \
    --job-id <value>
```

---

### 5.25 `start-topics-detection-job`

Starts an asynchronous topic detection job. Does not require `--language-code`.

**Synopsis:**
```bash
aws comprehend start-topics-detection-job \
    --input-data-config <value> \
    --output-data-config <value> \
    --data-access-role-arn <value> \
    [--job-name <value>] \
    [--number-of-topics <value>] \
    [--client-request-token <value>] \
    [--volume-kms-key-id <value>] \
    [--vpc-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-data-config` | **Yes** | structure | -- | Input data location and format |
| `--output-data-config` | **Yes** | structure | -- | Output location (receives topic-terms.csv and doc-topics.csv) |
| `--data-access-role-arn` | **Yes** | string | -- | IAM role ARN |
| `--job-name` | No | string | -- | Job identifier |
| `--number-of-topics` | No | integer | -- | Number of topics to detect (1-100) |
| `--client-request-token` | No | string | auto | Idempotency token |
| `--volume-kms-key-id` | No | string | -- | KMS key for storage volume |
| `--vpc-config` | No | structure | -- | VPC configuration |
| `--tags` | No | list | -- | Tags |

**Output Schema:**
```json
{
    "JobId": "string",
    "JobArn": "string",
    "JobStatus": "SUBMITTED|IN_PROGRESS|COMPLETED|FAILED|STOP_REQUESTED|STOPPED"
}
```

---

### 5.26 `describe-topics-detection-job`

Gets properties of a topics detection job.

**Synopsis:**
```bash
aws comprehend describe-topics-detection-job \
    --job-id <value>
```

---

### 5.27 `list-topics-detection-jobs`

Gets a list of topics detection jobs. **Paginated.**

**Synopsis:**
```bash
aws comprehend list-topics-detection-jobs \
    [--filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```
