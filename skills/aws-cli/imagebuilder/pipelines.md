# Pipelines

### 1.1 `create-image-pipeline`

Creates a new image pipeline. Image pipelines automate the creation of images.

**Synopsis:**
```bash
aws imagebuilder create-image-pipeline \
    --name <value> \
    --infrastructure-configuration-arn <value> \
    [--description <value>] \
    [--image-recipe-arn <value>] \
    [--container-recipe-arn <value>] \
    [--distribution-configuration-arn <value>] \
    [--image-tests-configuration <value>] \
    [--enhanced-image-metadata-enabled | --no-enhanced-image-metadata-enabled] \
    [--schedule <value>] \
    [--status <value>] \
    [--image-scanning-configuration <value>] \
    [--workflows <value>] \
    [--execution-role <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the pipeline |
| `--infrastructure-configuration-arn` | **Yes** | string | -- | ARN of the infrastructure configuration |
| `--description` | No | string | -- | Description of the pipeline |
| `--image-recipe-arn` | No | string | -- | ARN of the image recipe (mutually exclusive with `--container-recipe-arn`) |
| `--container-recipe-arn` | No | string | -- | ARN of the container recipe |
| `--distribution-configuration-arn` | No | string | -- | ARN of the distribution configuration |
| `--image-tests-configuration` | No | structure | None | Image test configuration. Shorthand: `imageTestsEnabled=boolean,timeoutMinutes=integer` |
| `--enhanced-image-metadata-enabled` | No | boolean | true | Enable enhanced image metadata collection |
| `--schedule` | No | structure | None | Schedule for pipeline. Shorthand: `scheduleExpression=string,timezone=string,pipelineExecutionStartCondition=string` |
| `--status` | No | string | `ENABLED` | Pipeline status: `ENABLED` or `DISABLED` |
| `--image-scanning-configuration` | No | structure | None | Image scanning configuration |
| `--workflows` | No | list | None | Workflow configurations for the pipeline |
| `--execution-role` | No | string | -- | Execution role ARN for the pipeline |
| `--tags` | No | map | None | Tags as key-value pairs |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Output Schema:**
```json
{
    "requestId": "string",
    "clientToken": "string",
    "imagePipelineArn": "string"
}
```

---

### 1.2 `get-image-pipeline`

Gets an image pipeline.

**Synopsis:**
```bash
aws imagebuilder get-image-pipeline \
    --image-pipeline-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--image-pipeline-arn` | **Yes** | string | -- | ARN of the image pipeline |

**Output Schema:**
```json
{
    "requestId": "string",
    "imagePipeline": {
        "arn": "string",
        "name": "string",
        "description": "string",
        "platform": "Windows|Linux",
        "enhancedImageMetadataEnabled": "boolean",
        "imageRecipeArn": "string",
        "containerRecipeArn": "string",
        "infrastructureConfigurationArn": "string",
        "distributionConfigurationArn": "string",
        "imageTestsConfiguration": {
            "imageTestsEnabled": "boolean",
            "timeoutMinutes": "integer"
        },
        "schedule": {
            "scheduleExpression": "string",
            "timezone": "string",
            "pipelineExecutionStartCondition": "EXPRESSION_MATCH_ONLY|EXPRESSION_MATCH_AND_DEPENDENCY_UPDATES_AVAILABLE"
        },
        "status": "DISABLED|ENABLED",
        "dateCreated": "string",
        "dateUpdated": "string",
        "dateLastRun": "string",
        "dateNextRun": "string",
        "tags": {
            "string": "string"
        },
        "imageScanningConfiguration": {
            "imageScanningEnabled": "boolean",
            "ecrConfiguration": {
                "repositoryName": "string",
                "containerTags": ["string"]
            }
        },
        "executionRole": "string",
        "workflows": [
            {
                "workflowArn": "string",
                "parameters": [
                    {
                        "name": "string",
                        "value": ["string"]
                    }
                ],
                "parallelGroup": "string",
                "onFailure": "CONTINUE|ABORT"
            }
        ]
    }
}
```

---

### 1.3 `list-image-pipelines`

Lists image pipelines. **Paginated operation.**

**Synopsis:**
```bash
aws imagebuilder list-image-pipelines \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | None | Filter results. Shorthand: `name=string,values=string,string ...` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "requestId": "string",
    "imagePipelineList": [
        {
            "arn": "string",
            "name": "string",
            "description": "string",
            "platform": "Windows|Linux",
            "status": "DISABLED|ENABLED",
            "dateCreated": "string",
            "dateUpdated": "string",
            "dateLastRun": "string",
            "dateNextRun": "string",
            "tags": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 1.4 `update-image-pipeline`

Updates an existing image pipeline.

**Synopsis:**
```bash
aws imagebuilder update-image-pipeline \
    --image-pipeline-arn <value> \
    --infrastructure-configuration-arn <value> \
    [--description <value>] \
    [--image-recipe-arn <value>] \
    [--container-recipe-arn <value>] \
    [--distribution-configuration-arn <value>] \
    [--image-tests-configuration <value>] \
    [--enhanced-image-metadata-enabled | --no-enhanced-image-metadata-enabled] \
    [--schedule <value>] \
    [--status <value>] \
    [--image-scanning-configuration <value>] \
    [--workflows <value>] \
    [--execution-role <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--image-pipeline-arn` | **Yes** | string | -- | ARN of the image pipeline to update |
| `--infrastructure-configuration-arn` | **Yes** | string | -- | ARN of the infrastructure configuration |
| `--description` | No | string | -- | Updated description |
| `--image-recipe-arn` | No | string | -- | ARN of the image recipe |
| `--container-recipe-arn` | No | string | -- | ARN of the container recipe |
| `--distribution-configuration-arn` | No | string | -- | ARN of the distribution configuration |
| `--image-tests-configuration` | No | structure | None | Image test configuration |
| `--enhanced-image-metadata-enabled` | No | boolean | -- | Enable enhanced image metadata |
| `--schedule` | No | structure | None | Updated schedule |
| `--status` | No | string | -- | Pipeline status: `ENABLED` or `DISABLED` |
| `--image-scanning-configuration` | No | structure | None | Image scanning configuration |
| `--workflows` | No | list | None | Workflow configurations |
| `--execution-role` | No | string | -- | Execution role ARN |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Output Schema:**
```json
{
    "requestId": "string",
    "clientToken": "string",
    "imagePipelineArn": "string"
}
```

---

### 1.5 `delete-image-pipeline`

Deletes an image pipeline.

**Synopsis:**
```bash
aws imagebuilder delete-image-pipeline \
    --image-pipeline-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--image-pipeline-arn` | **Yes** | string | -- | ARN of the image pipeline to delete |

**Output Schema:**
```json
{
    "requestId": "string",
    "imagePipelineArn": "string"
}
```

---

### 1.6 `start-image-pipeline-execution`

Manually triggers a pipeline execution.

**Synopsis:**
```bash
aws imagebuilder start-image-pipeline-execution \
    --image-pipeline-arn <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--image-pipeline-arn` | **Yes** | string | -- | ARN of the image pipeline to execute |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Output Schema:**
```json
{
    "requestId": "string",
    "clientToken": "string",
    "imageBuildVersionArn": "string"
}
```

---

### 1.7 `list-image-pipeline-images`

Lists images built by the specified pipeline. **Paginated operation.**

**Synopsis:**
```bash
aws imagebuilder list-image-pipeline-images \
    --image-pipeline-arn <value> \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--image-pipeline-arn` | **Yes** | string | -- | ARN of the image pipeline |
| `--filters` | No | list | None | Filter results |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "requestId": "string",
    "imageSummaryList": [
        {
            "arn": "string",
            "name": "string",
            "type": "AMI|DOCKER",
            "version": "string",
            "platform": "Windows|Linux",
            "state": {
                "status": "PENDING|CREATING|BUILDING|TESTING|DISTRIBUTING|INTEGRATING|AVAILABLE|CANCELLED|FAILED|DEPRECATED|DELETED|DISABLED",
                "reason": "string"
            },
            "owner": "string",
            "dateCreated": "string",
            "outputResources": {
                "amis": [
                    {
                        "region": "string",
                        "image": "string",
                        "name": "string",
                        "description": "string",
                        "state": {},
                        "accountId": "string"
                    }
                ],
                "containers": [
                    {
                        "region": "string",
                        "imageUris": ["string"]
                    }
                ]
            },
            "tags": {},
            "buildType": "USER_INITIATED|SCHEDULED|IMPORT"
        }
    ],
    "nextToken": "string"
}
```
