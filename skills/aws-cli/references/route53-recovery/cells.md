# Cells

Commands for managing Route 53 ARC cells via `aws route53-recovery-readiness`. A cell represents an independent unit of failover (e.g., an Availability Zone or Region).

### 7.1 `create-cell`

Creates a readiness cell. Cells can be nested to represent hierarchical structures.

**Synopsis:**
```bash
aws route53-recovery-readiness create-cell \
    --cell-name <value> \
    [--cells <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cell-name` | **Yes** | string | -- | Name of the cell (max 64 chars, alphanumeric + underscores) |
| `--cells` | No | list(string) | None | List of child cell ARNs for nested cells |
| `--tags` | No | map | None | Tags as key-value pairs |

**Output Schema:**
```json
{
    "CellArn": "string",
    "CellName": "string",
    "Cells": ["string"],
    "ParentReadinessScopes": ["string"],
    "Tags": {
        "string": "string"
    }
}
```

---

### 7.2 `get-cell`

Gets details about a cell.

**Synopsis:**
```bash
aws route53-recovery-readiness get-cell \
    --cell-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cell-name` | **Yes** | string | -- | Name of the cell |

**Output Schema:**
```json
{
    "CellArn": "string",
    "CellName": "string",
    "Cells": ["string"],
    "ParentReadinessScopes": ["string"],
    "Tags": {
        "string": "string"
    }
}
```

---

### 7.3 `update-cell`

Updates a cell's child cells.

**Synopsis:**
```bash
aws route53-recovery-readiness update-cell \
    --cell-name <value> \
    --cells <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cell-name` | **Yes** | string | -- | Name of the cell |
| `--cells` | **Yes** | list(string) | -- | Updated list of child cell ARNs |

**Output Schema:**
```json
{
    "CellArn": "string",
    "CellName": "string",
    "Cells": ["string"],
    "ParentReadinessScopes": ["string"],
    "Tags": {
        "string": "string"
    }
}
```

---

### 7.4 `delete-cell`

Deletes a cell.

**Synopsis:**
```bash
aws route53-recovery-readiness delete-cell \
    --cell-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cell-name` | **Yes** | string | -- | Name of the cell to delete |

**Output:** None on success.

---

### 7.5 `list-cells`

Lists all cells. **Paginated operation.**

**Synopsis:**
```bash
aws route53-recovery-readiness list-cells \
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
    "Cells": [
        {
            "CellArn": "string",
            "CellName": "string",
            "Cells": ["string"],
            "ParentReadinessScopes": ["string"],
            "Tags": {
                "string": "string"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 7.6 `get-cell-readiness-summary`

Gets a readiness summary for a cell, including per-readiness-check status. **Paginated operation.**

**Synopsis:**
```bash
aws route53-recovery-readiness get-cell-readiness-summary \
    --cell-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cell-name` | **Yes** | string | -- | Name of the cell |
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
