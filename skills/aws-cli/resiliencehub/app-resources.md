# App Resources

### 3.1 `create-app-version-resource`

Adds a resource to the draft version of a Resilience Hub application.

**Synopsis:**
```bash
aws resiliencehub create-app-version-resource \
    --app-arn <value> \
    --app-components <value> \
    --logical-resource-id <value> \
    --physical-resource-id <value> \
    --resource-type <value> \
    [--resource-name <value>] \
    [--additional-info <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--app-components` | **Yes** | list(string) | -- | App component names |
| `--logical-resource-id` | **Yes** | structure | -- | Logical resource ID. Shorthand: `identifier=string,logicalStackName=string,resourceGroupName=string,terraformSourceName=string,eksSourceName=string` |
| `--physical-resource-id` | **Yes** | string | -- | Physical resource identifier |
| `--resource-type` | **Yes** | string | -- | AWS resource type (e.g., `AWS::EC2::Instance`) |
| `--resource-name` | No | string | None | Resource name (1-255 chars) |
| `--additional-info` | No | map | None | Additional info |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "appArn": "string",
    "appVersion": "string",
    "physicalResource": {
        "physicalResourceId": {
            "identifier": "string",
            "type": "Arn|Native",
            "awsRegion": "string",
            "awsAccountId": "string"
        },
        "logicalResourceId": {},
        "resourceType": "string",
        "resourceName": "string",
        "appComponents": [],
        "additionalInfo": {},
        "excluded": "boolean",
        "sourceType": "string",
        "parentResourceName": "string"
    }
}
```

---

### 3.2 `delete-app-version-resource`

Deletes a resource from the draft version.

**Synopsis:**
```bash
aws resiliencehub delete-app-version-resource \
    --app-arn <value> \
    [--logical-resource-id <value>] \
    [--physical-resource-id <value>] \
    [--resource-name <value>] \
    [--aws-region <value>] \
    [--aws-account-id <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--logical-resource-id` | No | structure | None | Logical resource ID |
| `--physical-resource-id` | No | string | None | Physical resource ID |
| `--resource-name` | No | string | None | Resource name |
| `--aws-region` | No | string | None | AWS region of resource |
| `--aws-account-id` | No | string | None | AWS account ID |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "appArn": "string",
    "appVersion": "string",
    "physicalResource": {}
}
```

---

### 3.3 `describe-app-version-resource`

Describes a resource in an app version.

**Synopsis:**
```bash
aws resiliencehub describe-app-version-resource \
    --app-arn <value> \
    --app-version <value> \
    [--logical-resource-id <value>] \
    [--physical-resource-id <value>] \
    [--resource-name <value>] \
    [--aws-region <value>] \
    [--aws-account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--app-version` | **Yes** | string | -- | App version |
| `--logical-resource-id` | No | structure | None | Logical resource ID |
| `--physical-resource-id` | No | string | None | Physical resource ID |
| `--resource-name` | No | string | None | Resource name |
| `--aws-region` | No | string | None | AWS region |
| `--aws-account-id` | No | string | None | AWS account ID |

**Output Schema:**
```json
{
    "appArn": "string",
    "appVersion": "string",
    "physicalResource": {}
}
```

---

### 3.4 `list-app-version-resources`

Lists resources in an app version. **Paginated.**

**Synopsis:**
```bash
aws resiliencehub list-app-version-resources \
    --app-arn <value> \
    --app-version <value> \
    [--resolution-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--app-version` | **Yes** | string | -- | App version |
| `--resolution-id` | No | string | None | Resolution ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "physicalResources": [
        {
            "physicalResourceId": {},
            "logicalResourceId": {},
            "resourceType": "string",
            "resourceName": "string",
            "appComponents": [],
            "excluded": "boolean",
            "sourceType": "string"
        }
    ],
    "resolutionId": "string",
    "nextToken": "string"
}
```

---

### 3.5 `update-app-version-resource`

Updates a resource in the draft version.

**Synopsis:**
```bash
aws resiliencehub update-app-version-resource \
    --app-arn <value> \
    [--logical-resource-id <value>] \
    [--physical-resource-id <value>] \
    [--resource-name <value>] \
    [--aws-region <value>] \
    [--aws-account-id <value>] \
    [--app-components <value>] \
    [--additional-info <value>] \
    [--excluded | --no-excluded] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--logical-resource-id` | No | structure | None | Logical resource ID |
| `--physical-resource-id` | No | string | None | Physical resource ID |
| `--resource-name` | No | string | None | Resource name |
| `--aws-region` | No | string | None | AWS region |
| `--aws-account-id` | No | string | None | AWS account ID |
| `--app-components` | No | list(string) | None | Updated app components |
| `--additional-info` | No | map | None | Updated additional info |
| `--excluded` | No | boolean | None | Whether to exclude from assessment |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "appArn": "string",
    "appVersion": "string",
    "physicalResource": {}
}
```

---

### 3.6 `add-draft-app-version-resource-mappings`

Adds resource mappings to the draft app version.

**Synopsis:**
```bash
aws resiliencehub add-draft-app-version-resource-mappings \
    --app-arn <value> \
    --resource-mappings <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--resource-mappings` | **Yes** | list | -- | Resource mappings (JSON) |

**Output Schema:**
```json
{
    "appArn": "string",
    "appVersion": "string",
    "resourceMappings": [
        {
            "appRegistryAppName": "string",
            "eksSourceName": "string",
            "logicalStackName": "string",
            "mappingType": "CfnStack|Resource|AppRegistryApp|ResourceGroup|Terraform|EKS",
            "physicalResourceId": {},
            "resourceGroupName": "string",
            "resourceName": "string",
            "terraformSourceName": "string"
        }
    ]
}
```

---

### 3.7 `remove-draft-app-version-resource-mappings`

Removes resource mappings from the draft version.

**Synopsis:**
```bash
aws resiliencehub remove-draft-app-version-resource-mappings \
    --app-arn <value> \
    [--app-registry-app-names <value>] \
    [--eks-source-names <value>] \
    [--logical-stack-names <value>] \
    [--resource-group-names <value>] \
    [--resource-names <value>] \
    [--terraform-source-names <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--app-registry-app-names` | No | list(string) | None | AppRegistry app names to remove |
| `--eks-source-names` | No | list(string) | None | EKS source names to remove |
| `--logical-stack-names` | No | list(string) | None | CloudFormation stack names to remove |
| `--resource-group-names` | No | list(string) | None | Resource group names to remove |
| `--resource-names` | No | list(string) | None | Resource names to remove |
| `--terraform-source-names` | No | list(string) | None | Terraform source names to remove |

**Output Schema:**
```json
{
    "appArn": "string",
    "appVersion": "string"
}
```

---

### 3.8 `list-app-version-resource-mappings`

Lists resource mappings for an app version. **Paginated.**

**Synopsis:**
```bash
aws resiliencehub list-app-version-resource-mappings \
    --app-arn <value> \
    --app-version <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--app-version` | **Yes** | string | -- | App version |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "resourceMappings": [],
    "nextToken": "string"
}
```

---

### 3.9 `import-resources-to-draft-app-version`

Imports resources into the draft app version from various sources.

**Synopsis:**
```bash
aws resiliencehub import-resources-to-draft-app-version \
    --app-arn <value> \
    [--source-arns <value>] \
    [--terraform-sources <value>] \
    [--eks-sources <value>] \
    [--import-strategy <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--source-arns` | No | list(string) | None | Source ARNs (CloudFormation stacks, Resource Groups, AppRegistry apps) |
| `--terraform-sources` | No | list | None | Terraform state sources. JSON: `[{s3StateFileUrl}]` |
| `--eks-sources` | No | list | None | EKS sources. JSON: `[{eksClusterArn,namespaces}]` |
| `--import-strategy` | No | string | None | `AddOnly` or `ReplaceAll` |

**Output Schema:**
```json
{
    "appArn": "string",
    "appVersion": "string",
    "eksSources": [],
    "sourceArns": ["string"],
    "status": "Pending|InProgress|Failed|Success",
    "terraformSources": []
}
```

---

### 3.10 `describe-draft-app-version-resources-import-status`

Gets the import status for draft app version resources.

**Synopsis:**
```bash
aws resiliencehub describe-draft-app-version-resources-import-status \
    --app-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |

**Output Schema:**
```json
{
    "appArn": "string",
    "appVersion": "string",
    "errorMessage": "string",
    "status": "Pending|InProgress|Failed|Success",
    "statusChangeTime": "timestamp"
}
```

---

### 3.11 `describe-app-version-resources-resolution-status`

Gets the resource resolution status for an app version.

**Synopsis:**
```bash
aws resiliencehub describe-app-version-resources-resolution-status \
    --app-arn <value> \
    --app-version <value> \
    [--resolution-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--app-version` | **Yes** | string | -- | App version |
| `--resolution-id` | No | string | None | Resolution ID |

**Output Schema:**
```json
{
    "appArn": "string",
    "appVersion": "string",
    "errorMessage": "string",
    "resolutionId": "string",
    "status": "Pending|InProgress|Failed|Success"
}
```

---

### 3.12 `resolve-app-version-resources`

Resolves resources for an app version.

**Synopsis:**
```bash
aws resiliencehub resolve-app-version-resources \
    --app-arn <value> \
    --app-version <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--app-version` | **Yes** | string | -- | App version |

**Output Schema:**
```json
{
    "appArn": "string",
    "appVersion": "string",
    "resolutionId": "string",
    "status": "Pending|InProgress|Failed|Success"
}
```

---

### 3.13 `describe-app-version-template`

Describes the app version template.

**Synopsis:**
```bash
aws resiliencehub describe-app-version-template \
    --app-arn <value> \
    --app-version <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--app-version` | **Yes** | string | -- | App version |

**Output Schema:**
```json
{
    "appArn": "string",
    "appVersion": "string",
    "appTemplateBody": "string"
}
```

---

### 3.14 `put-draft-app-version-template`

Updates the draft app version template.

**Synopsis:**
```bash
aws resiliencehub put-draft-app-version-template \
    --app-arn <value> \
    --app-template-body <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--app-template-body` | **Yes** | string | -- | Template body JSON (0-409600 chars) |

**Output Schema:**
```json
{
    "appArn": "string",
    "appVersion": "string"
}
```

---

### 3.15 `list-app-input-sources`

Lists input sources for a Resilience Hub app. **Paginated.**

**Synopsis:**
```bash
aws resiliencehub list-app-input-sources \
    --app-arn <value> \
    --app-version <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--app-version` | **Yes** | string | -- | App version |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "appInputSources": [
        {
            "importType": "CfnStack|Resource|AppRegistryApp|ResourceGroup|Terraform|EKS",
            "resourceCount": "integer",
            "sourceArn": "string",
            "sourceName": "string",
            "terraformSource": {},
            "eksSourceClusterNamespace": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 3.16 `delete-app-input-source`

Deletes an input source from the draft app version.

**Synopsis:**
```bash
aws resiliencehub delete-app-input-source \
    --app-arn <value> \
    [--source-arn <value>] \
    [--terraform-source <value>] \
    [--eks-source-cluster-namespace <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--source-arn` | No | string | None | Source ARN to remove |
| `--terraform-source` | No | structure | None | Terraform source to remove |
| `--eks-source-cluster-namespace` | No | structure | None | EKS source to remove |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "appArn": "string",
    "appInputSource": {}
}
```

---

### 3.17 `list-unsupported-app-version-resources`

Lists unsupported resources in an app version. **Paginated.**

**Synopsis:**
```bash
aws resiliencehub list-unsupported-app-version-resources \
    --app-arn <value> \
    --app-version <value> \
    [--resolution-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--app-version` | **Yes** | string | -- | App version |
| `--resolution-id` | No | string | None | Resolution ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "resolutionId": "string",
    "unsupportedResources": [
        {
            "logicalResourceId": {},
            "physicalResourceId": {},
            "resourceType": "string",
            "unsupportedResourceStatus": "string"
        }
    ],
    "nextToken": "string"
}
```
