# Support Trusted Advisor

> **Important:** All `aws support` Trusted Advisor commands must use the **US East (N. Virginia)** region (`us-east-1`). Oregon and Ireland endpoints do not support Trusted Advisor operations.

### 4.1 `describe-trusted-advisor-checks`

Returns the list of all available Trusted Advisor checks, including name, ID, category, description, and metadata.

**Synopsis:**
```bash
aws support describe-trusted-advisor-checks \
    --language <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--language` | **Yes** | string | -- | Language code: `en`, `ja`, `zh`, `zh_TW`, `fr`, `de`, `id`, `it`, `ko`, `pt_BR`, `es` |

**Output Schema:**
```json
{
    "checks": [
        {
            "id": "string",
            "name": "string",
            "description": "string",
            "category": "string",
            "metadata": ["string"]
        }
    ]
}
```

---

### 4.2 `describe-trusted-advisor-check-result`

Returns the results of a Trusted Advisor check, including status, flagged resources, and resource counts.

**Synopsis:**
```bash
aws support describe-trusted-advisor-check-result \
    --check-id <value> \
    [--language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--check-id` | **Yes** | string | -- | The unique identifier for the Trusted Advisor check |
| `--language` | No | string | None | Language code: `en`, `ja`, `zh`, `zh_TW`, `fr`, `de`, `id`, `it`, `ko`, `pt_BR`, `es` |

**Output Schema:**
```json
{
    "result": {
        "checkId": "string",
        "timestamp": "string",
        "status": "ok|warning|error|not_available",
        "resourcesSummary": {
            "resourcesProcessed": "long",
            "resourcesFlagged": "long",
            "resourcesIgnored": "long",
            "resourcesSuppressed": "long"
        },
        "categorySpecificSummary": {
            "costOptimizing": {
                "estimatedMonthlySavings": "double",
                "estimatedPercentMonthlySavings": "double"
            }
        },
        "flaggedResources": [
            {
                "status": "string",
                "region": "string",
                "resourceId": "string",
                "isSuppressed": "boolean",
                "metadata": ["string"]
            }
        ]
    }
}
```

---

### 4.3 `describe-trusted-advisor-check-summaries`

Returns summaries for one or more Trusted Advisor checks.

**Synopsis:**
```bash
aws support describe-trusted-advisor-check-summaries \
    --check-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--check-ids` | **Yes** | list(string) | -- | List of Trusted Advisor check IDs |

**Output Schema:**
```json
{
    "summaries": [
        {
            "checkId": "string",
            "timestamp": "string",
            "status": "ok|warning|error|not_available",
            "hasFlaggedResources": "boolean",
            "resourcesSummary": {
                "resourcesProcessed": "long",
                "resourcesFlagged": "long",
                "resourcesIgnored": "long",
                "resourcesSuppressed": "long"
            },
            "categorySpecificSummary": {
                "costOptimizing": {
                    "estimatedMonthlySavings": "double",
                    "estimatedPercentMonthlySavings": "double"
                }
            }
        }
    ]
}
```

---

### 4.4 `refresh-trusted-advisor-check`

Requests a refresh of a Trusted Advisor check. Some checks refresh automatically; attempting to refresh those causes an `InvalidParameterValue` error.

**Synopsis:**
```bash
aws support refresh-trusted-advisor-check \
    --check-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--check-id` | **Yes** | string | -- | The unique identifier for the Trusted Advisor check |

**Output Schema:**
```json
{
    "status": {
        "checkId": "string",
        "status": "none|enqueued|processing|success|abandoned",
        "millisUntilNextRefreshable": "long"
    }
}
```

---

### 4.5 `describe-trusted-advisor-check-refresh-statuses`

Returns the refresh statuses of Trusted Advisor checks.

**Synopsis:**
```bash
aws support describe-trusted-advisor-check-refresh-statuses \
    --check-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--check-ids` | **Yes** | list(string) | -- | List of Trusted Advisor check IDs |

**Output Schema:**
```json
{
    "statuses": [
        {
            "checkId": "string",
            "status": "none|enqueued|processing|success|abandoned",
            "millisUntilNextRefreshable": "long"
        }
    ]
}
```
