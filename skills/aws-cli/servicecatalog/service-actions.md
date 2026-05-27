# Service Actions

### 7.1 `create-service-action`

Creates a self-service action.

**Synopsis:**
```bash
aws servicecatalog create-service-action \
    --name <value> \
    --definition-type <value> \
    --definition <value> \
    --idempotency-token <value> \
    [--description <value>] \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Service action name (1-256 chars) |
| `--definition-type` | **Yes** | string | -- | Definition type: `SSM_AUTOMATION` |
| `--definition` | **Yes** | map | -- | Definition map. Keys: `Name` (SSM document name), `Version` (doc version), `AssumeRole` (IAM role ARN), `Parameters` (JSON string) |
| `--idempotency-token` | **Yes** | string | -- | Idempotency token |
| `--description` | No | string | None | Description (max 1024 chars) |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{
    "ServiceActionDetail": {
        "ServiceActionSummary": {
            "Id": "string",
            "Name": "string",
            "Description": "string",
            "DefinitionType": "SSM_AUTOMATION"
        },
        "Definition": {
            "string": "string"
        }
    }
}
```

---

### 7.2 `delete-service-action`

Deletes a self-service action.

**Synopsis:**
```bash
aws servicecatalog delete-service-action \
    --id <value> \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Service action identifier |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{}
```

---

### 7.3 `describe-service-action`

Describes a self-service action.

**Synopsis:**
```bash
aws servicecatalog describe-service-action \
    --id <value> \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Service action identifier |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{
    "ServiceActionDetail": {
        "ServiceActionSummary": {
            "Id": "string",
            "Name": "string",
            "Description": "string",
            "DefinitionType": "SSM_AUTOMATION"
        },
        "Definition": {
            "string": "string"
        }
    }
}
```

---

### 7.4 `update-service-action`

Updates a self-service action.

**Synopsis:**
```bash
aws servicecatalog update-service-action \
    --id <value> \
    [--name <value>] \
    [--definition <value>] \
    [--description <value>] \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Service action identifier |
| `--name` | No | string | None | Updated name |
| `--definition` | No | map | None | Updated definition |
| `--description` | No | string | None | Updated description |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{
    "ServiceActionDetail": {
        "ServiceActionSummary": {
            "Id": "string",
            "Name": "string",
            "Description": "string",
            "DefinitionType": "SSM_AUTOMATION"
        },
        "Definition": {
            "string": "string"
        }
    }
}
```

---

### 7.5 `list-service-actions`

Lists all self-service actions. **Paginated operation.**

**Synopsis:**
```bash
aws servicecatalog list-service-actions \
    [--accept-language <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--accept-language` | No | string | None | Language code |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "ServiceActionSummaries": [
        {
            "Id": "string",
            "Name": "string",
            "Description": "string",
            "DefinitionType": "SSM_AUTOMATION"
        }
    ],
    "NextPageToken": "string"
}
```

---

### 7.6 `associate-service-action-with-provisioning-artifact`

Associates a self-service action with a provisioning artifact.

**Synopsis:**
```bash
aws servicecatalog associate-service-action-with-provisioning-artifact \
    --product-id <value> \
    --provisioning-artifact-id <value> \
    --service-action-id <value> \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--product-id` | **Yes** | string | -- | Product identifier |
| `--provisioning-artifact-id` | **Yes** | string | -- | Artifact identifier |
| `--service-action-id` | **Yes** | string | -- | Service action identifier |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{}
```

---

### 7.7 `disassociate-service-action-from-provisioning-artifact`

Disassociates a self-service action from a provisioning artifact.

**Synopsis:**
```bash
aws servicecatalog disassociate-service-action-from-provisioning-artifact \
    --product-id <value> \
    --provisioning-artifact-id <value> \
    --service-action-id <value> \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--product-id` | **Yes** | string | -- | Product identifier |
| `--provisioning-artifact-id` | **Yes** | string | -- | Artifact identifier |
| `--service-action-id` | **Yes** | string | -- | Service action identifier |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{}
```

---

### 7.8 `batch-associate-service-action-with-provisioning-artifact`

Associates multiple self-service actions with provisioning artifacts in a batch.

**Synopsis:**
```bash
aws servicecatalog batch-associate-service-action-with-provisioning-artifact \
    --service-action-associations <value> \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-action-associations` | **Yes** | list | -- | Associations. Shorthand: `ServiceActionId=string,ProductId=string,ProvisioningArtifactId=string ...` |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{
    "FailedServiceActionAssociations": [
        {
            "ServiceActionId": "string",
            "ProductId": "string",
            "ProvisioningArtifactId": "string",
            "ErrorCode": "DUPLICATE_RESOURCE|INTERNAL_FAILURE|LIMIT_EXCEEDED|RESOURCE_NOT_FOUND|THROTTLING|INVALID_PARAMETER",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 7.9 `batch-disassociate-service-action-from-provisioning-artifact`

Disassociates multiple self-service actions from provisioning artifacts in a batch.

**Synopsis:**
```bash
aws servicecatalog batch-disassociate-service-action-from-provisioning-artifact \
    --service-action-associations <value> \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-action-associations` | **Yes** | list | -- | Associations to remove. Shorthand: `ServiceActionId=string,ProductId=string,ProvisioningArtifactId=string ...` |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{
    "FailedServiceActionAssociations": [
        {
            "ServiceActionId": "string",
            "ProductId": "string",
            "ProvisioningArtifactId": "string",
            "ErrorCode": "DUPLICATE_RESOURCE|INTERNAL_FAILURE|LIMIT_EXCEEDED|RESOURCE_NOT_FOUND|THROTTLING|INVALID_PARAMETER",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 7.10 `list-service-actions-for-provisioning-artifact`

Returns a paginated list of self-service actions associated with the specified provisioning artifact. **Paginated operation.**

**Synopsis:**
```bash
aws servicecatalog list-service-actions-for-provisioning-artifact \
    --product-id <value> \
    --provisioning-artifact-id <value> \
    [--accept-language <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--product-id` | **Yes** | string | -- | Product identifier |
| `--provisioning-artifact-id` | **Yes** | string | -- | Artifact identifier |
| `--accept-language` | No | string | None | Language code |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "ServiceActionSummaries": [
        {
            "Id": "string",
            "Name": "string",
            "Description": "string",
            "DefinitionType": "SSM_AUTOMATION"
        }
    ],
    "NextPageToken": "string"
}
```

---

### 7.11 `describe-service-action-execution-parameters`

Finds the default parameters for a specific self-service action on a specific provisioned product.

**Synopsis:**
```bash
aws servicecatalog describe-service-action-execution-parameters \
    --provisioned-product-id <value> \
    --service-action-id <value> \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--provisioned-product-id` | **Yes** | string | -- | Provisioned product identifier |
| `--service-action-id` | **Yes** | string | -- | Service action identifier |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{
    "ServiceActionParameters": [
        {
            "Name": "string",
            "Type": "DEFAULT",
            "DefaultValues": ["string"]
        }
    ]
}
```

---

### 7.12 `execute-provisioned-product-service-action`

Executes a self-service action against a provisioned product.

**Synopsis:**
```bash
aws servicecatalog execute-provisioned-product-service-action \
    --provisioned-product-id <value> \
    --service-action-id <value> \
    --execute-token <value> \
    [--accept-language <value>] \
    [--parameters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--provisioned-product-id` | **Yes** | string | -- | Provisioned product identifier |
| `--service-action-id` | **Yes** | string | -- | Service action identifier |
| `--execute-token` | **Yes** | string | -- | Idempotency token |
| `--accept-language` | No | string | None | Language code |
| `--parameters` | No | map | None | Execution parameters (key-value pairs) |

**Output Schema:**
```json
{
    "RecordDetail": {
        "RecordId": "string",
        "ProvisionedProductName": "string",
        "Status": "CREATED|IN_PROGRESS|IN_PROGRESS_IN_ERROR|SUCCEEDED|FAILED",
        "CreatedTime": "timestamp",
        "UpdatedTime": "timestamp",
        "ProvisionedProductType": "string",
        "RecordType": "string",
        "ProvisionedProductId": "string",
        "ProductId": "string",
        "ProvisioningArtifactId": "string",
        "PathId": "string",
        "RecordErrors": [],
        "RecordTags": []
    }
}
```
