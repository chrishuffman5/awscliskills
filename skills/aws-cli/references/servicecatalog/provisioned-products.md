# Provisioned Products

### 4.1 `provision-product`

Provisions the specified product.

**Synopsis:**
```bash
aws servicecatalog provision-product \
    --provisioned-product-name <value> \
    [--product-id <value>] \
    [--product-name <value>] \
    [--provisioning-artifact-id <value>] \
    [--provisioning-artifact-name <value>] \
    [--path-id <value>] \
    [--path-name <value>] \
    [--provisioning-parameters <value>] \
    [--provisioning-preferences <value>] \
    [--tags <value>] \
    [--notification-arns <value>] \
    --provision-token <value> \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--provisioned-product-name` | **Yes** | string | -- | User-friendly name (1-128 chars) |
| `--product-id` | No | string | None | Product identifier |
| `--product-name` | No | string | None | Product name |
| `--provisioning-artifact-id` | No | string | None | Artifact identifier |
| `--provisioning-artifact-name` | No | string | None | Artifact name |
| `--path-id` | No | string | None | Launch path identifier |
| `--path-name` | No | string | None | Launch path name |
| `--provisioning-parameters` | No | list | None | Parameters. Shorthand: `Key=string,Value=string ...` |
| `--provisioning-preferences` | No | structure | None | StackSet preferences |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--notification-arns` | No | list(string) | None | SNS topic ARNs for notifications |
| `--provision-token` | **Yes** | string | -- | Idempotency token |
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
        "RecordType": "PROVISION_PRODUCT|UPDATE_PROVISIONED_PRODUCT|TERMINATE_PROVISIONED_PRODUCT",
        "ProvisionedProductId": "string",
        "ProductId": "string",
        "ProvisioningArtifactId": "string",
        "PathId": "string",
        "RecordErrors": [
            {
                "Code": "string",
                "Description": "string"
            }
        ],
        "RecordTags": [
            {
                "Key": "string",
                "Value": "string"
            }
        ],
        "LaunchRoleArn": "string"
    }
}
```

---

### 4.2 `terminate-provisioned-product`

Terminates the specified provisioned product.

**Synopsis:**
```bash
aws servicecatalog terminate-provisioned-product \
    [--provisioned-product-name <value>] \
    [--provisioned-product-id <value>] \
    --terminate-token <value> \
    [--ignore-errors | --no-ignore-errors] \
    [--accept-language <value>] \
    [--retain-physical-resources | --no-retain-physical-resources] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--provisioned-product-name` | No | string | None | Name (specify name or id) |
| `--provisioned-product-id` | No | string | None | Identifier |
| `--terminate-token` | **Yes** | string | -- | Idempotency token |
| `--ignore-errors` | No | boolean | false | Ignore errors during termination |
| `--retain-physical-resources` | No | boolean | false | Retain physical resources |
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

### 4.3 `update-provisioned-product`

Requests updates to the configuration of the specified provisioned product.

**Synopsis:**
```bash
aws servicecatalog update-provisioned-product \
    [--provisioned-product-name <value>] \
    [--provisioned-product-id <value>] \
    [--product-id <value>] \
    [--product-name <value>] \
    [--provisioning-artifact-id <value>] \
    [--provisioning-artifact-name <value>] \
    [--path-id <value>] \
    [--path-name <value>] \
    [--provisioning-parameters <value>] \
    [--provisioning-preferences <value>] \
    [--tags <value>] \
    --update-token <value> \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--provisioned-product-name` | No | string | None | Name (specify name or id) |
| `--provisioned-product-id` | No | string | None | Identifier |
| `--product-id` | No | string | None | New product identifier |
| `--product-name` | No | string | None | New product name |
| `--provisioning-artifact-id` | No | string | None | New artifact identifier |
| `--provisioning-artifact-name` | No | string | None | New artifact name |
| `--path-id` | No | string | None | New launch path |
| `--path-name` | No | string | None | New launch path name |
| `--provisioning-parameters` | No | list | None | Updated parameters |
| `--provisioning-preferences` | No | structure | None | StackSet preferences |
| `--tags` | No | list | None | Updated tags |
| `--update-token` | **Yes** | string | -- | Idempotency token |
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

### 4.4 `update-provisioned-product-properties`

Updates the properties of a provisioned product (owner, etc.).

**Synopsis:**
```bash
aws servicecatalog update-provisioned-product-properties \
    --provisioned-product-id <value> \
    --provisioned-product-properties <value> \
    --idempotency-token <value> \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--provisioned-product-id` | **Yes** | string | -- | Provisioned product identifier |
| `--provisioned-product-properties` | **Yes** | map | -- | Properties to update. Key: `OWNER`, `LAUNCH_ROLE` |
| `--idempotency-token` | **Yes** | string | -- | Idempotency token |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{
    "ProvisionedProductId": "string",
    "ProvisionedProductProperties": {
        "string": "string"
    },
    "RecordId": "string",
    "Status": "CREATED|IN_PROGRESS|IN_PROGRESS_IN_ERROR|SUCCEEDED|FAILED"
}
```

---

### 4.5 `describe-provisioned-product`

Gets information about the specified provisioned product.

**Synopsis:**
```bash
aws servicecatalog describe-provisioned-product \
    [--id <value>] \
    [--name <value>] \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | No | string | None | Provisioned product identifier |
| `--name` | No | string | None | Provisioned product name |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{
    "ProvisionedProductDetail": {
        "Name": "string",
        "Arn": "string",
        "Type": "string",
        "Id": "string",
        "Status": "AVAILABLE|UNDER_CHANGE|TAINTED|ERROR|PLAN_IN_PROGRESS",
        "StatusMessage": "string",
        "CreatedTime": "timestamp",
        "IdempotencyToken": "string",
        "LastRecordId": "string",
        "LastProvisioningRecordId": "string",
        "LastSuccessfulProvisioningRecordId": "string",
        "ProductId": "string",
        "ProvisioningArtifactId": "string",
        "LaunchRoleArn": "string"
    },
    "CloudWatchDashboards": [
        {
            "Name": "string"
        }
    ]
}
```

---

### 4.6 `search-provisioned-products`

Gets information about provisioned products with filtering. **Paginated operation.**

**Synopsis:**
```bash
aws servicecatalog search-provisioned-products \
    [--accept-language <value>] \
    [--access-level-filter <value>] \
    [--filters <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
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
| `--access-level-filter` | No | structure | None | Access level filter. Shorthand: `Key=Account\|Role\|User,Value=string` |
| `--filters` | No | map | None | Filters. Key: `SearchQuery` |
| `--sort-by` | No | string | None | Sort field: `arn`, `id`, `name`, `lastRecordId` |
| `--sort-order` | No | string | None | `ASCENDING` or `DESCENDING` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "ProvisionedProducts": [
        {
            "Name": "string",
            "Arn": "string",
            "Type": "string",
            "Id": "string",
            "Status": "AVAILABLE|UNDER_CHANGE|TAINTED|ERROR|PLAN_IN_PROGRESS",
            "StatusMessage": "string",
            "CreatedTime": "timestamp",
            "IdempotencyToken": "string",
            "LastRecordId": "string",
            "LastProvisioningRecordId": "string",
            "LastSuccessfulProvisioningRecordId": "string",
            "Tags": [
                {
                    "Key": "string",
                    "Value": "string"
                }
            ],
            "PhysicalId": "string",
            "ProductId": "string",
            "ProductName": "string",
            "ProvisioningArtifactId": "string",
            "ProvisioningArtifactName": "string",
            "UserArn": "string",
            "UserArnSession": "string"
        }
    ],
    "TotalResultsCount": "integer",
    "NextPageToken": "string"
}
```

---

### 4.7 `scan-provisioned-products`

Lists the provisioned products available for the specified portfolio. **Paginated operation.**

**Synopsis:**
```bash
aws servicecatalog scan-provisioned-products \
    [--accept-language <value>] \
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
| `--access-level-filter` | No | structure | None | Access level filter |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "ProvisionedProducts": [
        {
            "Name": "string",
            "Arn": "string",
            "Type": "string",
            "Id": "string",
            "Status": "AVAILABLE|UNDER_CHANGE|TAINTED|ERROR|PLAN_IN_PROGRESS",
            "StatusMessage": "string",
            "CreatedTime": "timestamp",
            "IdempotencyToken": "string",
            "LastRecordId": "string",
            "LastProvisioningRecordId": "string",
            "LastSuccessfulProvisioningRecordId": "string"
        }
    ],
    "NextPageToken": "string"
}
```

---

### 4.8 `get-provisioned-product-outputs`

Gets the outputs of a provisioned product. **Paginated operation.**

**Synopsis:**
```bash
aws servicecatalog get-provisioned-product-outputs \
    [--provisioned-product-id <value>] \
    [--provisioned-product-name <value>] \
    [--output-keys <value>] \
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
| `--provisioned-product-id` | No | string | None | Provisioned product identifier |
| `--provisioned-product-name` | No | string | None | Provisioned product name |
| `--output-keys` | No | list(string) | None | Specific output keys to retrieve |
| `--accept-language` | No | string | None | Language code |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "Outputs": [
        {
            "OutputKey": "string",
            "OutputValue": "string",
            "Description": "string"
        }
    ],
    "NextPageToken": "string"
}
```

---

### 4.9 `import-as-provisioned-product`

Imports a resource as a Service Catalog provisioned product.

**Synopsis:**
```bash
aws servicecatalog import-as-provisioned-product \
    --product-id <value> \
    --provisioning-artifact-id <value> \
    --provisioned-product-name <value> \
    --physical-id <value> \
    --idempotency-token <value> \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--product-id` | **Yes** | string | -- | Product identifier |
| `--provisioning-artifact-id` | **Yes** | string | -- | Artifact identifier |
| `--provisioned-product-name` | **Yes** | string | -- | Name for the provisioned product |
| `--physical-id` | **Yes** | string | -- | Physical ID of the resource (e.g., CloudFormation stack name/ID) |
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

### 4.10 `list-record-history`

Lists the specified requests or all requests. **Paginated operation.**

**Synopsis:**
```bash
aws servicecatalog list-record-history \
    [--accept-language <value>] \
    [--access-level-filter <value>] \
    [--search-filter <value>] \
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
| `--access-level-filter` | No | structure | None | Access level filter |
| `--search-filter` | No | structure | None | Search filter. Shorthand: `Key=product\|provisionedproduct,Value=string` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "RecordDetails": [
        {
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
            "RecordTags": [],
            "LaunchRoleArn": "string"
        }
    ],
    "NextPageToken": "string"
}
```

---

### 4.11 `describe-record`

Gets information about the specified record.

**Synopsis:**
```bash
aws servicecatalog describe-record \
    --id <value> \
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
| `--id` | **Yes** | string | -- | Record identifier |
| `--accept-language` | No | string | None | Language code |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

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
        "RecordTags": [],
        "LaunchRoleArn": "string"
    },
    "RecordOutputs": [
        {
            "OutputKey": "string",
            "OutputValue": "string",
            "Description": "string"
        }
    ],
    "NextPageToken": "string"
}
```

---

### 4.12 `list-stack-instances-for-provisioned-product`

Returns summary information about stack instances created from a provisioned StackSet product. **Paginated operation.**

**Synopsis:**
```bash
aws servicecatalog list-stack-instances-for-provisioned-product \
    --provisioned-product-id <value> \
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
| `--provisioned-product-id` | **Yes** | string | -- | Provisioned product identifier |
| `--accept-language` | No | string | None | Language code |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "StackInstances": [
        {
            "Account": "string",
            "Region": "string",
            "StackInstanceStatus": "CURRENT|OUTDATED|INOPERABLE"
        }
    ],
    "NextPageToken": "string"
}
```
