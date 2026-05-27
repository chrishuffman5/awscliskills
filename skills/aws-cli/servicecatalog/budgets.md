# Budgets

### 10.1 `associate-budget-with-resource`

Associates the specified budget with the specified resource (portfolio or product).

**Synopsis:**
```bash
aws servicecatalog associate-budget-with-resource \
    --budget-name <value> \
    --resource-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--budget-name` | **Yes** | string | -- | Name of the AWS Budgets budget |
| `--resource-id` | **Yes** | string | -- | Resource identifier (portfolio or product ID) |

**Output Schema:**
```json
{}
```

---

### 10.2 `disassociate-budget-from-resource`

Disassociates the specified budget from the specified resource.

**Synopsis:**
```bash
aws servicecatalog disassociate-budget-from-resource \
    --budget-name <value> \
    --resource-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--budget-name` | **Yes** | string | -- | Name of the budget |
| `--resource-id` | **Yes** | string | -- | Resource identifier |

**Output Schema:**
```json
{}
```

---

### 10.3 `list-budgets-for-resource`

Lists all budgets associated with the specified resource. **Paginated operation.**

**Synopsis:**
```bash
aws servicecatalog list-budgets-for-resource \
    --resource-id <value> \
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
| `--resource-id` | **Yes** | string | -- | Resource identifier |
| `--accept-language` | No | string | None | Language code |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "Budgets": [
        {
            "BudgetName": "string"
        }
    ],
    "NextPageToken": "string"
}
```
