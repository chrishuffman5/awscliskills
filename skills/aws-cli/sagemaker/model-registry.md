# Model Registry

## 1. `create-model-package-group`

Creates a model package group for organizing versioned model packages.

**Synopsis:**
```bash
aws sagemaker create-model-package-group \
    --model-package-group-name <value> \
    [--model-package-group-description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-package-group-name` | **Yes** | string | -- | Group name (1-63 chars) |
| `--model-package-group-description` | No | string | -- | Description (max 1024 chars) |
| `--tags` | No | list | -- | Key-value tags |

**Output Schema:**
```json
{
    "ModelPackageGroupArn": "string"
}
```

---

## 2. `describe-model-package-group`

Returns details about a model package group.

**Synopsis:**
```bash
aws sagemaker describe-model-package-group \
    --model-package-group-name <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-package-group-name` | **Yes** | string | -- | Group name or ARN |

**Output Schema:**
```json
{
    "ModelPackageGroupName": "string",
    "ModelPackageGroupArn": "string",
    "ModelPackageGroupDescription": "string",
    "CreationTime": "timestamp",
    "CreatedBy": {"UserProfileArn": "string", "UserProfileName": "string", "DomainId": "string"},
    "ModelPackageGroupStatus": "Pending|InProgress|Completed|Failed|Deleting|DeleteFailed"
}
```

---

## 3. `list-model-package-groups`

Lists model package groups. **Paginated operation.**

**Synopsis:**
```bash
aws sagemaker list-model-package-groups \
    [--creation-time-after <value>] \
    [--creation-time-before <value>] \
    [--name-contains <value>] \
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
| `--sort-by` | No | string | `CreationTime` | `Name`, `CreationTime` |
| `--sort-order` | No | string | `Ascending` | `Ascending`, `Descending` |

**Output Schema:**
```json
{
    "ModelPackageGroupSummaryList": [
        {
            "ModelPackageGroupName": "string",
            "ModelPackageGroupArn": "string",
            "ModelPackageGroupDescription": "string",
            "CreationTime": "timestamp",
            "ModelPackageGroupStatus": "string"
        }
    ],
    "NextToken": "string"
}
```

---

## 4. `delete-model-package-group`

Deletes a model package group (must be empty).

**Synopsis:**
```bash
aws sagemaker delete-model-package-group \
    --model-package-group-name <value>
```

**Output:** None

---

## 5. `get-model-package-group-policy` / `put-model-package-group-policy` / `delete-model-package-group-policy`

Manage resource policies for model package groups.

**Synopsis:**
```bash
aws sagemaker get-model-package-group-policy --model-package-group-name <value>
aws sagemaker put-model-package-group-policy --model-package-group-name <value> --resource-policy <value>
aws sagemaker delete-model-package-group-policy --model-package-group-name <value>
```

---

## 6. `create-model-package`

Creates a versioned model package for the model registry.

**Synopsis:**
```bash
aws sagemaker create-model-package \
    [--model-package-name <value>] \
    [--model-package-group-name <value>] \
    [--model-package-description <value>] \
    [--inference-specification <value>] \
    [--validation-specification <value>] \
    [--source-algorithm-specification <value>] \
    [--model-approval-status <value>] \
    [--model-metrics <value>] \
    [--client-token <value>] \
    [--domain <value>] \
    [--task <value>] \
    [--sample-payload-url <value>] \
    [--customer-metadata-properties <value>] \
    [--drift-check-baselines <value>] \
    [--additional-inference-specifications <value>] \
    [--skip-model-validation <value>] \
    [--source-uri <value>] \
    [--security-config <value>] \
    [--model-card <value>] \
    [--model-life-cycle <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-package-name` | No | string | -- | Name for unversioned package |
| `--model-package-group-name` | No | string | -- | Group name for versioned package |
| `--model-package-description` | No | string | -- | Description |
| `--inference-specification` | No | structure | -- | Container images, instance types, content types |
| `--validation-specification` | No | structure | -- | Validation profiles |
| `--source-algorithm-specification` | No | structure | -- | Source algorithms |
| `--model-approval-status` | No | string | -- | `Approved`, `Rejected`, `PendingManualApproval` |
| `--model-metrics` | No | structure | -- | Model quality, bias, explainability metrics |
| `--drift-check-baselines` | No | structure | -- | Drift check baselines |
| `--skip-model-validation` | No | string | -- | `All`, `None` |
| `--source-uri` | No | string | -- | Source URI |
| `--model-card` | No | structure | -- | Model card content or ARN |
| `--tags` | No | list | -- | Key-value tags |

**Inference Specification:**
```json
{
    "Containers": [
        {
            "Image": "string",
            "ImageDigest": "string",
            "ModelDataUrl": "string",
            "ModelDataSource": {...},
            "ProductId": "string",
            "Environment": {"string": "string"},
            "ModelInput": {"DataInputConfig": "string"},
            "Framework": "string",
            "FrameworkVersion": "string",
            "NearestModelName": "string",
            "AdditionalS3DataSource": {...}
        }
    ],
    "SupportedTransformInstanceTypes": ["ml.m5.xlarge", "..."],
    "SupportedRealtimeInferenceInstanceTypes": ["ml.m5.xlarge", "..."],
    "SupportedContentTypes": ["text/csv", "application/json"],
    "SupportedResponseMIMETypes": ["text/csv", "application/json"]
}
```

**Output Schema:**
```json
{
    "ModelPackageArn": "string"
}
```

---

## 7. `describe-model-package`

Returns details about a model package.

**Synopsis:**
```bash
aws sagemaker describe-model-package \
    --model-package-name <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-package-name` | **Yes** | string | -- | Model package name, ARN, or versioned ARN |

**Output Schema:**
```json
{
    "ModelPackageName": "string",
    "ModelPackageGroupName": "string",
    "ModelPackageVersion": "integer",
    "ModelPackageArn": "string",
    "ModelPackageDescription": "string",
    "CreationTime": "timestamp",
    "InferenceSpecification": {...},
    "SourceAlgorithmSpecification": {...},
    "ValidationSpecification": {...},
    "ModelPackageStatus": "Pending|InProgress|Completed|Failed|Deleting",
    "ModelPackageStatusDetails": {
        "ValidationStatuses": [{"Name": "string", "Status": "NotStarted|InProgress|Completed|Failed", "FailureReason": "string"}],
        "ImageScanStatuses": [...]
    },
    "CertifyForMarketplace": "boolean",
    "ModelApprovalStatus": "Approved|Rejected|PendingManualApproval",
    "CreatedBy": {...},
    "MetadataProperties": {...},
    "ModelMetrics": {...},
    "LastModifiedTime": "timestamp",
    "LastModifiedBy": {...},
    "ApprovalDescription": "string",
    "Domain": "string",
    "Task": "string",
    "SamplePayloadUrl": "string",
    "CustomerMetadataProperties": {"string": "string"},
    "DriftCheckBaselines": {...},
    "AdditionalInferenceSpecifications": [...],
    "SkipModelValidation": "All|None",
    "SourceUri": "string",
    "SecurityConfig": {...},
    "ModelCard": {...},
    "ModelLifeCycle": {...}
}
```

---

## 8. `list-model-packages`

Lists model packages. **Paginated operation.**

**Synopsis:**
```bash
aws sagemaker list-model-packages \
    [--model-approval-status <value>] \
    [--model-package-group-name <value>] \
    [--model-package-type <value>] \
    [--name-contains <value>] \
    [--creation-time-after <value>] \
    [--creation-time-before <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-approval-status` | No | string | -- | `Approved`, `Rejected`, `PendingManualApproval` |
| `--model-package-group-name` | No | string | -- | Filter by group name |
| `--model-package-type` | No | string | -- | `Versioned`, `Unversioned`, `Both` |
| `--name-contains` | No | string | -- | Filter by name substring |
| `--sort-by` | No | string | `CreationTime` | `Name`, `CreationTime` |
| `--sort-order` | No | string | `Ascending` | `Ascending`, `Descending` |

**Output Schema:**
```json
{
    "ModelPackageSummaryList": [
        {
            "ModelPackageName": "string",
            "ModelPackageGroupName": "string",
            "ModelPackageVersion": "integer",
            "ModelPackageArn": "string",
            "ModelPackageDescription": "string",
            "CreationTime": "timestamp",
            "ModelPackageStatus": "Pending|InProgress|Completed|Failed|Deleting",
            "ModelApprovalStatus": "Approved|Rejected|PendingManualApproval"
        }
    ],
    "NextToken": "string"
}
```

---

## 9. `update-model-package`

Updates a model package (approval status, description, metadata).

**Synopsis:**
```bash
aws sagemaker update-model-package \
    --model-package-arn <value> \
    [--model-approval-status <value>] \
    [--approval-description <value>] \
    [--customer-metadata-properties <value>] \
    [--customer-metadata-properties-to-remove <value>] \
    [--additional-inference-specifications-to-add <value>] \
    [--inference-specification <value>] \
    [--source-uri <value>] \
    [--model-card <value>] \
    [--model-life-cycle <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-package-arn` | **Yes** | string | -- | Model package ARN |
| `--model-approval-status` | No | string | -- | `Approved`, `Rejected`, `PendingManualApproval` |
| `--approval-description` | No | string | -- | Approval description |

**Output Schema:**
```json
{
    "ModelPackageArn": "string"
}
```

---

## 10. `delete-model-package`

Deletes a model package.

**Synopsis:**
```bash
aws sagemaker delete-model-package \
    --model-package-name <value>
```

**Output:** None

---

## 11. `batch-describe-model-package`

Gets details about multiple model packages in a single call.

**Synopsis:**
```bash
aws sagemaker batch-describe-model-package \
    --model-package-arn-list <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-package-arn-list` | **Yes** | list | -- | List of model package ARNs (1-50) |

**Output Schema:**
```json
{
    "ModelPackageSummaries": {
        "string": {
            "ModelPackageGroupName": "string",
            "ModelPackageVersion": "integer",
            "ModelPackageArn": "string",
            "ModelPackageDescription": "string",
            "CreationTime": "timestamp",
            "InferenceSpecification": {...},
            "ModelPackageStatus": "string",
            "ModelApprovalStatus": "string"
        }
    },
    "BatchDescribeModelPackageErrorMap": {
        "string": {"ErrorCode": "string", "ErrorResponse": "string"}
    }
}
```

---

## 12. `list-model-metadata`

Lists metadata for available models (SageMaker built-in algorithms and JumpStart models). **Paginated operation.**

**Synopsis:**
```bash
aws sagemaker list-model-metadata \
    [--search-expression <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--search-expression` | No | structure | -- | Filters: `Framework`, `FrameworkVersion`, `Task`, `Model` |

**Output Schema:**
```json
{
    "ModelMetadataSummaries": [
        {
            "Domain": "string",
            "Framework": "string",
            "Task": "string",
            "Model": "string",
            "FrameworkVersion": "string"
        }
    ],
    "NextToken": "string"
}
```
