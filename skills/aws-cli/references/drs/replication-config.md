# Replication Configuration

### 3.1 `create-replication-configuration-template`

Creates a new replication configuration template.

**Synopsis:**
```bash
aws drs create-replication-configuration-template \
    --staging-area-subnet-id <value> \
    --associate-default-security-group | --no-associate-default-security-group \
    --replication-servers-security-groups-ids <value> \
    --replication-server-instance-type <value> \
    --use-dedicated-replication-server | --no-use-dedicated-replication-server \
    --default-large-staging-disk-type <value> \
    --ebs-encryption <value> \
    [--ebs-encryption-key-arn <value>] \
    --data-plane-routing <value> \
    --create-public-ip <value> \
    --staging-area-tags <value> \
    --pit-policy <value> \
    [--bandwidth-throttling <value>] \
    [--tags <value>] \
    [--auto-replicate-new-disks | --no-auto-replicate-new-disks] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--staging-area-subnet-id` | **Yes** | string | -- | Subnet for the staging area |
| `--associate-default-security-group` | **Yes** | boolean | -- | Associate default security group |
| `--replication-servers-security-groups-ids` | **Yes** | list(string) | -- | Security group IDs for replication servers |
| `--replication-server-instance-type` | **Yes** | string | -- | EC2 instance type for replication server |
| `--use-dedicated-replication-server` | **Yes** | boolean | -- | Use a dedicated replication server |
| `--default-large-staging-disk-type` | **Yes** | string | -- | Default disk type: `GP2`, `GP3`, `ST1`, `AUTO` |
| `--ebs-encryption` | **Yes** | string | -- | EBS encryption: `DEFAULT`, `CUSTOM`, `NONE` |
| `--ebs-encryption-key-arn` | No | string | None | KMS key ARN (required when ebs-encryption is CUSTOM) |
| `--data-plane-routing` | **Yes** | string | -- | Data plane routing: `PRIVATE_IP`, `PUBLIC_IP` |
| `--create-public-ip` | **Yes** | string | -- | Create public IP: `ALWAYS`, `NEVER` |
| `--staging-area-tags` | **Yes** | map | -- | Tags for staging area resources |
| `--pit-policy` | **Yes** | list | -- | Point-in-time recovery policy |
| `--bandwidth-throttling` | No | long | None | Bandwidth throttling in Mbps (0 = unlimited) |
| `--tags` | No | map | None | Tags for the template |
| `--auto-replicate-new-disks` | No | boolean | None | Auto replicate new disks |

**PIT Policy Structure:**
```json
[
    {
        "ruleID": "long",
        "units": "MINUTE|HOUR|DAY",
        "interval": "integer",
        "retentionDuration": "integer",
        "enabled": true|false
    }
]
```

**Output Schema:**
```json
{
    "replicationConfigurationTemplateID": "string",
    "arn": "string",
    "stagingAreaSubnetId": "string",
    "associateDefaultSecurityGroup": "boolean",
    "replicationServersSecurityGroupsIDs": ["string"],
    "replicationServerInstanceType": "string",
    "useDedicatedReplicationServer": "boolean",
    "defaultLargeStagingDiskType": "GP2|GP3|ST1|AUTO",
    "ebsEncryption": "DEFAULT|CUSTOM|NONE",
    "ebsEncryptionKeyArn": "string",
    "dataPlaneRouting": "PRIVATE_IP|PUBLIC_IP",
    "createPublicIP": "ALWAYS|NEVER",
    "stagingAreaTags": {},
    "pitPolicy": [],
    "bandwidthThrottling": "long",
    "tags": {},
    "autoReplicateNewDisks": "boolean"
}
```

---

### 3.2 `delete-replication-configuration-template`

Deletes a single replication configuration template.

**Synopsis:**
```bash
aws drs delete-replication-configuration-template \
    --replication-configuration-template-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-configuration-template-id` | **Yes** | string | -- | Template ID |

**Output Schema:**
```json
{}
```

---

### 3.3 `describe-replication-configuration-templates`

Lists all replication configuration templates, filtered by IDs. **Paginated operation.**

**Synopsis:**
```bash
aws drs describe-replication-configuration-templates \
    [--replication-configuration-template-ids <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-configuration-template-ids` | No | list(string) | None | Template IDs to describe |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "items": [
        {
            "replicationConfigurationTemplateID": "string",
            "arn": "string",
            "stagingAreaSubnetId": "string",
            "associateDefaultSecurityGroup": "boolean",
            "replicationServersSecurityGroupsIDs": ["string"],
            "replicationServerInstanceType": "string",
            "useDedicatedReplicationServer": "boolean",
            "defaultLargeStagingDiskType": "string",
            "ebsEncryption": "string",
            "ebsEncryptionKeyArn": "string",
            "dataPlaneRouting": "string",
            "createPublicIP": "string",
            "stagingAreaTags": {},
            "pitPolicy": [],
            "bandwidthThrottling": "long",
            "tags": {},
            "autoReplicateNewDisks": "boolean"
        }
    ],
    "nextToken": "string"
}
```

---

### 3.4 `update-replication-configuration-template`

Updates a replication configuration template.

**Synopsis:**
```bash
aws drs update-replication-configuration-template \
    --replication-configuration-template-id <value> \
    [--staging-area-subnet-id <value>] \
    [--associate-default-security-group | --no-associate-default-security-group] \
    [--replication-servers-security-groups-ids <value>] \
    [--replication-server-instance-type <value>] \
    [--use-dedicated-replication-server | --no-use-dedicated-replication-server] \
    [--default-large-staging-disk-type <value>] \
    [--ebs-encryption <value>] \
    [--ebs-encryption-key-arn <value>] \
    [--data-plane-routing <value>] \
    [--create-public-ip <value>] \
    [--staging-area-tags <value>] \
    [--pit-policy <value>] \
    [--bandwidth-throttling <value>] \
    [--auto-replicate-new-disks | --no-auto-replicate-new-disks] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-configuration-template-id` | **Yes** | string | -- | Template ID |
| `--staging-area-subnet-id` | No | string | None | Updated staging subnet |
| `--associate-default-security-group` | No | boolean | None | Associate default security group |
| `--replication-servers-security-groups-ids` | No | list(string) | None | Updated security group IDs |
| `--replication-server-instance-type` | No | string | None | Updated instance type |
| `--use-dedicated-replication-server` | No | boolean | None | Use dedicated server |
| `--default-large-staging-disk-type` | No | string | None | Updated disk type |
| `--ebs-encryption` | No | string | None | Updated encryption |
| `--ebs-encryption-key-arn` | No | string | None | Updated KMS key |
| `--data-plane-routing` | No | string | None | Updated routing |
| `--create-public-ip` | No | string | None | Updated public IP setting |
| `--staging-area-tags` | No | map | None | Updated staging tags |
| `--pit-policy` | No | list | None | Updated PIT policy |
| `--bandwidth-throttling` | No | long | None | Updated bandwidth throttling |
| `--auto-replicate-new-disks` | No | boolean | None | Auto replicate new disks |

**Output Schema:** Same as `create-replication-configuration-template`.

---

### 3.5 `get-replication-configuration`

Gets the replication configuration for a specific source server.

**Synopsis:**
```bash
aws drs get-replication-configuration \
    --source-server-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-server-id` | **Yes** | string | -- | Source server ID |

**Output Schema:**
```json
{
    "sourceServerID": "string",
    "name": "string",
    "stagingAreaSubnetId": "string",
    "associateDefaultSecurityGroup": "boolean",
    "replicationServersSecurityGroupsIDs": ["string"],
    "replicationServerInstanceType": "string",
    "useDedicatedReplicationServer": "boolean",
    "defaultLargeStagingDiskType": "string",
    "replicatedDisks": [
        {
            "deviceName": "string",
            "isBootDisk": "boolean",
            "stagingDiskType": "AUTO|GP2|GP3|IO1|SC1|ST1|STANDARD",
            "iops": "long",
            "throughput": "long",
            "optimizedStagingDiskType": "string"
        }
    ],
    "ebsEncryption": "DEFAULT|CUSTOM|NONE",
    "ebsEncryptionKeyArn": "string",
    "dataPlaneRouting": "PRIVATE_IP|PUBLIC_IP",
    "createPublicIP": "ALWAYS|NEVER",
    "stagingAreaTags": {},
    "pitPolicy": [],
    "bandwidthThrottling": "long",
    "autoReplicateNewDisks": "boolean"
}
```

---

### 3.6 `update-replication-configuration`

Updates the replication configuration for a specific source server.

**Synopsis:**
```bash
aws drs update-replication-configuration \
    --source-server-id <value> \
    [--name <value>] \
    [--staging-area-subnet-id <value>] \
    [--associate-default-security-group | --no-associate-default-security-group] \
    [--replication-servers-security-groups-ids <value>] \
    [--replication-server-instance-type <value>] \
    [--use-dedicated-replication-server | --no-use-dedicated-replication-server] \
    [--default-large-staging-disk-type <value>] \
    [--replicated-disks <value>] \
    [--ebs-encryption <value>] \
    [--ebs-encryption-key-arn <value>] \
    [--data-plane-routing <value>] \
    [--create-public-ip <value>] \
    [--staging-area-tags <value>] \
    [--pit-policy <value>] \
    [--bandwidth-throttling <value>] \
    [--auto-replicate-new-disks | --no-auto-replicate-new-disks] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-server-id` | **Yes** | string | -- | Source server ID |
| `--name` | No | string | None | Replication configuration name |
| `--staging-area-subnet-id` | No | string | None | Staging subnet |
| `--associate-default-security-group` | No | boolean | None | Associate default security group |
| `--replication-servers-security-groups-ids` | No | list(string) | None | Security group IDs |
| `--replication-server-instance-type` | No | string | None | Instance type |
| `--use-dedicated-replication-server` | No | boolean | None | Use dedicated server |
| `--default-large-staging-disk-type` | No | string | None | Default disk type |
| `--replicated-disks` | No | list | None | Replicated disk configuration |
| `--ebs-encryption` | No | string | None | Encryption |
| `--ebs-encryption-key-arn` | No | string | None | KMS key |
| `--data-plane-routing` | No | string | None | Routing |
| `--create-public-ip` | No | string | None | Public IP |
| `--staging-area-tags` | No | map | None | Staging tags |
| `--pit-policy` | No | list | None | PIT policy |
| `--bandwidth-throttling` | No | long | None | Bandwidth throttling |
| `--auto-replicate-new-disks` | No | boolean | None | Auto replicate new disks |

**Output Schema:** Same as `get-replication-configuration`.
