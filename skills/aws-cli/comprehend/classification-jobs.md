# Classification Jobs

### 4.1 `start-document-classification-job`

Starts an asynchronous document classification job using a custom classifier.

**Synopsis:**
```bash
aws comprehend start-document-classification-job \
    --input-data-config <value> \
    --output-data-config <value> \
    --data-access-role-arn <value> \
    [--job-name <value>] \
    [--document-classifier-arn <value>] \
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
| `--job-name` | No | string | -- | Job identifier (1-256 chars) |
| `--document-classifier-arn` | No | string | -- | ARN of the document classifier to use |
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
    "DocumentClassifierArn": "string"
}
```

---

### 4.2 `describe-document-classification-job`

Gets the properties associated with a document classification job.

**Synopsis:**
```bash
aws comprehend describe-document-classification-job \
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
    "DocumentClassificationJobProperties": {
        "JobId": "string",
        "JobArn": "string",
        "JobName": "string",
        "JobStatus": "SUBMITTED|IN_PROGRESS|COMPLETED|FAILED|STOP_REQUESTED|STOPPED",
        "Message": "string",
        "SubmitTime": "timestamp",
        "EndTime": "timestamp",
        "DocumentClassifierArn": "string",
        "InputDataConfig": {
            "S3Uri": "string",
            "InputFormat": "ONE_DOC_PER_FILE|ONE_DOC_PER_LINE",
            "DocumentReaderConfig": {}
        },
        "OutputDataConfig": {
            "S3Uri": "string",
            "KmsKeyId": "string"
        },
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

### 4.3 `list-document-classification-jobs`

Gets a list of document classification jobs. **Paginated operation.**

**Synopsis:**
```bash
aws comprehend list-document-classification-jobs \
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
    "DocumentClassificationJobPropertiesList": [
        {
            "JobId": "string",
            "JobArn": "string",
            "JobName": "string",
            "JobStatus": "string",
            "Message": "string",
            "SubmitTime": "timestamp",
            "EndTime": "timestamp",
            "DocumentClassifierArn": "string",
            "InputDataConfig": {},
            "OutputDataConfig": {},
            "DataAccessRoleArn": "string",
            "VolumeKmsKeyId": "string",
            "VpcConfig": {}
        }
    ],
    "NextToken": "string"
}
```
