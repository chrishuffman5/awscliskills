# Queues

### 4.1 `create-queue`

Creates a processing queue for transcoding jobs.

**Synopsis:**
```bash
aws mediaconvert create-queue \
    --name <value> \
    [--concurrent-jobs <value>] \
    [--description <value>] \
    [--pricing-plan <value>] \
    [--reservation-plan-settings <value>] \
    [--status <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Queue name (unique within account) |
| `--concurrent-jobs` | No | integer | None | Max concurrent jobs |
| `--description` | No | string | None | Queue description |
| `--pricing-plan` | No | string | ON_DEMAND | `ON_DEMAND` or `RESERVED` |
| `--reservation-plan-settings` | No | structure | None | Required if pricing-plan is RESERVED |
| `--status` | No | string | ACTIVE | `ACTIVE` or `PAUSED` |
| `--tags` | No | map | None | Key-value tag pairs |

**ReservationPlanSettings:**
```json
{
    "Commitment": "ONE_YEAR",
    "RenewalType": "AUTO_RENEW|EXPIRE",
    "ReservedSlots": 1
}
```

**Output Schema:**
```json
{
    "Queue": {
        "Arn": "string",
        "Name": "string",
        "Description": "string",
        "Status": "ACTIVE|PAUSED",
        "Type": "SYSTEM|CUSTOM",
        "PricingPlan": "ON_DEMAND|RESERVED",
        "ConcurrentJobs": "integer",
        "ProgressingJobsCount": "integer",
        "SubmittedJobsCount": "integer",
        "CreatedAt": "timestamp",
        "LastUpdated": "timestamp",
        "ReservationPlan": {
            "Commitment": "ONE_YEAR",
            "ExpiresAt": "timestamp",
            "PurchasedAt": "timestamp",
            "RenewalType": "AUTO_RENEW|EXPIRE",
            "ReservedSlots": "integer",
            "Status": "ACTIVE|EXPIRED"
        },
        "ServiceOverrides": [
            {
                "Message": "string",
                "Name": "string",
                "OverrideValue": "string",
                "Value": "string"
            }
        ]
    }
}
```

---

### 4.2 `get-queue`

Retrieves a queue by name.

**Synopsis:**
```bash
aws mediaconvert get-queue \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Queue name |

**Output Schema:**
```json
{
    "Queue": {
        "Arn": "string",
        "Name": "string",
        "Description": "string",
        "Status": "ACTIVE|PAUSED",
        "Type": "SYSTEM|CUSTOM",
        "PricingPlan": "ON_DEMAND|RESERVED",
        "ConcurrentJobs": "integer",
        "ProgressingJobsCount": "integer",
        "SubmittedJobsCount": "integer",
        "CreatedAt": "timestamp",
        "LastUpdated": "timestamp",
        "ReservationPlan": {
            "Commitment": "ONE_YEAR",
            "ExpiresAt": "timestamp",
            "PurchasedAt": "timestamp",
            "RenewalType": "AUTO_RENEW|EXPIRE",
            "ReservedSlots": "integer",
            "Status": "ACTIVE|EXPIRED"
        },
        "ServiceOverrides": []
    }
}
```

---

### 4.3 `update-queue`

Updates a queue's settings, status, or reservation plan.

**Synopsis:**
```bash
aws mediaconvert update-queue \
    --name <value> \
    [--concurrent-jobs <value>] \
    [--description <value>] \
    [--reservation-plan-settings <value>] \
    [--status <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Queue name to modify |
| `--concurrent-jobs` | No | integer | None | Updated max concurrent jobs |
| `--description` | No | string | None | Updated description |
| `--reservation-plan-settings` | No | structure | None | Updated reservation plan |
| `--status` | No | string | None | `ACTIVE` or `PAUSED` |

**Output Schema:**
```json
{
    "Queue": {
        "Arn": "string",
        "Name": "string",
        "Description": "string",
        "Status": "ACTIVE|PAUSED",
        "Type": "SYSTEM|CUSTOM",
        "PricingPlan": "ON_DEMAND|RESERVED",
        "ConcurrentJobs": "integer",
        "ProgressingJobsCount": "integer",
        "SubmittedJobsCount": "integer",
        "CreatedAt": "timestamp",
        "LastUpdated": "timestamp",
        "ReservationPlan": {},
        "ServiceOverrides": []
    }
}
```

---

### 4.4 `list-queues`

Lists processing queues. **Paginated operation.**

**Synopsis:**
```bash
aws mediaconvert list-queues \
    [--list-by <value>] \
    [--order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--list-by` | No | string | CREATION_DATE | `NAME` or `CREATION_DATE` |
| `--order` | No | string | None | `ASCENDING` or `DESCENDING` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Max total items to return |

**Output Schema:**
```json
{
    "NextToken": "string",
    "Queues": [
        {
            "Arn": "string",
            "Name": "string",
            "Description": "string",
            "Status": "ACTIVE|PAUSED",
            "Type": "SYSTEM|CUSTOM",
            "PricingPlan": "ON_DEMAND|RESERVED",
            "ConcurrentJobs": "integer",
            "ProgressingJobsCount": "integer",
            "SubmittedJobsCount": "integer",
            "CreatedAt": "timestamp",
            "LastUpdated": "timestamp",
            "ReservationPlan": {},
            "ServiceOverrides": []
        }
    ],
    "TotalConcurrentJobs": "integer",
    "UnallocatedConcurrentJobs": "integer"
}
```

---

### 4.5 `delete-queue`

Deletes a queue. Cannot delete the default queue or a reserved queue with an active plan.

**Synopsis:**
```bash
aws mediaconvert delete-queue \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the queue to delete |

**Output:** None
