# Evaluation Jobs

### `create-evaluation-job`

Creates a model evaluation job. Supports automated evaluation (with built-in or custom metrics) and human evaluation workflows.

**Synopsis:**
```bash
aws bedrock create-evaluation-job \
    --job-name <value> \
    --role-arn <value> \
    --evaluation-config <value> \
    --inference-config <value> \
    --output-data-config <value> \
    [--job-description <value>] \
    [--client-request-token <value>] \
    [--customer-encryption-key-id <value>] \
    [--job-tags <value>] \
    [--application-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-name` | **Yes** | string | -- | Evaluation job name (1-63 chars). Pattern: `[a-z0-9](-*[a-z0-9]){0,62}` |
| `--role-arn` | **Yes** | string | -- | IAM role ARN for Bedrock to assume |
| `--evaluation-config` | **Yes** | structure | -- | Evaluation configuration (automated or human) |
| `--inference-config` | **Yes** | structure | -- | Model inference configuration |
| `--output-data-config` | **Yes** | structure | -- | S3 output location. Structure: `s3Uri=string` |
| `--job-description` | No | string | None | Description (1-200 chars) |
| `--client-request-token` | No | string | None | Idempotency token (1-256 chars) |
| `--customer-encryption-key-id` | No | string | None | KMS key ARN for encryption |
| `--job-tags` | No | list | None | Tags (max 200) |
| `--application-type` | No | string | None | `ModelEvaluation` or `RagEvaluation` |

**Automated Evaluation Config:**
```json
{
    "automated": {
        "datasetMetricConfigs": [
            {
                "taskType": "Summarization|Classification|QuestionAndAnswer|Generation|Custom",
                "dataset": {
                    "name": "string",
                    "datasetLocation": {
                        "s3Uri": "s3://bucket/dataset.jsonl"
                    }
                },
                "metricNames": ["Builtin.Correctness", "Builtin.Completeness"]
            }
        ],
        "evaluatorModelConfig": {
            "bedrockEvaluatorModels": [
                {
                    "modelIdentifier": "string"
                }
            ]
        }
    }
}
```

**Model Inference Config:**
```json
{
    "models": [
        {
            "bedrockModel": {
                "modelIdentifier": "anthropic.claude-3-sonnet-20240229-v1:0",
                "inferenceParams": "{\"maxTokens\":1024,\"temperature\":0.7}",
                "performanceConfig": {
                    "latency": "standard|optimized"
                }
            }
        }
    ]
}
```

**RAG Inference Config:**
```json
{
    "ragConfigs": [
        {
            "knowledgeBaseConfig": {
                "retrieveAndGenerateConfig": {
                    "type": "KNOWLEDGE_BASE",
                    "knowledgeBaseConfiguration": {
                        "knowledgeBaseId": "string",
                        "modelArn": "string"
                    }
                }
            }
        }
    ]
}
```

**Built-in Metrics:**
- Model evaluation: `Builtin.Accuracy`, `Builtin.Robustness`, `Builtin.Toxicity`
- LLM-as-judge: `Builtin.Correctness`, `Builtin.Completeness`, `Builtin.Faithfulness`, `Builtin.Helpfulness`, `Builtin.Coherence`, `Builtin.Relevance`, `Builtin.FollowingInstructions`, `Builtin.ProfessionalStyleAndTone`
- Responsible AI: `Builtin.Harmfulness`, `Builtin.Stereotyping`, `Builtin.Refusal`
- Knowledge base retrieval: `Builtin.ContextRelevance`, `Builtin.ContextCoverage`

**Output Schema:**
```json
{
    "jobArn": "string"
}
```

---

### `get-evaluation-job`

Gets details of an evaluation job.

**Synopsis:**
```bash
aws bedrock get-evaluation-job \
    --job-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-identifier` | **Yes** | string | -- | Job name or ARN |

**Output Schema:**
```json
{
    "jobName": "string",
    "jobArn": "string",
    "jobDescription": "string",
    "jobType": "Human|Automated",
    "status": "InProgress|Completed|Failed|Stopping|Stopped",
    "evaluationConfig": {...},
    "inferenceConfig": {...},
    "roleArn": "string",
    "customerEncryptionKeyId": "string",
    "outputDataConfig": {
        "s3Uri": "string"
    },
    "creationTime": "timestamp",
    "lastModifiedTime": "timestamp",
    "failureMessages": ["string"],
    "applicationType": "ModelEvaluation|RagEvaluation"
}
```

---

### `list-evaluation-jobs`

Lists evaluation jobs in the account. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock list-evaluation-jobs \
    [--creation-time-after <value>] \
    [--creation-time-before <value>] \
    [--status-equals <value>] \
    [--application-type-equals <value>] \
    [--name-contains <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--creation-time-after` | No | timestamp | None | Filter by creation time |
| `--creation-time-before` | No | timestamp | None | Filter by creation time |
| `--status-equals` | No | string | None | Filter: `InProgress`, `Completed`, `Failed`, `Stopping`, `Stopped` |
| `--application-type-equals` | No | string | None | Filter: `ModelEvaluation`, `RagEvaluation` |
| `--name-contains` | No | string | None | Filter by name substring |
| `--sort-by` | No | string | None | Sort field: `CreationTime` |
| `--sort-order` | No | string | None | `Ascending`, `Descending` |

**Output Schema:**
```json
{
    "nextToken": "string",
    "jobSummaries": [
        {
            "jobArn": "string",
            "jobName": "string",
            "status": "InProgress|Completed|Failed|Stopping|Stopped",
            "creationTime": "timestamp",
            "jobType": "Human|Automated",
            "evaluationTaskTypes": ["string"],
            "modelIdentifiers": ["string"],
            "ragIdentifiers": ["string"],
            "evaluatorModelIdentifiers": ["string"],
            "applicationType": "ModelEvaluation|RagEvaluation"
        }
    ]
}
```

---

### `stop-evaluation-job`

Stops a running evaluation job.

**Synopsis:**
```bash
aws bedrock stop-evaluation-job \
    --job-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-identifier` | **Yes** | string | -- | Job name or ARN |

**Output:** None (HTTP 200 on success)

---

### `batch-delete-evaluation-job`

Deletes multiple evaluation jobs in a single request.

**Synopsis:**
```bash
aws bedrock batch-delete-evaluation-job \
    --job-identifiers <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-identifiers` | **Yes** | list(string) | -- | List of job ARNs to delete (1-25) |

**Output Schema:**
```json
{
    "errors": [
        {
            "jobIdentifier": "string",
            "code": "string",
            "message": "string"
        }
    ],
    "evaluationJobs": [
        {
            "jobIdentifier": "string",
            "status": "Deleting"
        }
    ]
}
```
