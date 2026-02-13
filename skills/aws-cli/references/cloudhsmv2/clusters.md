# Clusters

### 1.1 `create-cluster`

Creates a new CloudHSM cluster. Can optionally restore from a backup.

**Synopsis:**
```bash
aws cloudhsmv2 create-cluster \
    --hsm-type <value> \
    --subnet-ids <value> \
    [--backup-retention-policy <value>] \
    [--source-backup-id <value>] \
    [--network-type <value>] \
    [--tag-list <value>] \
    [--mode <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hsm-type` | **Yes** | string | -- | HSM type: `hsm1.medium` or `hsm2m.medium` |
| `--subnet-ids` | **Yes** | list(string) | -- | 1-10 subnet IDs (one per AZ, all in same VPC) |
| `--backup-retention-policy` | No | structure | None | Backup retention policy |
| `--source-backup-id` | No | string | None | Backup ID or ARN to restore from |
| `--network-type` | No | string | `IPV4` | Network type: `IPV4` or `DUALSTACK` |
| `--tag-list` | No | list | None | Tags (1-50). Shorthand: `Key=string,Value=string ...` |
| `--mode` | No | string | None | Cluster mode: `FIPS` or `NON_FIPS` |

**Backup Retention Policy Structure:**
```json
{
    "Type": "DAYS",
    "Value": "string"
}
```

**Output Schema:**
```json
{
    "Cluster": {
        "BackupPolicy": "DEFAULT",
        "BackupRetentionPolicy": {
            "Type": "DAYS",
            "Value": "string"
        },
        "ClusterId": "string",
        "CreateTimestamp": "timestamp",
        "Hsms": [],
        "HsmType": "string",
        "PreCoPassword": "string",
        "SecurityGroup": "string",
        "SourceBackupId": "string",
        "State": "CREATE_IN_PROGRESS",
        "StateMessage": "string",
        "SubnetMapping": {
            "az": "subnet-id"
        },
        "VpcId": "string",
        "NetworkType": "IPV4|DUALSTACK",
        "Certificates": {
            "ClusterCsr": "string",
            "HsmCertificate": "string",
            "AwsHardwareCertificate": "string",
            "ManufacturerHardwareCertificate": "string",
            "ClusterCertificate": "string"
        },
        "TagList": [
            {
                "Key": "string",
                "Value": "string"
            }
        ],
        "Mode": "FIPS|NON_FIPS"
    }
}
```

---

### 1.2 `delete-cluster`

Deletes the specified CloudHSM cluster. The cluster must not contain any HSMs.

**Synopsis:**
```bash
aws cloudhsmv2 delete-cluster \
    --cluster-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | ID of the cluster to delete |

**Output Schema:**
```json
{
    "Cluster": {
        "ClusterId": "string",
        "State": "DELETE_IN_PROGRESS",
        "StateMessage": "string",
        "HsmType": "string",
        "VpcId": "string",
        "SubnetMapping": {},
        "CreateTimestamp": "timestamp"
    }
}
```

---

### 1.3 `describe-clusters`

Returns information about CloudHSM clusters. **Paginated operation.**

**Synopsis:**
```bash
aws cloudhsmv2 describe-clusters \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | map | None | Filter by `clusterIds`, `vpcIds`, or `states` (max 30 filters) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Clusters": [
        {
            "BackupPolicy": "DEFAULT",
            "BackupRetentionPolicy": {
                "Type": "DAYS",
                "Value": "string"
            },
            "ClusterId": "string",
            "CreateTimestamp": "timestamp",
            "Hsms": [
                {
                    "AvailabilityZone": "string",
                    "ClusterId": "string",
                    "SubnetId": "string",
                    "EniId": "string",
                    "EniIp": "string",
                    "EniIpV6": "string",
                    "HsmId": "string",
                    "HsmType": "string",
                    "State": "CREATE_IN_PROGRESS|ACTIVE|DEGRADED|DELETE_IN_PROGRESS|DELETED",
                    "StateMessage": "string"
                }
            ],
            "HsmType": "string",
            "PreCoPassword": "string",
            "SecurityGroup": "string",
            "SourceBackupId": "string",
            "State": "string",
            "StateMessage": "string",
            "SubnetMapping": {},
            "VpcId": "string",
            "NetworkType": "IPV4|DUALSTACK",
            "Certificates": {},
            "TagList": [],
            "Mode": "FIPS|NON_FIPS"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.4 `modify-cluster`

Modifies CloudHSM cluster settings such as backup retention policy or HSM type.

**Synopsis:**
```bash
aws cloudhsmv2 modify-cluster \
    --cluster-id <value> \
    [--backup-retention-policy <value>] \
    [--hsm-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | ID of the cluster to modify |
| `--backup-retention-policy` | No | structure | None | Updated backup retention policy |
| `--hsm-type` | No | string | None | New HSM type for the cluster |

**Output Schema:**
```json
{
    "Cluster": {
        "ClusterId": "string",
        "State": "string",
        "HsmType": "string",
        "BackupRetentionPolicy": {
            "Type": "DAYS",
            "Value": "string"
        }
    }
}
```

---

### 1.5 `initialize-cluster`

Initializes a CloudHSM cluster by providing the signed CSR and trust anchor certificate. Required before the cluster can be used.

**Synopsis:**
```bash
aws cloudhsmv2 initialize-cluster \
    --cluster-id <value> \
    --signed-cert <value> \
    --trust-anchor <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | ID of the cluster to initialize |
| `--signed-cert` | **Yes** | string | -- | Signed cluster certificate (use `fileb://` for file) |
| `--trust-anchor` | **Yes** | string | -- | Trust anchor certificate (use `fileb://` for file) |

**Output Schema:**
```json
{
    "State": "INITIALIZE_IN_PROGRESS|INITIALIZED|ACTIVE",
    "StateMessage": "string"
}
```
