# Exports & Imports

### 9.1 `list-exports`

Lists all exported output values in the account and region. **Paginated operation.**

**Synopsis:**
```bash
aws cloudformation list-exports \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "Exports": [
        {
            "ExportingStackId": "string",
            "Name": "string",
            "Value": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.2 `list-imports`

Lists all stacks that import the specified exported output value. **Paginated operation.**

**Synopsis:**
```bash
aws cloudformation list-imports \
    --export-name <value> \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--export-name` | **Yes** | string | -- | The name of the exported value |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "Imports": ["string"],
    "NextToken": "string"
}
```

---

### 9.3 `describe-account-limits`

Retrieves your account's CloudFormation limits, such as the maximum number of stacks. **Paginated operation.**

**Synopsis:**
```bash
aws cloudformation describe-account-limits \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "AccountLimits": [
        {
            "Name": "string",
            "Value": "integer"
        }
    ],
    "NextToken": "string"
}
```
