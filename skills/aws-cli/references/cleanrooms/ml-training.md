# ML Training

> Commands in this file use the `aws cleanroomsml` namespace.

## 11.1 `create-training-dataset`

Creates a training dataset for audience modeling.

**Synopsis:**
```bash
aws cleanroomsml create-training-dataset \
    --name <value> \
    --role-arn <value> \
    --training-data <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Training dataset name |
| `--role-arn` | **Yes** | string | -- | IAM role ARN for data access |
| `--training-data` | **Yes** | list | -- | Training data channel configurations |
| `--description` | No | string | None | Description |
| `--tags` | No | map | None | Key-value tags |

**Output Schema:**
```json
{
    "trainingDatasetArn": "string"
}
```

---

## 11.2 `delete-training-dataset`

Deletes a training dataset.

**Synopsis:**
```bash
aws cleanroomsml delete-training-dataset \
    --training-dataset-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--training-dataset-arn` | **Yes** | string | -- | Training dataset ARN |

**Output Schema:**

None (HTTP 200 on success).

---

## 11.3 `get-training-dataset`

Returns details for a training dataset.

**Synopsis:**
```bash
aws cleanroomsml get-training-dataset \
    --training-dataset-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--training-dataset-arn` | **Yes** | string | -- | Training dataset ARN |

**Output Schema:**
```json
{
    "createTime": "timestamp",
    "updateTime": "timestamp",
    "trainingDatasetArn": "string",
    "name": "string",
    "trainingData": [
        {
            "type": "INTERACTIONS",
            "inputConfig": {
                "schema": [
                    { "columnName": "string", "columnType": "string" }
                ],
                "dataSource": {
                    "glueDataSource": {
                        "tableName": "string",
                        "databaseName": "string",
                        "catalogId": "string"
                    }
                }
            }
        }
    ],
    "status": "ACTIVE",
    "roleArn": "string",
    "tags": { "string": "string" },
    "description": "string"
}
```

---

## 11.4 `list-training-datasets`

Lists training datasets. **Paginated operation.**

**Synopsis:**
```bash
aws cleanroomsml list-training-datasets \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Output Schema:**
```json
{
    "trainingDatasets": [
        {
            "createTime": "timestamp",
            "updateTime": "timestamp",
            "trainingDatasetArn": "string",
            "name": "string",
            "status": "string",
            "description": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 11.5 `create-ml-input-channel`

Creates an ML input channel for a collaboration membership.

**Synopsis:**
```bash
aws cleanroomsml create-ml-input-channel \
    --membership-identifier <value> \
    --configured-model-algorithm-associations <value> \
    --input-channel <value> \
    --name <value> \
    --retention-in-days <value> \
    [--description <value>] \
    [--kms-key-arn <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--configured-model-algorithm-associations` | **Yes** | list(string) | -- | Algorithm association ARNs |
| `--input-channel` | **Yes** | structure | -- | Input channel configuration |
| `--name` | **Yes** | string | -- | Channel name |
| `--retention-in-days` | **Yes** | integer | -- | Data retention in days |
| `--description` | No | string | None | Description |
| `--kms-key-arn` | No | string | None | KMS key ARN |
| `--tags` | No | map | None | Key-value tags |

**Output Schema:**
```json
{
    "mlInputChannelArn": "string"
}
```

---

## 11.6 `delete-ml-input-channel-data`

Deletes data from an ML input channel.

**Synopsis:**
```bash
aws cleanroomsml delete-ml-input-channel-data \
    --ml-input-channel-arn <value> \
    --membership-identifier <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ml-input-channel-arn` | **Yes** | string | -- | ML input channel ARN |
| `--membership-identifier` | **Yes** | string | -- | Membership ID |

**Output Schema:**

None (HTTP 200 on success).

---

## 11.7 `get-ml-input-channel`

Returns details for an ML input channel.

**Synopsis:**
```bash
aws cleanroomsml get-ml-input-channel \
    --ml-input-channel-arn <value> \
    --membership-identifier <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ml-input-channel-arn` | **Yes** | string | -- | ML input channel ARN |
| `--membership-identifier` | **Yes** | string | -- | Membership ID |

**Output Schema:**
```json
{
    "createTime": "timestamp",
    "updateTime": "timestamp",
    "membershipIdentifier": "string",
    "collaborationIdentifier": "string",
    "mlInputChannelArn": "string",
    "name": "string",
    "configuredModelAlgorithmAssociations": ["string"],
    "status": "CREATE_PENDING|CREATE_IN_PROGRESS|CREATE_FAILED|ACTIVE|DELETE_PENDING|DELETE_IN_PROGRESS|DELETE_FAILED|INACTIVE",
    "statusDetails": {},
    "retentionInDays": "integer",
    "inputChannel": {},
    "numberOfRecords": "long",
    "description": "string",
    "kmsKeyArn": "string",
    "tags": { "string": "string" }
}
```

---

## 11.8 `list-ml-input-channels`

Lists ML input channels for a membership. **Paginated operation.**

**Synopsis:**
```bash
aws cleanroomsml list-ml-input-channels \
    --membership-identifier <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Output Schema:**
```json
{
    "mlInputChannelsList": [
        {
            "createTime": "timestamp",
            "updateTime": "timestamp",
            "membershipIdentifier": "string",
            "collaborationIdentifier": "string",
            "name": "string",
            "configuredModelAlgorithmAssociations": ["string"],
            "mlInputChannelArn": "string",
            "status": "string",
            "description": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 11.9-11.10 Collaboration ML Input Channels

`get-collaboration-ml-input-channel` and `list-collaboration-ml-input-channels` provide collaboration-level views using `--collaboration-identifier`.

**Synopsis (get):**
```bash
aws cleanroomsml get-collaboration-ml-input-channel \
    --ml-input-channel-arn <value> \
    --collaboration-identifier <value>
```

**Synopsis (list):**
```bash
aws cleanroomsml list-collaboration-ml-input-channels \
    --collaboration-identifier <value> \
    [--starting-token <value>] [--page-size <value>] [--max-items <value>]
```
