# Components

### 1.1 `create-component-version`

Creates a new version of a component from a recipe file or a Lambda function.

**Synopsis:**
```bash
aws greengrassv2 create-component-version \
    [--inline-recipe <value>] \
    [--lambda-function <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--inline-recipe` | Conditional | blob | -- | Component recipe (fileb:// for file). One of inline-recipe or lambda-function required |
| `--lambda-function` | Conditional | structure | -- | Lambda function parameters. One of inline-recipe or lambda-function required |
| `--tags` | No | map | None | Tags (max 200) |
| `--client-token` | No | string | Auto | Idempotency token (1-64 chars) |

**Lambda Function structure:**
```json
{
    "lambdaArn": "arn:aws:lambda:us-east-1:123456789012:function:MyFunction:1",
    "componentName": "com.example.MyFunction",
    "componentVersion": "1.0.0",
    "componentPlatforms": [
        {
            "name": "Linux",
            "attributes": {"os": "linux"}
        }
    ],
    "componentDependencies": {
        "com.example.Dependency": {
            "versionRequirement": ">=1.0.0",
            "dependencyType": "HARD"
        }
    },
    "componentLambdaParameters": {
        "eventSources": [
            {"topic": "hello/world", "type": "IOT_CORE"}
        ],
        "maxQueueSize": 100,
        "maxInstancesCount": 1,
        "maxIdleTimeInSeconds": 60,
        "timeoutInSeconds": 3,
        "statusTimeoutInSeconds": 60,
        "pinned": true,
        "inputPayloadEncodingType": "json",
        "environmentVariables": {"KEY": "value"},
        "linuxProcessParams": {
            "isolationMode": "GreengrassContainer",
            "containerParams": {
                "memorySizeInKB": 16384,
                "mountROSysfs": false,
                "volumes": [],
                "devices": []
            }
        }
    }
}
```

**Output Schema:**
```json
{
    "arn": "string",
    "componentName": "string",
    "componentVersion": "string",
    "creationTimestamp": "timestamp",
    "status": {
        "componentState": "REQUESTED|INITIATED|DEPLOYABLE|FAILED|DEPRECATED",
        "message": "string",
        "errors": {"string": "string"},
        "vendorGuidance": "ACTIVE|DISCONTINUED|DELETED",
        "vendorGuidanceMessage": "string"
    }
}
```

---

### 1.2 `describe-component`

Retrieves metadata about a component version.

**Synopsis:**
```bash
aws greengrassv2 describe-component \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the component version |

**Output Schema:**
```json
{
    "arn": "string",
    "componentName": "string",
    "componentVersion": "string",
    "creationTimestamp": "timestamp",
    "publisher": "string",
    "description": "string",
    "status": {
        "componentState": "REQUESTED|INITIATED|DEPLOYABLE|FAILED|DEPRECATED",
        "message": "string",
        "errors": {"string": "string"},
        "vendorGuidance": "ACTIVE|DISCONTINUED|DELETED",
        "vendorGuidanceMessage": "string"
    },
    "platforms": [
        {
            "name": "string",
            "attributes": {"string": "string"}
        }
    ],
    "tags": {"string": "string"}
}
```

---

### 1.3 `get-component`

Gets the recipe for a component version.

**Synopsis:**
```bash
aws greengrassv2 get-component \
    --arn <value> \
    [--recipe-output-format <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the component version |
| `--recipe-output-format` | No | string | None | `JSON` or `YAML` |

**Output Schema:**
```json
{
    "recipeOutputFormat": "JSON|YAML",
    "recipe": "blob",
    "tags": {"string": "string"}
}
```

> **Tip:** Decode the recipe with: `--query recipe --output text | base64 --decode`

---

### 1.4 `get-component-version-artifact`

Gets a presigned URL to download an artifact for a component version.

**Synopsis:**
```bash
aws greengrassv2 get-component-version-artifact \
    --arn <value> \
    --artifact-name <value> \
    [--s3-endpoint-type <value>] \
    [--iot-endpoint-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the component version |
| `--artifact-name` | **Yes** | string | -- | Name of the artifact (1-256 chars) |
| `--s3-endpoint-type` | No | string | None | `REGIONAL` or `GLOBAL` |
| `--iot-endpoint-type` | No | string | None | `fips` or `standard` |

**Output Schema:**
```json
{
    "preSignedUrl": "string"
}
```

---

### 1.5 `list-components`

Lists components. **Paginated operation.**

**Synopsis:**
```bash
aws greengrassv2 list-components \
    [--scope <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scope` | No | string | None | `PRIVATE` or `PUBLIC` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "components": [
        {
            "arn": "string",
            "componentName": "string",
            "latestVersion": {
                "arn": "string",
                "componentVersion": "string",
                "creationTimestamp": "timestamp",
                "description": "string",
                "publisher": "string",
                "platforms": [
                    {"name": "string", "attributes": {"string": "string"}}
                ]
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 1.6 `list-component-versions`

Lists versions of a component. **Paginated operation.**

**Synopsis:**
```bash
aws greengrassv2 list-component-versions \
    --arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the component |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "componentVersions": [
        {
            "componentName": "string",
            "componentVersion": "string",
            "arn": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.7 `delete-component`

Deletes a component version.

**Synopsis:**
```bash
aws greengrassv2 delete-component \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the component version to delete |

**Output:** None

---

### 1.8 `resolve-component-candidates`

Identifies components that meet specified requirements for a deployment. Receives a list of component candidates and returns resolved component versions.

**Synopsis:**
```bash
aws greengrassv2 resolve-component-candidates \
    [--platform <value>] \
    [--component-candidates <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--platform` | No | structure | None | Platform to resolve for |
| `--component-candidates` | No | list | None | Components with version requirements |

**Platform structure:**
```json
{
    "name": "string",
    "attributes": {
        "os": "linux",
        "architecture": "amd64"
    }
}
```

**Component candidates:**
```json
[
    {
        "componentName": "string",
        "componentVersion": "string",
        "versionRequirements": {
            "dependencyName": ">=1.0.0 <2.0.0"
        }
    }
]
```

**Output Schema:**
```json
{
    "resolvedComponentVersions": [
        {
            "arn": "string",
            "componentName": "string",
            "componentVersion": "string",
            "recipe": "blob",
            "vendorGuidance": "ACTIVE|DISCONTINUED|DELETED",
            "message": "string"
        }
    ]
}
```
