# Actions

Custom and third-party action management for CodePipeline.

---

### 3.1 `put-action-revision`

Provides information to CodePipeline about new revisions to a source.

**Synopsis:**
```bash
aws codepipeline put-action-revision \
    --pipeline-name <value> \
    --stage-name <value> \
    --action-name <value> \
    --action-revision <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-name` | **Yes** | string | -- | Pipeline name |
| `--stage-name` | **Yes** | string | -- | Stage name |
| `--action-name` | **Yes** | string | -- | Action name |
| `--action-revision` | **Yes** | structure | -- | Action revision details. Shorthand: `revisionId=string,revisionChangeId=string,created=timestamp` |

**Output Schema:**
```json
{
    "newRevision": true|false,
    "pipelineExecutionId": "string"
}
```

---

### 3.2 `poll-for-jobs`

Returns information about any jobs for CodePipeline to act on. Used by custom action workers.

**Synopsis:**
```bash
aws codepipeline poll-for-jobs \
    --action-type-id <value> \
    [--max-batch-size <value>] \
    [--query-param <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--action-type-id` | **Yes** | structure | -- | Action type ID. Shorthand: `category=Source\|Build\|Deploy\|Test\|Invoke\|Approval,owner=AWS\|ThirdParty\|Custom,provider=string,version=string` |
| `--max-batch-size` | No | integer | None | Maximum number of jobs to return |
| `--query-param` | No | map | None | Map of properties for the job worker to match |

**Output Schema:**
```json
{
    "jobs": [
        {
            "id": "string",
            "data": {
                "actionTypeId": { },
                "actionConfiguration": {
                    "configuration": {}
                },
                "pipelineContext": {
                    "pipelineName": "string",
                    "stage": {
                        "name": "string"
                    },
                    "action": {
                        "name": "string",
                        "actionExecutionId": "string"
                    },
                    "pipelineArn": "string",
                    "pipelineExecutionId": "string"
                },
                "inputArtifacts": [
                    {
                        "name": "string",
                        "revision": "string",
                        "location": {
                            "type": "S3",
                            "s3Location": {
                                "bucketName": "string",
                                "objectKey": "string"
                            }
                        }
                    }
                ],
                "outputArtifacts": [],
                "artifactCredentials": {
                    "accessKeyId": "string",
                    "secretAccessKey": "string",
                    "sessionToken": "string"
                },
                "continuationToken": "string",
                "encryptionKey": {
                    "id": "string",
                    "type": "KMS"
                }
            },
            "nonce": "string",
            "accountId": "string"
        }
    ]
}
```

---

### 3.3 `acknowledge-job`

Returns information about a specified job and whether that job has been received by the job worker. Used by custom action workers.

**Synopsis:**
```bash
aws codepipeline acknowledge-job \
    --job-id <value> \
    --nonce <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID |
| `--nonce` | **Yes** | string | -- | System-generated nonce value |

**Output Schema:**
```json
{
    "status": "Created|Queued|Dispatched|InProgress|TimedOut|Succeeded|Failed"
}
```

---

### 3.4 `put-job-success-result`

Represents the success of a job as returned to the pipeline by a job worker. Used by custom action workers.

**Synopsis:**
```bash
aws codepipeline put-job-success-result \
    --job-id <value> \
    [--current-revision <value>] \
    [--continuation-token <value>] \
    [--execution-details <value>] \
    [--output-variables <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID |
| `--current-revision` | No | structure | None | Current revision. Shorthand: `revision=string,changeIdentifier=string,created=timestamp` |
| `--continuation-token` | No | string | None | Token for next poll (for async actions) |
| `--execution-details` | No | structure | None | Execution details. Shorthand: `summary=string,externalExecutionId=string,percentComplete=integer` |
| `--output-variables` | No | map | None | Key-value pairs to pass to subsequent actions |

**Output Schema:**
```json
{}
```

---

### 3.5 `put-job-failure-result`

Represents the failure of a job as returned to the pipeline by a job worker. Used by custom action workers.

**Synopsis:**
```bash
aws codepipeline put-job-failure-result \
    --job-id <value> \
    --failure-details <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID |
| `--failure-details` | **Yes** | structure | -- | Failure details. Shorthand: `type=JobFailed\|ConfigurationError\|PermissionError\|RevisionOutOfSync\|RevisionUnavailable\|SystemUnavailable,message=string,externalExecutionId=string` |

**Output Schema:**
```json
{}
```

---

### 3.6 `poll-for-third-party-jobs`

Determines whether there are any third-party jobs for a job worker to act on.

**Synopsis:**
```bash
aws codepipeline poll-for-third-party-jobs \
    --action-type-id <value> \
    [--max-batch-size <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--action-type-id` | **Yes** | structure | -- | Action type ID. Shorthand: `category=string,owner=string,provider=string,version=string` |
| `--max-batch-size` | No | integer | None | Maximum number of jobs to return |

**Output Schema:**
```json
{
    "jobs": [
        {
            "clientId": "string",
            "jobId": "string"
        }
    ]
}
```

---

### 3.7 `acknowledge-third-party-job`

Confirms a job worker has received the specified third-party job.

**Synopsis:**
```bash
aws codepipeline acknowledge-third-party-job \
    --job-id <value> \
    --nonce <value> \
    --client-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID |
| `--nonce` | **Yes** | string | -- | System-generated nonce |
| `--client-token` | **Yes** | string | -- | Client token from poll-for-third-party-jobs |

**Output Schema:**
```json
{
    "status": "Created|Queued|Dispatched|InProgress|TimedOut|Succeeded|Failed"
}
```

---

### 3.8 `put-third-party-job-success-result`

Represents the success of a third-party job as returned to the pipeline.

**Synopsis:**
```bash
aws codepipeline put-third-party-job-success-result \
    --job-id <value> \
    --client-token <value> \
    [--current-revision <value>] \
    [--continuation-token <value>] \
    [--execution-details <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID |
| `--client-token` | **Yes** | string | -- | Client token |
| `--current-revision` | No | structure | None | Current revision |
| `--continuation-token` | No | string | None | Token for next poll |
| `--execution-details` | No | structure | None | Execution details |

**Output Schema:**
```json
{}
```

---

### 3.9 `put-third-party-job-failure-result`

Represents the failure of a third-party job as returned to the pipeline.

**Synopsis:**
```bash
aws codepipeline put-third-party-job-failure-result \
    --job-id <value> \
    --client-token <value> \
    --failure-details <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID |
| `--client-token` | **Yes** | string | -- | Client token |
| `--failure-details` | **Yes** | structure | -- | Failure details |

**Output Schema:**
```json
{}
```
