# Code Security

### 7.1 `create-code-security-integration`

Creates a code security integration with a third-party source code provider.

**Synopsis:**
```bash
aws inspector2 create-code-security-integration \
    --name <value> \
    --type <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Integration name (1-60 chars) |
| `--type` | **Yes** | string | -- | Provider type: `GITHUB`, `GITLAB_SELF_MANAGED` |
| `--tags` | No | map | None | Tags. Shorthand: `KeyName1=string,KeyName2=string` |

**Output Schema:**
```json
{
    "integrationArn": "string",
    "authorizationUrl": "string",
    "status": "PENDING|IN_PROGRESS|ACTIVE|INACTIVE|DISABLING"
}
```

---

### 7.2 `delete-code-security-integration`

Deletes a code security integration.

**Synopsis:**
```bash
aws inspector2 delete-code-security-integration \
    --integration-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--integration-arn` | **Yes** | string | -- | ARN of the integration to delete |

**Output Schema:** Empty on success.

---

### 7.3 `update-code-security-integration`

Updates a code security integration.

**Synopsis:**
```bash
aws inspector2 update-code-security-integration \
    --integration-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--integration-arn` | **Yes** | string | -- | ARN of the integration to update |

**Output Schema:**
```json
{
    "integrationArn": "string",
    "authorizationUrl": "string",
    "status": "PENDING|IN_PROGRESS|ACTIVE|INACTIVE|DISABLING"
}
```

---

### 7.4 `get-code-security-integration`

Gets details for a code security integration.

**Synopsis:**
```bash
aws inspector2 get-code-security-integration \
    --integration-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--integration-arn` | **Yes** | string | -- | ARN of the integration |

**Output Schema:**
```json
{
    "integrationArn": "string",
    "name": "string",
    "type": "GITHUB|GITLAB_SELF_MANAGED",
    "status": "PENDING|IN_PROGRESS|ACTIVE|INACTIVE|DISABLING",
    "statusReason": "string",
    "createdOn": "timestamp",
    "lastUpdateOn": "timestamp",
    "tags": {"key": "value"},
    "authorizationUrl": "string"
}
```

---

### 7.5 `list-code-security-integrations`

Lists all code security integrations. **Paginated.**

**Synopsis:**
```bash
aws inspector2 list-code-security-integrations \
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
    "integrations": [
        {
            "integrationArn": "string",
            "name": "string",
            "type": "GITHUB|GITLAB_SELF_MANAGED",
            "status": "PENDING|IN_PROGRESS|ACTIVE|INACTIVE|DISABLING",
            "statusReason": "string",
            "createdOn": "timestamp",
            "lastUpdateOn": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 7.6 `create-code-security-scan-configuration`

Creates a scan configuration for code security.

**Synopsis:**
```bash
aws inspector2 create-code-security-scan-configuration \
    --configuration <value> \
    [--name <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration` | **Yes** | structure | -- | Scan configuration (continuous integration settings, rule sets) |
| `--name` | No | string | None | Configuration name |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "codeSecurityScanConfigurationArn": "string"
}
```

---

### 7.7 `delete-code-security-scan-configuration`

Deletes a code security scan configuration.

**Synopsis:**
```bash
aws inspector2 delete-code-security-scan-configuration \
    --code-security-scan-configuration-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--code-security-scan-configuration-arn` | **Yes** | string | -- | ARN of the configuration to delete |

**Output Schema:** Empty on success.

---

### 7.8 `update-code-security-scan-configuration`

Updates a code security scan configuration.

**Synopsis:**
```bash
aws inspector2 update-code-security-scan-configuration \
    --code-security-scan-configuration-arn <value> \
    --configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--code-security-scan-configuration-arn` | **Yes** | string | -- | ARN of the configuration to update |
| `--configuration` | **Yes** | structure | -- | Updated scan configuration |

**Output Schema:**
```json
{
    "codeSecurityScanConfigurationArn": "string"
}
```

---

### 7.9 `get-code-security-scan-configuration`

Gets a code security scan configuration.

**Synopsis:**
```bash
aws inspector2 get-code-security-scan-configuration \
    --code-security-scan-configuration-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--code-security-scan-configuration-arn` | **Yes** | string | -- | ARN of the configuration |

**Output Schema:**
```json
{
    "codeSecurityScanConfigurationArn": "string",
    "name": "string",
    "configuration": {
        "continuousIntegrationScanConfiguration": {
            "supportedRuleSets": ["string"]
        },
        "periodicScanConfiguration": {
            "frequency": "WEEKLY|MONTHLY|NEVER",
            "supportedRuleSets": ["string"]
        },
        "ruleSetCategories": ["SAST|IaC|SCA|SECRETS"]
    },
    "tags": {"key": "value"},
    "createdAt": "timestamp",
    "updatedAt": "timestamp",
    "ownerAccountId": "string",
    "level": "ORGANIZATION|ACCOUNT",
    "scopeSettings": {
        "projectSelectionScope": "ALL",
        "projectNames": ["string"]
    }
}
```

---

### 7.10 `list-code-security-scan-configurations`

Lists code security scan configurations. **Paginated.**

**Synopsis:**
```bash
aws inspector2 list-code-security-scan-configurations \
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
    "configurations": [
        {
            "codeSecurityScanConfigurationArn": "string",
            "name": "string",
            "ownerAccountId": "string",
            "level": "ORGANIZATION|ACCOUNT"
        }
    ],
    "nextToken": "string"
}
```

---

### 7.11 `list-code-security-scan-configuration-associations`

Lists associations between scan configurations and integrations. **Paginated.**

**Synopsis:**
```bash
aws inspector2 list-code-security-scan-configuration-associations \
    --filter <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter` | **Yes** | structure | -- | Filter by scan configuration ARN or integration ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "associations": [
        {
            "codeSecurityScanConfigurationArn": "string",
            "integrationArn": "string",
            "resourceId": "string",
            "status": "ASSOCIATING|ASSOCIATED|DISSOCIATING|DISSOCIATED|FAILED",
            "statusReason": "string",
            "lastUpdatedOn": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 7.12 `batch-associate-code-security-scan-configuration`

Associates a scan configuration with multiple integrations/repositories.

**Synopsis:**
```bash
aws inspector2 batch-associate-code-security-scan-configuration \
    --code-security-scan-configuration-arn <value> \
    --entries <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--code-security-scan-configuration-arn` | **Yes** | string | -- | ARN of the scan configuration |
| `--entries` | **Yes** | list | -- | Entries with integration ARN and resource ID |

**Output Schema:**
```json
{
    "successfulAssociations": [
        {
            "codeSecurityScanConfigurationArn": "string",
            "integrationArn": "string",
            "resourceId": "string",
            "status": "ASSOCIATING|ASSOCIATED"
        }
    ],
    "failedAssociations": [
        {
            "codeSecurityScanConfigurationArn": "string",
            "integrationArn": "string",
            "resourceId": "string",
            "statusCode": "INTERNAL_ERROR|ACCESS_DENIED|RESOURCE_NOT_FOUND",
            "statusMessage": "string"
        }
    ]
}
```

---

### 7.13 `batch-disassociate-code-security-scan-configuration`

Disassociates a scan configuration from multiple integrations/repositories.

**Synopsis:**
```bash
aws inspector2 batch-disassociate-code-security-scan-configuration \
    --code-security-scan-configuration-arn <value> \
    --entries <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--code-security-scan-configuration-arn` | **Yes** | string | -- | ARN of the scan configuration |
| `--entries` | **Yes** | list | -- | Entries with integration ARN and resource ID |

**Output Schema:**
```json
{
    "successfulDisassociations": [
        {
            "codeSecurityScanConfigurationArn": "string",
            "integrationArn": "string",
            "resourceId": "string",
            "status": "DISSOCIATING|DISSOCIATED"
        }
    ],
    "failedDisassociations": [
        {
            "codeSecurityScanConfigurationArn": "string",
            "integrationArn": "string",
            "resourceId": "string",
            "statusCode": "INTERNAL_ERROR|ACCESS_DENIED|RESOURCE_NOT_FOUND",
            "statusMessage": "string"
        }
    ]
}
```

---

### 7.14 `start-code-security-scan`

Starts an on-demand code security scan.

**Synopsis:**
```bash
aws inspector2 start-code-security-scan \
    --integration-arn <value> \
    --resource-id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--integration-arn` | **Yes** | string | -- | ARN of the code security integration |
| `--resource-id` | **Yes** | structure | -- | Resource identifier (project name) |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "scanId": "string",
    "status": "IN_PROGRESS|COMPLETED|FAILED"
}
```

---

### 7.15 `get-code-security-scan`

Gets the status of a code security scan.

**Synopsis:**
```bash
aws inspector2 get-code-security-scan \
    --integration-arn <value> \
    --resource-id <value> \
    --scan-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--integration-arn` | **Yes** | string | -- | ARN of the code security integration |
| `--resource-id` | **Yes** | structure | -- | Resource identifier |
| `--scan-id` | **Yes** | string | -- | ID of the scan |

**Output Schema:**
```json
{
    "scanId": "string",
    "integrationArn": "string",
    "resourceId": {
        "projectName": "string"
    },
    "status": "IN_PROGRESS|COMPLETED|FAILED",
    "createdAt": "timestamp",
    "updatedAt": "timestamp",
    "lastCommitId": "string",
    "findingCounts": {
        "critical": "long",
        "high": "long",
        "medium": "long",
        "low": "long"
    }
}
```
