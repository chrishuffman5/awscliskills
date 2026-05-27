# Transform

## 1. `create-transform-job`

Creates a batch transform job for running inference on a dataset.

**Synopsis:**
```bash
aws sagemaker create-transform-job \
    --transform-job-name <value> \
    --model-name <value> \
    --transform-input <value> \
    --transform-output <value> \
    --transform-resources <value> \
    [--max-concurrent-transforms <value>] \
    [--model-client-config <value>] \
    [--max-payload-in-mb <value>] \
    [--batch-strategy <value>] \
    [--environment <value>] \
    [--data-capture-config <value>] \
    [--data-processing <value>] \
    [--experiment-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--transform-job-name` | **Yes** | string | -- | Unique name (1-63 chars) |
| `--model-name` | **Yes** | string | -- | Model name |
| `--transform-input` | **Yes** | structure | -- | Input data config |
| `--transform-output` | **Yes** | structure | -- | Output data config |
| `--transform-resources` | **Yes** | structure | -- | Instance type and count |
| `--max-concurrent-transforms` | No | integer | -- | Max concurrent mini-batches (min 0) |
| `--model-client-config` | No | structure | -- | `InvocationsTimeoutInSeconds`, `InvocationsMaxRetries` |
| `--max-payload-in-mb` | No | integer | -- | Max payload size (0-100 MB) |
| `--batch-strategy` | No | string | -- | `MultiRecord` or `SingleRecord` |
| `--environment` | No | map | -- | Container environment variables |
| `--data-capture-config` | No | structure | -- | Data capture S3 config |
| `--data-processing` | No | structure | -- | `InputFilter`, `OutputFilter`, `JoinSource` (`Input`/`None`) |
| `--experiment-config` | No | structure | -- | Experiment/trial association |
| `--tags` | No | list | -- | Key-value tags |

**Transform Input:**
```json
{
    "DataSource": {
        "S3DataSource": {
            "S3DataType": "ManifestFile|S3Prefix|AugmentedManifestFile",
            "S3Uri": "string"
        }
    },
    "ContentType": "string",
    "CompressionType": "None|Gzip",
    "SplitType": "None|Line|RecordIO|TFRecord"
}
```

**Transform Output:**
```json
{
    "S3OutputPath": "string",
    "Accept": "string",
    "AssembleWith": "None|Line",
    "KmsKeyId": "string"
}
```

**Transform Resources:**
```json
{
    "InstanceType": "ml.m4.xlarge|ml.m5.xlarge|ml.c5.xlarge|ml.p3.2xlarge|...",
    "InstanceCount": "integer (min: 1)",
    "VolumeKmsKeyId": "string"
}
```

**Output Schema:**
```json
{
    "TransformJobArn": "string"
}
```

---

## 2. `describe-transform-job`

Returns details about a batch transform job.

```bash
aws sagemaker describe-transform-job --transform-job-name <value>
```

**Output Schema:**
```json
{
    "TransformJobName": "string",
    "TransformJobArn": "string",
    "TransformJobStatus": "InProgress|Completed|Failed|Stopping|Stopped",
    "FailureReason": "string",
    "ModelName": "string",
    "MaxConcurrentTransforms": "integer",
    "ModelClientConfig": {"InvocationsTimeoutInSeconds": "integer", "InvocationsMaxRetries": "integer"},
    "MaxPayloadInMB": "integer",
    "BatchStrategy": "MultiRecord|SingleRecord",
    "Environment": {"string": "string"},
    "TransformInput": {...},
    "TransformOutput": {...},
    "DataCaptureConfig": {...},
    "TransformResources": {...},
    "CreationTime": "timestamp",
    "TransformStartTime": "timestamp",
    "TransformEndTime": "timestamp",
    "LabelingJobArn": "string",
    "AutoMLJobArn": "string",
    "DataProcessing": {"InputFilter": "string", "OutputFilter": "string", "JoinSource": "Input|None"},
    "ExperimentConfig": {...}
}
```

---

## 3. `list-transform-jobs`

Lists batch transform jobs. **Paginated operation.**

```bash
aws sagemaker list-transform-jobs \
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
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name-contains` | No | string | -- | Filter by name substring |
| `--status-equals` | No | string | -- | `InProgress`, `Completed`, `Failed`, `Stopping`, `Stopped` |
| `--sort-by` | No | string | `CreationTime` | `Name`, `CreationTime`, `Status` |
| `--sort-order` | No | string | `Descending` | `Ascending`, `Descending` |

---

## 4. `stop-transform-job`

Stops a running batch transform job.

```bash
aws sagemaker stop-transform-job --transform-job-name <value>
```

**Output:** None
