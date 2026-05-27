# Constraints

### 6.1 `create-constraint`

Creates a constraint on a product within a portfolio.

**Synopsis:**
```bash
aws servicecatalog create-constraint \
    --portfolio-id <value> \
    --product-id <value> \
    --type <value> \
    --parameters <value> \
    --idempotency-token <value> \
    [--description <value>] \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--portfolio-id` | **Yes** | string | -- | Portfolio identifier |
| `--product-id` | **Yes** | string | -- | Product identifier |
| `--type` | **Yes** | string | -- | Constraint type: `LAUNCH`, `NOTIFICATION`, `STACKSET`, `TEMPLATE`, `RESOURCE_UPDATE` |
| `--parameters` | **Yes** | string | -- | Constraint parameters (JSON string, varies by type) |
| `--idempotency-token` | **Yes** | string | -- | Idempotency token |
| `--description` | No | string | None | Constraint description (max 2000 chars) |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{
    "ConstraintDetail": {
        "ConstraintId": "string",
        "Type": "LAUNCH|NOTIFICATION|STACKSET|TEMPLATE|RESOURCE_UPDATE",
        "Description": "string",
        "Owner": "string",
        "ProductId": "string",
        "PortfolioId": "string"
    },
    "ConstraintParameters": "string",
    "Status": "AVAILABLE|CREATING|FAILED"
}
```

---

### 6.2 `delete-constraint`

Deletes the specified constraint.

**Synopsis:**
```bash
aws servicecatalog delete-constraint \
    --id <value> \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Constraint identifier |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{}
```

---

### 6.3 `describe-constraint`

Gets information about the specified constraint.

**Synopsis:**
```bash
aws servicecatalog describe-constraint \
    --id <value> \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Constraint identifier |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{
    "ConstraintDetail": {
        "ConstraintId": "string",
        "Type": "LAUNCH|NOTIFICATION|STACKSET|TEMPLATE|RESOURCE_UPDATE",
        "Description": "string",
        "Owner": "string",
        "ProductId": "string",
        "PortfolioId": "string"
    },
    "ConstraintParameters": "string",
    "Status": "AVAILABLE|CREATING|FAILED"
}
```

---

### 6.4 `update-constraint`

Updates the specified constraint.

**Synopsis:**
```bash
aws servicecatalog update-constraint \
    --id <value> \
    [--description <value>] \
    [--parameters <value>] \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Constraint identifier |
| `--description` | No | string | None | Updated description |
| `--parameters` | No | string | None | Updated constraint parameters (JSON string) |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{
    "ConstraintDetail": {
        "ConstraintId": "string",
        "Type": "LAUNCH|NOTIFICATION|STACKSET|TEMPLATE|RESOURCE_UPDATE",
        "Description": "string",
        "Owner": "string",
        "ProductId": "string",
        "PortfolioId": "string"
    },
    "ConstraintParameters": "string",
    "Status": "AVAILABLE|CREATING|FAILED"
}
```

---

### 6.5 `list-constraints-for-portfolio`

Lists the constraints for the specified portfolio and product. **Paginated operation.**

**Synopsis:**
```bash
aws servicecatalog list-constraints-for-portfolio \
    --portfolio-id <value> \
    [--product-id <value>] \
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
| `--portfolio-id` | **Yes** | string | -- | Portfolio identifier |
| `--product-id` | No | string | None | Filter by product |
| `--accept-language` | No | string | None | Language code |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "ConstraintDetails": [
        {
            "ConstraintId": "string",
            "Type": "LAUNCH|NOTIFICATION|STACKSET|TEMPLATE|RESOURCE_UPDATE",
            "Description": "string",
            "Owner": "string",
            "ProductId": "string",
            "PortfolioId": "string"
        }
    ],
    "NextPageToken": "string"
}
```

---

### 6.6 `list-launch-paths`

Lists the paths to the specified product. A path shows how a user gets access to the product (through which portfolio). **Paginated operation.**

**Synopsis:**
```bash
aws servicecatalog list-launch-paths \
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
    "LaunchPathSummaries": [
        {
            "Id": "string",
            "ConstraintSummaries": [
                {
                    "Type": "string",
                    "Description": "string"
                }
            ],
            "Tags": [
                {
                    "Key": "string",
                    "Value": "string"
                }
            ],
            "Name": "string"
        }
    ],
    "NextPageToken": "string"
}
```
