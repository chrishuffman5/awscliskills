# Flows

QuickSight flows provide automated data preparation and transformation pipelines.

### 21.1 `list-flows`

Lists flows. **Paginated operation.**

**Synopsis:**
```bash
aws quicksight list-flows \
    --aws-account-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items |

**Output Schema:**
```json
{
    "Flows": [
        {
            "Arn": "string",
            "FlowId": "string",
            "Name": "string",
            "Status": "string",
            "CreatedTime": "timestamp",
            "LastUpdatedTime": "timestamp"
        }
    ],
    "NextToken": "string",
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 21.2 `search-flows`

Searches flows using filters. **Paginated operation.**

**Synopsis:**
```bash
aws quicksight search-flows \
    --aws-account-id <value> \
    --filters <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

---

### 21.3 `get-flow-metadata`

Returns metadata for a flow.

**Synopsis:**
```bash
aws quicksight get-flow-metadata \
    --aws-account-id <value> \
    --flow-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--flow-id` | **Yes** | string | -- | Flow ID |

**Output Schema:**
```json
{
    "FlowArn": "string",
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 21.4 `get-flow-permissions` / `update-flow-permissions`

Manage flow permissions.

**Synopsis:**
```bash
aws quicksight get-flow-permissions \
    --aws-account-id <value> \
    --flow-id <value>

aws quicksight update-flow-permissions \
    --aws-account-id <value> \
    --flow-id <value> \
    [--grant-permissions <value>] \
    [--revoke-permissions <value>]
```

**Output Schema (get):**
```json
{
    "FlowId": "string",
    "FlowArn": "string",
    "Permissions": [
        {
            "Principal": "string",
            "Actions": ["string"]
        }
    ],
    "RequestId": "string",
    "Status": "integer"
}
```
