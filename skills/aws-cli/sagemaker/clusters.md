# Clusters (HyperPod)

## 1. `create-cluster`

Creates a SageMaker HyperPod cluster for distributed training.

**Synopsis:**
```bash
aws sagemaker create-cluster \
    --cluster-name <value> \
    --instance-groups <value> \
    [--vpc-config <value>] \
    [--orchestrator <value>] \
    [--node-recovery <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name (1-63 chars) |
| `--instance-groups` | **Yes** | list | -- | Instance group definitions |
| `--vpc-config` | No | structure | -- | `SecurityGroupIds`, `Subnets` |
| `--orchestrator` | No | structure | -- | `Eks` config with `ClusterArn` |
| `--node-recovery` | No | string | -- | `Automatic` or `None` |
| `--tags` | No | list | -- | Key-value tags |

**Instance Group:**
```json
[
    {
        "InstanceCount": "integer",
        "InstanceGroupName": "string",
        "InstanceType": "ml.p4d.24xlarge|ml.p5.48xlarge|ml.trn1.32xlarge|...",
        "LifeCycleConfig": {
            "SourceS3Uri": "string",
            "OnCreate": "string"
        },
        "ExecutionRole": "string",
        "ThreadsPerCore": "integer",
        "InstanceStorageConfigs": [
            {"EbsVolumeConfig": {"VolumeSizeInGB": "integer"}}
        ],
        "OnStartDeepHealthChecks": ["InstanceStress|InstanceConnectivity"],
        "TrainingPlanArn": "string",
        "OverrideVpcConfig": {"SecurityGroupIds": [...], "Subnets": [...]}
    }
]
```

**Output Schema:**
```json
{
    "ClusterArn": "string"
}
```

---

## 2. `describe-cluster`

Returns details about a HyperPod cluster.

```bash
aws sagemaker describe-cluster --cluster-name <value>
```

**Output Schema:**
```json
{
    "ClusterArn": "string",
    "ClusterName": "string",
    "ClusterStatus": "Creating|Deleting|Failed|InService|RollingBack|SystemUpdating|Updating",
    "CreationTime": "timestamp",
    "FailureMessage": "string",
    "InstanceGroups": [
        {
            "CurrentCount": "integer",
            "TargetCount": "integer",
            "InstanceGroupName": "string",
            "InstanceType": "string",
            "LifeCycleConfig": {...},
            "ExecutionRole": "string",
            "ThreadsPerCore": "integer",
            "InstanceStorageConfigs": [...],
            "OnStartDeepHealthChecks": [...],
            "Status": "string",
            "TrainingPlanArn": "string",
            "OverrideVpcConfig": {...}
        }
    ],
    "VpcConfig": {"SecurityGroupIds": [...], "Subnets": [...]},
    "Orchestrator": {"Eks": {"ClusterArn": "string"}},
    "NodeRecovery": "Automatic|None"
}
```

---

## 3. `list-clusters`

Lists HyperPod clusters. **Paginated operation.**

```bash
aws sagemaker list-clusters \
    [--creation-time-after <value>] \
    [--creation-time-before <value>] \
    [--name-contains <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--training-plan-arn-equals <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

---

## 4. `update-cluster`

Updates a HyperPod cluster.

```bash
aws sagemaker update-cluster \
    --cluster-name <value> \
    --instance-groups <value> \
    [--node-recovery <value>]
```

**Output Schema:**
```json
{
    "ClusterArn": "string"
}
```

---

## 5. `delete-cluster`

Deletes a HyperPod cluster.

```bash
aws sagemaker delete-cluster --cluster-name <value>
```

**Output Schema:**
```json
{
    "ClusterArn": "string"
}
```

---

## 6. `update-cluster-software`

Updates the software on a HyperPod cluster.

```bash
aws sagemaker update-cluster-software --cluster-name <value>
```

**Output Schema:**
```json
{
    "ClusterArn": "string"
}
```

---

## 7. `describe-cluster-node`

Returns details about a specific cluster node.

```bash
aws sagemaker describe-cluster-node \
    --cluster-name <value> \
    --node-id <value>
```

**Output Schema:**
```json
{
    "NodeDetails": {
        "HyperPodNodeId": "string",
        "InstanceType": "string",
        "InstanceId": "string",
        "InstanceStatus": {
            "Status": "Running|Failure|Pending|ShuttingDown|SystemUpdating|DeepHealthCheckInProgress",
            "Message": "string"
        },
        "InstanceGroupName": "string",
        "LaunchTime": "timestamp",
        "LifeCycleConfig": {...},
        "ThreadsPerCore": "integer",
        "InstanceStorageConfigs": [...],
        "PrivatePrimaryIp": "string",
        "PrivateDnsHostname": "string",
        "Placement": {"AvailabilityZone": "string", "AvailabilityZoneId": "string"}
    }
}
```

---

## 8. `list-cluster-nodes`

Lists cluster nodes. **Paginated operation.**

```bash
aws sagemaker list-cluster-nodes \
    --cluster-name <value> \
    [--creation-time-after <value>] \
    [--creation-time-before <value>] \
    [--instance-group-name-contains <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

---

## 9. `batch-delete-cluster-nodes`

Deletes specific nodes from a cluster.

```bash
aws sagemaker batch-delete-cluster-nodes \
    --cluster-name <value> \
    --node-ids <value>
```

**Output Schema:**
```json
{
    "Failed": [{"Code": "string", "Message": "string", "NodeId": "string"}],
    "Successful": ["string"]
}
```

---

## Cluster Scheduler & Compute Quotas

### 10. `create-cluster-scheduler-config` / `describe-cluster-scheduler-config` / `list-cluster-scheduler-configs` / `update-cluster-scheduler-config` / `delete-cluster-scheduler-config`

Manage scheduler configurations for HyperPod clusters.

```bash
aws sagemaker create-cluster-scheduler-config --name <value> --cluster-arn <value> --scheduler-config <value>
aws sagemaker describe-cluster-scheduler-config --cluster-scheduler-config-id <value>
aws sagemaker list-cluster-scheduler-configs [--cluster-arn-equals <value>] [--name-contains <value>]
aws sagemaker update-cluster-scheduler-config --cluster-scheduler-config-id <value> --scheduler-config <value>
aws sagemaker delete-cluster-scheduler-config --cluster-scheduler-config-id <value>
```

---

### 11. `create-compute-quota` / `describe-compute-quota` / `list-compute-quotas` / `update-compute-quota` / `delete-compute-quota`

Manage compute quotas for HyperPod clusters.

```bash
aws sagemaker create-compute-quota --name <value> --cluster-arn <value> --compute-quota-config <value>
aws sagemaker describe-compute-quota --compute-quota-id <value>
aws sagemaker list-compute-quotas [--cluster-arn-equals <value>] [--name-contains <value>]
aws sagemaker update-compute-quota --compute-quota-id <value> --compute-quota-config <value>
aws sagemaker delete-compute-quota --compute-quota-id <value>
```
