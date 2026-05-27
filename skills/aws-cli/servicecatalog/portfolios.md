# Portfolios

### 1.1 `create-portfolio`

Creates a portfolio.

**Synopsis:**
```bash
aws servicecatalog create-portfolio \
    --display-name <value> \
    --provider-name <value> \
    [--description <value>] \
    [--tags <value>] \
    --idempotency-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--display-name` | **Yes** | string | -- | Name of the portfolio (1-100 chars) |
| `--provider-name` | **Yes** | string | -- | Name of the portfolio provider (1-50 chars) |
| `--description` | No | string | None | Description of the portfolio (max 2000 chars) |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--idempotency-token` | **Yes** | string | -- | Unique identifier for idempotent requests (auto-generated if using CLI) |

**Output Schema:**
```json
{
    "PortfolioDetail": {
        "Id": "string",
        "ARN": "string",
        "DisplayName": "string",
        "Description": "string",
        "CreatedTime": "timestamp",
        "ProviderName": "string"
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

### 1.2 `delete-portfolio`

Deletes the specified portfolio. You must first disassociate all products, constraints, and shared accounts.

**Synopsis:**
```bash
aws servicecatalog delete-portfolio \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Portfolio identifier |

**Output Schema:**
```json
{}
```

---

### 1.3 `describe-portfolio`

Gets information about the specified portfolio, including tags.

**Synopsis:**
```bash
aws servicecatalog describe-portfolio \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Portfolio identifier |

**Output Schema:**
```json
{
    "PortfolioDetail": {
        "Id": "string",
        "ARN": "string",
        "DisplayName": "string",
        "Description": "string",
        "CreatedTime": "timestamp",
        "ProviderName": "string"
    },
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

### 1.4 `update-portfolio`

Updates the specified portfolio.

**Synopsis:**
```bash
aws servicecatalog update-portfolio \
    --id <value> \
    [--display-name <value>] \
    [--description <value>] \
    [--provider-name <value>] \
    [--add-tags <value>] \
    [--remove-tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Portfolio identifier |
| `--display-name` | No | string | None | Updated display name |
| `--description` | No | string | None | Updated description |
| `--provider-name` | No | string | None | Updated provider name |
| `--add-tags` | No | list | None | Tags to add. Shorthand: `Key=string,Value=string ...` |
| `--remove-tags` | No | list(string) | None | Tag keys to remove |

**Output Schema:**
```json
{
    "PortfolioDetail": {
        "Id": "string",
        "ARN": "string",
        "DisplayName": "string",
        "Description": "string",
        "CreatedTime": "timestamp",
        "ProviderName": "string"
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

### 1.5 `list-portfolios`

Lists all portfolios in the catalog. **Paginated operation.**

**Synopsis:**
```bash
aws servicecatalog list-portfolios \
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
| `--accept-language` | No | string | None | Language code: `en`, `jp`, `zh` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items to return |

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

### 1.6 `list-accepted-portfolio-shares`

Lists all portfolios that have been shared with the calling account and accepted. **Paginated operation.**

**Synopsis:**
```bash
aws servicecatalog list-accepted-portfolio-shares \
    [--accept-language <value>] \
    [--portfolio-share-type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--accept-language` | No | string | None | Language code: `en`, `jp`, `zh` |
| `--portfolio-share-type` | No | string | None | Filter: `IMPORTED`, `AWS_SERVICECATALOG`, `AWS_ORGANIZATIONS` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items to return |

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

### 1.7 `accept-portfolio-share`

Accepts a portfolio share that has been offered.

**Synopsis:**
```bash
aws servicecatalog accept-portfolio-share \
    --portfolio-id <value> \
    [--accept-language <value>] \
    [--portfolio-share-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--portfolio-id` | **Yes** | string | -- | Portfolio identifier |
| `--accept-language` | No | string | None | Language code: `en`, `jp`, `zh` |
| `--portfolio-share-type` | No | string | None | Share type: `IMPORTED`, `AWS_SERVICECATALOG`, `AWS_ORGANIZATIONS` |

**Output Schema:**
```json
{}
```

---

### 1.8 `reject-portfolio-share`

Rejects a portfolio share that has been offered.

**Synopsis:**
```bash
aws servicecatalog reject-portfolio-share \
    --portfolio-id <value> \
    [--accept-language <value>] \
    [--portfolio-share-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--portfolio-id` | **Yes** | string | -- | Portfolio identifier |
| `--accept-language` | No | string | None | Language code: `en`, `jp`, `zh` |
| `--portfolio-share-type` | No | string | None | Share type: `IMPORTED`, `AWS_SERVICECATALOG`, `AWS_ORGANIZATIONS` |

**Output Schema:**
```json
{}
```

---

### 1.9 `create-portfolio-share`

Shares the specified portfolio with the specified account or organization node.

**Synopsis:**
```bash
aws servicecatalog create-portfolio-share \
    --portfolio-id <value> \
    [--account-id <value>] \
    [--organization-node <value>] \
    [--share-tag-options] \
    [--no-share-tag-options] \
    [--share-principals] \
    [--no-share-principals] \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--portfolio-id` | **Yes** | string | -- | Portfolio identifier |
| `--account-id` | No | string | None | AWS account ID to share with |
| `--organization-node` | No | structure | None | Organization node. Shorthand: `Type=ORGANIZATION\|ORGANIZATIONAL_UNIT\|ACCOUNT,Value=string` |
| `--share-tag-options` | No | boolean | false | Share tag options with the recipient |
| `--share-principals` | No | boolean | false | Share principals with the recipient |
| `--accept-language` | No | string | None | Language code: `en`, `jp`, `zh` |

**Output Schema:**
```json
{
    "PortfolioShareToken": "string"
}
```

---

### 1.10 `delete-portfolio-share`

Stops sharing the specified portfolio with the specified account or organization node.

**Synopsis:**
```bash
aws servicecatalog delete-portfolio-share \
    --portfolio-id <value> \
    [--account-id <value>] \
    [--organization-node <value>] \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--portfolio-id` | **Yes** | string | -- | Portfolio identifier |
| `--account-id` | No | string | None | AWS account ID to stop sharing with |
| `--organization-node` | No | structure | None | Organization node to stop sharing with |
| `--accept-language` | No | string | None | Language code: `en`, `jp`, `zh` |

**Output Schema:**
```json
{
    "PortfolioShareToken": "string"
}
```

---

### 1.11 `describe-portfolio-share-status`

Gets the status of the specified portfolio share operation.

**Synopsis:**
```bash
aws servicecatalog describe-portfolio-share-status \
    --portfolio-share-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--portfolio-share-token` | **Yes** | string | -- | Token returned by create/delete-portfolio-share |

**Output Schema:**
```json
{
    "PortfolioShareToken": "string",
    "PortfolioId": "string",
    "OrganizationNodeValue": "string",
    "Status": "NOT_STARTED|IN_PROGRESS|COMPLETED|COMPLETED_WITH_ERRORS|ERROR",
    "ShareDetails": {
        "SuccessfulShares": ["string"],
        "ShareErrors": [
            {
                "Accounts": ["string"],
                "Message": "string",
                "Error": "string"
            }
        ]
    }
}
```

---

### 1.12 `describe-portfolio-shares`

Returns a summary of each share for the specified portfolio. **Paginated operation.**

**Synopsis:**
```bash
aws servicecatalog describe-portfolio-shares \
    --portfolio-id <value> \
    --type <value> \
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
| `--type` | **Yes** | string | -- | Share type: `ACCOUNT`, `ORGANIZATION`, `ORGANIZATIONAL_UNIT`, `ORGANIZATION_MEMBER_ACCOUNT` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items to return |

**Output Schema:**
```json
{
    "NextPageToken": "string",
    "PortfolioShareDetails": [
        {
            "PrincipalId": "string",
            "Type": "ACCOUNT|ORGANIZATION|ORGANIZATIONAL_UNIT|ORGANIZATION_MEMBER_ACCOUNT",
            "Accepted": "boolean",
            "ShareTagOptions": "boolean",
            "SharePrincipals": "boolean"
        }
    ]
}
```

---

### 1.13 `list-portfolio-access`

Lists the account IDs that have access to the specified portfolio. **Paginated operation.**

**Synopsis:**
```bash
aws servicecatalog list-portfolio-access \
    --portfolio-id <value> \
    [--accept-language <value>] \
    [--organization-parent-id <value>] \
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
| `--accept-language` | No | string | None | Language code |
| `--organization-parent-id` | No | string | None | Organization parent ID for filtering |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items to return |

**Output Schema:**
```json
{
    "AccountIds": ["string"],
    "NextPageToken": "string"
}
```

---

### 1.14 `list-organization-portfolio-access`

Lists the organization nodes that have access to the specified portfolio. **Paginated operation.**

**Synopsis:**
```bash
aws servicecatalog list-organization-portfolio-access \
    --portfolio-id <value> \
    --organization-node-type <value> \
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
| `--organization-node-type` | **Yes** | string | -- | Node type: `ORGANIZATION`, `ORGANIZATIONAL_UNIT`, `ACCOUNT` |
| `--accept-language` | No | string | None | Language code |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items to return |

**Output Schema:**
```json
{
    "OrganizationNodes": [
        {
            "Type": "ORGANIZATION|ORGANIZATIONAL_UNIT|ACCOUNT",
            "Value": "string"
        }
    ],
    "NextPageToken": "string"
}
```

---

### 1.15 `update-portfolio-share`

Updates the specified portfolio share.

**Synopsis:**
```bash
aws servicecatalog update-portfolio-share \
    --portfolio-id <value> \
    [--account-id <value>] \
    [--organization-node <value>] \
    [--share-tag-options] \
    [--no-share-tag-options] \
    [--share-principals] \
    [--no-share-principals] \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--portfolio-id` | **Yes** | string | -- | Portfolio identifier |
| `--account-id` | No | string | None | AWS account ID |
| `--organization-node` | No | structure | None | Organization node |
| `--share-tag-options` | No | boolean | None | Enable sharing tag options |
| `--share-principals` | No | boolean | None | Enable sharing principals |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{
    "PortfolioShareToken": "string",
    "Status": "NOT_STARTED|IN_PROGRESS|COMPLETED|COMPLETED_WITH_ERRORS|ERROR"
}
```
