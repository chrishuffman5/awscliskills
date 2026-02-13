# Cost Categories

### 2.1 `create-cost-category-definition`

Creates a new cost category with categorization rules.

**Synopsis:**
```bash
aws ce create-cost-category-definition \
    --name <value> \
    --rule-version <value> \
    --rules <value> \
    [--effective-start <value>] \
    [--default-value <value>] \
    [--split-charge-rules <value>] \
    [--resource-tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Unique cost category name (1-50 chars) |
| `--rule-version` | **Yes** | string | -- | `CostCategoryExpression.v1` |
| `--rules` | **Yes** | list | -- | Categorization rules (1-500 rules). Each rule has a `Value`, `Rule` expression, and optional `Type` |
| `--effective-start` | No | string | Current month | Effective start date (first day of month, ISO 8601) |
| `--default-value` | No | string | None | Default value for uncategorized costs (1-50 chars) |
| `--split-charge-rules` | No | list | None | Rules to split charges between cost category values (1-10 rules) |
| `--resource-tags` | No | list | None | Tags for IAM access control (max 200) |

**Rule Structure:**
```json
{
    "Value": "string",
    "Rule": {
        "Dimensions": {
            "Key": "SERVICE|LINKED_ACCOUNT|REGION|...",
            "Values": ["string"],
            "MatchOptions": ["EQUALS"]
        }
    },
    "Type": "REGULAR|INHERITED_VALUE",
    "InheritedValue": {
        "DimensionName": "LINKED_ACCOUNT_NAME|TAG",
        "DimensionKey": "string"
    }
}
```

**Split Charge Rule Structure:**
```json
{
    "Source": "string",
    "Targets": ["string"],
    "Method": "FIXED|PROPORTIONAL|EVEN",
    "Parameters": [
        {
            "Type": "ALLOCATION_PERCENTAGES",
            "Values": ["string"]
        }
    ]
}
```

**Output Schema:**
```json
{
    "CostCategoryArn": "string",
    "EffectiveStart": "string"
}
```

---

### 2.2 `delete-cost-category-definition`

Deletes a cost category.

**Synopsis:**
```bash
aws ce delete-cost-category-definition \
    --cost-category-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cost-category-arn` | **Yes** | string | -- | ARN of the cost category to delete |

**Output Schema:**
```json
{
    "CostCategoryArn": "string",
    "EffectiveEnd": "string"
}
```

---

### 2.3 `describe-cost-category-definition`

Returns the definition of a cost category.

**Synopsis:**
```bash
aws ce describe-cost-category-definition \
    --cost-category-arn <value> \
    [--effective-on <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cost-category-arn` | **Yes** | string | -- | ARN of the cost category |
| `--effective-on` | No | string | None | Date to retrieve the effective definition for |

**Output Schema:**
```json
{
    "CostCategory": {
        "CostCategoryArn": "string",
        "EffectiveStart": "string",
        "EffectiveEnd": "string",
        "Name": "string",
        "RuleVersion": "CostCategoryExpression.v1",
        "Rules": [
            {
                "Value": "string",
                "Rule": {},
                "InheritedValue": {
                    "DimensionName": "LINKED_ACCOUNT_NAME|TAG",
                    "DimensionKey": "string"
                },
                "Type": "REGULAR|INHERITED_VALUE"
            }
        ],
        "SplitChargeRules": [
            {
                "Source": "string",
                "Targets": ["string"],
                "Method": "FIXED|PROPORTIONAL|EVEN",
                "Parameters": []
            }
        ],
        "ProcessingStatus": [
            {
                "Component": "COST_EXPLORER",
                "Status": "PROCESSING|APPLIED"
            }
        ],
        "DefaultValue": "string"
    }
}
```

---

### 2.4 `update-cost-category-definition`

Updates an existing cost category definition.

**Synopsis:**
```bash
aws ce update-cost-category-definition \
    --cost-category-arn <value> \
    --rule-version <value> \
    --rules <value> \
    [--effective-start <value>] \
    [--default-value <value>] \
    [--split-charge-rules <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cost-category-arn` | **Yes** | string | -- | ARN of the cost category to update |
| `--rule-version` | **Yes** | string | -- | `CostCategoryExpression.v1` |
| `--rules` | **Yes** | list | -- | Updated categorization rules (1-500) |
| `--effective-start` | No | string | Current month | Effective start date |
| `--default-value` | No | string | None | Default value for uncategorized costs |
| `--split-charge-rules` | No | list | None | Split charge rules (1-10) |

**Output Schema:**
```json
{
    "CostCategoryArn": "string",
    "EffectiveStart": "string"
}
```

---

### 2.5 `get-cost-categories`

Retrieves cost category names and values for a time period.

**Synopsis:**
```bash
aws ce get-cost-categories \
    --time-period <value> \
    [--search-string <value>] \
    [--cost-category-name <value>] \
    [--filter <value>] \
    [--sort-by <value>] \
    [--billing-view-arn <value>] \
    [--max-results <value>] \
    [--next-page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--time-period` | **Yes** | structure | -- | Start/end dates for retrieving cost categories |
| `--search-string` | No | string | None | String to search within cost category values |
| `--cost-category-name` | No | string | None | Unique name of the cost category |
| `--filter` | No | structure | None | Expression filter |
| `--sort-by` | No | list | None | Sort specification |
| `--billing-view-arn` | No | string | None | ARN of billing view |
| `--max-results` | No | integer | 1000 | Max results |
| `--next-page-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "NextPageToken": "string",
    "CostCategoryNames": ["string"],
    "CostCategoryValues": ["string"],
    "ReturnSize": "integer",
    "TotalSize": "integer"
}
```

---

### 2.6 `list-cost-category-definitions`

Returns a list of cost category definitions in the account. **Paginated.**

**Synopsis:**
```bash
aws ce list-cost-category-definitions \
    [--effective-on <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--effective-on` | No | string | None | Date to filter by effective definitions |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CostCategoryReferences": [
        {
            "CostCategoryArn": "string",
            "Name": "string",
            "EffectiveStart": "string",
            "EffectiveEnd": "string",
            "NumberOfRules": "integer",
            "ProcessingStatus": [
                {
                    "Component": "COST_EXPLORER",
                    "Status": "PROCESSING|APPLIED"
                }
            ],
            "Values": ["string"],
            "DefaultValue": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.7 `list-cost-category-resource-associations`

Lists resource associations for a cost category. **Paginated.**

**Synopsis:**
```bash
aws ce list-cost-category-resource-associations \
    --cost-category-arn <value> \
    [--cost-category-value <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cost-category-arn` | **Yes** | string | -- | ARN of the cost category |
| `--cost-category-value` | No | string | None | Filter by specific cost category value |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ResourceAssociations": [
        {
            "ResourceId": "string",
            "CostCategoryValue": "string"
        }
    ],
    "NextToken": "string"
}
```
