# Recovery Groups

Commands for managing Route 53 ARC recovery groups via `aws route53-recovery-readiness`.

### 6.1 `create-recovery-group`

Creates a recovery group. A recovery group represents an application and contains cells.

**Synopsis:**
```bash
aws route53-recovery-readiness create-recovery-group \
    --recovery-group-name <value> \
    [--cells <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--recovery-group-name` | **Yes** | string | -- | Name of the recovery group (max 64 chars, alphanumeric + underscores) |
| `--cells` | No | list(string) | None | List of cell ARNs to include |
| `--tags` | No | map | None | Tags as key-value pairs |

**Output Schema:**
```json
{
    "RecoveryGroupArn": "string",
    "RecoveryGroupName": "string",
    "Cells": ["string"],
    "Tags": {
        "string": "string"
    }
}
```

---

### 6.2 `get-recovery-group`

Gets details about a recovery group.

**Synopsis:**
```bash
aws route53-recovery-readiness get-recovery-group \
    --recovery-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--recovery-group-name` | **Yes** | string | -- | Name of the recovery group |

**Output Schema:**
```json
{
    "RecoveryGroupArn": "string",
    "RecoveryGroupName": "string",
    "Cells": ["string"],
    "Tags": {
        "string": "string"
    }
}
```

---

### 6.3 `update-recovery-group`

Updates a recovery group's cells.

**Synopsis:**
```bash
aws route53-recovery-readiness update-recovery-group \
    --recovery-group-name <value> \
    --cells <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--recovery-group-name` | **Yes** | string | -- | Name of the recovery group |
| `--cells` | **Yes** | list(string) | -- | Updated list of cell ARNs |

**Output Schema:**
```json
{
    "RecoveryGroupArn": "string",
    "RecoveryGroupName": "string",
    "Cells": ["string"],
    "Tags": {
        "string": "string"
    }
}
```

---

### 6.4 `delete-recovery-group`

Deletes a recovery group.

**Synopsis:**
```bash
aws route53-recovery-readiness delete-recovery-group \
    --recovery-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--recovery-group-name` | **Yes** | string | -- | Name of the recovery group to delete |

**Output:** None on success.

---

### 6.5 `list-recovery-groups`

Lists all recovery groups. **Paginated operation.**

**Synopsis:**
```bash
aws route53-recovery-readiness list-recovery-groups \
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
    "RecoveryGroups": [
        {
            "RecoveryGroupArn": "string",
            "RecoveryGroupName": "string",
            "Cells": ["string"],
            "Tags": {
                "string": "string"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 6.6 `get-recovery-group-readiness-summary`

Gets a readiness summary for a recovery group, including per-readiness-check status. **Paginated operation.**

**Synopsis:**
```bash
aws route53-recovery-readiness get-recovery-group-readiness-summary \
    --recovery-group-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--recovery-group-name` | **Yes** | string | -- | Name of the recovery group |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Readiness": "READY|NOT_READY|UNKNOWN|NOT_AUTHORIZED",
    "ReadinessChecks": [
        {
            "Readiness": "READY|NOT_READY|UNKNOWN|NOT_AUTHORIZED",
            "ReadinessCheckName": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.7 `get-architecture-recommendations`

Gets architecture improvement recommendations for a recovery group based on readiness assessment.

**Synopsis:**
```bash
aws route53-recovery-readiness get-architecture-recommendations \
    --recovery-group-name <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--recovery-group-name` | **Yes** | string | -- | Name of the recovery group |
| `--max-results` | No | integer | None | Max results to return (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "LastAuditTimestamp": "timestamp",
    "Recommendations": [
        {
            "RecommendationText": "string"
        }
    ],
    "NextToken": "string"
}
```
