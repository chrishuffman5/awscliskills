# Capacity

### 8.1 `create-capacity-reservation`

Creates a capacity reservation for a workgroup.

**Synopsis:**
```bash
aws athena create-capacity-reservation \
    --target-dpus <value> \
    --name <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-dpus` | **Yes** | integer | -- | Target DPU capacity (minimum 24) |
| `--name` | **Yes** | string | -- | Reservation name |
| `--tags` | No | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |

No output on success.

---

### 8.2 `cancel-capacity-reservation`

Cancels a capacity reservation.

**Synopsis:**
```bash
aws athena cancel-capacity-reservation \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Reservation to cancel |

No output on success.

---

### 8.3 `get-capacity-reservation`

Returns information about a capacity reservation.

**Synopsis:**
```bash
aws athena get-capacity-reservation \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Reservation name |

**Output Schema:**
```json
{
    "CapacityReservation": {
        "Name": "string",
        "Status": "PENDING|ACTIVE|CANCELLING|CANCELLED|FAILED|UPDATE_PENDING",
        "TargetDpus": "integer",
        "AllocatedDpus": "integer",
        "LastAllocation": {
            "Status": "PENDING|SUCCEEDED|FAILED",
            "StatusMessage": "string",
            "RequestTime": "timestamp",
            "RequestCompletionTime": "timestamp"
        },
        "LastSuccessfulAllocationTime": "timestamp",
        "CreationTime": "timestamp"
    }
}
```

---

### 8.4 `get-capacity-assignment-configuration`

Returns the capacity assignment configuration for a reservation.

**Synopsis:**
```bash
aws athena get-capacity-assignment-configuration \
    --capacity-reservation-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--capacity-reservation-name` | **Yes** | string | -- | Reservation name |

**Output Schema:**
```json
{
    "CapacityAssignmentConfiguration": {
        "CapacityReservationName": "string",
        "CapacityAssignments": [
            {
                "WorkGroupNames": ["string"]
            }
        ]
    }
}
```

---

### 8.5 `put-capacity-assignment-configuration`

Sets the capacity assignment configuration (assigns workgroups to a reservation).

**Synopsis:**
```bash
aws athena put-capacity-assignment-configuration \
    --capacity-reservation-name <value> \
    --capacity-assignments <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--capacity-reservation-name` | **Yes** | string | -- | Reservation name |
| `--capacity-assignments` | **Yes** | list | -- | Assignments. Shorthand: `WorkGroupNames=string,string ...` |

No output on success.

---

### 8.6 `list-capacity-reservations`

Lists capacity reservations. **Paginated operation.**

**Synopsis:**
```bash
aws athena list-capacity-reservations \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "CapacityReservations": [
        {
            "Name": "string",
            "Status": "string",
            "TargetDpus": "integer",
            "AllocatedDpus": "integer",
            "CreationTime": "timestamp",
            "LastSuccessfulAllocationTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
