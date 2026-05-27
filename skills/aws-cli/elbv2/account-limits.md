# Account Limits

### 9.1 `describe-account-limits`

Describes the current ELBv2 limits for your account. **Paginated operation.**

**Synopsis:**
```bash
aws elbv2 describe-account-limits \
    [--page-size <value>] \
    [--starting-token <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--page-size` | No | integer | -- | Number of items per API call |
| `--starting-token` | No | string | -- | Pagination token |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Limits": [
        {
            "Name": "string",
            "Max": "string"
        }
    ],
    "NextMarker": "string"
}
```

---
