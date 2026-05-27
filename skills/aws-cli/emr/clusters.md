# Clusters

### 1.1 `create-cluster`

Creates a new Amazon EMR cluster. The `aws emr create-cluster` command is a high-level command that simplifies cluster creation.

**Synopsis:**
```bash
aws emr create-cluster \
    --release-label <value> \
    [--name <value>] \
    [--log-uri <value>] \
    [--log-encryption-kms-key-id <value>] \
    [--additional-info <value>] \
    [--ami-version <value>] \
    [--applications <value>] \
    [--configurations <value>] \
    [--instance-type <value>] \
    [--instance-count <value>] \
    [--instance-groups <value>] \
    [--instance-fleets <value>] \
    [--auto-terminate | --no-auto-terminate] \
    [--use-default-roles] \
    [--service-role <value>] \
    [--ec2-attributes <value>] \
    [--auto-scaling-role <value>] \
    [--scale-down-behavior <value>] \
    [--security-configuration <value>] \
    [--tags <value>] \
    [--bootstrap-actions <value>] \
    [--steps <value>] \
    [--step-concurrency-level <value>] \
    [--custom-ami-id <value>] \
    [--ebs-root-volume-size <value>] \
    [--ebs-root-volume-iops <value>] \
    [--ebs-root-volume-throughput <value>] \
    [--repo-upgrade-on-boot <value>] \
    [--kerberos-attributes <value>] \
    [--managed-scaling-policy <value>] \
    [--placement-group-configs <value>] \
    [--auto-termination-policy <value>] \
    [--os-release-label <value>] \
    [--unhealthy-node-replacement | --no-unhealthy-node-replacement]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--release-label` | **Yes** | string | -- | EMR release (e.g., `emr-7.0.0`) |
| `--name` | No | string | -- | Cluster name |
| `--log-uri` | No | string | -- | S3 URI for cluster logs |
| `--applications` | No | list | -- | Applications to install. Shorthand: `Name=Spark Name=Hive` |
| `--instance-type` | No | string | -- | Instance type for uniform instance groups |
| `--instance-count` | No | integer | -- | Number of instances (including master) |
| `--instance-groups` | No | JSON/list | -- | Detailed instance group configuration |
| `--instance-fleets` | No | JSON/list | -- | Instance fleet configuration |
| `--auto-terminate` | No | boolean | false | Terminate after all steps complete |
| `--use-default-roles` | No | boolean | false | Use EMR_DefaultRole and EMR_EC2_DefaultRole |
| `--service-role` | No | string | -- | IAM service role for EMR |
| `--ec2-attributes` | No | structure | -- | EC2 settings (key pair, subnets, security groups, IAM profile) |
| `--auto-scaling-role` | No | string | -- | IAM role for auto scaling |
| `--scale-down-behavior` | No | string | -- | `TERMINATE_AT_INSTANCE_HOUR` or `TERMINATE_AT_TASK_COMPLETION` |
| `--security-configuration` | No | string | -- | Security configuration name |
| `--tags` | No | list | -- | Tags. Shorthand: `Key=string,Value=string` |
| `--bootstrap-actions` | No | list | -- | Bootstrap actions |
| `--steps` | No | list | -- | Steps to execute |
| `--step-concurrency-level` | No | integer | 1 | Maximum concurrent steps (1-256) |
| `--configurations` | No | JSON | -- | Application configurations (JSON or `file://`) |
| `--custom-ami-id` | No | string | -- | Custom AMI ID |
| `--ebs-root-volume-size` | No | integer | -- | Root volume size in GB |
| `--managed-scaling-policy` | No | structure | -- | Managed scaling policy |
| `--auto-termination-policy` | No | structure | -- | Auto-termination policy. Shorthand: `IdleTimeout=long` |
| `--os-release-label` | No | string | -- | OS release label |
| `--unhealthy-node-replacement` | No | boolean | -- | Enable unhealthy node replacement |

**EC2 Attributes Structure:**
```
KeyName=mykey,SubnetId=subnet-xxx,\
InstanceProfile=EMR_EC2_DefaultRole,\
EmrManagedMasterSecurityGroup=sg-xxx,\
EmrManagedSlaveSecurityGroup=sg-xxx
```

**Output Schema:**
```json
{
    "ClusterId": "string",
    "ClusterArn": "string"
}
```

---

### 1.2 `describe-cluster`

Describes the specified cluster.

**Synopsis:**
```bash
aws emr describe-cluster \
    --cluster-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID (e.g., `j-XXXXXXXXXXXXX`) |

**Output Schema:**
```json
{
    "Cluster": {
        "Id": "string",
        "Name": "string",
        "Status": {
            "State": "STARTING|BOOTSTRAPPING|RUNNING|WAITING|TERMINATING|TERMINATED|TERMINATED_WITH_ERRORS",
            "StateChangeReason": {
                "Code": "string",
                "Message": "string"
            },
            "Timeline": {
                "CreationDateTime": "timestamp",
                "ReadyDateTime": "timestamp",
                "EndDateTime": "timestamp"
            }
        },
        "Ec2InstanceAttributes": {
            "Ec2KeyName": "string",
            "Ec2SubnetId": "string",
            "Ec2AvailabilityZone": "string",
            "IamInstanceProfile": "string",
            "EmrManagedMasterSecurityGroup": "string",
            "EmrManagedSlaveSecurityGroup": "string",
            "ServiceAccessSecurityGroup": "string",
            "AdditionalMasterSecurityGroups": ["string"],
            "AdditionalSlaveSecurityGroups": ["string"]
        },
        "LogUri": "string",
        "ReleaseLabel": "string",
        "Applications": [
            {
                "Name": "string",
                "Version": "string"
            }
        ],
        "Tags": [{"Key": "string", "Value": "string"}],
        "ServiceRole": "string",
        "AutoScalingRole": "string",
        "ScaleDownBehavior": "string",
        "NormalizedInstanceHours": "integer",
        "MasterPublicDnsName": "string",
        "Configurations": [],
        "SecurityConfiguration": "string",
        "StepConcurrencyLevel": "integer",
        "ManagedScalingPolicy": {},
        "AutoTerminationPolicy": {
            "IdleTimeout": "long"
        },
        "ClusterArn": "string",
        "OSReleaseLabel": "string"
    }
}
```

---

### 1.3 `list-clusters`

Lists EMR clusters, optionally filtered by state. **Paginated operation.**

**Synopsis:**
```bash
aws emr list-clusters \
    [--created-after <value>] \
    [--created-before <value>] \
    [--cluster-states <value>] \
    [--active] \
    [--terminated] \
    [--failed] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--created-after` | No | timestamp | -- | Filter clusters created after this time |
| `--created-before` | No | timestamp | -- | Filter clusters created before this time |
| `--cluster-states` | No | list(string) | -- | Filter by states: `STARTING`, `BOOTSTRAPPING`, `RUNNING`, `WAITING`, `TERMINATING`, `TERMINATED`, `TERMINATED_WITH_ERRORS` |
| `--active` | No | boolean | -- | Shortcut for STARTING, BOOTSTRAPPING, RUNNING, WAITING |
| `--terminated` | No | boolean | -- | Shortcut for TERMINATED |
| `--failed` | No | boolean | -- | Shortcut for TERMINATED_WITH_ERRORS |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "Clusters": [
        {
            "Id": "string",
            "Name": "string",
            "Status": {
                "State": "string",
                "StateChangeReason": {},
                "Timeline": {}
            },
            "NormalizedInstanceHours": "integer",
            "ClusterArn": "string"
        }
    ],
    "Marker": "string"
}
```

---

### 1.4 `terminate-clusters`

Terminates one or more clusters.

**Synopsis:**
```bash
aws emr terminate-clusters \
    --cluster-ids <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-ids` | **Yes** | list(string) | -- | Cluster IDs to terminate |

No output on success.

---

### 1.5 `modify-cluster`

Modifies a running cluster's step concurrency level.

**Synopsis:**
```bash
aws emr modify-cluster \
    --cluster-id <value> \
    [--step-concurrency-level <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster to modify |
| `--step-concurrency-level` | No | integer | -- | New step concurrency level (1-256) |

**Output Schema:**
```json
{
    "StepConcurrencyLevel": "integer"
}
```

---

### 1.6 `put-auto-termination-policy`

Sets an auto-termination policy for a cluster.

**Synopsis:**
```bash
aws emr put-auto-termination-policy \
    --cluster-id <value> \
    --auto-termination-policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--auto-termination-policy` | **Yes** | structure | -- | Policy. Shorthand: `IdleTimeout=long` (in seconds) |

No output on success.

---

### 1.7 `get-auto-termination-policy`

Gets the auto-termination policy for a cluster.

**Synopsis:**
```bash
aws emr get-auto-termination-policy \
    --cluster-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |

**Output Schema:**
```json
{
    "AutoTerminationPolicy": {
        "IdleTimeout": "long"
    }
}
```

---

### 1.8 `remove-auto-termination-policy`

Removes the auto-termination policy from a cluster.

**Synopsis:**
```bash
aws emr remove-auto-termination-policy \
    --cluster-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |

No output on success.
