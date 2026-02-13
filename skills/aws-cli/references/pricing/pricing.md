# Pricing

### 1.1 `describe-services`

Lists the metadata for all available AWS services, including service codes and attribute names. When called with a specific service code, returns the attributes for that service. **Paginated.**

**Synopsis:**
```bash
aws pricing describe-services \
    [--service-code <value>] \
    [--format-version <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-code` | No | string | None | Service code (e.g., `AmazonEC2`). Omit to list all services |
| `--format-version` | No | string | None | Response format version: `aws_v1` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Services": [
        {
            "ServiceCode": "string",
            "AttributeNames": ["string"]
        }
    ],
    "FormatVersion": "string",
    "NextToken": "string"
}
```

---

### 1.2 `get-attribute-values`

Returns available values for a specified attribute of a service (e.g., all available instance types for EC2). **Paginated.**

**Synopsis:**
```bash
aws pricing get-attribute-values \
    --service-code <value> \
    --attribute-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-code` | **Yes** | string | -- | Service code (e.g., `AmazonEC2`) |
| `--attribute-name` | **Yes** | string | -- | Attribute name (e.g., `instanceType`, `location`, `operatingSystem`) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AttributeValues": [
        {
            "Value": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.3 `get-products`

Returns a list of products that match specified filters. Each product includes its pricing details as a JSON string. **Paginated.**

**Synopsis:**
```bash
aws pricing get-products \
    --service-code <value> \
    [--filters <value>] \
    [--format-version <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-code` | **Yes** | string | -- | Service code (e.g., `AmazonEC2`) |
| `--filters` | No | list | None | Filters (max 50). Shorthand: `Type=TERM_MATCH,Field=string,Value=string ...` |
| `--format-version` | No | string | None | Response format version: `aws_v1` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Structure:**
```json
[
    {
        "Type": "TERM_MATCH|EQUALS|CONTAINS|ANY_OF|NONE_OF",
        "Field": "string",
        "Value": "string"
    }
]
```

**Output Schema:**
```json
{
    "FormatVersion": "string",
    "PriceList": ["string"],
    "NextToken": "string"
}
```

Each element in `PriceList` is a JSON string containing the product's attributes and pricing terms (On-Demand, Reserved).

---

### 1.4 `list-price-lists`

Lists available price list files for download. **Paginated.**

**Synopsis:**
```bash
aws pricing list-price-lists \
    --service-code <value> \
    --effective-date <value> \
    --currency-code <value> \
    [--region-code <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-code` | **Yes** | string | -- | Service code (e.g., `AmazonEC2`) |
| `--effective-date` | **Yes** | timestamp | -- | Date for price list. Format: `YYYY-MM-DD` |
| `--currency-code` | **Yes** | string | -- | Currency code: `USD`, `CNY` |
| `--region-code` | No | string | None | AWS region code (e.g., `us-east-1`) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "PriceLists": [
        {
            "PriceListArn": "string",
            "RegionCode": "string",
            "CurrencyCode": "string",
            "FileFormats": ["string"]
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `get-price-list-file-url`

Gets a URL to download a specific price list file.

**Synopsis:**
```bash
aws pricing get-price-list-file-url \
    --price-list-arn <value> \
    --file-format <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--price-list-arn` | **Yes** | string | -- | ARN of the price list |
| `--file-format` | **Yes** | string | -- | File format: `json` or `csv` |

**Output Schema:**
```json
{
    "Url": "string"
}
```
