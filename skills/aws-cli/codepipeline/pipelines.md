# Pipelines

### 1.1 `create-pipeline`

Creates a pipeline. The pipeline structure is typically provided via JSON file.

**Synopsis:**
```bash
aws codepipeline create-pipeline \
    --pipeline <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline` | **Yes** | structure | -- | Pipeline structure (JSON) |
| `--tags` | No | list | None | Tags. Shorthand: `key=string,value=string ...` |

**Pipeline Structure:**
```json
{
    "name": "string",
    "roleArn": "string",
    "artifactStore": {
        "type": "S3",
        "location": "string",
        "encryptionKey": {
            "id": "string",
            "type": "KMS"
        }
    },
    "artifactStores": {
        "string": {
            "type": "S3",
            "location": "string",
            "encryptionKey": {
                "id": "string",
                "type": "KMS"
            }
        }
    },
    "stages": [
        {
            "name": "string",
            "blockers": [
                {
                    "name": "string",
                    "type": "Schedule"
                }
            ],
            "actions": [
                {
                    "name": "string",
                    "actionTypeId": {
                        "category": "Source|Build|Deploy|Test|Invoke|Approval",
                        "owner": "AWS|ThirdParty|Custom",
                        "provider": "string",
                        "version": "string"
                    },
                    "runOrder": "integer",
                    "configuration": {},
                    "outputArtifacts": [
                        {
                            "name": "string"
                        }
                    ],
                    "inputArtifacts": [
                        {
                            "name": "string"
                        }
                    ],
                    "roleArn": "string",
                    "region": "string",
                    "namespace": "string",
                    "timeoutInMinutes": "integer"
                }
            ],
            "onFailure": {
                "result": "ROLLBACK|FAIL",
                "retryConfiguration": {
                    "retryMode": "FAILED_ACTIONS|ALL_ACTIONS"
                },
                "conditions": []
            },
            "onSuccess": {
                "conditions": []
            },
            "beforeEntry": {
                "conditions": []
            }
        }
    ],
    "pipelineType": "V1|V2",
    "variables": [
        {
            "name": "string",
            "defaultValue": "string",
            "description": "string"
        }
    ],
    "triggers": [
        {
            "providerType": "CodeStarSourceConnection",
            "gitConfiguration": {
                "sourceActionName": "string",
                "push": [
                    {
                        "tags": {
                            "includes": ["string"],
                            "excludes": ["string"]
                        },
                        "branches": {
                            "includes": ["string"],
                            "excludes": ["string"]
                        },
                        "filePaths": {
                            "includes": ["string"],
                            "excludes": ["string"]
                        }
                    }
                ],
                "pullRequest": [
                    {
                        "events": ["OPEN|UPDATED|CLOSED"],
                        "branches": {
                            "includes": ["string"],
                            "excludes": ["string"]
                        },
                        "filePaths": {
                            "includes": ["string"],
                            "excludes": ["string"]
                        }
                    }
                ]
            }
        }
    ],
    "executionMode": "QUEUED|SUPERSEDED|PARALLEL"
}
```

**Output Schema:**
```json
{
    "pipeline": {
        "name": "string",
        "roleArn": "string",
        "artifactStore": { },
        "artifactStores": { },
        "stages": [],
        "version": "integer",
        "pipelineType": "V1|V2",
        "variables": [],
        "triggers": [],
        "executionMode": "QUEUED|SUPERSEDED|PARALLEL"
    },
    "tags": [
        {
            "key": "string",
            "value": "string"
        }
    ]
}
```

---

### 1.2 `delete-pipeline`

Deletes the specified pipeline.

**Synopsis:**
```bash
aws codepipeline delete-pipeline \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Pipeline name |

**Output Schema:**
```json
{}
```

---

### 1.3 `get-pipeline`

Returns the structure of a pipeline.

**Synopsis:**
```bash
aws codepipeline get-pipeline \
    --name <value> \
    [--version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Pipeline name |
| `--version` | No | integer | None | Pipeline version number |

**Output Schema:**
```json
{
    "pipeline": {
        "name": "string",
        "roleArn": "string",
        "artifactStore": { },
        "artifactStores": { },
        "stages": [
            {
                "name": "string",
                "blockers": [],
                "actions": [
                    {
                        "name": "string",
                        "actionTypeId": {
                            "category": "string",
                            "owner": "string",
                            "provider": "string",
                            "version": "string"
                        },
                        "runOrder": "integer",
                        "configuration": {},
                        "outputArtifacts": [],
                        "inputArtifacts": [],
                        "roleArn": "string",
                        "region": "string",
                        "namespace": "string",
                        "timeoutInMinutes": "integer"
                    }
                ]
            }
        ],
        "version": "integer",
        "pipelineType": "V1|V2",
        "variables": [],
        "triggers": [],
        "executionMode": "QUEUED|SUPERSEDED|PARALLEL"
    },
    "metadata": {
        "pipelineArn": "string",
        "created": "timestamp",
        "updated": "timestamp",
        "pollingDisabledAt": "timestamp"
    }
}
```

---

### 1.4 `list-pipelines`

Gets a summary of all pipelines in the account. **Paginated operation.**

**Synopsis:**
```bash
aws codepipeline list-pipelines \
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
    "pipelines": [
        {
            "name": "string",
            "version": "integer",
            "pipelineType": "V1|V2",
            "executionMode": "QUEUED|SUPERSEDED|PARALLEL",
            "created": "timestamp",
            "updated": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.5 `update-pipeline`

Updates a specified pipeline with edits or changes to its structure. Requires the full pipeline structure (use `get-pipeline` to retrieve, modify, then pass to `update-pipeline`).

**Synopsis:**
```bash
aws codepipeline update-pipeline \
    --pipeline <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline` | **Yes** | structure | -- | Updated pipeline structure (same format as `create-pipeline`) |

**Output Schema:**
Same as `create-pipeline` (without `tags`).

---

### 1.6 `start-pipeline-execution`

Starts the specified pipeline. Runs the most recent revision of every source action.

**Synopsis:**
```bash
aws codepipeline start-pipeline-execution \
    --name <value> \
    [--variables <value>] \
    [--client-request-token <value>] \
    [--source-revisions <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Pipeline name |
| `--variables` | No | list | None | Pipeline variables. Shorthand: `name=string,value=string ...` |
| `--client-request-token` | No | string | None | Idempotency token |
| `--source-revisions` | No | list | None | Source revisions to use. Shorthand: `actionName=string,revisionType=COMMIT_ID\|IMAGE_DIGEST\|S3_OBJECT_VERSION_ID\|S3_OBJECT_KEY,revisionValue=string ...` |

**Output Schema:**
```json
{
    "pipelineExecutionId": "string"
}
```

---

### 1.7 `stop-pipeline-execution`

Stops the specified pipeline execution.

**Synopsis:**
```bash
aws codepipeline stop-pipeline-execution \
    --pipeline-name <value> \
    --pipeline-execution-id <value> \
    [--abandon | --no-abandon] \
    [--reason <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-name` | **Yes** | string | -- | Pipeline name |
| `--pipeline-execution-id` | **Yes** | string | -- | Pipeline execution ID |
| `--abandon` | No | boolean | false | Abandon the execution (do not wait for in-progress actions) |
| `--reason` | No | string | None | Reason for stopping |

**Output Schema:**
```json
{
    "pipelineExecutionId": "string"
}
```

---

### 1.8 `get-pipeline-state`

Returns information about the state of a pipeline, including the stages and the latest execution in each stage.

**Synopsis:**
```bash
aws codepipeline get-pipeline-state \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Pipeline name |

**Output Schema:**
```json
{
    "pipelineName": "string",
    "pipelineVersion": "integer",
    "stageStates": [
        {
            "stageName": "string",
            "inboundExecution": {
                "pipelineExecutionId": "string",
                "status": "Cancelled|InProgress|Failed|Stopped|Stopping|Succeeded"
            },
            "inboundExecutions": [],
            "inboundTransitionState": {
                "enabled": true|false,
                "lastChangedBy": "string",
                "lastChangedAt": "timestamp",
                "disabledReason": "string"
            },
            "actionStates": [
                {
                    "actionName": "string",
                    "currentRevision": {
                        "revisionId": "string",
                        "revisionChangeId": "string",
                        "created": "timestamp"
                    },
                    "latestExecution": {
                        "actionExecutionId": "string",
                        "status": "InProgress|Abandoned|Succeeded|Failed",
                        "summary": "string",
                        "lastStatusChange": "timestamp",
                        "token": "string",
                        "lastUpdatedBy": "string",
                        "externalExecutionId": "string",
                        "externalExecutionUrl": "string",
                        "percentComplete": "integer",
                        "errorDetails": {
                            "code": "string",
                            "message": "string"
                        }
                    },
                    "entityUrl": "string",
                    "revisionUrl": "string"
                }
            ],
            "latestExecution": {
                "pipelineExecutionId": "string",
                "status": "Cancelled|InProgress|Failed|Stopped|Stopping|Succeeded"
            },
            "beforeEntryConditionState": { },
            "onSuccessConditionState": { },
            "onFailureConditionState": { }
        }
    ],
    "created": "timestamp",
    "updated": "timestamp"
}
```

---

### 1.9 `get-pipeline-execution`

Returns information about an execution of a pipeline.

**Synopsis:**
```bash
aws codepipeline get-pipeline-execution \
    --pipeline-name <value> \
    --pipeline-execution-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-name` | **Yes** | string | -- | Pipeline name |
| `--pipeline-execution-id` | **Yes** | string | -- | Pipeline execution ID |

**Output Schema:**
```json
{
    "pipelineExecution": {
        "pipelineName": "string",
        "pipelineVersion": "integer",
        "pipelineExecutionId": "string",
        "status": "Cancelled|InProgress|Stopped|Stopping|Succeeded|Superseded|Failed",
        "statusSummary": "string",
        "artifactRevisions": [
            {
                "name": "string",
                "revisionId": "string",
                "revisionChangeIdentifier": "string",
                "revisionSummary": "string",
                "created": "timestamp",
                "revisionUrl": "string"
            }
        ],
        "variables": [
            {
                "name": "string",
                "resolvedValue": "string"
            }
        ],
        "trigger": {
            "triggerType": "CreatePipeline|StartPipelineExecution|PollForSourceChanges|Webhook|CloudWatchEvent|PutActionRevision|WebhookV2|ManualRollback|AutomatedRollback",
            "triggerDetail": "string"
        },
        "executionMode": "QUEUED|SUPERSEDED|PARALLEL",
        "executionType": "STANDARD|ROLLBACK"
    }
}
```

---

### 1.10 `list-pipeline-executions`

Gets a summary of the most recent executions for a pipeline. **Paginated operation.**

**Synopsis:**
```bash
aws codepipeline list-pipeline-executions \
    --pipeline-name <value> \
    [--filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-name` | **Yes** | string | -- | Pipeline name |
| `--filter` | No | structure | None | Filter by execution mode. Shorthand: `succeededInStage={stageName=string}` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "pipelineExecutionSummaries": [
        {
            "pipelineExecutionId": "string",
            "status": "Cancelled|InProgress|Stopped|Stopping|Succeeded|Superseded|Failed",
            "statusSummary": "string",
            "startTime": "timestamp",
            "lastUpdateTime": "timestamp",
            "sourceRevisions": [
                {
                    "actionName": "string",
                    "revisionId": "string",
                    "revisionSummary": "string",
                    "revisionUrl": "string"
                }
            ],
            "trigger": {
                "triggerType": "string",
                "triggerDetail": "string"
            },
            "stopTrigger": {
                "reason": "string"
            },
            "executionMode": "QUEUED|SUPERSEDED|PARALLEL",
            "executionType": "STANDARD|ROLLBACK",
            "rollbackMetadata": {
                "rollbackTargetPipelineExecutionId": "string"
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 1.11 `retry-stage-execution`

Retries the latest failed actions in a stage.

**Synopsis:**
```bash
aws codepipeline retry-stage-execution \
    --pipeline-name <value> \
    --stage-name <value> \
    --pipeline-execution-id <value> \
    --retry-mode <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-name` | **Yes** | string | -- | Pipeline name |
| `--stage-name` | **Yes** | string | -- | Stage name to retry |
| `--pipeline-execution-id` | **Yes** | string | -- | Pipeline execution ID |
| `--retry-mode` | **Yes** | string | -- | Retry mode: `FAILED_ACTIONS`, `ALL_ACTIONS` |

**Output Schema:**
```json
{
    "pipelineExecutionId": "string"
}
```
