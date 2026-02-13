# Topics

## 3.1 `create-topic`

Creates a new topic in the specified MSK cluster.

**Synopsis:**
```bash
aws kafka create-topic \
    --cluster-arn <value> \
    --topic-name <value> \
    --partition-count <value> \
    --replication-factor <value> \
    [--configs <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |
| `--topic-name` | **Yes** | string | -- | Name of the topic to create |
| `--partition-count` | **Yes** | integer | -- | Number of partitions (min: 1) |
| `--replication-factor` | **Yes** | integer | -- | Replication factor (min: 1) |
| `--configs` | No | string | None | Topic configurations encoded as a Base64 string |

**Output Schema:**
```json
{
    "TopicArn": "string",
    "TopicName": "string",
    "Status": "CREATING|UPDATING|DELETING|ACTIVE"
}
```

---

## 3.2 `delete-topic`

Deletes a topic from the specified cluster.

**Synopsis:**
```bash
aws kafka delete-topic \
    --cluster-arn <value> \
    --topic-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |
| `--topic-name` | **Yes** | string | -- | Name of the topic to delete |

**Output Schema:**
```json
{
    "TopicArn": "string",
    "TopicName": "string",
    "Status": "CREATING|UPDATING|DELETING|ACTIVE"
}
```

---

## 3.3 `describe-topic`

Returns details for the specified topic.

**Synopsis:**
```bash
aws kafka describe-topic \
    --cluster-arn <value> \
    --topic-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |
| `--topic-name` | **Yes** | string | -- | Name of the topic |

**Output Schema:**
```json
{
    "TopicArn": "string",
    "TopicName": "string",
    "PartitionCount": "integer",
    "ReplicationFactor": "integer",
    "Status": "CREATING|UPDATING|DELETING|ACTIVE",
    "Configs": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```

---

## 3.4 `describe-topic-partitions`

Returns partition details for the specified topic.

**Synopsis:**
```bash
aws kafka describe-topic-partitions \
    --cluster-arn <value> \
    --topic-name <value> \
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
| `--topic-name` | **Yes** | string | -- | Name of the topic |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "TopicArn": "string",
    "TopicName": "string",
    "Partitions": [
        {
            "PartitionIndex": "integer",
            "LeaderBrokerId": "integer",
            "ReplicaBrokerIds": ["integer"],
            "InSyncReplicaBrokerIds": ["integer"]
        }
    ],
    "NextToken": "string"
}
```

---

## 3.5 `list-topics`

Lists all topics in the specified cluster. **Paginated operation.**

**Synopsis:**
```bash
aws kafka list-topics \
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
    "Topics": [
        {
            "TopicArn": "string",
            "TopicName": "string",
            "PartitionCount": "integer",
            "ReplicationFactor": "integer",
            "Status": "CREATING|UPDATING|DELETING|ACTIVE"
        }
    ],
    "NextToken": "string"
}
```

---

## 3.6 `update-topic`

Updates the configuration of a topic.

**Synopsis:**
```bash
aws kafka update-topic \
    --cluster-arn <value> \
    --topic-name <value> \
    [--partition-count <value>] \
    [--configs <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |
| `--topic-name` | **Yes** | string | -- | Name of the topic |
| `--partition-count` | No | integer | None | New partition count (can only increase) |
| `--configs` | No | string | None | Updated topic configurations encoded as a Base64 string |

**Output Schema:**
```json
{
    "TopicArn": "string",
    "TopicName": "string",
    "Status": "CREATING|UPDATING|DELETING|ACTIVE"
}
```
