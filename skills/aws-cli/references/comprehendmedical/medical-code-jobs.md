# Medical Code Jobs

All medical code inference jobs follow the same pattern: start, describe, list, stop. Each job type maps clinical text to a specific medical coding system.

## ICD-10-CM Inference Jobs

### 4.1 `start-icd10-cm-inference-job`

Starts an asynchronous ICD-10-CM inference job on documents in S3.

**Synopsis:**
```bash
aws comprehendmedical start-icd10-cm-inference-job \
    --input-data-config <value> \
    --output-data-config <value> \
    --data-access-role-arn <value> \
    --language-code <value> \
    [--job-name <value>] \
    [--client-request-token <value>] \
    [--kms-key <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-data-config` | **Yes** | structure | -- | Input S3 location: `S3Bucket=string,S3Key=string` |
| `--output-data-config` | **Yes** | structure | -- | Output S3 location: `S3Bucket=string,S3Key=string` |
| `--data-access-role-arn` | **Yes** | string | -- | IAM role ARN with S3 access |
| `--language-code` | **Yes** | string | -- | Must be `en` |
| `--job-name` | No | string | None | Job name (1-256 chars) |
| `--client-request-token` | No | string | None | Idempotency token (1-64 chars) |
| `--kms-key` | No | string | None | KMS key for encryption |

**Output Schema:**
```json
{
    "JobId": "string (1-32 chars)"
}
```

---

### 4.2 `describe-icd10-cm-inference-job`

Gets details about an ICD-10-CM inference job.

**Synopsis:**
```bash
aws comprehendmedical describe-icd10-cm-inference-job \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID (1-32 chars) |

**Output Schema:**
```json
{
    "ComprehendMedicalAsyncJobProperties": {
        "JobId": "string",
        "JobStatus": "SUBMITTED|IN_PROGRESS|COMPLETED|PARTIAL_SUCCESS|FAILED|STOP_REQUESTED|STOPPED",
        "Message": "string",
        "SubmitTime": "timestamp",
        "EndTime": "timestamp",
        "ExpirationTime": "timestamp",
        "InputDataConfig": {"S3Bucket": "string", "S3Key": "string"},
        "OutputDataConfig": {"S3Bucket": "string", "S3Key": "string"},
        "LanguageCode": "en",
        "DataAccessRoleArn": "string",
        "ManifestFilePath": "string",
        "KMSKey": "string",
        "ModelVersion": "string",
        "JobName": "string"
    }
}
```

---

### 4.3 `list-icd10-cm-inference-jobs`

Lists ICD-10-CM inference jobs. **Paginated operation.**

**Synopsis:**
```bash
aws comprehendmedical list-icd10-cm-inference-jobs \
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
| `--filter` | No | structure | None | Filter: `{JobName=string,JobStatus=string,SubmitTimeBefore=timestamp,SubmitTimeAfter=timestamp}` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ComprehendMedicalAsyncJobPropertiesList": [],
    "NextToken": "string"
}
```

---

### 4.4 `stop-icd10-cm-inference-job`

Stops an ICD-10-CM inference job.

**Synopsis:**
```bash
aws comprehendmedical stop-icd10-cm-inference-job \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID (1-32 chars) |

**Output Schema:**
```json
{
    "JobId": "string"
}
```

---

## RxNorm Inference Jobs

### 4.5 `start-rx-norm-inference-job`

Starts an asynchronous RxNorm inference job on documents in S3.

**Synopsis:**
```bash
aws comprehendmedical start-rx-norm-inference-job \
    --input-data-config <value> \
    --output-data-config <value> \
    --data-access-role-arn <value> \
    --language-code <value> \
    [--job-name <value>] \
    [--client-request-token <value>] \
    [--kms-key <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-data-config` | **Yes** | structure | -- | Input S3 location |
| `--output-data-config` | **Yes** | structure | -- | Output S3 location |
| `--data-access-role-arn` | **Yes** | string | -- | IAM role ARN |
| `--language-code` | **Yes** | string | -- | Must be `en` |
| `--job-name` | No | string | None | Job name (1-256 chars) |
| `--client-request-token` | No | string | None | Idempotency token |
| `--kms-key` | No | string | None | KMS key |

**Output Schema:**
```json
{
    "JobId": "string (1-32 chars)"
}
```

---

### 4.6 `describe-rx-norm-inference-job`

Gets details about an RxNorm inference job.

**Synopsis:**
```bash
aws comprehendmedical describe-rx-norm-inference-job \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID (1-32 chars) |

**Output Schema:** Same as `describe-icd10-cm-inference-job`.

---

### 4.7 `list-rx-norm-inference-jobs`

Lists RxNorm inference jobs. **Paginated operation.**

**Synopsis:**
```bash
aws comprehendmedical list-rx-norm-inference-jobs \
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
| `--filter` | No | structure | None | Filter by name, status, or time |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:** Same as `list-icd10-cm-inference-jobs`.

---

### 4.8 `stop-rx-norm-inference-job`

Stops an RxNorm inference job.

**Synopsis:**
```bash
aws comprehendmedical stop-rx-norm-inference-job \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID (1-32 chars) |

**Output Schema:**
```json
{
    "JobId": "string"
}
```

---

## SNOMED CT Inference Jobs

### 4.9 `start-snomedct-inference-job`

Starts an asynchronous SNOMED CT inference job on documents in S3.

**Synopsis:**
```bash
aws comprehendmedical start-snomedct-inference-job \
    --input-data-config <value> \
    --output-data-config <value> \
    --data-access-role-arn <value> \
    --language-code <value> \
    [--job-name <value>] \
    [--client-request-token <value>] \
    [--kms-key <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-data-config` | **Yes** | structure | -- | Input S3 location |
| `--output-data-config` | **Yes** | structure | -- | Output S3 location |
| `--data-access-role-arn` | **Yes** | string | -- | IAM role ARN |
| `--language-code` | **Yes** | string | -- | Must be `en` |
| `--job-name` | No | string | None | Job name (1-256 chars) |
| `--client-request-token` | No | string | None | Idempotency token |
| `--kms-key` | No | string | None | KMS key |

**Output Schema:**
```json
{
    "JobId": "string (1-32 chars)"
}
```

---

### 4.10 `describe-snomedct-inference-job`

Gets details about a SNOMED CT inference job.

**Synopsis:**
```bash
aws comprehendmedical describe-snomedct-inference-job \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID (1-32 chars) |

**Output Schema:** Same as `describe-icd10-cm-inference-job`.

---

### 4.11 `list-snomedct-inference-jobs`

Lists SNOMED CT inference jobs. **Paginated operation.**

**Synopsis:**
```bash
aws comprehendmedical list-snomedct-inference-jobs \
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
| `--filter` | No | structure | None | Filter by name, status, or time |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:** Same as `list-icd10-cm-inference-jobs`.

---

### 4.12 `stop-snomedct-inference-job`

Stops a SNOMED CT inference job.

**Synopsis:**
```bash
aws comprehendmedical stop-snomedct-inference-job \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID (1-32 chars) |

**Output Schema:**
```json
{
    "JobId": "string"
}
```
