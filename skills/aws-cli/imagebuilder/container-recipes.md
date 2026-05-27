# Container Recipes

### 3.1 `create-container-recipe`

Creates a new container recipe for building container images.

**Synopsis:**
```bash
aws imagebuilder create-container-recipe \
    --container-type <value> \
    --name <value> \
    --semantic-version <value> \
    --components <value> \
    --parent-image <value> \
    --target-repository <value> \
    [--description <value>] \
    [--instance-configuration <value>] \
    [--dockerfile-template-data <value>] \
    [--dockerfile-template-uri <value>] \
    [--platform-override <value>] \
    [--image-os-version-override <value>] \
    [--working-directory <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-type` | **Yes** | string | -- | Container type: `DOCKER` |
| `--name` | **Yes** | string | -- | Name of the container recipe |
| `--semantic-version` | **Yes** | string | -- | Semantic version (e.g., `1.0.0`) |
| `--components` | **Yes** | list | -- | Components to include |
| `--parent-image` | **Yes** | string | -- | Base image for the container recipe |
| `--target-repository` | **Yes** | structure | -- | Target ECR repository. Shorthand: `service=ECR,repositoryName=string` |
| `--description` | No | string | -- | Description |
| `--instance-configuration` | No | structure | None | Instance configuration for build |
| `--dockerfile-template-data` | No | string | -- | Inline Dockerfile template |
| `--dockerfile-template-uri` | No | string | -- | S3 URI of Dockerfile template |
| `--platform-override` | No | string | -- | Override platform: `Windows` or `Linux` |
| `--image-os-version-override` | No | string | -- | Override OS version |
| `--working-directory` | No | string | -- | Working directory |
| `--tags` | No | map | None | Tags |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Output Schema:**
```json
{
    "requestId": "string",
    "clientToken": "string",
    "containerRecipeArn": "string"
}
```

---

### 3.2 `get-container-recipe`

Gets a container recipe.

**Synopsis:**
```bash
aws imagebuilder get-container-recipe \
    --container-recipe-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-recipe-arn` | **Yes** | string | -- | ARN of the container recipe |

**Output Schema:**
```json
{
    "requestId": "string",
    "containerRecipe": {
        "arn": "string",
        "containerType": "DOCKER",
        "name": "string",
        "description": "string",
        "platform": "Windows|Linux",
        "owner": "string",
        "version": "string",
        "components": [
            {
                "componentArn": "string",
                "parameters": []
            }
        ],
        "instanceConfiguration": {
            "image": "string",
            "blockDeviceMappings": []
        },
        "dockerfileTemplateData": "string",
        "kmsKeyId": "string",
        "encrypted": "boolean",
        "parentImage": "string",
        "dateCreated": "string",
        "tags": {},
        "workingDirectory": "string",
        "targetRepository": {
            "service": "ECR",
            "repositoryName": "string"
        }
    }
}
```

---

### 3.3 `list-container-recipes`

Lists container recipes. **Paginated operation.**

**Synopsis:**
```bash
aws imagebuilder list-container-recipes \
    [--owner <value>] \
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
| `--owner` | No | string | `Self` | Owner filter: `Self`, `Shared`, `Amazon`, `ThirdParty` |
| `--filters` | No | list | None | Filters |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "requestId": "string",
    "containerRecipeSummaryList": [
        {
            "arn": "string",
            "containerType": "DOCKER",
            "name": "string",
            "platform": "Windows|Linux",
            "owner": "string",
            "parentImage": "string",
            "dateCreated": "string",
            "tags": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 3.4 `get-container-recipe-policy`

Gets the policy for a container recipe.

**Synopsis:**
```bash
aws imagebuilder get-container-recipe-policy \
    --container-recipe-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-recipe-arn` | **Yes** | string | -- | ARN of the container recipe |

**Output Schema:**
```json
{
    "requestId": "string",
    "policy": "string"
}
```

---

### 3.5 `put-container-recipe-policy`

Applies a policy to a container recipe for cross-account sharing.

**Synopsis:**
```bash
aws imagebuilder put-container-recipe-policy \
    --container-recipe-arn <value> \
    --policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-recipe-arn` | **Yes** | string | -- | ARN of the container recipe |
| `--policy` | **Yes** | string | -- | Resource policy JSON document |

**Output Schema:**
```json
{
    "requestId": "string",
    "containerRecipeArn": "string"
}
```

---

### 3.6 `delete-container-recipe`

Deletes a container recipe.

**Synopsis:**
```bash
aws imagebuilder delete-container-recipe \
    --container-recipe-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-recipe-arn` | **Yes** | string | -- | ARN of the container recipe to delete |

**Output Schema:**
```json
{
    "requestId": "string",
    "containerRecipeArn": "string"
}
```
