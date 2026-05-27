# Processing

## 1. `create-processing-job`

Creates a processing job for data preprocessing, postprocessing, feature engineering, or model evaluation.

**Synopsis:**
```bash
aws sagemaker create-processing-job \
    --processing-job-name <value> \
    --processing-resources <value> \
    --app-specification <value> \
    --role-arn <value> \
    [--processing-inputs <value>] \
    [--processing-output-config <value>] \
    [--stopping-condition <value>] \
    [--environment <value>] \
    [--network-config <value>] \
    [--experiment-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--processing-job-name` | **Yes** | string | -- | Unique name (1-63 chars) |
| `--processing-resources` | **Yes** | structure | -- | Compute cluster config |
| `--app-specification` | **Yes** | structure | -- | Docker container image and entrypoint |
| `--role-arn` | **Yes** | string | -- | IAM role ARN |
| `--processing-inputs` | No | list | -- | Input data (0-10 items, from S3/Athena/Redshift) |
| `--processing-output-config` | No | structure | -- | Output destinations (S3 or Feature Store) |
| `--stopping-condition` | No | structure | -- | `MaxRuntimeInSeconds` (1-777600) |
| `--environment` | No | map | -- | Container environment variables (max 100) |
| `--network-config` | No | structure | -- | VPC config and network isolation |
| `--experiment-config` | No | structure | -- | Experiment/trial association |
| `--tags` | No | list | -- | Key-value tags (max 50) |

**Processing Resources:**
```json
{
    "ClusterConfig": {
        "InstanceCount": "integer (1-100)",
        "InstanceType": "ml.t3.medium|ml.m5.xlarge|ml.c5.xlarge|ml.p3.2xlarge|ml.g4dn.xlarge|...",
        "VolumeSizeInGB": "integer (1-16384)",
        "VolumeKmsKeyId": "string"
    }
}
```

**App Specification:**
```json
{
    "ImageUri": "string",
    "ContainerEntrypoint": ["string"],
    "ContainerArguments": ["string"]
}
```

**Processing Input (S3):**
```json
{
    "InputName": "string",
    "S3Input": {
        "S3Uri": "string",
        "LocalPath": "string",
        "S3DataType": "ManifestFile|S3Prefix",
        "S3InputMode": "Pipe|File",
        "S3DataDistributionType": "FullyReplicated|ShardedByS3Key",
        "S3CompressionType": "None|Gzip"
    }
}
```

**Processing Output:**
```json
{
    "Outputs": [
        {
            "OutputName": "string",
            "S3Output": {
                "S3Uri": "string",
                "LocalPath": "string",
                "S3UploadMode": "Continuous|EndOfJob"
            },
            "FeatureStoreOutput": {
                "FeatureGroupName": "string"
            }
        }
    ],
    "KmsKeyId": "string"
}
```

**Output Schema:**
```json
{
    "ProcessingJobArn": "string"
}
```

---

## 2. `describe-processing-job`

Returns detailed information about a processing job.

**Synopsis:**
```bash
aws sagemaker describe-processing-job \
    --processing-job-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--processing-job-name` | **Yes** | string | -- | Name of the processing job |

**Output Schema:**
```json
{
    "ProcessingJobName": "string",
    "ProcessingJobArn": "string",
    "ProcessingInputs": [...],
    "ProcessingOutputConfig": {...},
    "ProcessingResources": {
        "ClusterConfig": {
            "InstanceCount": "integer",
            "InstanceType": "string",
            "VolumeSizeInGB": "integer",
            "VolumeKmsKeyId": "string"
        }
    },
    "StoppingCondition": {"MaxRuntimeInSeconds": "integer"},
    "AppSpecification": {
        "ImageUri": "string",
        "ContainerEntrypoint": ["string"],
        "ContainerArguments": ["string"]
    },
    "Environment": {"string": "string"},
    "NetworkConfig": {
        "EnableInterContainerTrafficEncryption": "boolean",
        "EnableNetworkIsolation": "boolean",
        "VpcConfig": {"SecurityGroupIds": ["string"], "Subnets": ["string"]}
    },
    "RoleArn": "string",
    "ExperimentConfig": {"ExperimentName": "string", "TrialName": "string", "RunName": "string"},
    "ProcessingJobStatus": "InProgress|Completed|Failed|Stopping|Stopped",
    "ExitMessage": "string",
    "FailureReason": "string",
    "ProcessingEndTime": "timestamp",
    "ProcessingStartTime": "timestamp",
    "LastModifiedTime": "timestamp",
    "CreationTime": "timestamp",
    "AutoMLJobArn": "string",
    "TrainingJobArn": "string"
}
```

---

## 3. `list-processing-jobs`

Lists processing jobs. **Paginated operation.**

**Synopsis:**
```bash
aws sagemaker list-processing-jobs \
    [--creation-time-after <value>] \
    [--creation-time-before <value>] \
    [--last-modified-time-after <value>] \
    [--last-modified-time-before <value>] \
    [--name-contains <value>] \
    [--status-equals <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--creation-time-after` | No | timestamp | -- | Filter by creation time |
| `--creation-time-before` | No | timestamp | -- | Filter by creation time |
| `--name-contains` | No | string | -- | Filter by name substring |
| `--status-equals` | No | string | -- | `InProgress`, `Completed`, `Failed`, `Stopping`, `Stopped` |
| `--sort-by` | No | string | `CreationTime` | `Name`, `CreationTime`, `Status` |
| `--sort-order` | No | string | `Ascending` | `Ascending`, `Descending` |

**Output Schema:**
```json
{
    "ProcessingJobSummaries": [
        {
            "ProcessingJobName": "string",
            "ProcessingJobArn": "string",
            "CreationTime": "timestamp",
            "ProcessingEndTime": "timestamp",
            "LastModifiedTime": "timestamp",
            "ProcessingJobStatus": "InProgress|Completed|Failed|Stopping|Stopped",
            "FailureReason": "string",
            "ExitMessage": "string"
        }
    ],
    "NextToken": "string"
}
```

---

## 4. `stop-processing-job`

Stops a running processing job.

**Synopsis:**
```bash
aws sagemaker stop-processing-job \
    --processing-job-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--processing-job-name` | **Yes** | string | -- | Name of the processing job to stop |

**Output:** None

---

## 5. `delete-processing-job`

Deletes a processing job.

**Synopsis:**
```bash
aws sagemaker delete-processing-job \
    --processing-job-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--processing-job-name` | **Yes** | string | -- | Name of the processing job to delete |

**Output:** None
