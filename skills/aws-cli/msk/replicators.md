# Replicators

## 5.1 `create-replicator`

Creates an MSK replicator for cross-cluster data replication.

**Synopsis:**
```bash
aws kafka create-replicator \
    --replicator-name <value> \
    --kafka-clusters <value> \
    --replication-info-list <value> \
    --service-execution-role-arn <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replicator-name` | **Yes** | string | -- | Name of the replicator (1-128 chars, alphanumeric + hyphens) |
| `--kafka-clusters` | **Yes** | list | -- | Kafka clusters to use as source/target |
| `--replication-info-list` | **Yes** | list | -- | Replication flow configurations (source-to-target) |
| `--service-execution-role-arn` | **Yes** | string | -- | IAM role ARN for accessing cluster resources |
| `--description` | No | string | None | Description (max 1024 chars) |
| `--tags` | No | map | None | Key-value tags |

**KafkaClusters Structure:**
```json
[
    {
        "AmazonMskCluster": {
            "MskClusterArn": "arn:aws:kafka:us-east-1:123456789012:cluster/source/abc"
        },
        "VpcConfig": {
            "SubnetIds": ["subnet-abc", "subnet-def"],
            "SecurityGroupIds": ["sg-123"]
        }
    },
    {
        "AmazonMskCluster": {
            "MskClusterArn": "arn:aws:kafka:us-west-2:123456789012:cluster/target/def"
        },
        "VpcConfig": {
            "SubnetIds": ["subnet-ghi", "subnet-jkl"],
            "SecurityGroupIds": ["sg-456"]
        }
    }
]
```

**ReplicationInfoList Structure:**
```json
[
    {
        "SourceKafkaClusterArn": "arn:aws:kafka:us-east-1:...",
        "TargetKafkaClusterArn": "arn:aws:kafka:us-west-2:...",
        "TargetCompressionType": "NONE|GZIP|SNAPPY|LZ4|ZSTD",
        "TopicReplication": {
            "TopicsToReplicate": [".*"],
            "TopicsToExclude": ["__.*"],
            "CopyAccessControlListsForTopics": true,
            "CopyTopicConfigurations": true,
            "DetectAndCopyNewTopics": true,
            "StartingPosition": { "Type": "LATEST|EARLIEST" },
            "TopicNameConfiguration": { "Type": "PREFIXED_WITH_SOURCE_CLUSTER_ALIAS|IDENTICAL" }
        },
        "ConsumerGroupReplication": {
            "ConsumerGroupsToReplicate": [".*"],
            "ConsumerGroupsToExclude": [],
            "DetectAndCopyNewConsumerGroups": true,
            "SynchroniseConsumerGroupOffsets": true
        }
    }
]
```

**Output Schema:**
```json
{
    "ReplicatorArn": "string",
    "ReplicatorName": "string",
    "ReplicatorState": "RUNNING|CREATING|UPDATING|DELETING|FAILED"
}
```

---

## 5.2 `delete-replicator`

Deletes an MSK replicator.

**Synopsis:**
```bash
aws kafka delete-replicator \
    --replicator-arn <value> \
    [--current-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replicator-arn` | **Yes** | string | -- | ARN of the replicator to delete |
| `--current-version` | No | string | None | Current version of the replicator |

**Output Schema:**
```json
{
    "ReplicatorArn": "string",
    "ReplicatorState": "RUNNING|CREATING|UPDATING|DELETING|FAILED"
}
```

---

## 5.3 `describe-replicator`

Returns details for the specified replicator.

**Synopsis:**
```bash
aws kafka describe-replicator \
    --replicator-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replicator-arn` | **Yes** | string | -- | ARN of the replicator |

**Output Schema:**
```json
{
    "CreationTime": "timestamp",
    "CurrentVersion": "string",
    "IsReplicatorReference": "boolean",
    "KafkaClusters": [
        {
            "AmazonMskCluster": { "MskClusterArn": "string" },
            "KafkaClusterAlias": "string",
            "VpcConfig": {
                "SecurityGroupIds": ["string"],
                "SubnetIds": ["string"]
            }
        }
    ],
    "ReplicationInfoList": [
        {
            "ConsumerGroupReplication": {
                "ConsumerGroupsToExclude": ["string"],
                "ConsumerGroupsToReplicate": ["string"],
                "DetectAndCopyNewConsumerGroups": "boolean",
                "SynchroniseConsumerGroupOffsets": "boolean"
            },
            "SourceKafkaClusterAlias": "string",
            "TargetCompressionType": "string",
            "TargetKafkaClusterAlias": "string",
            "TopicReplication": {
                "CopyAccessControlListsForTopics": "boolean",
                "CopyTopicConfigurations": "boolean",
                "DetectAndCopyNewTopics": "boolean",
                "TopicsToExclude": ["string"],
                "TopicsToReplicate": ["string"],
                "StartingPosition": { "Type": "string" },
                "TopicNameConfiguration": { "Type": "string" }
            }
        }
    ],
    "ReplicatorArn": "string",
    "ReplicatorDescription": "string",
    "ReplicatorName": "string",
    "ReplicatorResourceArn": "string",
    "ReplicatorState": "RUNNING|CREATING|UPDATING|DELETING|FAILED",
    "ServiceExecutionRoleArn": "string",
    "StateInfo": { "Code": "string", "Message": "string" },
    "Tags": { "string": "string" }
}
```

---

## 5.4 `list-replicators`

Lists all MSK replicators in the account. **Paginated operation.**

**Synopsis:**
```bash
aws kafka list-replicators \
    [--replicator-name-filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replicator-name-filter` | No | string | None | Filter by replicator name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Replicators": [
        {
            "CreationTime": "timestamp",
            "CurrentVersion": "string",
            "IsReplicatorReference": "boolean",
            "KafkaClustersSummary": [
                {
                    "AmazonMskCluster": { "MskClusterArn": "string" },
                    "KafkaClusterAlias": "string"
                }
            ],
            "ReplicationInfoSummaryList": [
                {
                    "SourceKafkaClusterAlias": "string",
                    "TargetKafkaClusterAlias": "string"
                }
            ],
            "ReplicatorArn": "string",
            "ReplicatorName": "string",
            "ReplicatorResourceArn": "string",
            "ReplicatorState": "string"
        }
    ],
    "NextToken": "string"
}
```

---

## 5.5 `update-replication-info`

Updates replication configuration for an existing replicator.

**Synopsis:**
```bash
aws kafka update-replication-info \
    --replicator-arn <value> \
    --current-version <value> \
    --source-kafka-cluster-arn <value> \
    --target-kafka-cluster-arn <value> \
    [--consumer-group-replication <value>] \
    [--topic-replication <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replicator-arn` | **Yes** | string | -- | ARN of the replicator |
| `--current-version` | **Yes** | string | -- | Current version of the replicator |
| `--source-kafka-cluster-arn` | **Yes** | string | -- | Source cluster ARN |
| `--target-kafka-cluster-arn` | **Yes** | string | -- | Target cluster ARN |
| `--consumer-group-replication` | No | structure | None | Updated consumer group replication config |
| `--topic-replication` | No | structure | None | Updated topic replication config |

**Output Schema:**
```json
{
    "ReplicatorArn": "string",
    "ReplicatorState": "RUNNING|CREATING|UPDATING|DELETING|FAILED"
}
```
