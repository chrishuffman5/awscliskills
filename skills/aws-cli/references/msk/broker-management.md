# Broker Management

## 4.1 `update-broker-count`

Scales the number of broker nodes in the cluster.

**Synopsis:**
```bash
aws kafka update-broker-count \
    --cluster-arn <value> \
    --current-version <value> \
    --target-number-of-broker-nodes <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |
| `--current-version` | **Yes** | string | -- | Current cluster version |
| `--target-number-of-broker-nodes` | **Yes** | integer | -- | Target broker count (1-15) |

**Output Schema:**
```json
{
    "ClusterArn": "string",
    "ClusterOperationArn": "string"
}
```

---

## 4.2 `update-broker-storage`

Updates the EBS storage capacity for broker nodes.

**Synopsis:**
```bash
aws kafka update-broker-storage \
    --cluster-arn <value> \
    --current-version <value> \
    --target-broker-ebs-volume-info <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |
| `--current-version` | **Yes** | string | -- | Current cluster version |
| `--target-broker-ebs-volume-info` | **Yes** | list | -- | Target EBS volume info per broker. Shorthand: `KafkaBrokerNodeId=string,VolumeSizeGB=integer,ProvisionedThroughput={Enabled=boolean,VolumeThroughput=integer}` |

**Output Schema:**
```json
{
    "ClusterArn": "string",
    "ClusterOperationArn": "string"
}
```

---

## 4.3 `update-broker-type`

Changes the broker instance type for the cluster.

**Synopsis:**
```bash
aws kafka update-broker-type \
    --cluster-arn <value> \
    --current-version <value> \
    --target-instance-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |
| `--current-version` | **Yes** | string | -- | Current cluster version |
| `--target-instance-type` | **Yes** | string | -- | Target instance type (e.g., `kafka.m5.large`, `kafka.m5.xlarge`) |

**Output Schema:**
```json
{
    "ClusterArn": "string",
    "ClusterOperationArn": "string"
}
```

---

## 4.4 `update-storage`

Updates storage configuration for the cluster (volume size, provisioned throughput, storage mode).

**Synopsis:**
```bash
aws kafka update-storage \
    --cluster-arn <value> \
    --current-version <value> \
    [--provisioned-throughput <value>] \
    [--storage-mode <value>] \
    [--volume-size-gb <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |
| `--current-version` | **Yes** | string | -- | Current cluster version |
| `--provisioned-throughput` | No | structure | None | Provisioned throughput settings. Shorthand: `Enabled=boolean,VolumeThroughput=integer` |
| `--storage-mode` | No | string | None | Storage mode: `LOCAL` or `TIERED` |
| `--volume-size-gb` | No | integer | None | Target volume size in GB |

**Output Schema:**
```json
{
    "ClusterArn": "string",
    "ClusterOperationArn": "string"
}
```

---

## 4.5 `reboot-broker`

Reboots a specific broker in the cluster.

**Synopsis:**
```bash
aws kafka reboot-broker \
    --cluster-arn <value> \
    --broker-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |
| `--broker-ids` | **Yes** | list(string) | -- | List of broker IDs to reboot (e.g., `"1"`) |

**Output Schema:**
```json
{
    "ClusterArn": "string",
    "ClusterOperationArn": "string"
}
```

---

## 4.6 `list-nodes`

Lists the nodes in a cluster. **Paginated operation.**

**Synopsis:**
```bash
aws kafka list-nodes \
    --cluster-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "NodeInfoList": [
        {
            "AddedToClusterTime": "string",
            "BrokerNodeInfo": {
                "AttachedENIId": "string",
                "BrokerId": "double",
                "ClientSubnet": "string",
                "ClientVpcIpAddress": "string",
                "CurrentBrokerSoftwareInfo": {
                    "ConfigurationArn": "string",
                    "ConfigurationRevision": "integer",
                    "KafkaVersion": "string"
                },
                "Endpoints": ["string"]
            },
            "InstanceType": "string",
            "NodeARN": "string",
            "NodeType": "BROKER"
        }
    ],
    "NextToken": "string"
}
```

---

## 4.7 `update-connectivity`

Updates cluster connectivity settings (public access, VPC connectivity).

**Synopsis:**
```bash
aws kafka update-connectivity \
    --cluster-arn <value> \
    --current-version <value> \
    --connectivity-info <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |
| `--current-version` | **Yes** | string | -- | Current cluster version |
| `--connectivity-info` | **Yes** | structure | -- | Connectivity configuration (PublicAccess, VpcConnectivity) |

**ConnectivityInfo Structure:**
```json
{
    "PublicAccess": {
        "Type": "DISABLED|SERVICE_PROVIDED_EIPS"
    },
    "VpcConnectivity": {
        "ClientAuthentication": {
            "Sasl": {
                "Scram": { "Enabled": true },
                "Iam": { "Enabled": true }
            },
            "Tls": { "Enabled": true }
        }
    }
}
```

**Output Schema:**
```json
{
    "ClusterArn": "string",
    "ClusterOperationArn": "string"
}
```

---

## 4.8 `update-security`

Updates the security settings for the cluster.

**Synopsis:**
```bash
aws kafka update-security \
    --cluster-arn <value> \
    --current-version <value> \
    [--client-authentication <value>] \
    [--encryption-info <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |
| `--current-version` | **Yes** | string | -- | Current cluster version |
| `--client-authentication` | No | structure | None | Client authentication settings |
| `--encryption-info` | No | structure | None | Encryption settings |

**Output Schema:**
```json
{
    "ClusterArn": "string",
    "ClusterOperationArn": "string"
}
```
