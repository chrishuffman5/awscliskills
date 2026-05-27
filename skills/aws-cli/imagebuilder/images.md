# Images

### 5.1 `create-image`

Creates a new image. This operation starts the image build process.

**Synopsis:**
```bash
aws imagebuilder create-image \
    --infrastructure-configuration-arn <value> \
    [--image-recipe-arn <value>] \
    [--container-recipe-arn <value>] \
    [--distribution-configuration-arn <value>] \
    [--image-tests-configuration <value>] \
    [--enhanced-image-metadata-enabled | --no-enhanced-image-metadata-enabled] \
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
| `--infrastructure-configuration-arn` | **Yes** | string | -- | ARN of the infrastructure configuration |
| `--image-recipe-arn` | No | string | -- | ARN of the image recipe (mutually exclusive with container recipe) |
| `--container-recipe-arn` | No | string | -- | ARN of the container recipe |
| `--distribution-configuration-arn` | No | string | -- | ARN of the distribution configuration |
| `--image-tests-configuration` | No | structure | None | Image test configuration |
| `--enhanced-image-metadata-enabled` | No | boolean | true | Enable enhanced metadata |
| `--image-scanning-configuration` | No | structure | None | Image scanning configuration |
| `--workflows` | No | list | None | Workflow configurations |
| `--execution-role` | No | string | -- | Execution role ARN |
| `--tags` | No | map | None | Tags |
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

### 5.2 `get-image`

Gets an image.

**Synopsis:**
```bash
aws imagebuilder get-image \
    --image-build-version-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--image-build-version-arn` | **Yes** | string | -- | ARN of the image build version |

**Output Schema:**
```json
{
    "requestId": "string",
    "image": {
        "arn": "string",
        "type": "AMI|DOCKER",
        "name": "string",
        "version": "string",
        "platform": "Windows|Linux",
        "enhancedImageMetadataEnabled": "boolean",
        "osVersion": "string",
        "state": {
            "status": "PENDING|CREATING|BUILDING|TESTING|DISTRIBUTING|INTEGRATING|AVAILABLE|CANCELLED|FAILED|DEPRECATED|DELETED|DISABLED",
            "reason": "string"
        },
        "imageRecipe": {},
        "containerRecipe": {},
        "sourcePipelineName": "string",
        "sourcePipelineArn": "string",
        "infrastructureConfiguration": {},
        "distributionConfiguration": {},
        "imageTestsConfiguration": {
            "imageTestsEnabled": "boolean",
            "timeoutMinutes": "integer"
        },
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
        "buildType": "USER_INITIATED|SCHEDULED|IMPORT",
        "imageSource": "AMAZON_MANAGED|AWS_MARKETPLACE|IMPORTED|CUSTOM",
        "scanState": {
            "status": "PENDING|SCANNING|COLLECTING|COMPLETED|ABANDONED|FAILED|TIMED_OUT",
            "reason": "string"
        },
        "imageScanningConfiguration": {},
        "executionRole": "string",
        "workflows": []
    }
}
```

---

### 5.3 `list-images`

Lists images. **Paginated operation.**

**Synopsis:**
```bash
aws imagebuilder list-images \
    [--owner <value>] \
    [--filters <value>] \
    [--by-name | --no-by-name] \
    [--include-deprecated | --no-include-deprecated] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--owner` | No | string | `Self` | Owner filter: `Self`, `Shared`, `Amazon`, `ThirdParty` |
| `--filters` | No | list | None | Filters. Names: `name`, `osVersion`, `platform` |
| `--by-name` | No | boolean | false | Return only latest version |
| `--include-deprecated` | No | boolean | false | Include deprecated images |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "requestId": "string",
    "imageVersionList": [
        {
            "arn": "string",
            "name": "string",
            "type": "AMI|DOCKER",
            "version": "string",
            "platform": "Windows|Linux",
            "osVersion": "string",
            "owner": "string",
            "dateCreated": "string",
            "buildType": "USER_INITIATED|SCHEDULED|IMPORT",
            "imageSource": "AMAZON_MANAGED|AWS_MARKETPLACE|IMPORTED|CUSTOM"
        }
    ],
    "nextToken": "string"
}
```

---

### 5.4 `list-image-build-versions`

Lists image build versions. **Paginated operation.**

**Synopsis:**
```bash
aws imagebuilder list-image-build-versions \
    --image-version-arn <value> \
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
| `--image-version-arn` | **Yes** | string | -- | ARN of the image version |
| `--filters` | No | list | None | Filters |
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
            "osVersion": "string",
            "state": {
                "status": "string",
                "reason": "string"
            },
            "owner": "string",
            "dateCreated": "string",
            "outputResources": {},
            "tags": {},
            "buildType": "string",
            "imageSource": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 5.5 `get-image-policy`

Gets the policy for an image.

**Synopsis:**
```bash
aws imagebuilder get-image-policy \
    --image-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--image-arn` | **Yes** | string | -- | ARN of the image |

**Output Schema:**
```json
{
    "requestId": "string",
    "policy": "string"
}
```

---

### 5.6 `put-image-policy`

Applies a policy to an image for cross-account sharing.

**Synopsis:**
```bash
aws imagebuilder put-image-policy \
    --image-arn <value> \
    --policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--image-arn` | **Yes** | string | -- | ARN of the image |
| `--policy` | **Yes** | string | -- | Resource policy JSON document |

**Output Schema:**
```json
{
    "requestId": "string",
    "imageArn": "string"
}
```

---

### 5.7 `delete-image`

Deletes an image.

**Synopsis:**
```bash
aws imagebuilder delete-image \
    --image-build-version-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--image-build-version-arn` | **Yes** | string | -- | ARN of the image build version to delete |

**Output Schema:**
```json
{
    "requestId": "string",
    "imageBuildVersionArn": "string"
}
```

---

### 5.8 `cancel-image-creation`

Cancels an in-progress image creation.

**Synopsis:**
```bash
aws imagebuilder cancel-image-creation \
    --image-build-version-arn <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--image-build-version-arn` | **Yes** | string | -- | ARN of the image build version to cancel |
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

### 5.9 `import-vm-image`

Imports a VM image as the basis for an Image Builder image.

**Synopsis:**
```bash
aws imagebuilder import-vm-image \
    --name <value> \
    --semantic-version <value> \
    --platform <value> \
    --vm-import-task-id <value> \
    [--description <value>] \
    [--os-version <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name for the imported image |
| `--semantic-version` | **Yes** | string | -- | Semantic version |
| `--platform` | **Yes** | string | -- | Platform: `Windows` or `Linux` |
| `--vm-import-task-id` | **Yes** | string | -- | ImportImage task ID from EC2 |
| `--description` | No | string | -- | Description |
| `--os-version` | No | string | -- | OS version |
| `--tags` | No | map | None | Tags |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Output Schema:**
```json
{
    "requestId": "string",
    "clientToken": "string",
    "imageArn": "string"
}
```
