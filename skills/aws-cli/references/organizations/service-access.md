# Service Access

### 7.1 `enable-aws-service-access`

Enables integration of an AWS service with AWS Organizations. This allows the service to perform operations in your organization member accounts.

**Synopsis:**
```bash
aws organizations enable-aws-service-access \
    --service-principal <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-principal` | **Yes** | string | -- | Service principal to enable (e.g., `config.amazonaws.com`, `cloudtrail.amazonaws.com`, `guardduty.amazonaws.com`, `sso.amazonaws.com`) |

**Output Schema:**
```json
{}
```

---

### 7.2 `disable-aws-service-access`

Disables integration of an AWS service with AWS Organizations.

**Synopsis:**
```bash
aws organizations disable-aws-service-access \
    --service-principal <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-principal` | **Yes** | string | -- | Service principal to disable |

**Output Schema:**
```json
{}
```

---

### 7.3 `list-aws-service-access-for-organization`

Returns a list of the AWS services enabled for integration with your organization. **Paginated operation.**

**Synopsis:**
```bash
aws organizations list-aws-service-access-for-organization \
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
    "EnabledServicePrincipals": [
        {
            "ServicePrincipal": "string",
            "DateEnabled": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
