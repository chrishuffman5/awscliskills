# Products

### 2.1 `create-product`

Creates a product.

**Synopsis:**
```bash
aws servicecatalog create-product \
    --name <value> \
    --owner <value> \
    --product-type <value> \
    [--description <value>] \
    [--distributor <value>] \
    [--support-description <value>] \
    [--support-email <value>] \
    [--support-url <value>] \
    [--tags <value>] \
    [--provisioning-artifact-parameters <value>] \
    [--source-connection <value>] \
    --idempotency-token <value> \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Product name (max 8191 chars) |
| `--owner` | **Yes** | string | -- | Product owner (max 8191 chars) |
| `--product-type` | **Yes** | string | -- | `CLOUD_FORMATION_TEMPLATE`, `MARKETPLACE`, `TERRAFORM_OPEN_SOURCE`, `TERRAFORM_CLOUD`, `EXTERNAL` |
| `--description` | No | string | None | Product description |
| `--distributor` | No | string | None | Distributor name |
| `--support-description` | No | string | None | Support information |
| `--support-email` | No | string | None | Support email |
| `--support-url` | No | string | None | Support URL |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--provisioning-artifact-parameters` | No | structure | None | Provisioning artifact configuration |
| `--source-connection` | No | structure | None | Source connection (CodeStar) |
| `--idempotency-token` | **Yes** | string | -- | Idempotency token |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{
    "ProductViewDetail": {
        "ProductViewSummary": {
            "Id": "string",
            "ProductId": "string",
            "Name": "string",
            "Owner": "string",
            "ShortDescription": "string",
            "Type": "string",
            "Distributor": "string",
            "HasDefaultPath": "boolean",
            "SupportEmail": "string",
            "SupportDescription": "string",
            "SupportUrl": "string"
        },
        "Status": "AVAILABLE|CREATING|FAILED",
        "ProductARN": "string",
        "CreatedTime": "timestamp",
        "SourceConnection": {
            "Type": "CODESTAR",
            "ConnectionParameters": {
                "CodeStar": {
                    "ConnectionArn": "string",
                    "Repository": "string",
                    "Branch": "string",
                    "ArtifactPath": "string"
                }
            },
            "LastSync": {
                "LastSyncTime": "timestamp",
                "LastSyncStatus": "SUCCEEDED|FAILED",
                "LastSyncStatusMessage": "string",
                "LastSuccessfulSyncTime": "timestamp",
                "LastSuccessfulSyncProvisioningArtifactId": "string"
            }
        }
    },
    "ProvisioningArtifactDetail": {
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "Type": "CLOUD_FORMATION_TEMPLATE|MARKETPLACE_AMI|MARKETPLACE_CAR|TERRAFORM_OPEN_SOURCE|TERRAFORM_CLOUD",
        "CreatedTime": "timestamp",
        "Active": "boolean",
        "Guidance": "DEFAULT|DEPRECATED",
        "SourceRevision": "string"
    },
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```

---

### 2.2 `delete-product`

Deletes the specified product. Must remove all provisioning artifacts and disassociate from all portfolios first.

**Synopsis:**
```bash
aws servicecatalog delete-product \
    --id <value> \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Product identifier |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{}
```

---

### 2.3 `describe-product`

Gets information about the specified product (end user view).

**Synopsis:**
```bash
aws servicecatalog describe-product \
    [--id <value>] \
    [--name <value>] \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | No | string | None | Product identifier (specify id or name) |
| `--name` | No | string | None | Product name |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{
    "ProductViewSummary": {
        "Id": "string",
        "ProductId": "string",
        "Name": "string",
        "Owner": "string",
        "ShortDescription": "string",
        "Type": "string",
        "Distributor": "string",
        "HasDefaultPath": "boolean",
        "SupportEmail": "string",
        "SupportDescription": "string",
        "SupportUrl": "string"
    },
    "ProvisioningArtifacts": [
        {
            "Id": "string",
            "Name": "string",
            "Description": "string",
            "CreatedTime": "timestamp",
            "Guidance": "DEFAULT|DEPRECATED"
        }
    ],
    "Budgets": [
        {
            "BudgetName": "string"
        }
    ],
    "LaunchPaths": [
        {
            "Id": "string",
            "Name": "string"
        }
    ]
}
```

---

### 2.4 `describe-product-as-admin`

Gets information about the specified product (admin view with full details).

**Synopsis:**
```bash
aws servicecatalog describe-product-as-admin \
    [--id <value>] \
    [--name <value>] \
    [--accept-language <value>] \
    [--source-portfolio-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | No | string | None | Product identifier (specify id or name) |
| `--name` | No | string | None | Product name |
| `--accept-language` | No | string | None | Language code |
| `--source-portfolio-id` | No | string | None | Source portfolio for an imported product |

**Output Schema:**
```json
{
    "ProductViewDetail": {
        "ProductViewSummary": {
            "Id": "string",
            "ProductId": "string",
            "Name": "string",
            "Owner": "string",
            "ShortDescription": "string",
            "Type": "string",
            "Distributor": "string",
            "HasDefaultPath": "boolean",
            "SupportEmail": "string",
            "SupportDescription": "string",
            "SupportUrl": "string"
        },
        "Status": "AVAILABLE|CREATING|FAILED",
        "ProductARN": "string",
        "CreatedTime": "timestamp",
        "SourceConnection": {}
    },
    "ProvisioningArtifactSummaries": [
        {
            "Id": "string",
            "Name": "string",
            "Description": "string",
            "CreatedTime": "timestamp",
            "ProvisioningArtifactMetadata": {
                "string": "string"
            }
        }
    ],
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ],
    "TagOptions": [
        {
            "Key": "string",
            "Value": "string",
            "Active": "boolean",
            "Id": "string",
            "Owner": "string"
        }
    ],
    "Budgets": [
        {
            "BudgetName": "string"
        }
    ]
}
```

---

### 2.5 `describe-product-view`

Gets information about the specified product by its product view ID.

**Synopsis:**
```bash
aws servicecatalog describe-product-view \
    --id <value> \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Product view identifier |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{
    "ProductViewSummary": {
        "Id": "string",
        "ProductId": "string",
        "Name": "string",
        "Owner": "string",
        "ShortDescription": "string",
        "Type": "string",
        "Distributor": "string",
        "HasDefaultPath": "boolean",
        "SupportEmail": "string",
        "SupportDescription": "string",
        "SupportUrl": "string"
    },
    "ProvisioningArtifacts": [
        {
            "Id": "string",
            "Name": "string",
            "Description": "string",
            "CreatedTime": "timestamp",
            "Guidance": "DEFAULT|DEPRECATED"
        }
    ]
}
```

---

### 2.6 `update-product`

Updates the specified product.

**Synopsis:**
```bash
aws servicecatalog update-product \
    --id <value> \
    [--name <value>] \
    [--owner <value>] \
    [--description <value>] \
    [--distributor <value>] \
    [--support-description <value>] \
    [--support-email <value>] \
    [--support-url <value>] \
    [--add-tags <value>] \
    [--remove-tags <value>] \
    [--source-connection <value>] \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Product identifier |
| `--name` | No | string | None | Updated name |
| `--owner` | No | string | None | Updated owner |
| `--description` | No | string | None | Updated description |
| `--distributor` | No | string | None | Updated distributor |
| `--support-description` | No | string | None | Updated support description |
| `--support-email` | No | string | None | Updated support email |
| `--support-url` | No | string | None | Updated support URL |
| `--add-tags` | No | list | None | Tags to add |
| `--remove-tags` | No | list(string) | None | Tag keys to remove |
| `--source-connection` | No | structure | None | Source connection |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{
    "ProductViewDetail": {
        "ProductViewSummary": {},
        "Status": "AVAILABLE|CREATING|FAILED",
        "ProductARN": "string",
        "CreatedTime": "timestamp"
    },
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```

---

### 2.7 `list-portfolios-for-product`

Lists all portfolios associated with the specified product. **Paginated operation.**

**Synopsis:**
```bash
aws servicecatalog list-portfolios-for-product \
    --product-id <value> \
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
| `--accept-language` | No | string | None | Language code |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "PortfolioDetails": [
        {
            "Id": "string",
            "ARN": "string",
            "DisplayName": "string",
            "Description": "string",
            "CreatedTime": "timestamp",
            "ProviderName": "string"
        }
    ],
    "NextPageToken": "string"
}
```

---

### 2.8 `associate-product-with-portfolio`

Associates the specified product with the specified portfolio.

**Synopsis:**
```bash
aws servicecatalog associate-product-with-portfolio \
    --product-id <value> \
    --portfolio-id <value> \
    [--source-portfolio-id <value>] \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--product-id` | **Yes** | string | -- | Product identifier |
| `--portfolio-id` | **Yes** | string | -- | Portfolio identifier |
| `--source-portfolio-id` | No | string | None | Source portfolio (for shared products) |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{}
```

---

### 2.9 `disassociate-product-from-portfolio`

Disassociates the specified product from the specified portfolio.

**Synopsis:**
```bash
aws servicecatalog disassociate-product-from-portfolio \
    --product-id <value> \
    --portfolio-id <value> \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--product-id` | **Yes** | string | -- | Product identifier |
| `--portfolio-id` | **Yes** | string | -- | Portfolio identifier |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{}
```

---

### 2.10 `copy-product`

Copies the specified source product to the specified target product or a new product.

**Synopsis:**
```bash
aws servicecatalog copy-product \
    --source-product-arn <value> \
    [--target-product-id <value>] \
    [--target-product-name <value>] \
    [--source-provisioning-artifact-identifiers <value>] \
    [--copy-options <value>] \
    --idempotency-token <value> \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-product-arn` | **Yes** | string | -- | ARN of the source product |
| `--target-product-id` | No | string | None | Target product ID (for updating existing product) |
| `--target-product-name` | No | string | None | Name for the new product |
| `--source-provisioning-artifact-identifiers` | No | list | None | Identifiers of artifacts to copy |
| `--copy-options` | No | list(string) | None | Options: `CopyTags` |
| `--idempotency-token` | **Yes** | string | -- | Idempotency token |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{
    "CopyProductToken": "string"
}
```

---

### 2.11 `describe-copy-product-status`

Gets the status of the specified copy product operation.

**Synopsis:**
```bash
aws servicecatalog describe-copy-product-status \
    --copy-product-token <value> \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--copy-product-token` | **Yes** | string | -- | Token from copy-product |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{
    "CopyProductStatus": "SUCCEEDED|IN_PROGRESS|FAILED",
    "TargetProductId": "string",
    "StatusDetail": "string"
}
```

---

### 2.12 `search-products`

Gets information about products for the current account (end user view). **Paginated operation.**

**Synopsis:**
```bash
aws servicecatalog search-products \
    [--accept-language <value>] \
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
| `--filters` | No | map | None | Filters. Keys: `FullTextSearch`, `Owner`, `ProductType`, `SourceProductId` |
| `--sort-by` | No | string | None | Sort field: `Title`, `VersionCount`, `CreationDate` |
| `--sort-order` | No | string | None | `ASCENDING` or `DESCENDING` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "ProductViewSummaries": [
        {
            "Id": "string",
            "ProductId": "string",
            "Name": "string",
            "Owner": "string",
            "ShortDescription": "string",
            "Type": "string",
            "Distributor": "string",
            "HasDefaultPath": "boolean",
            "SupportEmail": "string",
            "SupportDescription": "string",
            "SupportUrl": "string"
        }
    ],
    "ProductViewAggregations": {
        "string": [
            {
                "Value": "string",
                "ApproximateCount": "integer"
            }
        ]
    },
    "NextPageToken": "string"
}
```

---

### 2.13 `search-products-as-admin`

Gets information about products for the current account (admin view). **Paginated operation.**

**Synopsis:**
```bash
aws servicecatalog search-products-as-admin \
    [--accept-language <value>] \
    [--portfolio-id <value>] \
    [--filters <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--product-source <value>] \
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
| `--portfolio-id` | No | string | None | Filter by portfolio |
| `--filters` | No | map | None | Filters. Keys: `FullTextSearch`, `Owner`, `ProductType`, `SourceProductId` |
| `--sort-by` | No | string | None | Sort field: `Title`, `VersionCount`, `CreationDate` |
| `--sort-order` | No | string | None | `ASCENDING` or `DESCENDING` |
| `--product-source` | No | string | None | Product source: `ACCOUNT` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "ProductViewDetails": [
        {
            "ProductViewSummary": {},
            "Status": "AVAILABLE|CREATING|FAILED",
            "ProductARN": "string",
            "CreatedTime": "timestamp",
            "SourceConnection": {}
        }
    ],
    "NextPageToken": "string"
}
```
