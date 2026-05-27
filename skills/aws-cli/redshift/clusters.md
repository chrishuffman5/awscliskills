# Clusters

### 1.1 `create-cluster`

Creates a new Amazon Redshift provisioned cluster.

**Synopsis:**
```bash
aws redshift create-cluster \
    --cluster-identifier <value> \
    --node-type <value> \
    --master-username <value> \
    [--master-user-password <value>] \
    [--db-name <value>] \
    [--cluster-type <value>] \
    [--number-of-nodes <value>] \
    [--cluster-subnet-group-name <value>] \
    [--availability-zone <value>] \
    [--preferred-maintenance-window <value>] \
    [--cluster-parameter-group-name <value>] \
    [--automated-snapshot-retention-period <value>] \
    [--manual-snapshot-retention-period <value>] \
    [--port <value>] \
    [--cluster-version <value>] \
    [--allow-version-upgrade | --no-allow-version-upgrade] \
    [--publicly-accessible | --no-publicly-accessible] \
    [--encrypted | --no-encrypted] \
    [--kms-key-id <value>] \
    [--enhanced-vpc-routing | --no-enhanced-vpc-routing] \
    [--iam-roles <value>] \
    [--maintenance-track-name <value>] \
    [--default-iam-role-arn <value>] \
    [--aqua-configuration-status <value>] \
    [--manage-master-password | --no-manage-master-password] \
    [--master-password-secret-kms-key-id <value>] \
    [--multi-az | --no-multi-az] \
    [--tags <value>] \
    [--vpc-security-group-ids <value>] \
    [--elastic-ip <value>] \
    [--hsm-client-certificate-identifier <value>] \
    [--hsm-configuration-identifier <value>] \
    [--snapshot-schedule-identifier <value>] \
    [--availability-zone-relocation | --no-availability-zone-relocation] \
    [--ip-address-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-identifier` | **Yes** | string | -- | Unique cluster identifier (lowercase, max 63 chars) |
| `--node-type` | **Yes** | string | -- | Node type: `ra3.xlplus`, `ra3.4xlarge`, `ra3.16xlarge`, `dc2.large`, `dc2.8xlarge` |
| `--master-username` | **Yes** | string | -- | Master user name (1-128 chars, must start with letter) |
| `--master-user-password` | No | string | -- | Master user password (8-64 chars, at least one uppercase, one lowercase, one digit). Omit if using `--manage-master-password` |
| `--db-name` | No | string | `dev` | Initial database name |
| `--cluster-type` | No | string | `multi-node` | `single-node` or `multi-node` |
| `--number-of-nodes` | No | integer | 1 | Number of compute nodes (required for multi-node) |
| `--cluster-subnet-group-name` | No | string | -- | Subnet group for VPC deployment |
| `--availability-zone` | No | string | -- | Preferred AZ |
| `--preferred-maintenance-window` | No | string | -- | Maintenance window (e.g., `sun:05:00-sun:05:30`) |
| `--cluster-parameter-group-name` | No | string | -- | Parameter group to associate |
| `--automated-snapshot-retention-period` | No | integer | 1 | Days to retain automated snapshots (0-35) |
| `--manual-snapshot-retention-period` | No | integer | -1 | Days to retain manual snapshots (-1 = indefinite) |
| `--port` | No | integer | 5439 | Database port (1150-65535) |
| `--cluster-version` | No | string | `1.0` | Redshift engine version |
| `--allow-version-upgrade` | No | boolean | true | Allow automatic version upgrades |
| `--publicly-accessible` | No | boolean | true | Create cluster with public IP |
| `--encrypted` | No | boolean | false | Enable at-rest encryption |
| `--kms-key-id` | No | string | -- | KMS key for encryption |
| `--enhanced-vpc-routing` | No | boolean | false | Force traffic through VPC |
| `--iam-roles` | No | list(string) | -- | IAM role ARNs to associate |
| `--maintenance-track-name` | No | string | `current` | Maintenance track name |
| `--default-iam-role-arn` | No | string | -- | Default IAM role ARN |
| `--aqua-configuration-status` | No | string | `auto` | AQUA status: `enabled`, `disabled`, `auto` |
| `--manage-master-password` | No | boolean | false | Use Secrets Manager for master password |
| `--master-password-secret-kms-key-id` | No | string | -- | KMS key for Secrets Manager secret |
| `--multi-az` | No | boolean | false | Enable Multi-AZ deployment |
| `--tags` | No | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |
| `--vpc-security-group-ids` | No | list(string) | -- | VPC security group IDs |
| `--elastic-ip` | No | string | -- | Elastic IP address for the cluster |
| `--ip-address-type` | No | string | -- | IP address type: `ipv4`, `dualstack` |
| `--snapshot-schedule-identifier` | No | string | -- | Snapshot schedule to associate |

**Output Schema:**
```json
{
    "Cluster": {
        "ClusterIdentifier": "string",
        "NodeType": "string",
        "ClusterStatus": "creating",
        "MasterUsername": "string",
        "DBName": "string",
        "Endpoint": {
            "Address": "string",
            "Port": "integer"
        },
        "ClusterCreateTime": "timestamp",
        "AutomatedSnapshotRetentionPeriod": "integer",
        "ClusterSecurityGroups": [],
        "VpcSecurityGroups": [
            {
                "VpcSecurityGroupId": "string",
                "Status": "string"
            }
        ],
        "ClusterParameterGroups": [
            {
                "ParameterGroupName": "string",
                "ParameterApplyStatus": "string"
            }
        ],
        "ClusterSubnetGroupName": "string",
        "VpcId": "string",
        "AvailabilityZone": "string",
        "PreferredMaintenanceWindow": "string",
        "ClusterVersion": "string",
        "AllowVersionUpgrade": "boolean",
        "NumberOfNodes": "integer",
        "PubliclyAccessible": "boolean",
        "Encrypted": "boolean",
        "ClusterPublicKey": "string",
        "ClusterNodes": [
            {
                "NodeRole": "string",
                "PrivateIPAddress": "string",
                "PublicIPAddress": "string"
            }
        ],
        "Tags": [{"Key": "string", "Value": "string"}],
        "KmsKeyId": "string",
        "EnhancedVpcRouting": "boolean",
        "IamRoles": [
            {
                "IamRoleArn": "string",
                "ApplyStatus": "string"
            }
        ],
        "MaintenanceTrackName": "string",
        "AquaConfiguration": {
            "AquaStatus": "enabled|disabled|applying",
            "AquaConfigurationStatus": "enabled|disabled|auto"
        },
        "MultiAZ": "string",
        "TotalStorageCapacityInMegaBytes": "long",
        "MasterPasswordSecretArn": "string",
        "MasterPasswordSecretKmsKeyId": "string",
        "IpAddressType": "string"
    }
}
```

---

### 1.2 `delete-cluster`

Deletes a previously provisioned cluster. Optionally creates a final snapshot.

**Synopsis:**
```bash
aws redshift delete-cluster \
    --cluster-identifier <value> \
    [--skip-final-cluster-snapshot | --no-skip-final-cluster-snapshot] \
    [--final-cluster-snapshot-identifier <value>] \
    [--final-cluster-snapshot-retention-period <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-identifier` | **Yes** | string | -- | Cluster to delete |
| `--skip-final-cluster-snapshot` | No | boolean | false | Skip creating a final snapshot |
| `--final-cluster-snapshot-identifier` | No | string | -- | Name of the final snapshot (required if not skipping) |
| `--final-cluster-snapshot-retention-period` | No | integer | -- | Days to retain the final snapshot |

**Output Schema:**
```json
{
    "Cluster": {
        "ClusterIdentifier": "string",
        "ClusterStatus": "deleting",
        "NodeType": "string",
        "NumberOfNodes": "integer",
        "DBName": "string",
        "MasterUsername": "string"
    }
}
```

---

### 1.3 `describe-clusters`

Returns properties of provisioned clusters. **Paginated operation.**

**Synopsis:**
```bash
aws redshift describe-clusters \
    [--cluster-identifier <value>] \
    [--tag-keys <value>] \
    [--tag-values <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-identifier` | No | string | -- | Specific cluster to describe |
| `--tag-keys` | No | list(string) | -- | Filter by tag keys |
| `--tag-values` | No | list(string) | -- | Filter by tag values |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page (max 100) |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "Clusters": [
        {
            "ClusterIdentifier": "string",
            "NodeType": "string",
            "ClusterStatus": "string",
            "MasterUsername": "string",
            "DBName": "string",
            "Endpoint": {
                "Address": "string",
                "Port": "integer"
            },
            "ClusterCreateTime": "timestamp",
            "AutomatedSnapshotRetentionPeriod": "integer",
            "ManualSnapshotRetentionPeriod": "integer",
            "ClusterSecurityGroups": [],
            "VpcSecurityGroups": [],
            "ClusterParameterGroups": [],
            "ClusterSubnetGroupName": "string",
            "VpcId": "string",
            "AvailabilityZone": "string",
            "PreferredMaintenanceWindow": "string",
            "ClusterVersion": "string",
            "AllowVersionUpgrade": "boolean",
            "NumberOfNodes": "integer",
            "PubliclyAccessible": "boolean",
            "Encrypted": "boolean",
            "ClusterPublicKey": "string",
            "ClusterNodes": [],
            "ClusterRevisionNumber": "string",
            "Tags": [],
            "KmsKeyId": "string",
            "EnhancedVpcRouting": "boolean",
            "IamRoles": [],
            "MaintenanceTrackName": "string",
            "ElasticResizeNumberOfNodeOptions": "string",
            "AquaConfiguration": {},
            "TotalStorageCapacityInMegaBytes": "long",
            "MultiAZ": "string",
            "IpAddressType": "string",
            "MasterPasswordSecretArn": "string"
        }
    ],
    "Marker": "string"
}
```

---

### 1.4 `modify-cluster`

Modifies the settings for a cluster.

**Synopsis:**
```bash
aws redshift modify-cluster \
    --cluster-identifier <value> \
    [--cluster-type <value>] \
    [--node-type <value>] \
    [--number-of-nodes <value>] \
    [--cluster-security-groups <value>] \
    [--vpc-security-group-ids <value>] \
    [--master-user-password <value>] \
    [--cluster-parameter-group-name <value>] \
    [--automated-snapshot-retention-period <value>] \
    [--manual-snapshot-retention-period <value>] \
    [--preferred-maintenance-window <value>] \
    [--cluster-version <value>] \
    [--allow-version-upgrade | --no-allow-version-upgrade] \
    [--publicly-accessible | --no-publicly-accessible] \
    [--encrypted | --no-encrypted] \
    [--kms-key-id <value>] \
    [--enhanced-vpc-routing | --no-enhanced-vpc-routing] \
    [--new-cluster-identifier <value>] \
    [--elastic-ip <value>] \
    [--maintenance-track-name <value>] \
    [--availability-zone <value>] \
    [--availability-zone-relocation | --no-availability-zone-relocation] \
    [--port <value>] \
    [--manage-master-password | --no-manage-master-password] \
    [--master-password-secret-kms-key-id <value>] \
    [--multi-az | --no-multi-az] \
    [--ip-address-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-identifier` | **Yes** | string | -- | Cluster to modify |
| `--cluster-type` | No | string | -- | New cluster type: `single-node`, `multi-node` |
| `--node-type` | No | string | -- | New node type |
| `--number-of-nodes` | No | integer | -- | New number of nodes |
| `--master-user-password` | No | string | -- | New master user password |
| `--cluster-parameter-group-name` | No | string | -- | New parameter group |
| `--automated-snapshot-retention-period` | No | integer | -- | New automated snapshot retention (0-35 days) |
| `--preferred-maintenance-window` | No | string | -- | New maintenance window |
| `--allow-version-upgrade` | No | boolean | -- | Allow automatic version upgrades |
| `--publicly-accessible` | No | boolean | -- | Make cluster publicly accessible |
| `--encrypted` | No | boolean | -- | Enable encryption |
| `--kms-key-id` | No | string | -- | KMS key for encryption |
| `--enhanced-vpc-routing` | No | boolean | -- | Enable enhanced VPC routing |
| `--new-cluster-identifier` | No | string | -- | Rename the cluster |
| `--manage-master-password` | No | boolean | -- | Use Secrets Manager for password |
| `--multi-az` | No | boolean | -- | Enable Multi-AZ |
| `--ip-address-type` | No | string | -- | IP address type: `ipv4`, `dualstack` |

**Output Schema:**
```json
{
    "Cluster": {
        "ClusterIdentifier": "string",
        "ClusterStatus": "string",
        "NodeType": "string",
        "NumberOfNodes": "integer",
        "PendingModifiedValues": {
            "MasterUserPassword": "string",
            "NodeType": "string",
            "NumberOfNodes": "integer",
            "ClusterType": "string",
            "ClusterVersion": "string",
            "AutomatedSnapshotRetentionPeriod": "integer",
            "ClusterIdentifier": "string",
            "PubliclyAccessible": "boolean",
            "EnhancedVpcRouting": "boolean",
            "MaintenanceTrackName": "string",
            "EncryptionType": "string"
        }
    }
}
```

---

### 1.5 `reboot-cluster`

Reboots a cluster. The cluster must be in the `available` state.

**Synopsis:**
```bash
aws redshift reboot-cluster \
    --cluster-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-identifier` | **Yes** | string | -- | Cluster to reboot |

**Output Schema:**
```json
{
    "Cluster": {
        "ClusterIdentifier": "string",
        "ClusterStatus": "rebooting"
    }
}
```

---

### 1.6 `resize-cluster`

Changes the node type and/or number of nodes for a cluster.

**Synopsis:**
```bash
aws redshift resize-cluster \
    --cluster-identifier <value> \
    [--cluster-type <value>] \
    [--node-type <value>] \
    [--number-of-nodes <value>] \
    [--classic | --no-classic] \
    [--reserved-node-id <value>] \
    [--target-reserved-node-offering-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-identifier` | **Yes** | string | -- | Cluster to resize |
| `--cluster-type` | No | string | -- | New cluster type: `single-node`, `multi-node` |
| `--node-type` | No | string | -- | New node type |
| `--number-of-nodes` | No | integer | -- | New number of nodes |
| `--classic` | No | boolean | false | Use classic resize instead of elastic resize |
| `--reserved-node-id` | No | string | -- | Reserved node to exchange |
| `--target-reserved-node-offering-id` | No | string | -- | Target reserved node offering |

**Output Schema:**
```json
{
    "Cluster": {
        "ClusterIdentifier": "string",
        "ClusterStatus": "resizing",
        "NodeType": "string",
        "NumberOfNodes": "integer"
    }
}
```

---

### 1.7 `pause-cluster`

Pauses a cluster. The cluster must be in the `available` state.

**Synopsis:**
```bash
aws redshift pause-cluster \
    --cluster-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-identifier` | **Yes** | string | -- | Cluster to pause |

**Output Schema:**
```json
{
    "Cluster": {
        "ClusterIdentifier": "string",
        "ClusterStatus": "pausing"
    }
}
```

---

### 1.8 `resume-cluster`

Resumes a paused cluster.

**Synopsis:**
```bash
aws redshift resume-cluster \
    --cluster-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-identifier` | **Yes** | string | -- | Cluster to resume |

**Output Schema:**
```json
{
    "Cluster": {
        "ClusterIdentifier": "string",
        "ClusterStatus": "resuming"
    }
}
```

---

### 1.9 `restore-from-cluster-snapshot`

Creates a new cluster from a snapshot.

**Synopsis:**
```bash
aws redshift restore-from-cluster-snapshot \
    --cluster-identifier <value> \
    [--snapshot-identifier <value>] \
    [--snapshot-arn <value>] \
    [--snapshot-cluster-identifier <value>] \
    [--port <value>] \
    [--availability-zone <value>] \
    [--allow-version-upgrade | --no-allow-version-upgrade] \
    [--cluster-subnet-group-name <value>] \
    [--publicly-accessible | --no-publicly-accessible] \
    [--owner-account <value>] \
    [--hsm-client-certificate-identifier <value>] \
    [--hsm-configuration-identifier <value>] \
    [--elastic-ip <value>] \
    [--cluster-parameter-group-name <value>] \
    [--cluster-security-groups <value>] \
    [--vpc-security-group-ids <value>] \
    [--preferred-maintenance-window <value>] \
    [--automated-snapshot-retention-period <value>] \
    [--manual-snapshot-retention-period <value>] \
    [--kms-key-id <value>] \
    [--node-type <value>] \
    [--enhanced-vpc-routing | --no-enhanced-vpc-routing] \
    [--additional-info <value>] \
    [--iam-roles <value>] \
    [--maintenance-track-name <value>] \
    [--snapshot-schedule-identifier <value>] \
    [--number-of-nodes <value>] \
    [--availability-zone-relocation | --no-availability-zone-relocation] \
    [--aqua-configuration-status <value>] \
    [--default-iam-role-arn <value>] \
    [--reserved-node-id <value>] \
    [--target-reserved-node-offering-id <value>] \
    [--manage-master-password | --no-manage-master-password] \
    [--master-password-secret-kms-key-id <value>] \
    [--multi-az | --no-multi-az] \
    [--ip-address-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-identifier` | **Yes** | string | -- | Identifier for the new cluster |
| `--snapshot-identifier` | No | string | -- | Snapshot to restore from (either this or `--snapshot-arn` required) |
| `--snapshot-arn` | No | string | -- | ARN of the snapshot |
| `--snapshot-cluster-identifier` | No | string | -- | Cluster that created the snapshot |
| `--port` | No | integer | -- | Port for the new cluster |
| `--availability-zone` | No | string | -- | AZ for the new cluster |
| `--cluster-subnet-group-name` | No | string | -- | Subnet group for VPC deployment |
| `--publicly-accessible` | No | boolean | -- | Public accessibility |
| `--owner-account` | No | string | -- | Account that owns the snapshot |
| `--node-type` | No | string | -- | Node type for the new cluster |
| `--number-of-nodes` | No | integer | -- | Number of nodes |
| `--enhanced-vpc-routing` | No | boolean | -- | Enable enhanced VPC routing |
| `--manage-master-password` | No | boolean | -- | Use Secrets Manager for password |
| `--multi-az` | No | boolean | -- | Enable Multi-AZ |

**Output Schema:**
```json
{
    "Cluster": {
        "ClusterIdentifier": "string",
        "ClusterStatus": "creating",
        "NodeType": "string",
        "NumberOfNodes": "integer",
        "DBName": "string",
        "MasterUsername": "string",
        "Endpoint": {
            "Address": "string",
            "Port": "integer"
        },
        "ClusterSnapshotCopyStatus": {
            "DestinationRegion": "string",
            "RetentionPeriod": "long",
            "ManualSnapshotRetentionPeriod": "integer",
            "SnapshotCopyGrantName": "string"
        }
    }
}
```
