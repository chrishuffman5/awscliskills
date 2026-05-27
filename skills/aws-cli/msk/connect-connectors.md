# Connect Connectors

> Commands in this file use the `aws kafkaconnect` namespace.

## 9.1 `create-connector`

Creates a new Kafka Connect connector.

**Synopsis:**
```bash
aws kafkaconnect create-connector \
    --connector-name <value> \
    --connector-configuration <value> \
    --capacity <value> \
    --kafka-cluster <value> \
    --kafka-cluster-client-authentication <value> \
    --kafka-cluster-encryption-in-transit <value> \
    --kafka-connect-version <value> \
    --plugins <value> \
    --service-execution-role-arn <value> \
    [--connector-description <value>] \
    [--log-delivery <value>] \
    [--worker-configuration <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connector-name` | **Yes** | string | -- | Connector name (1-128 chars) |
| `--connector-configuration` | **Yes** | map | -- | Key-value pairs for connector configuration |
| `--capacity` | **Yes** | structure | -- | Capacity settings (autoScaling or provisionedCapacity) |
| `--kafka-cluster` | **Yes** | structure | -- | Kafka cluster configuration (bootstrap servers, VPC) |
| `--kafka-cluster-client-authentication` | **Yes** | structure | -- | Authentication type: `NONE` or `IAM` |
| `--kafka-cluster-encryption-in-transit` | **Yes** | structure | -- | Encryption type: `PLAINTEXT` or `TLS` |
| `--kafka-connect-version` | **Yes** | string | -- | Kafka Connect version |
| `--plugins` | **Yes** | list | -- | Custom plugin specification |
| `--service-execution-role-arn` | **Yes** | string | -- | IAM role ARN |
| `--connector-description` | No | string | None | Description (max 1024 chars) |
| `--log-delivery` | No | structure | None | Log delivery configuration |
| `--worker-configuration` | No | structure | None | Worker configuration ARN and revision |
| `--tags` | No | map | None | Key-value tags |

**Capacity Structure (Auto Scaling):**
```json
{
    "autoScaling": {
        "maxWorkerCount": 10,
        "mcuCount": 1,
        "minWorkerCount": 1,
        "scaleInPolicy": {
            "cpuUtilizationPercentage": 20
        },
        "scaleOutPolicy": {
            "cpuUtilizationPercentage": 80
        }
    }
}
```

**Capacity Structure (Provisioned):**
```json
{
    "provisionedCapacity": {
        "mcuCount": 1,
        "workerCount": 2
    }
}
```

**KafkaCluster Structure:**
```json
{
    "apacheKafkaCluster": {
        "bootstrapServers": "b-1.cluster.abc.kafka.us-east-1.amazonaws.com:9098",
        "vpc": {
            "securityGroups": ["sg-123"],
            "subnets": ["subnet-abc", "subnet-def"]
        }
    }
}
```

**Output Schema:**
```json
{
    "connectorArn": "string",
    "connectorName": "string",
    "connectorState": "RUNNING|CREATING|UPDATING|DELETING|FAILED"
}
```

---

## 9.2 `delete-connector`

Deletes a Kafka Connect connector.

**Synopsis:**
```bash
aws kafkaconnect delete-connector \
    --connector-arn <value> \
    [--current-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connector-arn` | **Yes** | string | -- | ARN of the connector to delete |
| `--current-version` | No | string | None | Current version of the connector |

**Output Schema:**
```json
{
    "connectorArn": "string",
    "connectorState": "RUNNING|CREATING|UPDATING|DELETING|FAILED"
}
```

---

## 9.3 `describe-connector`

Returns details for the specified connector.

**Synopsis:**
```bash
aws kafkaconnect describe-connector \
    --connector-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connector-arn` | **Yes** | string | -- | ARN of the connector |

**Output Schema:**
```json
{
    "capacity": {
        "autoScaling": {
            "maxWorkerCount": "integer",
            "mcuCount": "integer",
            "minWorkerCount": "integer",
            "scaleInPolicy": { "cpuUtilizationPercentage": "integer" },
            "scaleOutPolicy": { "cpuUtilizationPercentage": "integer" }
        },
        "provisionedCapacity": {
            "mcuCount": "integer",
            "workerCount": "integer"
        }
    },
    "connectorArn": "string",
    "connectorConfiguration": { "string": "string" },
    "connectorDescription": "string",
    "connectorName": "string",
    "connectorState": "RUNNING|CREATING|UPDATING|DELETING|FAILED",
    "creationTime": "timestamp",
    "currentVersion": "string",
    "kafkaCluster": {
        "apacheKafkaCluster": {
            "bootstrapServers": "string",
            "vpc": {
                "securityGroups": ["string"],
                "subnets": ["string"]
            }
        }
    },
    "kafkaClusterClientAuthentication": { "authenticationType": "string" },
    "kafkaClusterEncryptionInTransit": { "encryptionType": "string" },
    "kafkaConnectVersion": "string",
    "logDelivery": {
        "workerLogDelivery": {
            "cloudWatchLogs": { "enabled": "boolean", "logGroup": "string" },
            "firehose": { "deliveryStream": "string", "enabled": "boolean" },
            "s3": { "bucket": "string", "enabled": "boolean", "prefix": "string" }
        }
    },
    "plugins": [
        {
            "customPlugin": {
                "customPluginArn": "string",
                "revision": "long"
            }
        }
    ],
    "serviceExecutionRoleArn": "string",
    "stateDescription": {
        "code": "string",
        "message": "string"
    },
    "workerConfiguration": {
        "revision": "long",
        "workerConfigurationArn": "string"
    }
}
```

---

## 9.4 `list-connectors`

Lists all Kafka Connect connectors. **Paginated operation.**

**Synopsis:**
```bash
aws kafkaconnect list-connectors \
    [--connector-name-prefix <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connector-name-prefix` | No | string | None | Filter by connector name prefix |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "connectors": [
        {
            "capacity": {},
            "connectorArn": "string",
            "connectorDescription": "string",
            "connectorName": "string",
            "connectorState": "string",
            "creationTime": "timestamp",
            "currentVersion": "string",
            "kafkaCluster": {},
            "kafkaClusterClientAuthentication": {},
            "kafkaClusterEncryptionInTransit": {},
            "kafkaConnectVersion": "string",
            "logDelivery": {},
            "plugins": [],
            "serviceExecutionRoleArn": "string",
            "workerConfiguration": {}
        }
    ],
    "nextToken": "string"
}
```

---

## 9.5 `update-connector`

Updates the capacity of a connector.

**Synopsis:**
```bash
aws kafkaconnect update-connector \
    --connector-arn <value> \
    --current-version <value> \
    --capacity <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connector-arn` | **Yes** | string | -- | ARN of the connector |
| `--current-version` | **Yes** | string | -- | Current version of the connector |
| `--capacity` | **Yes** | structure | -- | Updated capacity settings |

**Output Schema:**
```json
{
    "connectorArn": "string",
    "connectorState": "RUNNING|CREATING|UPDATING|DELETING|FAILED"
}
```

---

## 9.6 `describe-connector-operation`

Returns details for a connector operation.

**Synopsis:**
```bash
aws kafkaconnect describe-connector-operation \
    --connector-operation-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connector-operation-arn` | **Yes** | string | -- | ARN of the connector operation |

**Output Schema:**
```json
{
    "connectorArn": "string",
    "connectorOperationArn": "string",
    "connectorOperationState": "string",
    "connectorOperationType": "string",
    "creationTime": "timestamp",
    "endTime": "timestamp",
    "errorInfo": {
        "errorCode": "string",
        "errorMessage": "string"
    },
    "operationSteps": [
        {
            "stepType": "string",
            "stepState": "string"
        }
    ]
}
```

---

## 9.7 `list-connector-operations`

Lists operations for a connector. **Paginated operation.**

**Synopsis:**
```bash
aws kafkaconnect list-connector-operations \
    --connector-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connector-arn` | **Yes** | string | -- | ARN of the connector |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "connectorOperations": [
        {
            "connectorOperationArn": "string",
            "connectorOperationState": "string",
            "connectorOperationType": "string",
            "creationTime": "timestamp",
            "endTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```
