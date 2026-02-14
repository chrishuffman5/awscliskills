# Fleets

### 5.1 `create-fleet`

Creates a fleet of vehicles.

**Synopsis:**
```bash
aws iotfleetwise create-fleet \
    --fleet-id <value> \
    --signal-catalog-arn <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID (1-100 chars) |
| `--signal-catalog-arn` | **Yes** | string | -- | ARN of the signal catalog |
| `--description` | No | string | None | Description (1-2048 chars) |
| `--tags` | No | list | None | Tags (max 50) |

**Output Schema:**
```json
{
    "id": "string",
    "arn": "string"
}
```

---

### 5.2 `get-fleet`

Retrieves information about a fleet.

**Synopsis:**
```bash
aws iotfleetwise get-fleet \
    --fleet-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID |

**Output Schema:**
```json
{
    "id": "string",
    "arn": "string",
    "description": "string",
    "signalCatalogArn": "string",
    "creationTime": "timestamp",
    "lastModificationTime": "timestamp"
}
```

---

### 5.3 `list-fleets`

Lists fleets. **Paginated operation.**

**Synopsis:**
```bash
aws iotfleetwise list-fleets \
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
    "fleetSummaries": [
        {
            "id": "string",
            "arn": "string",
            "description": "string",
            "signalCatalogArn": "string",
            "creationTime": "timestamp",
            "lastModificationTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 5.4 `update-fleet`

Updates a fleet description.

**Synopsis:**
```bash
aws iotfleetwise update-fleet \
    --fleet-id <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID |
| `--description` | No | string | None | Updated description |

**Output Schema:**
```json
{
    "id": "string",
    "arn": "string"
}
```

---

### 5.5 `delete-fleet`

Deletes a fleet. Vehicles are not deleted but are disassociated.

**Synopsis:**
```bash
aws iotfleetwise delete-fleet \
    --fleet-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID |

**Output Schema:**
```json
{
    "id": "string",
    "arn": "string"
}
```

---

### 5.6 `associate-vehicle-fleet`

Associates a vehicle with a fleet.

**Synopsis:**
```bash
aws iotfleetwise associate-vehicle-fleet \
    --vehicle-name <value> \
    --fleet-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vehicle-name` | **Yes** | string | -- | Vehicle name |
| `--fleet-id` | **Yes** | string | -- | Fleet ID |

**Output:** None

---

### 5.7 `disassociate-vehicle-fleet`

Removes a vehicle from a fleet.

**Synopsis:**
```bash
aws iotfleetwise disassociate-vehicle-fleet \
    --vehicle-name <value> \
    --fleet-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vehicle-name` | **Yes** | string | -- | Vehicle name |
| `--fleet-id` | **Yes** | string | -- | Fleet ID |

**Output:** None

---

### 5.8 `list-fleets-for-vehicle`

Lists fleets that a vehicle belongs to. **Paginated operation.**

**Synopsis:**
```bash
aws iotfleetwise list-fleets-for-vehicle \
    --vehicle-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vehicle-name` | **Yes** | string | -- | Vehicle name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "fleets": ["string"],
    "nextToken": "string"
}
```

---

### 5.9 `list-vehicles-in-fleet`

Lists vehicles in a fleet. **Paginated operation.**

**Synopsis:**
```bash
aws iotfleetwise list-vehicles-in-fleet \
    --fleet-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "vehicles": ["string"],
    "nextToken": "string"
}
```
