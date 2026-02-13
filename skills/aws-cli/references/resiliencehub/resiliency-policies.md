# Resiliency Policies

### 6.1 `create-resiliency-policy`

Creates a resiliency policy with RTO/RPO targets for disruption types.

**Synopsis:**
```bash
aws resiliencehub create-resiliency-policy \
    --policy-name <value> \
    --policy <value> \
    --tier <value> \
    [--client-token <value>] \
    [--data-location-constraint <value>] \
    [--policy-description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-name` | **Yes** | string | -- | Policy name (2-60 chars, alphanumeric/hyphens/underscores) |
| `--policy` | **Yes** | map | -- | RTO/RPO targets by disruption type. Keys: `Software`, `Hardware`, `AZ`, `Region` |
| `--tier` | **Yes** | string | -- | `MissionCritical`, `Critical`, `Important`, `CoreServices`, `NonCritical`, `NotApplicable` |
| `--client-token` | No | string | Auto | Idempotency token (1-63 chars) |
| `--data-location-constraint` | No | string | None | `AnyLocation`, `SameContinent`, `SameCountry` |
| `--policy-description` | No | string | None | Description (0-500 chars) |
| `--tags` | No | map | None | Resource tags (1-50 tags) |

**Policy Structure:**
```
Software={rpoInSecs=integer,rtoInSecs=integer},Hardware={rpoInSecs=integer,rtoInSecs=integer},AZ={rpoInSecs=integer,rtoInSecs=integer},Region={rpoInSecs=integer,rtoInSecs=integer}
```

**Output Schema:**
```json
{
    "policy": {
        "creationTime": "timestamp",
        "dataLocationConstraint": "AnyLocation|SameContinent|SameCountry",
        "estimatedCostTier": "L1|L2|L3|L4",
        "policy": {
            "Software|Hardware|AZ|Region": {
                "rpoInSecs": "integer",
                "rtoInSecs": "integer"
            }
        },
        "policyArn": "string",
        "policyDescription": "string",
        "policyName": "string",
        "tags": {"string": "string"},
        "tier": "MissionCritical|Critical|Important|CoreServices|NonCritical|NotApplicable"
    }
}
```

---

### 6.2 `delete-resiliency-policy`

Deletes a resiliency policy.

**Synopsis:**
```bash
aws resiliencehub delete-resiliency-policy \
    --policy-arn <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-arn` | **Yes** | string | -- | Resiliency policy ARN |
| `--client-token` | No | string | Auto | Idempotency token (1-63 chars) |

**Output Schema:**
```json
{
    "policyArn": "string"
}
```

---

### 6.3 `describe-resiliency-policy`

Describes a resiliency policy.

**Synopsis:**
```bash
aws resiliencehub describe-resiliency-policy \
    --policy-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-arn` | **Yes** | string | -- | Resiliency policy ARN |

**Output Schema:**
```json
{
    "policy": {
        "creationTime": "timestamp",
        "dataLocationConstraint": "AnyLocation|SameContinent|SameCountry",
        "estimatedCostTier": "L1|L2|L3|L4",
        "policy": {
            "Software|Hardware|AZ|Region": {
                "rpoInSecs": "integer",
                "rtoInSecs": "integer"
            }
        },
        "policyArn": "string",
        "policyDescription": "string",
        "policyName": "string",
        "tags": {"string": "string"},
        "tier": "MissionCritical|Critical|Important|CoreServices|NonCritical|NotApplicable"
    }
}
```

---

### 6.4 `list-resiliency-policies`

Lists resiliency policies. **Paginated operation.**

**Synopsis:**
```bash
aws resiliencehub list-resiliency-policies \
    [--max-results <value>] \
    [--next-token <value>] \
    [--policy-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Max results per page (1-100) |
| `--next-token` | No | string | None | Pagination token |
| `--policy-name` | No | string | None | Filter by policy name |

**Output Schema:**
```json
{
    "resiliencyPolicies": [
        {
            "creationTime": "timestamp",
            "dataLocationConstraint": "AnyLocation|SameContinent|SameCountry",
            "estimatedCostTier": "L1|L2|L3|L4",
            "policy": {
                "Software|Hardware|AZ|Region": {
                    "rpoInSecs": "integer",
                    "rtoInSecs": "integer"
                }
            },
            "policyArn": "string",
            "policyDescription": "string",
            "policyName": "string",
            "tags": {"string": "string"},
            "tier": "MissionCritical|Critical|Important|CoreServices|NonCritical|NotApplicable"
        }
    ],
    "nextToken": "string"
}
```

---

### 6.5 `update-resiliency-policy`

Updates a resiliency policy.

**Synopsis:**
```bash
aws resiliencehub update-resiliency-policy \
    --policy-arn <value> \
    [--data-location-constraint <value>] \
    [--policy <value>] \
    [--policy-description <value>] \
    [--policy-name <value>] \
    [--tier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-arn` | **Yes** | string | -- | Resiliency policy ARN |
| `--data-location-constraint` | No | string | None | `AnyLocation`, `SameContinent`, `SameCountry` |
| `--policy` | No | map | None | Updated RTO/RPO targets by disruption type |
| `--policy-description` | No | string | None | Updated description (0-500 chars) |
| `--policy-name` | No | string | None | Updated name |
| `--tier` | No | string | None | Updated tier |

**Output Schema:**
```json
{
    "policy": {
        "creationTime": "timestamp",
        "dataLocationConstraint": "AnyLocation|SameContinent|SameCountry",
        "estimatedCostTier": "L1|L2|L3|L4",
        "policy": {
            "Software|Hardware|AZ|Region": {
                "rpoInSecs": "integer",
                "rtoInSecs": "integer"
            }
        },
        "policyArn": "string",
        "policyDescription": "string",
        "policyName": "string",
        "tags": {"string": "string"},
        "tier": "MissionCritical|Critical|Important|CoreServices|NonCritical|NotApplicable"
    }
}
```

---

### 6.6 `list-suggested-resiliency-policies`

Lists suggested resiliency policies. **Paginated operation.**

**Synopsis:**
```bash
aws resiliencehub list-suggested-resiliency-policies \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Max results per page (1-100) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "resiliencyPolicies": [
        {
            "creationTime": "timestamp",
            "dataLocationConstraint": "AnyLocation|SameContinent|SameCountry",
            "estimatedCostTier": "L1|L2|L3|L4",
            "policy": {
                "Software|Hardware|AZ|Region": {
                    "rpoInSecs": "integer",
                    "rtoInSecs": "integer"
                }
            },
            "policyArn": "string",
            "policyDescription": "string",
            "policyName": "string",
            "tags": {"string": "string"},
            "tier": "MissionCritical|Critical|Important|CoreServices|NonCritical|NotApplicable"
        }
    ],
    "nextToken": "string"
}
```
