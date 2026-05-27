# Analytics

### 26.1 `associate-analytics-data-set`

Associates an analytics data set with an instance.

**Synopsis:**
```bash
aws connect associate-analytics-data-set \
    --instance-id <value> \
    --data-set-id <value> \
    [--target-account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--data-set-id` | **Yes** | string | -- | Data set ID |
| `--target-account-id` | No | string | None | Target AWS account for cross-account |

**Output Schema:**
```json
{
    "DataSetId": "string",
    "TargetAccountId": "string",
    "ResourceShareId": "string",
    "ResourceShareArn": "string"
}
```

---

### 26.2 `batch-associate-analytics-data-set`

Batch associates analytics data sets.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--data-set-ids` | **Yes** | list | -- | Data set IDs |
| `--target-account-id` | No | string | None | Target account |

**Output Schema:**
```json
{
    "Created": [ { "DataSetId": "string", "TargetAccountId": "string", "ResourceShareId": "string", "ResourceShareArn": "string" } ],
    "Errors": [ { "ErrorCode": "string", "ErrorMessage": "string" } ]
}
```

---

### 26.3 `list-analytics-data-associations`

Lists analytics data associations. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--data-set-id` | No | string | None | Filter by data set |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-1000) |

---

### 26.4 `list-analytics-data-lake-data-sets`

Lists analytics data lake data sets. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |

---

### 26.5 `disassociate-analytics-data-set`

Disassociates an analytics data set.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--data-set-id` | **Yes** | string | -- | Data set ID |
| `--target-account-id` | No | string | None | Target account |

**Output:** None

---

### 26.6 `batch-disassociate-analytics-data-set`

Batch disassociates analytics data sets.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--data-set-ids` | **Yes** | list | -- | Data set IDs |
| `--target-account-id` | No | string | None | Target account |

**Output Schema:**
```json
{
    "Deleted": ["string"],
    "Errors": [ { "ErrorCode": "string", "ErrorMessage": "string" } ]
}
```

---

### 26.7 `associate-flow`

Associates a flow with a resource.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--resource-id` | **Yes** | string | -- | Resource ID |
| `--flow-id` | **Yes** | string | -- | Flow ID |
| `--resource-type` | **Yes** | string | -- | Resource type |

**Output:** None

---

### 26.8 `get-flow-association`

Gets a flow association.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--resource-id` | **Yes** | string | -- | Resource ID |
| `--resource-type` | **Yes** | string | -- | Resource type |

**Output Schema:**
```json
{
    "ResourceId": "string",
    "FlowId": "string",
    "ResourceType": "string"
}
```

---

### 26.9 `list-flow-associations`

Lists flow associations. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--resource-type` | No | string | None | Filter by resource type |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-1000) |

---

### 26.10 `batch-get-flow-association`

Batch gets flow associations.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--resource-ids` | **Yes** | list | -- | Resource IDs |
| `--resource-type` | No | string | None | Resource type |

**Output Schema:**
```json
{
    "FlowAssociationSummaryList": [ { "ResourceId": "string", "FlowId": "string", "ResourceType": "string" } ]
}
```

---

### 26.11 `disassociate-flow`

Disassociates a flow from a resource.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--resource-id` | **Yes** | string | -- | Resource ID |
| `--resource-type` | **Yes** | string | -- | Resource type |

**Output:** None
