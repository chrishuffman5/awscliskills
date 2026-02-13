# Endpoints

## 1. `create-endpoint-config`

Creates an endpoint configuration that defines model variants, instance types, and data capture settings.

**Synopsis:**
```bash
aws sagemaker create-endpoint-config \
    --endpoint-config-name <value> \
    --production-variants <value> \
    [--data-capture-config <value>] \
    [--kms-key-id <value>] \
    [--async-inference-config <value>] \
    [--explainer-config <value>] \
    [--shadow-production-variants <value>] \
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
| `--endpoint-config-name` | **Yes** | string | -- | Name (1-63 chars, alphanumeric + hyphens) |
| `--production-variants` | **Yes** | list | -- | Production variant definitions (1-10) |
| `--data-capture-config` | No | structure | -- | Data capture for inference monitoring |
| `--kms-key-id` | No | string | -- | KMS key for encryption |
| `--async-inference-config` | No | structure | -- | Async inference S3 output and notifications |
| `--explainer-config` | No | structure | -- | SageMaker Clarify explainer |
| `--shadow-production-variants` | No | list | -- | Shadow variants for canary testing |
| `--execution-role-arn` | No | string | -- | IAM role ARN |
| `--vpc-config` | No | structure | -- | VPC config |
| `--enable-network-isolation` | No | boolean | false | Isolate containers |
| `--tags` | No | list | -- | Key-value tags (max 50) |

**Production Variant Structure:**
```json
{
    "VariantName": "string",
    "ModelName": "string",
    "InitialInstanceCount": "integer",
    "InstanceType": "ml.t2.medium|ml.m5.xlarge|ml.p3.2xlarge|...",
    "InitialVariantWeight": "float (default: 1.0)",
    "ServerlessConfig": {
        "MemorySizeInMB": "integer (1024-6144)",
        "MaxConcurrency": "integer (1-200)",
        "ProvisionedConcurrency": "integer (1-200)"
    },
    "ManagedInstanceScaling": {
        "Status": "ENABLED|DISABLED",
        "MinInstanceCount": "integer",
        "MaxInstanceCount": "integer"
    },
    "RoutingConfig": {
        "RoutingStrategy": "LEAST_OUTSTANDING_REQUESTS|RANDOM"
    },
    "ModelDataDownloadTimeoutInSeconds": "integer (60-3600)",
    "ContainerStartupHealthCheckTimeoutInSeconds": "integer (60-3600)",
    "VolumeSizeInGB": "integer (1-512)",
    "EnableSSMAccess": "boolean",
    "InferenceAmiVersion": "string"
}
```

**Data Capture Config:**
```json
{
    "EnableCapture": true,
    "InitialSamplingPercentage": "integer (0-100)",
    "DestinationS3Uri": "string",
    "CaptureOptions": [{"CaptureMode": "Input|Output|InputAndOutput"}],
    "CaptureContentTypeHeader": {
        "CsvContentTypes": ["string"],
        "JsonContentTypes": ["string"]
    }
}
```

**Async Inference Config:**
```json
{
    "ClientConfig": {"MaxConcurrentInvocationsPerInstance": "integer (1-1000)"},
    "OutputConfig": {
        "S3OutputPath": "string",
        "S3FailurePath": "string",
        "KmsKeyId": "string",
        "NotificationConfig": {
            "SuccessTopic": "string",
            "ErrorTopic": "string",
            "IncludeInferenceResponseIn": ["SUCCESS_NOTIFICATION_TOPIC|ERROR_NOTIFICATION_TOPIC"]
        }
    }
}
```

**Output Schema:**
```json
{
    "EndpointConfigArn": "string"
}
```

---

## 2. `describe-endpoint-config`

Returns the description of an endpoint configuration.

**Synopsis:**
```bash
aws sagemaker describe-endpoint-config \
    --endpoint-config-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-config-name` | **Yes** | string | -- | Name of the endpoint configuration |

**Output Schema:**
```json
{
    "EndpointConfigName": "string",
    "EndpointConfigArn": "string",
    "ProductionVariants": [
        {
            "VariantName": "string",
            "ModelName": "string",
            "InitialInstanceCount": "integer",
            "InstanceType": "string",
            "InitialVariantWeight": "float",
            "ServerlessConfig": {...},
            "ManagedInstanceScaling": {...},
            "RoutingConfig": {...}
        }
    ],
    "DataCaptureConfig": {...},
    "KmsKeyId": "string",
    "CreationTime": "timestamp",
    "AsyncInferenceConfig": {...},
    "ExplainerConfig": {...},
    "ShadowProductionVariants": [...],
    "ExecutionRoleArn": "string",
    "VpcConfig": {...},
    "EnableNetworkIsolation": "boolean"
}
```

---

## 3. `list-endpoint-configs`

Lists endpoint configurations. **Paginated operation.**

**Synopsis:**
```bash
aws sagemaker list-endpoint-configs \
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
| `--sort-order` | No | string | `Ascending` | `Ascending`, `Descending` |
| `--name-contains` | No | string | -- | Filter by name substring |
| `--creation-time-before` | No | timestamp | -- | Filter by creation time |
| `--creation-time-after` | No | timestamp | -- | Filter by creation time |

**Output Schema:**
```json
{
    "EndpointConfigs": [
        {
            "EndpointConfigName": "string",
            "EndpointConfigArn": "string",
            "CreationTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

## 4. `delete-endpoint-config`

Deletes an endpoint configuration.

**Synopsis:**
```bash
aws sagemaker delete-endpoint-config \
    --endpoint-config-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-config-name` | **Yes** | string | -- | Name of the endpoint configuration to delete |

**Output:** None

---

## 5. `create-endpoint`

Creates an endpoint using the specified endpoint configuration.

**Synopsis:**
```bash
aws sagemaker create-endpoint \
    --endpoint-name <value> \
    --endpoint-config-name <value> \
    [--deployment-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-name` | **Yes** | string | -- | Endpoint name (max 63 chars) |
| `--endpoint-config-name` | **Yes** | string | -- | Endpoint configuration name |
| `--deployment-config` | No | structure | -- | Blue/green or rolling update deployment strategy |
| `--tags` | No | list | -- | Key-value tags (max 50) |

**Deployment Config Structure:**
```json
{
    "BlueGreenUpdatePolicy": {
        "TrafficRoutingConfiguration": {
            "Type": "ALL_AT_ONCE|CANARY|LINEAR",
            "WaitIntervalInSeconds": "integer",
            "CanarySize": {"Type": "INSTANCE_COUNT|CAPACITY_PERCENT", "Value": "integer"},
            "LinearStepSize": {"Type": "INSTANCE_COUNT|CAPACITY_PERCENT", "Value": "integer"}
        },
        "TerminationWaitInSeconds": "integer",
        "MaximumExecutionTimeoutInSeconds": "integer"
    },
    "RollingUpdatePolicy": {
        "MaximumBatchSize": {"Type": "INSTANCE_COUNT|CAPACITY_PERCENT", "Value": "integer"},
        "WaitIntervalInSeconds": "integer",
        "MaximumExecutionTimeoutInSeconds": "integer",
        "RollbackMaximumBatchSize": {"Type": "INSTANCE_COUNT|CAPACITY_PERCENT", "Value": "integer"}
    },
    "AutoRollbackConfiguration": {
        "Alarms": [{"AlarmName": "string"}]
    }
}
```

**Output Schema:**
```json
{
    "EndpointArn": "string"
}
```

---

## 6. `describe-endpoint`

Returns the description of an endpoint.

**Synopsis:**
```bash
aws sagemaker describe-endpoint \
    --endpoint-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-name` | **Yes** | string | -- | Name of the endpoint |

**Output Schema:**
```json
{
    "EndpointName": "string",
    "EndpointArn": "string",
    "EndpointConfigName": "string",
    "ProductionVariants": [
        {
            "VariantName": "string",
            "DeployedImages": [{"SpecifiedImage": "string", "ResolvedImage": "string", "ResolutionTime": "timestamp"}],
            "CurrentWeight": "float",
            "DesiredWeight": "float",
            "CurrentInstanceCount": "integer",
            "DesiredInstanceCount": "integer",
            "VariantStatus": [{"Status": "Creating|Updating|Deleting|ActivatingTraffic|Baking", "StatusMessage": "string"}],
            "CurrentServerlessConfig": {...},
            "ManagedInstanceScaling": {...},
            "RoutingConfig": {...}
        }
    ],
    "DataCaptureConfig": {
        "EnableCapture": "boolean",
        "CaptureStatus": "Started|Stopped",
        "CurrentSamplingPercentage": "integer",
        "DestinationS3Uri": "string"
    },
    "EndpointStatus": "OutOfService|Creating|Updating|SystemUpdating|RollingBack|InService|Deleting|Failed|UpdateRollbackFailed",
    "FailureReason": "string",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp",
    "LastDeploymentConfig": {...},
    "AsyncInferenceConfig": {...},
    "PendingDeploymentSummary": {
        "EndpointConfigName": "string",
        "ProductionVariants": [...],
        "StartTime": "timestamp"
    },
    "ExplainerConfig": {...},
    "ShadowProductionVariants": [...]
}
```

---

## 7. `list-endpoints`

Lists endpoints. **Paginated operation.**

**Synopsis:**
```bash
aws sagemaker list-endpoints \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--name-contains <value>] \
    [--creation-time-before <value>] \
    [--creation-time-after <value>] \
    [--last-modified-time-before <value>] \
    [--last-modified-time-after <value>] \
    [--status-equals <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sort-by` | No | string | `CreationTime` | `Name`, `CreationTime`, `Status` |
| `--sort-order` | No | string | `Ascending` | `Ascending`, `Descending` |
| `--name-contains` | No | string | -- | Filter by name substring |
| `--status-equals` | No | string | -- | `OutOfService`, `Creating`, `Updating`, `SystemUpdating`, `RollingBack`, `InService`, `Deleting`, `Failed`, `UpdateRollbackFailed` |

**Output Schema:**
```json
{
    "Endpoints": [
        {
            "EndpointName": "string",
            "EndpointArn": "string",
            "CreationTime": "timestamp",
            "LastModifiedTime": "timestamp",
            "EndpointStatus": "string"
        }
    ],
    "NextToken": "string"
}
```

---

## 8. `update-endpoint`

Updates an existing endpoint to use a different endpoint configuration.

**Synopsis:**
```bash
aws sagemaker update-endpoint \
    --endpoint-name <value> \
    --endpoint-config-name <value> \
    [--retain-all-variant-properties | --no-retain-all-variant-properties] \
    [--exclude-retained-variant-properties <value>] \
    [--deployment-config <value>] \
    [--retain-deployment-config | --no-retain-deployment-config] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-name` | **Yes** | string | -- | Endpoint name |
| `--endpoint-config-name` | **Yes** | string | -- | New endpoint configuration name |
| `--retain-all-variant-properties` | No | boolean | false | Retain variant properties from previous config |
| `--exclude-retained-variant-properties` | No | list | -- | Properties to exclude from retention |
| `--deployment-config` | No | structure | -- | Deployment strategy |
| `--retain-deployment-config` | No | boolean | false | Retain deployment config from previous update |

**Output Schema:**
```json
{
    "EndpointArn": "string"
}
```

---

## 9. `update-endpoint-weights-and-capacities`

Updates variant weights and instance counts for an existing endpoint.

**Synopsis:**
```bash
aws sagemaker update-endpoint-weights-and-capacities \
    --endpoint-name <value> \
    --desired-weights-and-capacities <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-name` | **Yes** | string | -- | Endpoint name |
| `--desired-weights-and-capacities` | **Yes** | list | -- | Array of `{VariantName, DesiredWeight, DesiredInstanceCount, ServerlessUpdateConfig}` |

**Output Schema:**
```json
{
    "EndpointArn": "string"
}
```

---

## 10. `delete-endpoint`

Deletes an endpoint and its associated resources.

**Synopsis:**
```bash
aws sagemaker delete-endpoint \
    --endpoint-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-name` | **Yes** | string | -- | Name of the endpoint to delete |

**Output:** None

---

## 11. `create-inference-component`

Creates an inference component on an existing endpoint.

**Synopsis:**
```bash
aws sagemaker create-inference-component \
    --inference-component-name <value> \
    --endpoint-name <value> \
    [--variant-name <value>] \
    [--specification <value>] \
    [--runtime-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--inference-component-name` | **Yes** | string | -- | Inference component name (max 63 chars) |
| `--endpoint-name` | **Yes** | string | -- | Endpoint name |
| `--variant-name` | No | string | -- | Production variant name |
| `--specification` | No | structure | -- | Model/container spec and compute resources |
| `--runtime-config` | No | structure | -- | `CopyCount` (number of copies to deploy) |
| `--tags` | No | list | -- | Key-value tags |

**Output Schema:**
```json
{
    "InferenceComponentArn": "string"
}
```

---

## 12. `describe-inference-component`

Returns information about an inference component.

**Synopsis:**
```bash
aws sagemaker describe-inference-component \
    --inference-component-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--inference-component-name` | **Yes** | string | -- | Inference component name |

**Output Schema:**
```json
{
    "InferenceComponentName": "string",
    "InferenceComponentArn": "string",
    "EndpointName": "string",
    "EndpointArn": "string",
    "VariantName": "string",
    "FailureReason": "string",
    "Specification": {
        "ModelName": "string",
        "Container": {
            "DeployedImage": {"SpecifiedImage": "string", "ResolvedImage": "string"},
            "ArtifactUrl": "string",
            "Environment": {"string": "string"}
        },
        "StartupParameters": {
            "ModelDataDownloadTimeoutInSeconds": "integer",
            "ContainerStartupHealthCheckTimeoutInSeconds": "integer"
        },
        "ComputeResourceRequirements": {
            "NumberOfCpuCoresRequired": "float",
            "NumberOfAcceleratorDevicesRequired": "float",
            "MinMemoryRequiredInMb": "integer",
            "MaxMemoryRequiredInMb": "integer"
        }
    },
    "RuntimeConfig": {"CurrentCopyCount": "integer", "DesiredCopyCount": "integer"},
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp",
    "InferenceComponentStatus": "Creating|InService|Failed|Updating|Deleting"
}
```

---

## 13. `list-inference-components`

Lists inference components. **Paginated operation.**

**Synopsis:**
```bash
aws sagemaker list-inference-components \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--name-contains <value>] \
    [--creation-time-before <value>] \
    [--creation-time-after <value>] \
    [--last-modified-time-before <value>] \
    [--last-modified-time-after <value>] \
    [--status-equals <value>] \
    [--endpoint-name-equals <value>] \
    [--variant-name-equals <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sort-by` | No | string | -- | `Name`, `CreationTime`, `Status` |
| `--sort-order` | No | string | -- | `Ascending`, `Descending` |
| `--name-contains` | No | string | -- | Filter by name substring |
| `--status-equals` | No | string | -- | `Creating`, `InService`, `Failed`, `Updating`, `Deleting` |
| `--endpoint-name-equals` | No | string | -- | Filter by endpoint name |
| `--variant-name-equals` | No | string | -- | Filter by variant name |

**Output Schema:**
```json
{
    "InferenceComponents": [
        {
            "CreationTime": "timestamp",
            "InferenceComponentArn": "string",
            "InferenceComponentName": "string",
            "EndpointArn": "string",
            "EndpointName": "string",
            "VariantName": "string",
            "InferenceComponentStatus": "Creating|InService|Failed|Updating|Deleting",
            "LastModifiedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

## 14. `update-inference-component`

Updates an inference component.

**Synopsis:**
```bash
aws sagemaker update-inference-component \
    --inference-component-name <value> \
    [--specification <value>] \
    [--runtime-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--inference-component-name` | **Yes** | string | -- | Inference component name |
| `--specification` | No | structure | -- | Updated model/container spec |
| `--runtime-config` | No | structure | -- | Updated `CopyCount` |

**Output Schema:**
```json
{
    "InferenceComponentArn": "string"
}
```

---

## 15. `update-inference-component-runtime-config`

Updates the runtime config (copy count) of an inference component.

**Synopsis:**
```bash
aws sagemaker update-inference-component-runtime-config \
    --inference-component-name <value> \
    --desired-runtime-config <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--inference-component-name` | **Yes** | string | -- | Inference component name |
| `--desired-runtime-config` | **Yes** | structure | -- | `CopyCount` |

**Output Schema:**
```json
{
    "InferenceComponentArn": "string"
}
```

---

## 16. `delete-inference-component`

Deletes an inference component.

**Synopsis:**
```bash
aws sagemaker delete-inference-component \
    --inference-component-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--inference-component-name` | **Yes** | string | -- | Name of the inference component to delete |

**Output:** None
