# Milestones

### 5.1 `create-milestone`

Creates a milestone for a workload, capturing a snapshot of the current state.

**Synopsis:**
```bash
aws wellarchitected create-milestone \
    --workload-id <value> \
    --milestone-name <value> \
    --client-request-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-id` | **Yes** | string | -- | Workload ID (32 hex chars) |
| `--milestone-name` | **Yes** | string | -- | Milestone name (3-100 chars) |
| `--client-request-token` | **Yes** | string | -- | Idempotency token |

**Output Schema:**
```json
{
    "WorkloadId": "string",
    "MilestoneNumber": "integer"
}
```

---

### 5.2 `get-milestone`

Retrieves a milestone for a workload.

**Synopsis:**
```bash
aws wellarchitected get-milestone \
    --workload-id <value> \
    --milestone-number <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-id` | **Yes** | string | -- | Workload ID |
| `--milestone-number` | **Yes** | integer | -- | Milestone number (1-100) |

**Output Schema:**
```json
{
    "WorkloadId": "string",
    "Milestone": {
        "MilestoneNumber": "integer",
        "MilestoneName": "string",
        "RecordedAt": "timestamp",
        "Workload": {
            "WorkloadId": "string",
            "WorkloadArn": "string",
            "WorkloadName": "string",
            "Description": "string",
            "Environment": "PRODUCTION|PREPRODUCTION",
            "RiskCounts": {},
            "ImprovementStatus": "string",
            "Lenses": ["string"],
            "Owner": "string"
        }
    }
}
```

---

### 5.3 `list-milestones`

Lists milestones for a workload. **Paginated.**

**Synopsis:**
```bash
aws wellarchitected list-milestones \
    --workload-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-id` | **Yes** | string | -- | Workload ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "WorkloadId": "string",
    "MilestoneSummaries": [
        {
            "MilestoneNumber": "integer",
            "MilestoneName": "string",
            "RecordedAt": "timestamp",
            "WorkloadSummary": {
                "WorkloadId": "string",
                "WorkloadName": "string",
                "RiskCounts": {},
                "ImprovementStatus": "string"
            }
        }
    ],
    "NextToken": "string"
}
```
