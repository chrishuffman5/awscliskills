# Continuous Deployment

### 9.1 `create-continuous-deployment-policy`

Creates a continuous deployment policy for testing changes with a staging distribution before promoting to production.

**Synopsis:**
```bash
aws cloudfront create-continuous-deployment-policy \
    --continuous-deployment-policy-config <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--continuous-deployment-policy-config` | **Yes** | structure | Continuous deployment policy configuration |

**Config structure:**

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `StagingDistributionDnsNames` | **Yes** | structure | Staging distribution DNS names (`Quantity`, `Items`) |
| `Enabled` | **Yes** | boolean | Whether the policy is enabled |
| `TrafficConfig` | No | structure | Traffic routing configuration |

**TrafficConfig:**

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `Type` | **Yes** | string | `SingleWeight` or `SingleHeader` |
| `SingleWeightConfig.Weight` | Conditional | float | Traffic percentage (0 to 0.15). Required if Type is `SingleWeight` |
| `SingleWeightConfig.SessionStickinessConfig` | No | structure | `IdleTTL` (300-3600s), `MaximumTTL` (300-3600s) |
| `SingleHeaderConfig.Header` | Conditional | string | Header name (must start with `aws-cf-cd-`). Required if Type is `SingleHeader` |
| `SingleHeaderConfig.Value` | Conditional | string | Header value |

**Output Schema:**
```json
{
    "ContinuousDeploymentPolicy": {
        "Id": "string",
        "LastModifiedTime": "timestamp",
        "ContinuousDeploymentPolicyConfig": { "..." }
    },
    "Location": "string",
    "ETag": "string"
}
```

---

### 9.2 `get-continuous-deployment-policy`

Gets a continuous deployment policy.

**Synopsis:**
```bash
aws cloudfront get-continuous-deployment-policy \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Policy ID |

**Output Schema:**
```json
{
    "ContinuousDeploymentPolicy": {
        "Id": "string",
        "LastModifiedTime": "timestamp",
        "ContinuousDeploymentPolicyConfig": { "..." }
    },
    "ETag": "string"
}
```

---

### 9.3 `get-continuous-deployment-policy-config`

Gets the configuration for a continuous deployment policy.

**Synopsis:**
```bash
aws cloudfront get-continuous-deployment-policy-config \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Policy ID |

**Output Schema:**
```json
{
    "ContinuousDeploymentPolicyConfig": { "..." },
    "ETag": "string"
}
```

---

### 9.4 `list-continuous-deployment-policies`

Lists continuous deployment policies.

**Synopsis:**
```bash
aws cloudfront list-continuous-deployment-policies \
    [--marker <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--marker` | No | string | None | Pagination marker |
| `--max-items` | No | string | None | Maximum items to return |

**Output Schema:**
```json
{
    "ContinuousDeploymentPolicyList": {
        "MaxItems": "integer",
        "Quantity": "integer",
        "NextMarker": "string",
        "Items": [
            {
                "ContinuousDeploymentPolicy": {
                    "Id": "string",
                    "LastModifiedTime": "timestamp",
                    "ContinuousDeploymentPolicyConfig": { "..." }
                }
            }
        ]
    }
}
```

---

### 9.5 `update-continuous-deployment-policy`

Updates a continuous deployment policy.

**Synopsis:**
```bash
aws cloudfront update-continuous-deployment-policy \
    --id <value> \
    --continuous-deployment-policy-config <value> \
    --if-match <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Policy ID |
| `--continuous-deployment-policy-config` | **Yes** | structure | Updated configuration |
| `--if-match` | **Yes** | string | ETag from `get-continuous-deployment-policy` |

**Output Schema:** Same as `get-continuous-deployment-policy`.

---

### 9.6 `delete-continuous-deployment-policy`

Deletes a continuous deployment policy.

**Synopsis:**
```bash
aws cloudfront delete-continuous-deployment-policy \
    --id <value> \
    --if-match <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Policy ID |
| `--if-match` | **Yes** | string | ETag from `get-continuous-deployment-policy` |

**Output:** None.

---

### 9.7 `update-distribution-with-staging-config`

Copies the staging distribution's configuration to the primary distribution, effectively promoting the staging config to production.

**Synopsis:**
```bash
aws cloudfront update-distribution-with-staging-config \
    --id <value> \
    [--staging-distribution-id <value>] \
    [--if-match <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Primary distribution ID |
| `--staging-distribution-id` | No | string | Staging distribution ID |
| `--if-match` | No | string | ETag for optimistic locking |

**Output Schema:**
```json
{
    "Distribution": { "..." },
    "ETag": "string"
}
```

---
