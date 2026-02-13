# Configuration

## 2.1 `create-configuration`

Creates a new MSK broker configuration.

**Synopsis:**
```bash
aws kafka create-configuration \
    --name <value> \
    --server-properties <value> \
    [--description <value>] \
    [--kafka-versions <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Configuration name |
| `--server-properties` | **Yes** | blob | -- | Contents of server.properties file. Use `fileb://` prefix for file input |
| `--description` | No | string | None | Description of the configuration |
| `--kafka-versions` | No | list(string) | None | Compatible Apache Kafka versions |

**Output Schema:**
```json
{
    "Arn": "string",
    "CreationTime": "timestamp",
    "LatestRevision": {
        "CreationTime": "timestamp",
        "Description": "string",
        "Revision": "long"
    },
    "Name": "string",
    "State": "ACTIVE|DELETING|DELETE_FAILED"
}
```

---

## 2.2 `delete-configuration`

Deletes an MSK configuration.

**Synopsis:**
```bash
aws kafka delete-configuration \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the configuration to delete |

**Output Schema:**
```json
{
    "Arn": "string",
    "State": "ACTIVE|DELETING|DELETE_FAILED"
}
```

---

## 2.3 `describe-configuration`

Returns a description of a configuration.

**Synopsis:**
```bash
aws kafka describe-configuration \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the configuration |

**Output Schema:**
```json
{
    "Arn": "string",
    "CreationTime": "timestamp",
    "Description": "string",
    "KafkaVersions": ["string"],
    "LatestRevision": {
        "CreationTime": "timestamp",
        "Description": "string",
        "Revision": "long"
    },
    "Name": "string",
    "State": "ACTIVE|DELETING|DELETE_FAILED"
}
```

---

## 2.4 `describe-configuration-revision`

Returns a description of a specific configuration revision.

**Synopsis:**
```bash
aws kafka describe-configuration-revision \
    --arn <value> \
    --revision <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the configuration |
| `--revision` | **Yes** | long | -- | Revision number |

**Output Schema:**
```json
{
    "Arn": "string",
    "CreationTime": "timestamp",
    "Description": "string",
    "Revision": "long",
    "ServerProperties": "blob"
}
```

---

## 2.5 `list-configurations`

Lists all MSK configurations in the account. **Paginated operation.**

**Synopsis:**
```bash
aws kafka list-configurations \
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
    "Configurations": [
        {
            "Arn": "string",
            "CreationTime": "timestamp",
            "Description": "string",
            "KafkaVersions": ["string"],
            "LatestRevision": {
                "CreationTime": "timestamp",
                "Description": "string",
                "Revision": "long"
            },
            "Name": "string",
            "State": "ACTIVE|DELETING|DELETE_FAILED"
        }
    ],
    "NextToken": "string"
}
```

---

## 2.6 `list-configuration-revisions`

Lists revisions for a configuration. **Paginated operation.**

**Synopsis:**
```bash
aws kafka list-configuration-revisions \
    --arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the configuration |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Revisions": [
        {
            "CreationTime": "timestamp",
            "Description": "string",
            "Revision": "long"
        }
    ],
    "NextToken": "string"
}
```

---

## 2.7 `update-cluster-configuration`

Updates the cluster to use a specified configuration revision.

**Synopsis:**
```bash
aws kafka update-cluster-configuration \
    --cluster-arn <value> \
    --current-version <value> \
    --configuration-info <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |
| `--current-version` | **Yes** | string | -- | Current cluster version (from describe-cluster) |
| `--configuration-info` | **Yes** | structure | -- | Configuration ARN and revision. Shorthand: `Arn=string,Revision=long` |

**Output Schema:**
```json
{
    "ClusterArn": "string",
    "ClusterOperationArn": "string"
}
```

---

## 2.8 `update-cluster-kafka-version`

Upgrades the Apache Kafka version of the cluster.

**Synopsis:**
```bash
aws kafka update-cluster-kafka-version \
    --cluster-arn <value> \
    --current-version <value> \
    --target-kafka-version <value> \
    [--configuration-info <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |
| `--current-version` | **Yes** | string | -- | Current cluster version |
| `--target-kafka-version` | **Yes** | string | -- | Target Kafka version to upgrade to |
| `--configuration-info` | No | structure | None | Configuration to use after upgrade |

**Output Schema:**
```json
{
    "ClusterArn": "string",
    "ClusterOperationArn": "string"
}
```

---

## 2.9 `update-monitoring`

Updates the monitoring settings for a cluster.

**Synopsis:**
```bash
aws kafka update-monitoring \
    --cluster-arn <value> \
    --current-version <value> \
    [--enhanced-monitoring <value>] \
    [--open-monitoring <value>] \
    [--logging-info <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |
| `--current-version` | **Yes** | string | -- | Current cluster version |
| `--enhanced-monitoring` | No | string | None | Monitoring level: `DEFAULT`, `PER_BROKER`, `PER_TOPIC_PER_BROKER`, `PER_TOPIC_PER_PARTITION` |
| `--open-monitoring` | No | structure | None | Prometheus exporter settings |
| `--logging-info` | No | structure | None | Broker log delivery settings |

**Output Schema:**
```json
{
    "ClusterArn": "string",
    "ClusterOperationArn": "string"
}
```

---

## 2.10 `update-rebalancing`

Updates the intelligent rebalancing configuration for the cluster.

**Synopsis:**
```bash
aws kafka update-rebalancing \
    --cluster-arn <value> \
    --current-version <value> \
    --rebalancing <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |
| `--current-version` | **Yes** | string | -- | Current cluster version |
| `--rebalancing` | **Yes** | structure | -- | Rebalancing settings. Shorthand: `Status=PAUSED\|ACTIVE` |

**Output Schema:**
```json
{
    "ClusterArn": "string",
    "ClusterOperationArn": "string"
}
```
