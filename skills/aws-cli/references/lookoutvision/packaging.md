# Packaging

### 4.1 `describe-model-packaging-job`

Describes a model packaging job. Model packaging creates an AWS IoT Greengrass component for deploying a Lookout for Vision model to edge devices.

**Synopsis:**
```bash
aws lookoutvision describe-model-packaging-job \
    --project-name <value> \
    --job-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-name` | **Yes** | string | -- | Project containing the packaging job |
| `--job-name` | **Yes** | string | -- | Name of the packaging job |

**Output Schema:**
```json
{
    "ModelPackagingDescription": {
        "JobName": "string",
        "ProjectName": "string",
        "ModelVersion": "string",
        "ModelPackagingConfiguration": {
            "Greengrass": {
                "CompilerOptions": "string",
                "TargetDevice": "string",
                "TargetPlatform": {
                    "Os": "LINUX",
                    "Arch": "ARM64|X86_64",
                    "Accelerator": "NVIDIA"
                },
                "S3OutputLocation": {
                    "Bucket": "string",
                    "Prefix": "string"
                },
                "ComponentName": "string",
                "ComponentVersion": "string",
                "ComponentDescription": "string",
                "Tags": [
                    {
                        "Key": "string",
                        "Value": "string"
                    }
                ]
            }
        },
        "ModelPackagingJobDescription": "string",
        "ModelPackagingMethod": "string",
        "ModelPackagingOutputDetails": {
            "Greengrass": {
                "ComponentVersionArn": "string",
                "ComponentName": "string",
                "ComponentVersion": "string"
            }
        },
        "Status": "CREATED|RUNNING|SUCCEEDED|FAILED",
        "StatusMessage": "string",
        "CreationTimestamp": "timestamp",
        "LastUpdatedTimestamp": "timestamp"
    }
}
```

---

### 4.2 `list-model-packaging-jobs`

Lists model packaging jobs for a project. **Paginated operation.**

**Synopsis:**
```bash
aws lookoutvision list-model-packaging-jobs \
    --project-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-name` | **Yes** | string | -- | Project to list packaging jobs for |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Maximum total items to return |

**Output Schema:**
```json
{
    "ModelPackagingJobs": [
        {
            "JobName": "string",
            "ProjectName": "string",
            "ModelVersion": "string",
            "ModelPackagingJobDescription": "string",
            "ModelPackagingMethod": "string",
            "Status": "CREATED|RUNNING|SUCCEEDED|FAILED",
            "StatusMessage": "string",
            "CreationTimestamp": "timestamp",
            "LastUpdatedTimestamp": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.3 `start-model-packaging-job`

Starts a model packaging job that creates an AWS IoT Greengrass component for deploying a model to an edge device managed by Greengrass. You can specify a target device or a target platform for compilation.

**Synopsis:**
```bash
aws lookoutvision start-model-packaging-job \
    --project-name <value> \
    --model-version <value> \
    --configuration <value> \
    [--job-name <value>] \
    [--description <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-name` | **Yes** | string | -- | Project containing the model |
| `--model-version` | **Yes** | string | -- | Model version to package |
| `--configuration` | **Yes** | structure | -- | Greengrass component configuration |
| `--job-name` | No | string | Auto | Custom name for the packaging job |
| `--description` | No | string | None | Description for the packaging job |
| `--client-token` | No | string | Auto | Idempotency token (active for 8 hours) |

**Configuration Structure (Greengrass):**
```json
{
    "Greengrass": {
        "CompilerOptions": "string",
        "TargetDevice": "jetson_xavier",
        "TargetPlatform": {
            "Os": "LINUX",
            "Arch": "ARM64|X86_64",
            "Accelerator": "NVIDIA"
        },
        "S3OutputLocation": {
            "Bucket": "string",
            "Prefix": "string"
        },
        "ComponentName": "string",
        "ComponentVersion": "string",
        "ComponentDescription": "string",
        "Tags": [
            {
                "Key": "string",
                "Value": "string"
            }
        ]
    }
}
```

> **Note:** Specify either `TargetDevice` or `TargetPlatform`, not both.

**Output Schema:**
```json
{
    "JobName": "string"
}
```
