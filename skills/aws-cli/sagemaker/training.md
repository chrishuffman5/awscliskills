# Training

## 1. `create-training-job`

Creates a training job. A training job trains a model using the specified algorithm, input data, and compute resources.

**Synopsis:**
```bash
aws sagemaker create-training-job \
    --training-job-name <value> \
    --role-arn <value> \
    --output-data-config <value> \
    [--algorithm-specification <value>] \
    [--hyper-parameters <value>] \
    [--input-data-config <value>] \
    [--resource-config <value>] \
    [--stopping-condition <value>] \
    [--vpc-config <value>] \
    [--enable-managed-spot-training | --no-enable-managed-spot-training] \
    [--enable-network-isolation | --no-enable-network-isolation] \
    [--enable-inter-container-traffic-encryption | --no-enable-inter-container-traffic-encryption] \
    [--checkpoint-config <value>] \
    [--debug-hook-config <value>] \
    [--debug-rule-configurations <value>] \
    [--profiler-config <value>] \
    [--profiler-rule-configurations <value>] \
    [--tensor-board-output-config <value>] \
    [--experiment-config <value>] \
    [--environment <value>] \
    [--retry-strategy <value>] \
    [--remote-debug-config <value>] \
    [--infra-check-config <value>] \
    [--session-chaining-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--training-job-name` | **Yes** | string | -- | Unique name (1-63 chars, alphanumeric + hyphens) |
| `--role-arn` | **Yes** | string | -- | IAM role ARN for SageMaker |
| `--output-data-config` | **Yes** | structure | -- | S3 location for model artifacts (`S3OutputPath`, `KmsKeyId`, `CompressionType`) |
| `--algorithm-specification` | No | structure | -- | Training algorithm (`TrainingImage`, `AlgorithmName`, `TrainingInputMode`: `Pipe`/`File`/`FastFile`, `MetricDefinitions`) |
| `--hyper-parameters` | No | map | -- | Algorithm-specific parameters (max 100, 256 chars each) |
| `--input-data-config` | No | list | -- | Input data channels (S3, EFS, or FSx) |
| `--resource-config` | No | structure | -- | `InstanceType`, `InstanceCount`, `VolumeSizeInGB`, `KeepAlivePeriodInSeconds`, `InstanceGroups` |
| `--stopping-condition` | No | structure | -- | `MaxRuntimeInSeconds`, `MaxWaitTimeInSeconds`, `MaxPendingTimeInSeconds` |
| `--vpc-config` | No | structure | -- | `SecurityGroupIds`, `Subnets` |
| `--enable-managed-spot-training` | No | boolean | false | Use EC2 Spot instances (up to 80% savings) |
| `--enable-network-isolation` | No | boolean | false | Isolate training container from network |
| `--enable-inter-container-traffic-encryption` | No | boolean | false | Encrypt distributed training traffic |
| `--checkpoint-config` | No | structure | -- | `S3Uri`, `LocalPath` for managed spot checkpoints |
| `--debug-hook-config` | No | structure | -- | SageMaker Debugger output config |
| `--debug-rule-configurations` | No | list | -- | Debugger rules (max 20) |
| `--profiler-config` | No | structure | -- | System/framework profiling |
| `--profiler-rule-configurations` | No | list | -- | Profiler rules (max 20) |
| `--tensor-board-output-config` | No | structure | -- | TensorBoard S3 output |
| `--experiment-config` | No | structure | -- | `ExperimentName`, `TrialName`, `RunName` |
| `--environment` | No | map | -- | Container environment variables (max 100) |
| `--retry-strategy` | No | structure | -- | `MaximumRetryAttempts` (1-30) |
| `--remote-debug-config` | No | structure | -- | `EnableRemoteDebug` |
| `--infra-check-config` | No | structure | -- | `EnableInfraCheck` |
| `--session-chaining-config` | No | structure | -- | `EnableSessionTagChaining` |
| `--tags` | No | list | -- | Key-value tags (max 50) |

**Output Schema:**
```json
{
    "TrainingJobArn": "string"
}
```

---

## 2. `describe-training-job`

Returns detailed information about a training job.

**Synopsis:**
```bash
aws sagemaker describe-training-job \
    --training-job-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--training-job-name` | **Yes** | string | -- | Name of the training job |

**Output Schema:**
```json
{
    "TrainingJobName": "string",
    "TrainingJobArn": "string",
    "TuningJobArn": "string",
    "LabelingJobArn": "string",
    "AutoMLJobArn": "string",
    "ModelArtifacts": {
        "S3ModelArtifacts": "string"
    },
    "TrainingJobStatus": "InProgress|Completed|Failed|Stopping|Stopped|Deleting",
    "SecondaryStatus": "Starting|LaunchingMLInstances|PreparingTrainingStack|Downloading|DownloadingTrainingImage|Training|Uploading|Stopping|Stopped|MaxRuntimeExceeded|Completed|Failed|Interrupted|MaxWaitTimeExceeded|Updating|Restarting|Pending",
    "FailureReason": "string",
    "HyperParameters": {"string": "string"},
    "AlgorithmSpecification": {
        "TrainingImage": "string",
        "AlgorithmName": "string",
        "TrainingInputMode": "Pipe|File|FastFile",
        "MetricDefinitions": [{"Name": "string", "Regex": "string"}],
        "EnableSageMakerMetricsTimeSeries": true
    },
    "RoleArn": "string",
    "InputDataConfig": [
        {
            "ChannelName": "string",
            "DataSource": {
                "S3DataSource": {
                    "S3DataType": "ManifestFile|S3Prefix|AugmentedManifestFile",
                    "S3Uri": "string",
                    "S3DataDistributionType": "FullyReplicated|ShardedByS3Key"
                },
                "FileSystemDataSource": {
                    "FileSystemId": "string",
                    "FileSystemAccessMode": "rw|ro",
                    "FileSystemType": "EFS|FSxLustre",
                    "DirectoryPath": "string"
                }
            },
            "ContentType": "string",
            "CompressionType": "None|Gzip",
            "InputMode": "Pipe|File|FastFile"
        }
    ],
    "OutputDataConfig": {
        "KmsKeyId": "string",
        "S3OutputPath": "string",
        "CompressionType": "GZIP|NONE"
    },
    "ResourceConfig": {
        "InstanceType": "string",
        "InstanceCount": "integer",
        "VolumeSizeInGB": "integer",
        "VolumeKmsKeyId": "string",
        "KeepAlivePeriodInSeconds": "integer",
        "InstanceGroups": [{"InstanceType": "string", "InstanceCount": "integer", "InstanceGroupName": "string"}]
    },
    "WarmPoolStatus": {
        "Status": "Available|Terminated|Reused|InUse",
        "ResourceRetainedBillableTimeInSeconds": "integer",
        "ReusedByJob": "string"
    },
    "VpcConfig": {
        "SecurityGroupIds": ["string"],
        "Subnets": ["string"]
    },
    "StoppingCondition": {
        "MaxRuntimeInSeconds": "integer",
        "MaxWaitTimeInSeconds": "integer",
        "MaxPendingTimeInSeconds": "integer"
    },
    "CreationTime": "timestamp",
    "TrainingStartTime": "timestamp",
    "TrainingEndTime": "timestamp",
    "LastModifiedTime": "timestamp",
    "SecondaryStatusTransitions": [
        {"Status": "string", "StartTime": "timestamp", "EndTime": "timestamp", "StatusMessage": "string"}
    ],
    "FinalMetricDataList": [
        {"MetricName": "string", "Value": "float", "Timestamp": "timestamp"}
    ],
    "EnableNetworkIsolation": "boolean",
    "EnableInterContainerTrafficEncryption": "boolean",
    "EnableManagedSpotTraining": "boolean",
    "TrainingTimeInSeconds": "integer",
    "BillableTimeInSeconds": "integer",
    "CheckpointConfig": {"S3Uri": "string", "LocalPath": "string"},
    "DebugHookConfig": {"LocalPath": "string", "S3OutputPath": "string"},
    "ExperimentConfig": {"ExperimentName": "string", "TrialName": "string", "RunName": "string"},
    "DebugRuleEvaluationStatuses": [
        {"RuleConfigurationName": "string", "RuleEvaluationStatus": "InProgress|NoIssuesFound|IssuesFound|Error|Stopping|Stopped"}
    ],
    "ProfilerConfig": {"S3OutputPath": "string", "DisableProfiler": "boolean"},
    "ProfilingStatus": "Enabled|Disabled",
    "Environment": {"string": "string"},
    "RetryStrategy": {"MaximumRetryAttempts": "integer"},
    "RemoteDebugConfig": {"EnableRemoteDebug": "boolean"},
    "InfraCheckConfig": {"EnableInfraCheck": "boolean"}
}
```

---

## 3. `list-training-jobs`

Lists training jobs. **Paginated operation.**

**Synopsis:**
```bash
aws sagemaker list-training-jobs \
    [--creation-time-after <value>] \
    [--creation-time-before <value>] \
    [--last-modified-time-after <value>] \
    [--last-modified-time-before <value>] \
    [--name-contains <value>] \
    [--status-equals <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--warm-pool-status-equals <value>] \
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
| `--last-modified-time-after` | No | timestamp | -- | Filter by modification time |
| `--last-modified-time-before` | No | timestamp | -- | Filter by modification time |
| `--name-contains` | No | string | -- | Filter by name substring |
| `--status-equals` | No | string | -- | `InProgress`, `Completed`, `Failed`, `Stopping`, `Stopped`, `Deleting` |
| `--sort-by` | No | string | `CreationTime` | `Name`, `CreationTime`, `Status` |
| `--sort-order` | No | string | `Ascending` | `Ascending`, `Descending` |
| `--warm-pool-status-equals` | No | string | -- | `Available`, `Terminated`, `Reused`, `InUse` |

**Output Schema:**
```json
{
    "TrainingJobSummaries": [
        {
            "TrainingJobName": "string",
            "TrainingJobArn": "string",
            "CreationTime": "timestamp",
            "TrainingEndTime": "timestamp",
            "LastModifiedTime": "timestamp",
            "TrainingJobStatus": "InProgress|Completed|Failed|Stopping|Stopped|Deleting",
            "SecondaryStatus": "string",
            "WarmPoolStatus": {
                "Status": "Available|Terminated|Reused|InUse",
                "ResourceRetainedBillableTimeInSeconds": "integer",
                "ReusedByJob": "string"
            }
        }
    ],
    "NextToken": "string"
}
```

---

## 4. `stop-training-job`

Stops a running training job.

**Synopsis:**
```bash
aws sagemaker stop-training-job \
    --training-job-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--training-job-name` | **Yes** | string | -- | Name of the training job to stop |

**Output:** None

---

## 5. `update-training-job`

Updates properties of a training job (profiler config, remote debug, resource config).

**Synopsis:**
```bash
aws sagemaker update-training-job \
    --training-job-name <value> \
    [--profiler-config <value>] \
    [--profiler-rule-configurations <value>] \
    [--resource-config <value>] \
    [--remote-debug-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--training-job-name` | **Yes** | string | -- | Name of the training job |
| `--profiler-config` | No | structure | -- | Updated profiler config |
| `--profiler-rule-configurations` | No | list | -- | Updated profiler rules |
| `--resource-config` | No | structure | -- | Updated `KeepAlivePeriodInSeconds` |
| `--remote-debug-config` | No | structure | -- | Enable/disable remote debug |

**Output Schema:**
```json
{
    "TrainingJobArn": "string"
}
```

---

## 6. `delete-training-job`

Deletes a training job. Only jobs in `Completed`, `Failed`, or `Stopped` state can be deleted.

**Synopsis:**
```bash
aws sagemaker delete-training-job \
    --training-job-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--training-job-name` | **Yes** | string | -- | Name of the training job to delete |

**Output:** None

---

## 7. `create-training-plan`

Creates a training plan for reserving compute capacity.

**Synopsis:**
```bash
aws sagemaker create-training-plan \
    --training-plan-name <value> \
    --training-plan-offering-id <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--training-plan-name` | **Yes** | string | -- | Training plan name (1-64 chars) |
| `--training-plan-offering-id` | **Yes** | string | -- | Offering ID from search results |
| `--tags` | No | list | -- | Key-value tags |

**Output Schema:**
```json
{
    "TrainingPlanArn": "string"
}
```

---

## 8. `describe-training-plan`

Gets details about a training plan.

**Synopsis:**
```bash
aws sagemaker describe-training-plan \
    --training-plan-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--training-plan-name` | **Yes** | string | -- | Training plan name |

**Output Schema:**
```json
{
    "TrainingPlanArn": "string",
    "TrainingPlanName": "string",
    "Status": "Pending|Active|Scheduled|Expired|Failed",
    "StatusMessage": "string",
    "DurationHours": "long",
    "DurationMinutes": "long",
    "StartTime": "timestamp",
    "EndTime": "timestamp",
    "UpfrontFee": "string",
    "CurrencyCode": "string",
    "TotalInstanceCount": "integer",
    "AvailableInstanceCount": "integer",
    "InUseInstanceCount": "integer",
    "TargetResources": ["training-job|hyperpod-cluster"],
    "ReservedCapacitySummaries": [
        {
            "ReservedCapacityArn": "string",
            "InstanceType": "string",
            "TotalInstanceCount": "integer",
            "Status": "string",
            "AvailableInstanceCount": "integer",
            "InUseInstanceCount": "integer"
        }
    ]
}
```

---

## 9. `list-training-plans`

Lists training plans. **Paginated operation.**

**Synopsis:**
```bash
aws sagemaker list-training-plans \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--name-contains <value>] \
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
| `--sort-by` | No | string | -- | Sort field: `TrainingPlanName`, `StartTime`, `Status` |
| `--sort-order` | No | string | -- | `Ascending`, `Descending` |
| `--name-contains` | No | string | -- | Filter by name substring |
| `--status-equals` | No | string | -- | `Pending`, `Active`, `Scheduled`, `Expired`, `Failed` |

**Output Schema:**
```json
{
    "TrainingPlanSummaries": [
        {
            "TrainingPlanArn": "string",
            "TrainingPlanName": "string",
            "Status": "Pending|Active|Scheduled|Expired|Failed"
        }
    ],
    "NextToken": "string"
}
```

---

## 10. `search-training-plan-offerings`

Searches available training plan offerings.

**Synopsis:**
```bash
aws sagemaker search-training-plan-offerings \
    --instance-type <value> \
    --instance-count <value> \
    [--start-time-after <value>] \
    [--end-time-before <value>] \
    [--duration-hours <value>] \
    [--target-resources <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-type` | **Yes** | string | -- | ML instance type |
| `--instance-count` | **Yes** | integer | -- | Number of instances |
| `--start-time-after` | No | timestamp | -- | Earliest start time |
| `--end-time-before` | No | timestamp | -- | Latest end time |
| `--duration-hours` | No | long | -- | Minimum duration in hours |
| `--target-resources` | No | list | -- | `training-job`, `hyperpod-cluster` |

**Output Schema:**
```json
{
    "TrainingPlanOfferings": [
        {
            "TrainingPlanOfferingId": "string",
            "TargetResources": ["training-job|hyperpod-cluster"],
            "RequestedStartTimeAfter": "timestamp",
            "RequestedEndTimeBefore": "timestamp",
            "DurationHours": "long",
            "DurationMinutes": "long",
            "UpfrontFee": "string",
            "CurrencyCode": "string",
            "ReservedCapacityOfferings": [
                {
                    "InstanceType": "string",
                    "InstanceCount": "integer",
                    "AvailabilityZone": "string",
                    "DurationHours": "long",
                    "DurationMinutes": "long",
                    "StartTime": "timestamp",
                    "EndTime": "timestamp"
                }
            ]
        }
    ]
}
```
