# Principals

### 8.1 `associate-principal-with-portfolio`

Associates the specified principal ARN with the specified portfolio.

**Synopsis:**
```bash
aws servicecatalog associate-principal-with-portfolio \
    --portfolio-id <value> \
    --principal-arn <value> \
    --principal-type <value> \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--portfolio-id` | **Yes** | string | -- | Portfolio identifier |
| `--principal-arn` | **Yes** | string | -- | IAM principal ARN (user, group, role, or organization) |
| `--principal-type` | **Yes** | string | -- | Principal type: `IAM` or `IAM_PATTERN` |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{}
```

---

### 8.2 `disassociate-principal-from-portfolio`

Disassociates a previously associated principal ARN from a specified portfolio.

**Synopsis:**
```bash
aws servicecatalog disassociate-principal-from-portfolio \
    --portfolio-id <value> \
    --principal-arn <value> \
    [--principal-type <value>] \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--portfolio-id` | **Yes** | string | -- | Portfolio identifier |
| `--principal-arn` | **Yes** | string | -- | IAM principal ARN |
| `--principal-type` | No | string | `IAM` | Principal type: `IAM` or `IAM_PATTERN` |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{}
```

---

### 8.3 `list-principals-for-portfolio`

Lists all principal ARNs associated with the specified portfolio. **Paginated operation.**

**Synopsis:**
```bash
aws servicecatalog list-principals-for-portfolio \
    --portfolio-id <value> \
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
| `--accept-language` | No | string | None | Language code |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "Principals": [
        {
            "PrincipalARN": "string",
            "PrincipalType": "IAM|IAM_PATTERN"
        }
    ],
    "NextPageToken": "string"
}
```
