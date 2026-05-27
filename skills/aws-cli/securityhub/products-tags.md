# Products & Tags

### 14.1 `describe-products`

Returns information about product integrations. **Paginated operation.**

**Synopsis:**
```bash
aws securityhub describe-products \
    [--product-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--product-arn` | No | string | None | Specific product ARN (omit for all) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Products": [
        {
            "ProductArn": "string",
            "ProductName": "string",
            "CompanyName": "string",
            "Description": "string",
            "Categories": ["string"],
            "IntegrationTypes": ["SEND_FINDINGS_TO_SECURITY_HUB|RECEIVE_FINDINGS_FROM_SECURITY_HUB|UPDATE_FINDINGS_IN_SECURITY_HUB"],
            "MarketplaceUrl": "string",
            "ActivationUrl": "string",
            "ProductSubscriptionResourcePolicy": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 14.2 `enable-import-findings-for-product`

Enables the integration of a partner product to import findings.

**Synopsis:**
```bash
aws securityhub enable-import-findings-for-product \
    --product-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--product-arn` | **Yes** | string | -- | ARN of the product to enable |

**Output Schema:**
```json
{
    "ProductSubscriptionArn": "string"
}
```

---

### 14.3 `disable-import-findings-for-product`

Disables the import of findings for a partner product.

**Synopsis:**
```bash
aws securityhub disable-import-findings-for-product \
    --product-subscription-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--product-subscription-arn` | **Yes** | string | -- | Product subscription ARN |

**Output:** None (HTTP 200 on success)

---

### 14.4 `list-enabled-products-for-import`

Lists enabled products for findings import. **Paginated operation.**

**Synopsis:**
```bash
aws securityhub list-enabled-products-for-import \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ProductSubscriptions": ["string"],
    "NextToken": "string"
}
```

---

### 14.5 `tag-resource`

Adds tags to a Security Hub resource.

**Synopsis:**
```bash
aws securityhub tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | map | -- | Tags to add (max 50) |

**Output:** None (HTTP 200 on success)

---

### 14.6 `untag-resource`

Removes tags from a Security Hub resource.

**Synopsis:**
```bash
aws securityhub untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to untag |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output:** None (HTTP 200 on success)

---

### 14.7 `list-tags-for-resource`

Returns tags for a Security Hub resource.

**Synopsis:**
```bash
aws securityhub list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |

**Output Schema:**
```json
{
    "Tags": {
        "string": "string"
    }
}
```
