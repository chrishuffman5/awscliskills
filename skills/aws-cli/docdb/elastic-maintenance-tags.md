# Elastic Maintenance & Tags (`aws docdb-elastic`)

## Maintenance

### 10.1 `apply-pending-maintenance-action`

Applies a pending maintenance action to an elastic cluster resource.

**Synopsis:**
```bash
aws docdb-elastic apply-pending-maintenance-action \
    --resource-arn <value> \
    --apply-action <value> \
    --opt-in-type <value> \
    [--apply-on <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the elastic cluster resource |
| `--apply-action` | **Yes** | string | -- | Pending maintenance action to apply |
| `--opt-in-type` | **Yes** | string | -- | Opt-in type: `IMMEDIATE`, `NEXT_MAINTENANCE`, `UNDO_OPT_IN` |
| `--apply-on` | No | string | -- | Specific date to apply the action |

**Output Schema:**
```json
{
    "resourcePendingMaintenanceAction": {
        "resourceArn": "string",
        "pendingMaintenanceActionDetails": [
            {
                "action": "string",
                "autoAppliedAfterDate": "string",
                "forcedApplyDate": "string",
                "optInStatus": "string",
                "currentApplyDate": "string",
                "description": "string"
            }
        ]
    }
}
```

---

### 10.2 `get-pending-maintenance-action`

Retrieves all pending maintenance actions for an elastic cluster resource.

**Synopsis:**
```bash
aws docdb-elastic get-pending-maintenance-action \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the elastic cluster resource |

**Output Schema:**
```json
{
    "resourcePendingMaintenanceAction": {
        "resourceArn": "string",
        "pendingMaintenanceActionDetails": [
            {
                "action": "string",
                "autoAppliedAfterDate": "string",
                "forcedApplyDate": "string",
                "optInStatus": "string",
                "currentApplyDate": "string",
                "description": "string"
            }
        ]
    }
}
```

---

### 10.3 `list-pending-maintenance-actions`

Returns a list of all pending maintenance actions for elastic cluster resources. **Paginated operation.**

**Synopsis:**
```bash
aws docdb-elastic list-pending-maintenance-actions \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Maximum results per page |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "resourcePendingMaintenanceActions": [
        {
            "resourceArn": "string",
            "pendingMaintenanceActionDetails": [
                {
                    "action": "string",
                    "autoAppliedAfterDate": "string",
                    "forcedApplyDate": "string",
                    "optInStatus": "string",
                    "currentApplyDate": "string",
                    "description": "string"
                }
            ]
        }
    ],
    "nextToken": "string"
}
```

---

## Tags

### 10.4 `tag-resource`

Adds metadata tags to an elastic cluster resource.

**Synopsis:**
```bash
aws docdb-elastic tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the elastic cluster resource |
| `--tags` | **Yes** | map | -- | Tags. Shorthand: `KeyName1=string,KeyName2=string` |

**Output:** None (HTTP 200 on success)

---

### 10.5 `untag-resource`

Removes metadata tags from an elastic cluster resource.

**Synopsis:**
```bash
aws docdb-elastic untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the elastic cluster resource |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output:** None (HTTP 200 on success)

---

### 10.6 `list-tags-for-resource`

Lists all tags on an elastic cluster resource.

**Synopsis:**
```bash
aws docdb-elastic list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the elastic cluster resource |

**Output Schema:**
```json
{
    "tags": {
        "string": "string"
    }
}
```
