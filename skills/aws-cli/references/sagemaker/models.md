# Models

## 1. `create-model`

Creates a model in SageMaker. A model contains the location of model artifacts and the Docker image used for inference.

**Synopsis:**
```bash
aws sagemaker create-model \
    --model-name <value> \
    [--primary-container <value>] \
    [--containers <value>] \
    [--inference-execution-config <value>] \
    [--execution-role-arn <value>] \
    [--vpc-config <value>] \
    [--enable-network-isolation | --no-enable-network-isolation] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-name` | **Yes** | string | -- | Model name (0-63 chars, `[a-zA-Z0-9](-*[a-zA-Z0-9])*`) |
| `--primary-container` | No | structure | -- | Primary container with inference code and artifacts |
| `--containers` | No | list | -- | Inference pipeline containers (0-15) |
| `--inference-execution-config` | No | structure | -- | Multi-container mode: `Serial` or `Direct` |
| `--execution-role-arn` | No | string | -- | IAM role ARN for model artifact access |
| `--vpc-config` | No | structure | -- | `SecurityGroupIds`, `Subnets` |
| `--enable-network-isolation` | No | boolean | false | Isolate model container from network |
| `--tags` | No | list | -- | Key-value tags (max 50) |

**Container Structure:**
```json
{
    "ContainerHostname": "string",
    "Image": "string",
    "ImageConfig": {
        "RepositoryAccessMode": "Platform|Vpc",
        "RepositoryAuthConfig": {
            "RepositoryCredentialsProviderArn": "string"
        }
    },
    "Mode": "SingleModel|MultiModel",
    "ModelDataUrl": "string",
    "ModelDataSource": {
        "S3DataSource": {
            "S3Uri": "string",
            "S3DataType": "S3Prefix|S3Object",
            "CompressionType": "None|Gzip",
            "ModelAccessConfig": {"AcceptEula": true},
            "HubAccessConfig": {"HubContentArn": "string"}
        }
    },
    "Environment": {"string": "string"},
    "ModelPackageName": "string",
    "MultiModelConfig": {"ModelCacheSetting": "Enabled|Disabled"}
}
```

**Output Schema:**
```json
{
    "ModelArn": "string"
}
```

---

## 2. `describe-model`

Describes a model.

**Synopsis:**
```bash
aws sagemaker describe-model \
    --model-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-name` | **Yes** | string | -- | Name of the model |

**Output Schema:**
```json
{
    "ModelName": "string",
    "PrimaryContainer": {
        "ContainerHostname": "string",
        "Image": "string",
        "ImageConfig": {
            "RepositoryAccessMode": "Platform|Vpc"
        },
        "Mode": "SingleModel|MultiModel",
        "ModelDataUrl": "string",
        "ModelDataSource": {...},
        "Environment": {"string": "string"},
        "ModelPackageName": "string"
    },
    "Containers": [...],
    "InferenceExecutionConfig": {"Mode": "Serial|Direct"},
    "ExecutionRoleArn": "string",
    "VpcConfig": {
        "SecurityGroupIds": ["string"],
        "Subnets": ["string"]
    },
    "CreationTime": "timestamp",
    "ModelArn": "string",
    "EnableNetworkIsolation": "boolean",
    "DeploymentRecommendation": {
        "RecommendationStatus": "IN_PROGRESS|COMPLETED|FAILED|NOT_APPLICABLE",
        "RealTimeInferenceRecommendations": [
            {
                "RecommendationId": "string",
                "InstanceType": "string",
                "Environment": {"string": "string"}
            }
        ]
    }
}
```

---

## 3. `list-models`

Lists models. **Paginated operation.**

**Synopsis:**
```bash
aws sagemaker list-models \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--name-contains <value>] \
    [--creation-time-before <value>] \
    [--creation-time-after <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sort-by` | No | string | `CreationTime` | `Name`, `CreationTime` |
| `--sort-order` | No | string | `Descending` | `Ascending`, `Descending` |
| `--name-contains` | No | string | -- | Filter by name substring |
| `--creation-time-before` | No | timestamp | -- | Filter by creation time |
| `--creation-time-after` | No | timestamp | -- | Filter by creation time |

**Output Schema:**
```json
{
    "Models": [
        {
            "ModelName": "string",
            "ModelArn": "string",
            "CreationTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

## 4. `delete-model`

Deletes a model. Deleting a model does not delete endpoints that use it.

**Synopsis:**
```bash
aws sagemaker delete-model \
    --model-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-name` | **Yes** | string | -- | Name of the model to delete |

**Output:** None

---

## 5. `create-compilation-job`

Compiles a model for deployment on edge devices or specific instance types using SageMaker Neo.

**Synopsis:**
```bash
aws sagemaker create-compilation-job \
    --compilation-job-name <value> \
    --role-arn <value> \
    --output-config <value> \
    --stopping-condition <value> \
    [--input-config <value>] \
    [--model-package-version-arn <value>] \
    [--vpc-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--compilation-job-name` | **Yes** | string | -- | Unique name (1-63 chars) |
| `--role-arn` | **Yes** | string | -- | IAM role ARN |
| `--output-config` | **Yes** | structure | -- | Target device/platform and S3 output |
| `--stopping-condition` | **Yes** | structure | -- | `MaxRuntimeInSeconds`, `MaxWaitTimeInSeconds` |
| `--input-config` | No | structure | -- | `S3Uri`, `DataInputConfig`, `Framework` (`TENSORFLOW`/`PYTORCH`/`MXNET`/`ONNX`/`XGBOOST`/etc.), `FrameworkVersion` |
| `--model-package-version-arn` | No | string | -- | Alternative to `--input-config` |
| `--vpc-config` | No | structure | -- | VPC config |
| `--tags` | No | list | -- | Key-value tags (max 50) |

**Output Config Structure:**
```json
{
    "S3OutputLocation": "string",
    "TargetDevice": "lambda|ml_m4|ml_m5|ml_c4|ml_c5|ml_p2|ml_p3|ml_g4dn|ml_inf1|ml_inf2|ml_trn1|jetson_tx1|jetson_tx2|jetson_nano|jetson_xavier|rasp3b|rasp4b|...",
    "TargetPlatform": {
        "Os": "ANDROID|LINUX",
        "Arch": "X86_64|X86|ARM64|ARM_EABI|ARM_EABIHF",
        "Accelerator": "INTEL_GRAPHICS|MALI|NVIDIA|NNA"
    },
    "CompilerOptions": "string",
    "KmsKeyId": "string"
}
```

**Output Schema:**
```json
{
    "CompilationJobArn": "string"
}
```

---

## 6. `describe-compilation-job`

Returns information about a compilation job.

**Synopsis:**
```bash
aws sagemaker describe-compilation-job \
    --compilation-job-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--compilation-job-name` | **Yes** | string | -- | Name of the compilation job |

**Output Schema:**
```json
{
    "CompilationJobName": "string",
    "CompilationJobArn": "string",
    "CompilationJobStatus": "INPROGRESS|COMPLETED|FAILED|STARTING|STOPPING|STOPPED",
    "CompilationStartTime": "timestamp",
    "CompilationEndTime": "timestamp",
    "StoppingCondition": {"MaxRuntimeInSeconds": "integer"},
    "InferenceImage": "string",
    "ModelPackageVersionArn": "string",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp",
    "FailureReason": "string",
    "ModelArtifacts": {"S3ModelArtifacts": "string"},
    "ModelDigests": {"ArtifactDigest": "string"},
    "RoleArn": "string",
    "InputConfig": {
        "S3Uri": "string",
        "DataInputConfig": "string",
        "Framework": "TENSORFLOW|KERAS|MXNET|ONNX|PYTORCH|XGBOOST|TFLITE|DARKNET|SKLEARN",
        "FrameworkVersion": "string"
    },
    "OutputConfig": {
        "S3OutputLocation": "string",
        "TargetDevice": "string",
        "TargetPlatform": {"Os": "string", "Arch": "string", "Accelerator": "string"},
        "CompilerOptions": "string",
        "KmsKeyId": "string"
    },
    "VpcConfig": {"SecurityGroupIds": ["string"], "Subnets": ["string"]},
    "DerivedInformation": {"DerivedDataInputConfig": "string"}
}
```

---

## 7. `list-compilation-jobs`

Lists compilation jobs. **Paginated operation.**

**Synopsis:**
```bash
aws sagemaker list-compilation-jobs \
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
| `--status-equals` | No | string | -- | `INPROGRESS`, `COMPLETED`, `FAILED`, `STARTING`, `STOPPING`, `STOPPED` |
| `--sort-by` | No | string | `CreationTime` | `Name`, `CreationTime`, `Status` |
| `--sort-order` | No | string | `Ascending` | `Ascending`, `Descending` |

**Output Schema:**
```json
{
    "CompilationJobSummaries": [
        {
            "CompilationJobName": "string",
            "CompilationJobArn": "string",
            "CreationTime": "timestamp",
            "CompilationStartTime": "timestamp",
            "CompilationEndTime": "timestamp",
            "CompilationTargetDevice": "string",
            "CompilationTargetPlatformOs": "ANDROID|LINUX",
            "CompilationTargetPlatformArch": "X86_64|X86|ARM64|ARM_EABI|ARM_EABIHF",
            "CompilationTargetPlatformAccelerator": "INTEL_GRAPHICS|MALI|NVIDIA|NNA",
            "LastModifiedTime": "timestamp",
            "CompilationJobStatus": "INPROGRESS|COMPLETED|FAILED|STARTING|STOPPING|STOPPED"
        }
    ],
    "NextToken": "string"
}
```

---

## 8. `stop-compilation-job`

Stops a running compilation job.

**Synopsis:**
```bash
aws sagemaker stop-compilation-job \
    --compilation-job-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--compilation-job-name` | **Yes** | string | -- | Name of the compilation job to stop |

**Output:** None

---

## 9. `delete-compilation-job`

Deletes a compilation job.

**Synopsis:**
```bash
aws sagemaker delete-compilation-job \
    --compilation-job-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--compilation-job-name` | **Yes** | string | -- | Name of the compilation job to delete |

**Output:** None
