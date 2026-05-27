# ML Inference

> Commands in this file use the `aws cleanroomsml` namespace.

## 13.1 `start-trained-model-inference-job`

Starts an inference job using a trained model.

**Synopsis:**
```bash
aws cleanroomsml start-trained-model-inference-job \
    --membership-identifier <value> \
    --name <value> \
    --trained-model-arn <value> \
    --configured-model-algorithm-association-arn <value> \
    --resource-config <value> \
    --output-configuration <value> \
    --data-source <value> \
    [--description <value>] \
    [--container-execution-parameters <value>] \
    [--environment <value>] \
    [--kms-key-arn <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--name` | **Yes** | string | -- | Inference job name |
| `--trained-model-arn` | **Yes** | string | -- | Trained model ARN |
| `--configured-model-algorithm-association-arn` | **Yes** | string | -- | Algorithm association ARN |
| `--resource-config` | **Yes** | structure | -- | Compute configuration |
| `--output-configuration` | **Yes** | structure | -- | Output configuration |
| `--data-source` | **Yes** | structure | -- | Input data source |
| `--description` | No | string | None | Description |
| `--container-execution-parameters` | No | structure | None | Container execution parameters |
| `--environment` | No | map | None | Environment variables |
| `--kms-key-arn` | No | string | None | KMS key |
| `--tags` | No | map | None | Key-value tags |

**Output Schema:**
```json
{
    "trainedModelInferenceJobArn": "string"
}
```

---

## 13.2 `cancel-trained-model-inference-job`

Cancels a running inference job.

**Synopsis:**
```bash
aws cleanroomsml cancel-trained-model-inference-job \
    --membership-identifier <value> \
    --trained-model-inference-job-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--trained-model-inference-job-arn` | **Yes** | string | -- | Inference job ARN |

**Output Schema:**

None (HTTP 200 on success).

---

## 13.3 `get-trained-model-inference-job`

Returns details for an inference job.

**Synopsis:**
```bash
aws cleanroomsml get-trained-model-inference-job \
    --membership-identifier <value> \
    --trained-model-inference-job-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--trained-model-inference-job-arn` | **Yes** | string | -- | Inference job ARN |

**Output Schema:**
```json
{
    "createTime": "timestamp",
    "updateTime": "timestamp",
    "trainedModelInferenceJobArn": "string",
    "configuredModelAlgorithmAssociationArn": "string",
    "name": "string",
    "status": "CREATE_PENDING|CREATE_IN_PROGRESS|CREATE_FAILED|ACTIVE|CANCEL_PENDING|CANCEL_IN_PROGRESS|INACTIVE",
    "trainedModelArn": "string",
    "resourceConfig": {},
    "outputConfiguration": {},
    "membershipIdentifier": "string",
    "collaborationIdentifier": "string",
    "dataSource": {},
    "containerExecutionParameters": {},
    "statusDetails": {},
    "description": "string",
    "environment": {},
    "kmsKeyArn": "string",
    "metricsStatus": "string",
    "metricsStatusDetails": "string",
    "logsStatus": "string",
    "logsStatusDetails": "string",
    "tags": {}
}
```

---

## 13.4 `list-trained-model-inference-jobs`

Lists inference jobs for a membership. **Paginated operation.**

**Synopsis:**
```bash
aws cleanroomsml list-trained-model-inference-jobs \
    --membership-identifier <value> \
    [--trained-model-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Output Schema:**
```json
{
    "trainedModelInferenceJobs": [
        {
            "trainedModelInferenceJobArn": "string",
            "configuredModelAlgorithmAssociationArn": "string",
            "membershipIdentifier": "string",
            "trainedModelArn": "string",
            "collaborationIdentifier": "string",
            "status": "string",
            "outputConfiguration": {},
            "name": "string",
            "description": "string",
            "metricsStatus": "string",
            "logsStatus": "string",
            "createTime": "timestamp",
            "updateTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

## 13.5 `start-trained-model-export-job`

Starts a trained model export job.

**Synopsis:**
```bash
aws cleanroomsml start-trained-model-export-job \
    --membership-identifier <value> \
    --name <value> \
    --trained-model-arn <value> \
    --output-configuration <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--name` | **Yes** | string | -- | Export job name |
| `--trained-model-arn` | **Yes** | string | -- | Trained model ARN |
| `--output-configuration` | **Yes** | structure | -- | Output configuration |
| `--description` | No | string | None | Description |

**Output Schema:**

None (HTTP 200 on success).

---

## 13.6-13.7 Collaboration Inference and Export Jobs

`list-collaboration-trained-model-export-jobs` and `list-collaboration-trained-model-inference-jobs` provide collaboration-level views.

**Synopsis (list export jobs):**
```bash
aws cleanroomsml list-collaboration-trained-model-export-jobs \
    --collaboration-identifier <value> \
    --trained-model-arn <value> \
    [--starting-token <value>] [--page-size <value>] [--max-items <value>]
```

**Synopsis (list inference jobs):**
```bash
aws cleanroomsml list-collaboration-trained-model-inference-jobs \
    --collaboration-identifier <value> \
    [--trained-model-arn <value>] \
    [--starting-token <value>] [--page-size <value>] [--max-items <value>]
```
