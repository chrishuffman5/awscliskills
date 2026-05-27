# Account

### 12.1 `get-account-settings`

Returns Lambda account-level settings and resource limits.

**Synopsis:**
```bash
aws lambda get-account-settings \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "AccountLimit": {
        "TotalCodeSize": "long",
        "CodeSizeUnzipped": "long",
        "CodeSizeZipped": "long",
        "ConcurrentExecutions": "integer",
        "UnreservedConcurrentExecutions": "integer"
    },
    "AccountUsage": {
        "TotalCodeSize": "long",
        "FunctionCount": "long"
    }
}
```

---
