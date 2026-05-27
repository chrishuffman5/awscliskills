# Entity Detection Jobs

### 3.1 `start-entities-detection-job`

Starts an asynchronous entity detection job for a collection of documents.

**Synopsis:**
```bash
aws comprehend start-entities-detection-job \
    --input-data-config <value> \
    --output-data-config <value> \
    --data-access-role-arn <value> \
    --language-code <value> \
    [--job-name <value>] \
    [--entity-recognizer-arn <value>] \
    [--client-request-token <value>] \
    [--volume-kms-key-id <value>] \
    [--vpc-config <value>] \
    [--tags <value>] \
    [--flywheel-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-data-config` | **Yes** | structure | -- | Input data location and format. Shorthand: `S3Uri=string,InputFormat=ONE_DOC_PER_FILE\|ONE_DOC_PER_LINE` |
| `--output-data-config` | **Yes** | structure | -- | Output location. Shorthand: `S3Uri=string,KmsKeyId=string` |
| `--data-access-role-arn` | **Yes** | string | -- | IAM role ARN granting read access to input data |
| `--language-code` | **Yes** | string | -- | Language code: `en`, `es`, `fr`, `de`, `it`, `pt`, `ar`, `hi`, `ja`, `ko`, `zh`, `zh-TW` |
| `--job-name` | No | string | -- | Job identifier (1-256 chars) |
| `--entity-recognizer-arn` | No | string | -- | ARN of custom entity recognizer for custom entity detection |
| `--client-request-token` | No | string | auto | Idempotency token (1-64 chars) |
| `--volume-kms-key-id` | No | string | -- | KMS key for encrypting compute instance storage |
| `--vpc-config` | No | structure | -- | VPC config. Shorthand: `SecurityGroupIds=string,string,Subnets=string,string` |
| `--tags` | No | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |
| `--flywheel-arn` | No | string | -- | ARN of flywheel associated with the model |

**Output Schema:**
```json
{
    "JobId": "string",
    "JobArn": "string",
    "JobStatus": "SUBMITTED|IN_PROGRESS|COMPLETED|FAILED|STOP_REQUESTED|STOPPED",
    "EntityRecognizerArn": "string"
}
```

---

### 3.2 `describe-entities-detection-job`

Gets the properties associated with an entities detection job.

**Synopsis:**
```bash
aws comprehend describe-entities-detection-job \
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
    "EntitiesDetectionJobProperties": {
        "JobId": "string",
        "JobArn": "string",
        "JobName": "string",
        "JobStatus": "SUBMITTED|IN_PROGRESS|COMPLETED|FAILED|STOP_REQUESTED|STOPPED",
        "Message": "string",
        "SubmitTime": "timestamp",
        "EndTime": "timestamp",
        "EntityRecognizerArn": "string",
        "InputDataConfig": {
            "S3Uri": "string",
            "InputFormat": "ONE_DOC_PER_FILE|ONE_DOC_PER_LINE",
            "DocumentReaderConfig": {}
        },
        "OutputDataConfig": {
            "S3Uri": "string",
            "KmsKeyId": "string"
        },
        "LanguageCode": "string",
        "DataAccessRoleArn": "string",
        "VolumeKmsKeyId": "string",
        "VpcConfig": {
            "SecurityGroupIds": ["string"],
            "Subnets": ["string"]
        },
        "FlywheelArn": "string"
    }
}
```

---

### 3.3 `list-entities-detection-jobs`

Gets a list of entities detection jobs. **Paginated operation.**

**Synopsis:**
```bash
aws comprehend list-entities-detection-jobs \
    [--filter <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter` | No | structure | -- | Filter results. Shorthand: `JobName=string,JobStatus=SUBMITTED\|IN_PROGRESS\|COMPLETED\|FAILED\|STOP_REQUESTED\|STOPPED,SubmitTimeBefore=timestamp,SubmitTimeAfter=timestamp` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "EntitiesDetectionJobPropertiesList": [
        {
            "JobId": "string",
            "JobArn": "string",
            "JobName": "string",
            "JobStatus": "string",
            "Message": "string",
            "SubmitTime": "timestamp",
            "EndTime": "timestamp",
            "EntityRecognizerArn": "string",
            "InputDataConfig": {},
            "OutputDataConfig": {},
            "LanguageCode": "string",
            "DataAccessRoleArn": "string",
            "VolumeKmsKeyId": "string",
            "VpcConfig": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 3.4 `stop-entities-detection-job`

Stops an entities detection job in progress.

**Synopsis:**
```bash
aws comprehend stop-entities-detection-job \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | The identifier of the job to stop |

**Output Schema:**
```json
{
    "JobId": "string",
    "JobStatus": "SUBMITTED|IN_PROGRESS|COMPLETED|FAILED|STOP_REQUESTED|STOPPED"
}
```
