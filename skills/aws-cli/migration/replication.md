# Replication

### 2.1 `create-replication-configuration-template`

Creates a replication configuration template that defines default replication settings for source servers.

**Synopsis:**
```bash
aws mgn create-replication-configuration-template \
    --replication-server-instance-type <value> \
    --use-dedicated-replication-server | --no-use-dedicated-replication-server \
    --default-large-staging-disk-type <value> \
    --ebs-encryption <value> \
    --data-plane-routing <value> \
    --staging-area-subnet-id <value> \
    --staging-area-tags <value> \
    --replication-servers-security-groups-i-ds <value> \
    --bandwidth-throttling <value> \
    [--associate-default-security-group | --no-associate-default-security-group] \
    [--create-public-ip | --no-create-public-ip] \
    [--ebs-encryption-key-arn <value>] \
    [--use-fips-endpoint | --no-use-fips-endpoint] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-server-instance-type` | **Yes** | string | -- | EC2 instance type for replication servers |
| `--use-dedicated-replication-server` | **Yes** | boolean | -- | Use dedicated or shared replication server |
| `--default-large-staging-disk-type` | **Yes** | string | -- | Disk type: `GP2`, `GP3`, `ST1`, `AUTO` |
| `--ebs-encryption` | **Yes** | string | -- | `DEFAULT`, `CUSTOM`, `NONE` |
| `--data-plane-routing` | **Yes** | string | -- | `PRIVATE_IP` or `PUBLIC_IP` |
| `--staging-area-subnet-id` | **Yes** | string | -- | Subnet ID for staging area |
| `--staging-area-tags` | **Yes** | map | -- | Tags for staging resources. Shorthand: `KeyName1=string,KeyName2=string` |
| `--replication-servers-security-groups-i-ds` | **Yes** | list(string) | -- | Security group IDs |
| `--bandwidth-throttling` | **Yes** | long | -- | Bandwidth throttling in Mbps (0 = unlimited) |
| `--associate-default-security-group` | No | boolean | None | Associate default SG |
| `--create-public-ip` | No | boolean | None | Create public IP for replication server |
| `--ebs-encryption-key-arn` | No | string | None | Custom KMS key ARN (when encryption is CUSTOM) |
| `--use-fips-endpoint` | No | boolean | None | Use FIPS endpoint |
| `--tags` | No | map | None | Tags for the template |

**Output Schema:**
```json
{
    "replicationConfigurationTemplateID": "string",
    "arn": "string",
    "replicationServerInstanceType": "string",
    "useDedicatedReplicationServer": true|false,
    "defaultLargeStagingDiskType": "GP2|GP3|ST1|AUTO",
    "ebsEncryption": "DEFAULT|CUSTOM|NONE",
    "ebsEncryptionKeyArn": "string",
    "dataPlaneRouting": "PRIVATE_IP|PUBLIC_IP",
    "stagingAreaSubnetId": "string",
    "stagingAreaTags": {"key": "value"},
    "replicationServersSecurityGroupsIDs": ["string"],
    "bandwidthThrottling": "long",
    "associateDefaultSecurityGroup": true|false,
    "createPublicIP": true|false,
    "useFipsEndpoint": true|false,
    "tags": {"key": "value"}
}
```

---

### 2.2 `delete-replication-configuration-template`

Deletes a replication configuration template.

**Synopsis:**
```bash
aws mgn delete-replication-configuration-template \
    --replication-configuration-template-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-configuration-template-id` | **Yes** | string | -- | Template ID |

**Output:** None

---

### 2.3 `describe-replication-configuration-templates`

Describes replication configuration templates. **Paginated.**

**Synopsis:**
```bash
aws mgn describe-replication-configuration-templates \
    [--replication-configuration-template-i-ds <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-configuration-template-i-ds` | No | list(string) | None | Filter by template IDs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "items": [{"replicationConfigurationTemplateID": "string", "...": "..."}],
    "nextToken": "string"
}
```

---

### 2.4 `update-replication-configuration-template`

Updates a replication configuration template.

**Synopsis:**
```bash
aws mgn update-replication-configuration-template \
    --replication-configuration-template-id <value> \
    [--replication-server-instance-type <value>] \
    [--use-dedicated-replication-server | --no-use-dedicated-replication-server] \
    [--default-large-staging-disk-type <value>] \
    [--ebs-encryption <value>] \
    [--ebs-encryption-key-arn <value>] \
    [--data-plane-routing <value>] \
    [--staging-area-subnet-id <value>] \
    [--staging-area-tags <value>] \
    [--replication-servers-security-groups-i-ds <value>] \
    [--bandwidth-throttling <value>] \
    [--associate-default-security-group | --no-associate-default-security-group] \
    [--create-public-ip | --no-create-public-ip] \
    [--use-fips-endpoint | --no-use-fips-endpoint] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same as create but with required `--replication-configuration-template-id` and all others optional.

**Output Schema:** Same as create.

---

### 2.5 `get-replication-configuration`

Gets the replication configuration for a specific source server.

**Synopsis:**
```bash
aws mgn get-replication-configuration \
    --source-server-id <value> \
    [--account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-server-id` | **Yes** | string | -- | Source server ID |
| `--account-id` | No | string | None | Account ID |

**Output Schema:**
```json
{
    "sourceServerID": "string",
    "name": "string",
    "replicationServerInstanceType": "string",
    "useDedicatedReplicationServer": true|false,
    "defaultLargeStagingDiskType": "string",
    "ebsEncryption": "string",
    "ebsEncryptionKeyArn": "string",
    "dataPlaneRouting": "string",
    "stagingAreaSubnetId": "string",
    "stagingAreaTags": {},
    "replicatedDisks": [
        {
            "deviceName": "string",
            "isBootDisk": true|false,
            "stagingDiskType": "AUTO|GP2|GP3|IO1|SC1|ST1|STANDARD",
            "iops": "long",
            "throughput": "long"
        }
    ],
    "replicationServersSecurityGroupsIDs": ["string"],
    "bandwidthThrottling": "long",
    "associateDefaultSecurityGroup": true|false,
    "createPublicIP": true|false,
    "useFipsEndpoint": true|false
}
```

---

### 2.6 `update-replication-configuration`

Updates the replication configuration for a specific source server.

**Synopsis:**
```bash
aws mgn update-replication-configuration \
    --source-server-id <value> \
    [--account-id <value>] \
    [--name <value>] \
    [--replication-server-instance-type <value>] \
    [--use-dedicated-replication-server | --no-use-dedicated-replication-server] \
    [--staging-area-subnet-id <value>] \
    [--staging-area-tags <value>] \
    [--bandwidth-throttling <value>] \
    [--replicated-disks <value>] \
    [--ebs-encryption <value>] \
    [--ebs-encryption-key-arn <value>] \
    [--data-plane-routing <value>] \
    [--replication-servers-security-groups-i-ds <value>] \
    [--default-large-staging-disk-type <value>] \
    [--associate-default-security-group | --no-associate-default-security-group] \
    [--create-public-ip | --no-create-public-ip] \
    [--use-fips-endpoint | --no-use-fips-endpoint] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same as get-replication-configuration output but all optional except `--source-server-id`.

**Output Schema:** Same as get-replication-configuration.

---

### 2.7 `start-replication`

Starts replication for a source server.

**Synopsis:**
```bash
aws mgn start-replication \
    --source-server-id <value> \
    [--account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-server-id` | **Yes** | string | -- | Source server ID |
| `--account-id` | No | string | None | Account ID |

**Output Schema:** Single source server item.

---

### 2.8 `stop-replication`

Stops replication for a source server. Cannot be undone.

**Synopsis:**
```bash
aws mgn stop-replication \
    --source-server-id <value> \
    [--account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same as start-replication.

**Output Schema:** Single source server item.

---

### 2.9 `pause-replication`

Pauses replication for a source server. Can be resumed later.

**Synopsis:**
```bash
aws mgn pause-replication \
    --source-server-id <value> \
    [--account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same as start-replication.

**Output Schema:** Single source server item.

---

### 2.10 `resume-replication`

Resumes paused replication for a source server.

**Synopsis:**
```bash
aws mgn resume-replication \
    --source-server-id <value> \
    [--account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same as start-replication.

**Output Schema:** Single source server item.

---

### 2.11 `retry-data-replication`

Retries failed data replication for a source server.

**Synopsis:**
```bash
aws mgn retry-data-replication \
    --source-server-id <value> \
    [--account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same as start-replication.

**Output Schema:** Single source server item.
