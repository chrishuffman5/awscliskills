# ML Trained Models

> Commands in this file use the `aws cleanroomsml` namespace.

## 12.1 `create-trained-model`

Creates a trained model within a membership.

**Synopsis:**
```bash
aws cleanroomsml create-trained-model \
    --membership-identifier <value> \
    --name <value> \
    --configured-model-algorithm-association-arn <value> \
    --resource-config <value> \
    [--data-channels <value>] \
    [--description <value>] \
    [--environment <value>] \
    [--hyperparameters <value>] \
    [--kms-key-arn <value>] \
    [--stopping-condition <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--name` | **Yes** | string | -- | Trained model name |
| `--configured-model-algorithm-association-arn` | **Yes** | string | -- | Algorithm association ARN |
| `--resource-config` | **Yes** | structure | -- | Compute resource configuration (instance type, count, volume size) |
| `--data-channels` | No | list | None | Data channel configurations |
| `--description` | No | string | None | Description |
| `--environment` | No | map | None | Environment variables |
| `--hyperparameters` | No | map | None | Hyperparameters |
| `--kms-key-arn` | No | string | None | KMS key for encryption |
| `--stopping-condition` | No | structure | None | Training stopping condition |
| `--tags` | No | map | None | Key-value tags |

**Output Schema:**
```json
{
    "trainedModelArn": "string"
}
```

---

## 12.2 `cancel-trained-model`

Cancels a trained model that is being created.

**Synopsis:**
```bash
aws cleanroomsml cancel-trained-model \
    --membership-identifier <value> \
    --trained-model-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--trained-model-arn` | **Yes** | string | -- | Trained model ARN |

**Output Schema:**

None (HTTP 200 on success).

---

## 12.3 `delete-trained-model-output`

Deletes output from a trained model.

**Synopsis:**
```bash
aws cleanroomsml delete-trained-model-output \
    --membership-identifier <value> \
    --trained-model-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--trained-model-arn` | **Yes** | string | -- | Trained model ARN |

**Output Schema:**

None (HTTP 200 on success).

---

## 12.4 `get-trained-model`

Returns details for a trained model.

**Synopsis:**
```bash
aws cleanroomsml get-trained-model \
    --membership-identifier <value> \
    --trained-model-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--trained-model-arn` | **Yes** | string | -- | Trained model ARN |

**Output Schema:**
```json
{
    "membershipIdentifier": "string",
    "collaborationIdentifier": "string",
    "trainedModelArn": "string",
    "name": "string",
    "description": "string",
    "status": "CREATE_PENDING|CREATE_IN_PROGRESS|CREATE_FAILED|ACTIVE|DELETE_PENDING|DELETE_IN_PROGRESS|DELETE_FAILED|INACTIVE|CANCEL_PENDING|CANCEL_IN_PROGRESS",
    "statusDetails": {},
    "configuredModelAlgorithmAssociationArn": "string",
    "resourceConfig": {
        "instanceType": "string",
        "instanceCount": "integer",
        "volumeSizeInGB": "integer"
    },
    "stoppingCondition": {
        "maxRuntimeInSeconds": "integer"
    },
    "metricsStatus": "PUBLISH_SUCCEEDED|PUBLISH_FAILED",
    "metricsStatusDetails": "string",
    "logsStatus": "PUBLISH_SUCCEEDED|PUBLISH_FAILED",
    "logsStatusDetails": "string",
    "trainingContainerImageDigest": "string",
    "createTime": "timestamp",
    "updateTime": "timestamp",
    "hyperparameters": {},
    "environment": {},
    "kmsKeyArn": "string",
    "tags": {},
    "dataChannels": []
}
```

---

## 12.5 `list-trained-models`

Lists trained models for a membership. **Paginated operation.**

**Synopsis:**
```bash
aws cleanroomsml list-trained-models \
    --membership-identifier <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Output Schema:**
```json
{
    "trainedModels": [
        {
            "createTime": "timestamp",
            "updateTime": "timestamp",
            "trainedModelArn": "string",
            "name": "string",
            "description": "string",
            "membershipIdentifier": "string",
            "collaborationIdentifier": "string",
            "status": "string",
            "configuredModelAlgorithmAssociationArn": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 12.6 `list-trained-model-versions`

Lists versions of a trained model. **Paginated operation.**

**Synopsis:**
```bash
aws cleanroomsml list-trained-model-versions \
    --membership-identifier <value> \
    --trained-model-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Output Schema:**
```json
{
    "trainedModelVersions": [
        {
            "trainedModelArn": "string",
            "trainedModelVersionIdentifier": "string",
            "createTime": "timestamp",
            "status": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 12.7-12.8 Collaboration Trained Models

`get-collaboration-trained-model` and `list-collaboration-trained-models` provide collaboration-level views.

**Synopsis (get):**
```bash
aws cleanroomsml get-collaboration-trained-model \
    --trained-model-arn <value> \
    --collaboration-identifier <value>
```

**Synopsis (list):**
```bash
aws cleanroomsml list-collaboration-trained-models \
    --collaboration-identifier <value> \
    [--starting-token <value>] [--page-size <value>] [--max-items <value>]
```
