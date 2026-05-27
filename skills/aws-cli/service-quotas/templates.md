# Templates

Quota templates allow you to define quota values that are automatically applied to new accounts created in your AWS Organization.

### 3.1 `associate-service-quota-template`

Associates your quota request template with your organization. When new member accounts are created, the template automatically requests quota increases.

**Synopsis:**
```bash
aws service-quotas associate-service-quota-template \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

This command takes no service-specific parameters.

**Output Schema:**
```json
{}
```

---

### 3.2 `disassociate-service-quota-template`

Disassociates the quota request template from your organization.

**Synopsis:**
```bash
aws service-quotas disassociate-service-quota-template \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

This command takes no service-specific parameters.

**Output Schema:**
```json
{}
```

---

### 3.3 `get-association-for-service-quota-template`

Gets the association status for the quota request template.

**Synopsis:**
```bash
aws service-quotas get-association-for-service-quota-template \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

This command takes no service-specific parameters.

**Output Schema:**
```json
{
    "ServiceQuotaTemplateAssociationStatus": "ASSOCIATED|DISASSOCIATED"
}
```

---

### 3.4 `put-service-quota-increase-request-into-template`

Adds a quota increase request to the quota request template.

**Synopsis:**
```bash
aws service-quotas put-service-quota-increase-request-into-template \
    --quota-code <value> \
    --service-code <value> \
    --desired-value <value> \
    --aws-region <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--quota-code` | **Yes** | string | -- | Quota code (e.g., `L-1216C47A`) |
| `--service-code` | **Yes** | string | -- | Service code (e.g., `ec2`) |
| `--desired-value` | **Yes** | double | -- | Desired quota value |
| `--aws-region` | **Yes** | string | -- | AWS Region for the template entry |

**Output Schema:**
```json
{
    "ServiceQuotaIncreaseRequestInTemplate": {
        "ServiceCode": "string",
        "ServiceName": "string",
        "QuotaCode": "string",
        "QuotaName": "string",
        "DesiredValue": "double",
        "AwsRegion": "string",
        "Unit": "string",
        "GlobalQuota": "boolean"
    }
}
```

---

### 3.5 `get-service-quota-increase-request-from-template`

Gets information about a specific quota increase request in the template.

**Synopsis:**
```bash
aws service-quotas get-service-quota-increase-request-from-template \
    --service-code <value> \
    --quota-code <value> \
    --aws-region <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-code` | **Yes** | string | -- | Service code |
| `--quota-code` | **Yes** | string | -- | Quota code |
| `--aws-region` | **Yes** | string | -- | AWS Region |

**Output Schema:**
```json
{
    "ServiceQuotaIncreaseRequestInTemplate": {
        "ServiceCode": "string",
        "ServiceName": "string",
        "QuotaCode": "string",
        "QuotaName": "string",
        "DesiredValue": "double",
        "AwsRegion": "string",
        "Unit": "string",
        "GlobalQuota": "boolean"
    }
}
```

---

### 3.6 `list-service-quota-increase-requests-in-template`

Lists the quota increase requests in the specified quota request template. **Paginated operation.**

**Synopsis:**
```bash
aws service-quotas list-service-quota-increase-requests-in-template \
    [--service-code <value>] \
    [--aws-region <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-code` | No | string | -- | Filter by service code |
| `--aws-region` | No | string | -- | Filter by AWS Region |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ServiceQuotaIncreaseRequestInTemplateList": [
        {
            "ServiceCode": "string",
            "ServiceName": "string",
            "QuotaCode": "string",
            "QuotaName": "string",
            "DesiredValue": "double",
            "AwsRegion": "string",
            "Unit": "string",
            "GlobalQuota": "boolean"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.7 `delete-service-quota-increase-request-from-template`

Removes a quota increase request from the quota request template.

**Synopsis:**
```bash
aws service-quotas delete-service-quota-increase-request-from-template \
    --service-code <value> \
    --quota-code <value> \
    --aws-region <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-code` | **Yes** | string | -- | Service code |
| `--quota-code` | **Yes** | string | -- | Quota code |
| `--aws-region` | **Yes** | string | -- | AWS Region |

**Output Schema:**
```json
{}
```
