# Setup

### 4.1 `create-resource-explorer-setup`

Sets up Resource Explorer across multiple Regions in a single operation. Creates indexes and a view in each specified Region, and optionally designates an aggregator Region.

**Synopsis:**
```bash
aws resource-explorer-2 create-resource-explorer-setup \
    --region-list <value> \
    --view-name <value> \
    [--aggregator-regions <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--region-list` | **Yes** | list(string) | -- | Regions to enable Resource Explorer in (min 1) |
| `--view-name` | **Yes** | string | -- | Name for the view created in each Region (1-64 chars, alphanumeric + dash) |
| `--aggregator-regions` | No | list(string) | None | Region(s) to designate as aggregator (max 1) |

**Output Schema:**
```json
{
    "TaskId": "string"
}
```

> Use `get-resource-explorer-setup` with the returned TaskId to monitor progress.

---

### 4.2 `delete-resource-explorer-setup`

Deletes Resource Explorer setup across Regions. Removes indexes and views from the specified Regions or all Regions.

**Synopsis:**
```bash
aws resource-explorer-2 delete-resource-explorer-setup \
    [--region-list <value>] \
    [--delete-in-all-regions | --no-delete-in-all-regions] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--region-list` | No | list(string) | None | Regions to remove setup from. Mutually exclusive with `--delete-in-all-regions` |
| `--delete-in-all-regions` | No | boolean | None | Delete setup in all enabled Regions. Mutually exclusive with `--region-list` |

**Output Schema:**
```json
{
    "TaskId": "string"
}
```

---

### 4.3 `get-resource-explorer-setup`

Retrieves the status of a setup or deletion task. **Paginated.**

**Synopsis:**
```bash
aws resource-explorer-2 get-resource-explorer-setup \
    --task-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-id` | **Yes** | string | -- | Task ID returned by create/delete setup (UUID format) |

**Output Schema:**
```json
{
    "Regions": [
        {
            "Region": "string",
            "Index": {
                "Status": "SUCCEEDED|FAILED|IN_PROGRESS|SKIPPED",
                "Index": {
                    "Region": "string",
                    "Arn": "string",
                    "Type": "LOCAL|AGGREGATOR"
                },
                "ErrorDetails": {
                    "Code": "string",
                    "Message": "string"
                }
            },
            "View": {
                "Status": "SUCCEEDED|FAILED|IN_PROGRESS|SKIPPED",
                "View": {
                    "ViewArn": "string",
                    "ViewName": "string",
                    "Owner": "string",
                    "LastUpdatedAt": "timestamp",
                    "Scope": "string",
                    "IncludedProperties": [{ "Name": "string" }],
                    "Filters": { "FilterString": "string" }
                },
                "ErrorDetails": {
                    "Code": "string",
                    "Message": "string"
                }
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 4.4 `get-account-level-service-configuration`

Retrieves the Organization-level service configuration for Resource Explorer. Only callable from the management account.

**Synopsis:**
```bash
aws resource-explorer-2 get-account-level-service-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None.

**Output Schema:**
```json
{
    "OrgConfiguration": {
        "AWSServiceAccessStatus": "ENABLED|DISABLED",
        "ServiceLinkedRole": "string"
    }
}
```

---

### 4.5 `list-streaming-access-for-services`

Lists AWS services that have been granted streaming access to Resource Explorer data. **Paginated.**

**Synopsis:**
```bash
aws resource-explorer-2 list-streaming-access-for-services \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:** Pagination only.

**Output Schema:**
```json
{
    "StreamingAccessForServices": [
        {
            "ServicePrincipal": "string",
            "CreatedAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
