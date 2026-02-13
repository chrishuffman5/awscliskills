# Image Recipes

### 2.1 `create-image-recipe`

Creates a new image recipe. An image recipe defines how images are configured, tested, and assessed.

**Synopsis:**
```bash
aws imagebuilder create-image-recipe \
    --name <value> \
    --semantic-version <value> \
    --components <value> \
    --parent-image <value> \
    [--description <value>] \
    [--block-device-mappings <value>] \
    [--additional-instance-configuration <value>] \
    [--working-directory <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the recipe |
| `--semantic-version` | **Yes** | string | -- | Semantic version (e.g., `1.0.0`) |
| `--components` | **Yes** | list | -- | Components to include. Shorthand: `componentArn=string,parameters=[{name=string,value=[string]}] ...` |
| `--parent-image` | **Yes** | string | -- | Base image ARN or AMI ID |
| `--description` | No | string | -- | Description of the recipe |
| `--block-device-mappings` | No | list | None | Block device mappings for the image |
| `--additional-instance-configuration` | No | structure | None | Additional instance configuration (user data, Systems Manager agent) |
| `--working-directory` | No | string | -- | Working directory for build and test workflows |
| `--tags` | No | map | None | Tags as key-value pairs |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Block Device Mapping Structure:**
```json
{
    "deviceName": "string",
    "ebs": {
        "encrypted": "boolean",
        "deleteOnTermination": "boolean",
        "iops": "integer",
        "kmsKeyId": "string",
        "snapshotId": "string",
        "volumeSize": "integer",
        "volumeType": "standard|io1|io2|gp2|gp3|sc1|st1",
        "throughput": "integer"
    },
    "virtualName": "string",
    "noDevice": "string"
}
```

**Output Schema:**
```json
{
    "requestId": "string",
    "clientToken": "string",
    "imageRecipeArn": "string"
}
```

---

### 2.2 `get-image-recipe`

Gets an image recipe.

**Synopsis:**
```bash
aws imagebuilder get-image-recipe \
    --image-recipe-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--image-recipe-arn` | **Yes** | string | -- | ARN of the image recipe |

**Output Schema:**
```json
{
    "requestId": "string",
    "imageRecipe": {
        "arn": "string",
        "type": "AMI|DOCKER",
        "name": "string",
        "description": "string",
        "platform": "Windows|Linux",
        "owner": "string",
        "version": "string",
        "components": [
            {
                "componentArn": "string",
                "parameters": [
                    {
                        "name": "string",
                        "value": ["string"]
                    }
                ]
            }
        ],
        "parentImage": "string",
        "blockDeviceMappings": [],
        "dateCreated": "string",
        "tags": {},
        "workingDirectory": "string",
        "additionalInstanceConfiguration": {
            "systemsManagerAgent": {
                "uninstallAfterBuild": "boolean"
            },
            "userDataOverride": "string"
        }
    }
}
```

---

### 2.3 `list-image-recipes`

Lists image recipes. **Paginated operation.**

**Synopsis:**
```bash
aws imagebuilder list-image-recipes \
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
| `--filters` | No | list | None | Filters. Use `name=string,values=string,string` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "requestId": "string",
    "imageRecipeSummaryList": [
        {
            "arn": "string",
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

### 2.4 `get-image-recipe-policy`

Gets the policy for an image recipe.

**Synopsis:**
```bash
aws imagebuilder get-image-recipe-policy \
    --image-recipe-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--image-recipe-arn` | **Yes** | string | -- | ARN of the image recipe |

**Output Schema:**
```json
{
    "requestId": "string",
    "policy": "string"
}
```

---

### 2.5 `put-image-recipe-policy`

Applies a policy to an image recipe for cross-account sharing.

**Synopsis:**
```bash
aws imagebuilder put-image-recipe-policy \
    --image-recipe-arn <value> \
    --policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--image-recipe-arn` | **Yes** | string | -- | ARN of the image recipe |
| `--policy` | **Yes** | string | -- | Resource policy JSON document |

**Output Schema:**
```json
{
    "requestId": "string",
    "imageRecipeArn": "string"
}
```

---

### 2.6 `delete-image-recipe`

Deletes an image recipe.

**Synopsis:**
```bash
aws imagebuilder delete-image-recipe \
    --image-recipe-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--image-recipe-arn` | **Yes** | string | -- | ARN of the image recipe to delete |

**Output Schema:**
```json
{
    "requestId": "string",
    "imageRecipeArn": "string"
}
```
