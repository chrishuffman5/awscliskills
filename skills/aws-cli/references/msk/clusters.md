# Clusters

## 1.1 `create-cluster`

Creates a new provisioned Amazon MSK cluster.

**Synopsis:**
```bash
aws kafka create-cluster \
    --cluster-name <value> \
    --broker-node-group-info <value> \
    --kafka-version <value> \
    --number-of-broker-nodes <value> \
    [--client-authentication <value>] \
    [--configuration-info <value>] \
    [--encryption-info <value>] \
    [--enhanced-monitoring <value>] \
    [--open-monitoring <value>] \
    [--logging-info <value>] \
    [--tags <value>] \
    [--storage-mode <value>] \
    [--rebalancing <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name (1-64 characters) |
| `--broker-node-group-info` | **Yes** | structure | -- | Broker node configuration (subnets, instance type, storage, security groups) |
| `--kafka-version` | **Yes** | string | -- | Apache Kafka version (e.g., `3.6.0`) |
| `--number-of-broker-nodes` | **Yes** | integer | -- | Number of broker nodes (1-15) |
| `--client-authentication` | No | structure | None | Client authentication settings (SASL, TLS, Unauthenticated) |
| `--configuration-info` | No | structure | None | Broker configuration ARN and revision |
| `--encryption-info` | No | structure | None | Encryption at rest and in transit settings |
| `--enhanced-monitoring` | No | string | `DEFAULT` | Monitoring level: `DEFAULT`, `PER_BROKER`, `PER_TOPIC_PER_BROKER`, `PER_TOPIC_PER_PARTITION` |
| `--open-monitoring` | No | structure | None | Prometheus monitoring (JMX/Node exporter) |
| `--logging-info` | No | structure | None | Broker log delivery (CloudWatch, Firehose, S3) |
| `--tags` | No | map | None | Key-value tags |
| `--storage-mode` | No | string | `LOCAL` | Storage mode: `LOCAL` or `TIERED` |
| `--rebalancing` | No | structure | None | Intelligent rebalancing: `PAUSED` or `ACTIVE` |

**BrokerNodeGroupInfo Structure:**
```json
{
    "BrokerAZDistribution": "DEFAULT",
    "ClientSubnets": ["subnet-abc", "subnet-def"],
    "InstanceType": "kafka.m5.large",
    "SecurityGroups": ["sg-123"],
    "StorageInfo": {
        "EbsStorageInfo": {
            "VolumeSize": 100,
            "ProvisionedThroughput": {
                "Enabled": true,
                "VolumeThroughput": 250
            }
        }
    },
    "ConnectivityInfo": {
        "PublicAccess": {
            "Type": "DISABLED"
        }
    },
    "ZoneIds": ["use1-az1", "use1-az2"]
}
```

**Output Schema:**
```json
{
    "ClusterArn": "string",
    "ClusterName": "string",
    "State": "ACTIVE|CREATING|DELETING|FAILED|HEALING|MAINTENANCE|REBOOTING_BROKER|UPDATING"
}
```

---

## 1.2 `create-cluster-v2`

Creates a provisioned or serverless MSK cluster using the v2 API.

**Synopsis:**
```bash
aws kafka create-cluster-v2 \
    --cluster-name <value> \
    [--tags <value>] \
    [--provisioned <value>] \
    [--serverless <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name (1-64 characters) |
| `--tags` | No | map | None | Key-value tags |
| `--provisioned` | No | structure | None | Provisioned cluster settings (BrokerNodeGroupInfo, KafkaVersion, NumberOfBrokerNodes required within) |
| `--serverless` | No | structure | None | Serverless cluster settings (VpcConfigs required within) |

**Serverless Structure:**
```json
{
    "VpcConfigs": [
        {
            "SubnetIds": ["subnet-abc", "subnet-def"],
            "SecurityGroupIds": ["sg-123"]
        }
    ],
    "ClientAuthentication": {
        "Sasl": {
            "Iam": {
                "Enabled": true
            }
        }
    }
}
```

**Output Schema:**
```json
{
    "ClusterArn": "string",
    "ClusterName": "string",
    "State": "ACTIVE|CREATING|DELETING|FAILED|HEALING|MAINTENANCE|REBOOTING_BROKER|UPDATING",
    "ClusterType": "PROVISIONED|SERVERLESS"
}
```

---

## 1.3 `delete-cluster`

Deletes the specified MSK cluster.

**Synopsis:**
```bash
aws kafka delete-cluster \
    --cluster-arn <value> \
    [--current-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster to delete |
| `--current-version` | No | string | None | Current version of the cluster |

**Output Schema:**
```json
{
    "ClusterArn": "string",
    "State": "ACTIVE|CREATING|DELETING|FAILED|HEALING|MAINTENANCE|REBOOTING_BROKER|UPDATING"
}
```

---

## 1.4 `describe-cluster`

Returns details for the specified provisioned MSK cluster.

**Synopsis:**
```bash
aws kafka describe-cluster \
    --cluster-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |

**Output Schema:**
```json
{
    "ClusterInfo": {
        "ActiveOperationArn": "string",
        "BrokerNodeGroupInfo": {
            "BrokerAZDistribution": "DEFAULT",
            "ClientSubnets": ["string"],
            "InstanceType": "string",
            "SecurityGroups": ["string"],
            "StorageInfo": {
                "EbsStorageInfo": {
                    "VolumeSize": "integer",
                    "ProvisionedThroughput": {
                        "Enabled": "boolean",
                        "VolumeThroughput": "integer"
                    }
                }
            },
            "ConnectivityInfo": {
                "PublicAccess": {
                    "Type": "string"
                },
                "VpcConnectivity": {
                    "ClientAuthentication": {}
                }
            },
            "ZoneIds": ["string"]
        },
        "ClientAuthentication": {
            "Sasl": {
                "Scram": { "Enabled": "boolean" },
                "Iam": { "Enabled": "boolean" }
            },
            "Tls": {
                "CertificateAuthorityArnList": ["string"],
                "Enabled": "boolean"
            },
            "Unauthenticated": { "Enabled": "boolean" }
        },
        "ClusterArn": "string",
        "ClusterName": "string",
        "CreationTime": "timestamp",
        "CurrentBrokerSoftwareInfo": {
            "ConfigurationArn": "string",
            "ConfigurationRevision": "integer",
            "KafkaVersion": "string"
        },
        "CurrentVersion": "string",
        "EncryptionInfo": {
            "EncryptionAtRest": { "DataVolumeKMSKeyId": "string" },
            "EncryptionInTransit": {
                "ClientBroker": "TLS|TLS_PLAINTEXT|PLAINTEXT",
                "InCluster": "boolean"
            }
        },
        "EnhancedMonitoring": "DEFAULT|PER_BROKER|PER_TOPIC_PER_BROKER|PER_TOPIC_PER_PARTITION",
        "OpenMonitoring": {
            "Prometheus": {
                "JmxExporter": { "EnabledInBroker": "boolean" },
                "NodeExporter": { "EnabledInBroker": "boolean" }
            }
        },
        "LoggingInfo": {
            "BrokerLogs": {
                "CloudWatchLogs": { "Enabled": "boolean", "LogGroup": "string" },
                "Firehose": { "DeliveryStream": "string", "Enabled": "boolean" },
                "S3": { "Bucket": "string", "Enabled": "boolean", "Prefix": "string" }
            }
        },
        "NumberOfBrokerNodes": "integer",
        "State": "ACTIVE|CREATING|DELETING|FAILED|HEALING|MAINTENANCE|REBOOTING_BROKER|UPDATING",
        "StateInfo": { "Code": "string", "Message": "string" },
        "Tags": { "string": "string" },
        "ZookeeperConnectString": "string",
        "ZookeeperConnectStringTls": "string",
        "StorageMode": "LOCAL|TIERED",
        "CustomerActionStatus": "CRITICAL_ACTION_REQUIRED|ACTION_RECOMMENDED|NONE"
    }
}
```

---

## 1.5 `describe-cluster-v2`

Returns details for the specified cluster using the v2 API (supports both provisioned and serverless).

**Synopsis:**
```bash
aws kafka describe-cluster-v2 \
    --cluster-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |

**Output Schema:**
```json
{
    "ClusterInfo": {
        "ActiveOperationArn": "string",
        "ClusterType": "PROVISIONED|SERVERLESS",
        "ClusterArn": "string",
        "ClusterName": "string",
        "CreationTime": "timestamp",
        "CurrentVersion": "string",
        "State": "ACTIVE|CREATING|DELETING|FAILED|HEALING|MAINTENANCE|REBOOTING_BROKER|UPDATING",
        "StateInfo": { "Code": "string", "Message": "string" },
        "Tags": { "string": "string" },
        "Provisioned": {
            "BrokerNodeGroupInfo": {},
            "CurrentBrokerSoftwareInfo": {},
            "ClientAuthentication": {},
            "EncryptionInfo": {},
            "EnhancedMonitoring": "string",
            "OpenMonitoring": {},
            "LoggingInfo": {},
            "NumberOfBrokerNodes": "integer",
            "ZookeeperConnectString": "string",
            "ZookeeperConnectStringTls": "string",
            "StorageMode": "LOCAL|TIERED",
            "CustomerActionStatus": "string"
        },
        "Serverless": {
            "VpcConfigs": [
                {
                    "SubnetIds": ["string"],
                    "SecurityGroupIds": ["string"]
                }
            ],
            "ClientAuthentication": {
                "Sasl": { "Iam": { "Enabled": "boolean" } }
            }
        }
    }
}
```

---

## 1.6 `list-clusters`

Lists all provisioned MSK clusters in the account. **Paginated operation.**

**Synopsis:**
```bash
aws kafka list-clusters \
    [--cluster-name-filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name-filter` | No | string | None | Filter by cluster name prefix |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (1-100) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ClusterInfoList": [
        {
            "ClusterArn": "string",
            "ClusterName": "string",
            "CreationTime": "timestamp",
            "CurrentVersion": "string",
            "State": "string",
            "Tags": {}
        }
    ],
    "NextToken": "string"
}
```

---

## 1.7 `list-clusters-v2`

Lists all MSK clusters (provisioned and serverless) in the account. **Paginated operation.**

**Synopsis:**
```bash
aws kafka list-clusters-v2 \
    [--cluster-name-filter <value>] \
    [--cluster-type-filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name-filter` | No | string | None | Filter by cluster name prefix |
| `--cluster-type-filter` | No | string | None | Filter by type: `PROVISIONED` or `SERVERLESS` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (1-100) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ClusterInfoList": [
        {
            "ClusterArn": "string",
            "ClusterName": "string",
            "ClusterType": "PROVISIONED|SERVERLESS",
            "CreationTime": "timestamp",
            "CurrentVersion": "string",
            "State": "string",
            "Tags": {}
        }
    ],
    "NextToken": "string"
}
```

---

## 1.8 `get-bootstrap-brokers`

Returns the bootstrap broker connection strings for a cluster.

**Synopsis:**
```bash
aws kafka get-bootstrap-brokers \
    --cluster-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |

**Output Schema:**
```json
{
    "BootstrapBrokerString": "string",
    "BootstrapBrokerStringTls": "string",
    "BootstrapBrokerStringSaslScram": "string",
    "BootstrapBrokerStringSaslIam": "string",
    "BootstrapBrokerStringPublicTls": "string",
    "BootstrapBrokerStringPublicSaslScram": "string",
    "BootstrapBrokerStringPublicSaslIam": "string",
    "BootstrapBrokerStringVpcConnectivityTls": "string",
    "BootstrapBrokerStringVpcConnectivitySaslScram": "string",
    "BootstrapBrokerStringVpcConnectivitySaslIam": "string"
}
```

---

## 1.9 `get-compatible-kafka-versions`

Gets the list of Apache Kafka versions to which you can update the cluster.

**Synopsis:**
```bash
aws kafka get-compatible-kafka-versions \
    [--cluster-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | No | string | None | ARN of the cluster (if omitted, returns all version compatibility info) |

**Output Schema:**
```json
{
    "CompatibleKafkaVersions": [
        {
            "SourceVersion": "string",
            "TargetVersions": ["string"]
        }
    ]
}
```

---

## 1.10 `list-kafka-versions`

Lists all available Apache Kafka versions. **Paginated operation.**

**Synopsis:**
```bash
aws kafka list-kafka-versions \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "KafkaVersions": [
        {
            "Version": "string",
            "Status": "ACTIVE|DEPRECATED"
        }
    ],
    "NextToken": "string"
}
```
