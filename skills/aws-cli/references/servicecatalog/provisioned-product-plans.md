# Provisioned Product Plans

### 5.1 `create-provisioned-product-plan`

Creates a plan for provisioning a product. Allows reviewing changes before executing.

**Synopsis:**
```bash
aws servicecatalog create-provisioned-product-plan \
    --plan-name <value> \
    --plan-type <value> \
    --product-id <value> \
    --provisioned-product-name <value> \
    --provisioning-artifact-id <value> \
    --idempotency-token <value> \
    [--path-id <value>] \
    [--provisioning-parameters <value>] \
    [--notification-arns <value>] \
    [--tags <value>] \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--plan-name` | **Yes** | string | -- | Name of the plan |
| `--plan-type` | **Yes** | string | -- | Plan type: `CLOUDFORMATION` |
| `--product-id` | **Yes** | string | -- | Product identifier |
| `--provisioned-product-name` | **Yes** | string | -- | Name for the provisioned product |
| `--provisioning-artifact-id` | **Yes** | string | -- | Artifact identifier |
| `--idempotency-token` | **Yes** | string | -- | Idempotency token |
| `--path-id` | No | string | None | Launch path identifier |
| `--provisioning-parameters` | No | list | None | Parameters. Shorthand: `Key=string,Value=string,UsePreviousValue=boolean ...` |
| `--notification-arns` | No | list(string) | None | SNS topic ARNs |
| `--tags` | No | list | None | Tags |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{
    "PlanName": "string",
    "PlanId": "string",
    "ProvisionProductId": "string",
    "ProvisionedProductName": "string",
    "ProvisioningArtifactId": "string"
}
```

---

### 5.2 `delete-provisioned-product-plan`

Deletes the specified plan.

**Synopsis:**
```bash
aws servicecatalog delete-provisioned-product-plan \
    --plan-id <value> \
    [--ignore-errors | --no-ignore-errors] \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--plan-id` | **Yes** | string | -- | Plan identifier |
| `--ignore-errors` | No | boolean | false | Ignore errors during deletion |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{}
```

---

### 5.3 `describe-provisioned-product-plan`

Gets information about the resource changes for the specified plan. **Paginated operation.**

**Synopsis:**
```bash
aws servicecatalog describe-provisioned-product-plan \
    --plan-id <value> \
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
| `--plan-id` | **Yes** | string | -- | Plan identifier |
| `--accept-language` | No | string | None | Language code |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "ProvisionedProductPlanDetails": {
        "CreatedTime": "timestamp",
        "PathId": "string",
        "ProductId": "string",
        "PlanName": "string",
        "PlanId": "string",
        "ProvisionProductId": "string",
        "ProvisionProductName": "string",
        "PlanType": "CLOUDFORMATION",
        "ProvisioningArtifactId": "string",
        "Status": "CREATE_IN_PROGRESS|CREATE_SUCCESS|CREATE_FAILED|EXECUTE_IN_PROGRESS|EXECUTE_SUCCESS|EXECUTE_FAILED",
        "UpdatedTime": "timestamp",
        "NotificationArns": ["string"],
        "ProvisioningParameters": [
            {
                "Key": "string",
                "Value": "string",
                "UsePreviousValue": "boolean"
            }
        ],
        "Tags": [],
        "StatusMessage": "string"
    },
    "ResourceChanges": [
        {
            "Action": "ADD|MODIFY|REMOVE",
            "LogicalResourceId": "string",
            "PhysicalResourceId": "string",
            "ResourceType": "string",
            "Replacement": "TRUE|FALSE|CONDITIONAL",
            "Scope": ["PROPERTIES|METADATA|CREATIONPOLICY|UPDATEPOLICY|DELETIONPOLICY|TAGS"],
            "Details": [
                {
                    "Target": {
                        "Attribute": "string",
                        "Name": "string",
                        "RequiresRecreation": "NEVER|CONDITIONALLY|ALWAYS"
                    },
                    "Evaluation": "STATIC|DYNAMIC",
                    "CausingEntity": "string"
                }
            ]
        }
    ],
    "NextPageToken": "string"
}
```

---

### 5.4 `execute-provisioned-product-plan`

Provisions or updates a product based on the specified plan.

**Synopsis:**
```bash
aws servicecatalog execute-provisioned-product-plan \
    --plan-id <value> \
    --idempotency-token <value> \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--plan-id` | **Yes** | string | -- | Plan identifier |
| `--idempotency-token` | **Yes** | string | -- | Idempotency token |
| `--accept-language` | No | string | None | Language code |

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

---

### 5.5 `list-provisioned-product-plans`

Lists the plans for the specified provisioned product or all plans the user has access to. **Paginated operation.**

**Synopsis:**
```bash
aws servicecatalog list-provisioned-product-plans \
    [--accept-language <value>] \
    [--provision-product-id <value>] \
    [--access-level-filter <value>] \
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
| `--provision-product-id` | No | string | None | Filter by provisioned product |
| `--access-level-filter` | No | structure | None | Access level filter |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "ProvisionedProductPlans": [
        {
            "PlanName": "string",
            "PlanId": "string",
            "ProvisionProductId": "string",
            "ProvisionProductName": "string",
            "PlanType": "CLOUDFORMATION",
            "ProvisioningArtifactId": "string"
        }
    ],
    "NextPageToken": "string"
}
```
