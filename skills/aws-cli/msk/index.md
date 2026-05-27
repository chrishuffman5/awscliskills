# AWS CLI v2 -- MSK (Managed Streaming for Apache Kafka) Command Reference Index

> Based on AWS CLI v2 documentation. Sources: https://docs.aws.amazon.com/cli/latest/reference/kafka/ , https://docs.aws.amazon.com/cli/latest/reference/kafkaconnect/

---

## Quick Reference — `aws kafka`

| Command | Category | Description |
|---------|----------|-------------|
| `create-cluster` | Cluster | Create a provisioned MSK cluster |
| `create-cluster-v2` | Cluster | Create a provisioned or serverless MSK cluster (v2 API) |
| `delete-cluster` | Cluster | Delete an MSK cluster |
| `describe-cluster` | Cluster | Describe a provisioned cluster |
| `describe-cluster-v2` | Cluster | Describe a cluster (v2 API, provisioned or serverless) |
| `list-clusters` | Cluster | List provisioned clusters |
| `list-clusters-v2` | Cluster | List clusters (v2 API, provisioned and serverless) |
| `get-bootstrap-brokers` | Cluster | Get bootstrap broker connection strings |
| `get-compatible-kafka-versions` | Cluster | Get compatible Kafka version upgrade paths |
| `list-kafka-versions` | Cluster | List available Apache Kafka versions |
| `create-configuration` | Configuration | Create a broker configuration |
| `delete-configuration` | Configuration | Delete a configuration |
| `describe-configuration` | Configuration | Describe a configuration |
| `describe-configuration-revision` | Configuration | Describe a specific configuration revision |
| `list-configurations` | Configuration | List all configurations |
| `list-configuration-revisions` | Configuration | List revisions for a configuration |
| `update-cluster-configuration` | Configuration | Apply a configuration to a cluster |
| `update-cluster-kafka-version` | Configuration | Upgrade the Apache Kafka version |
| `update-monitoring` | Configuration | Update monitoring settings |
| `update-rebalancing` | Configuration | Update intelligent rebalancing settings |
| `create-topic` | Topic | Create a topic in a cluster |
| `delete-topic` | Topic | Delete a topic |
| `describe-topic` | Topic | Describe a topic |
| `describe-topic-partitions` | Topic | Describe topic partitions |
| `list-topics` | Topic | List topics in a cluster |
| `update-topic` | Topic | Update topic configuration |
| `update-broker-count` | Broker | Scale the number of brokers |
| `update-broker-storage` | Broker | Update broker EBS storage |
| `update-broker-type` | Broker | Change broker instance type |
| `update-storage` | Broker | Update storage configuration |
| `reboot-broker` | Broker | Reboot a specific broker |
| `list-nodes` | Broker | List nodes in a cluster |
| `update-connectivity` | Broker | Update cluster connectivity settings |
| `update-security` | Broker | Update cluster security settings |
| `create-replicator` | Replicator | Create a cross-cluster replicator |
| `delete-replicator` | Replicator | Delete a replicator |
| `describe-replicator` | Replicator | Describe a replicator |
| `list-replicators` | Replicator | List all replicators |
| `update-replication-info` | Replicator | Update replication configuration |
| `create-vpc-connection` | VPC | Create a VPC connection to a cluster |
| `delete-vpc-connection` | VPC | Delete a VPC connection |
| `describe-vpc-connection` | VPC | Describe a VPC connection |
| `list-vpc-connections` | VPC | List VPC connections |
| `list-client-vpc-connections` | VPC | List client VPC connections for a cluster |
| `reject-client-vpc-connection` | VPC | Reject a client VPC connection request |
| `batch-associate-scram-secret` | SCRAM | Associate SCRAM secrets with a cluster |
| `batch-disassociate-scram-secret` | SCRAM | Disassociate SCRAM secrets from a cluster |
| `list-scram-secrets` | SCRAM | List SCRAM secrets for a cluster |
| `describe-cluster-operation` | Operations | Describe a cluster operation |
| `describe-cluster-operation-v2` | Operations | Describe a cluster operation (v2 API) |
| `list-cluster-operations` | Operations | List cluster operations |
| `list-cluster-operations-v2` | Operations | List cluster operations (v2 API) |
| `get-cluster-policy` | Policy | Get the cluster resource policy |
| `put-cluster-policy` | Policy | Set a cluster resource policy |
| `delete-cluster-policy` | Policy | Delete a cluster resource policy |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

## Quick Reference — `aws kafkaconnect`

| Command | Category | Description |
|---------|----------|-------------|
| `create-connector` | Connector | Create a Kafka Connect connector |
| `delete-connector` | Connector | Delete a connector |
| `describe-connector` | Connector | Describe a connector |
| `list-connectors` | Connector | List all connectors |
| `update-connector` | Connector | Update connector capacity |
| `describe-connector-operation` | Connector | Describe a connector operation |
| `list-connector-operations` | Connector | List connector operations |
| `create-custom-plugin` | Plugin | Create a custom plugin |
| `delete-custom-plugin` | Plugin | Delete a custom plugin |
| `describe-custom-plugin` | Plugin | Describe a custom plugin |
| `list-custom-plugins` | Plugin | List all custom plugins |
| `create-worker-configuration` | Worker | Create a worker configuration |
| `delete-worker-configuration` | Worker | Delete a worker configuration |
| `describe-worker-configuration` | Worker | Describe a worker configuration |
| `list-worker-configurations` | Worker | List all worker configurations |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws kafka` and `aws kafkaconnect` commands.

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `--debug` | boolean | false | Enable debug logging to stderr |
| `--endpoint-url` | string | -- | Override the default service endpoint URL |
| `--no-verify-ssl` | boolean | false | Disable SSL certificate verification |
| `--no-paginate` | boolean | false | Disable automatic pagination |
| `--output` | string | `json` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | -- | JMESPath query to filter output |
| `--profile` | string | `default` | Named AWS credential profile |
| `--region` | string | from config | AWS region to send requests to |
| `--version` | string | -- | Display the CLI version |
| `--color` | string | `auto` | Toggle color output: `on`, `off`, `auto` |
| `--no-sign-request` | boolean | false | Do not sign requests |
| `--ca-bundle` | string | -- | Path to custom CA certificate bundle |
| `--cli-read-timeout` | integer | 60 | Socket read timeout in seconds |
| `--cli-connect-timeout` | integer | 60 | Socket connect timeout in seconds |
| `--cli-binary-format` | string | `base64` | Format for binary blob input: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from a JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from a YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton: `input`, `yaml-input`, `output` |

---

## Common Patterns

### Cluster States
| State | Description |
|-------|-------------|
| `ACTIVE` | Cluster is running and available |
| `CREATING` | Cluster is being created |
| `DELETING` | Cluster is being deleted |
| `FAILED` | Cluster creation or operation failed |
| `HEALING` | Cluster is auto-recovering |
| `MAINTENANCE` | Cluster is undergoing maintenance |
| `REBOOTING_BROKER` | A broker is being rebooted |
| `UPDATING` | Cluster is being updated |

### Enhanced Monitoring Levels
| Level | Description |
|-------|-------------|
| `DEFAULT` | Basic broker-level metrics |
| `PER_BROKER` | Enhanced per-broker metrics |
| `PER_TOPIC_PER_BROKER` | Per-topic metrics on each broker |
| `PER_TOPIC_PER_PARTITION` | Most detailed — per-partition metrics |

### Client Authentication Types
| Type | Description |
|------|-------------|
| SASL/SCRAM | Username/password via AWS Secrets Manager |
| SASL/IAM | IAM-based authentication |
| TLS | Mutual TLS with ACM Private CA |
| Unauthenticated | No client authentication |

### Connector States (kafkaconnect)
| State | Description |
|-------|-------------|
| `RUNNING` | Connector is active |
| `CREATING` | Connector is being created |
| `UPDATING` | Connector is being updated |
| `DELETING` | Connector is being deleted |
| `FAILED` | Connector has failed |
