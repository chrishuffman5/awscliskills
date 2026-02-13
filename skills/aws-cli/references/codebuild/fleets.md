# Fleets

### 8.1 `create-fleet`

Creates a compute fleet.

**Synopsis:**
```bash
aws codebuild create-fleet \
    --name <value> \
    --base-capacity <value> \
    --environment-type <value> \
    --compute-type <value> \
    [--scaling-configuration <value>] \
    [--overflow-behavior <value>] \
    [--vpc-config <value>] \
    [--fleet-service-role <value>] \
    [--tags <value>] \
    [--image-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Fleet name |
| `--base-capacity` | **Yes** | integer | -- | Initial number of machines in the fleet |
| `--environment-type` | **Yes** | string | -- | Environment type: `LINUX_CONTAINER`, `LINUX_GPU_CONTAINER`, `ARM_CONTAINER`, `WINDOWS_SERVER_2019_CONTAINER`, `WINDOWS_SERVER_2022_CONTAINER` |
| `--compute-type` | **Yes** | string | -- | Compute type (e.g., `BUILD_GENERAL1_SMALL`, `BUILD_GENERAL1_MEDIUM`, etc.) |
| `--scaling-configuration` | No | structure | None | Auto-scaling configuration |
| `--overflow-behavior` | No | string | `QUEUE` | Behavior when fleet is at capacity: `QUEUE`, `ON_DEMAND` |
| `--vpc-config` | No | structure | None | VPC configuration |
| `--fleet-service-role` | No | string | None | IAM service role ARN for fleet |
| `--tags` | No | list | None | Tags (max 50). Shorthand: `key=string,value=string ...` |
| `--image-id` | No | string | None | Custom AMI ID for fleet machines |

**Scaling Configuration Structure:**
```json
{
    "scalingType": "TARGET_TRACKING_SCALING",
    "targetTrackingScalingConfigs": [
        {
            "metricType": "FLEET_UTILIZATION_RATE",
            "targetValue": "double"
        }
    ],
    "maxCapacity": "integer"
}
```

**Output Schema:**
```json
{
    "fleet": {
        "arn": "string",
        "name": "string",
        "id": "string",
        "created": "timestamp",
        "lastModified": "timestamp",
        "status": {
            "statusCode": "CREATING|UPDATING|ROTATING|PENDING_DELETION|DELETING|CREATE_FAILED|UPDATE_ROLLBACK_FAILED|ACTIVE",
            "context": "CREATE_FAILED|UPDATE_FAILED|ACTION_REQUIRED",
            "message": "string"
        },
        "baseCapacity": "integer",
        "environmentType": "string",
        "computeType": "string",
        "scalingConfiguration": {
            "scalingType": "TARGET_TRACKING_SCALING",
            "targetTrackingScalingConfigs": [],
            "maxCapacity": "integer",
            "desiredCapacity": "integer"
        },
        "overflowBehavior": "QUEUE|ON_DEMAND",
        "vpcConfig": {
            "vpcId": "string",
            "subnets": ["string"],
            "securityGroupIds": ["string"]
        },
        "fleetServiceRole": "string",
        "tags": [],
        "imageId": "string"
    }
}
```

---

### 8.2 `delete-fleet`

Deletes a compute fleet. Builds in progress are completed; queued builds fail immediately.

**Synopsis:**
```bash
aws codebuild delete-fleet \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | Fleet ARN |

**Output Schema:**
```json
{}
```

---

### 8.3 `batch-get-fleets`

Gets information about one or more compute fleets.

**Synopsis:**
```bash
aws codebuild batch-get-fleets \
    --names <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--names` | **Yes** | list(string) | -- | Fleet names or ARNs (max 100) |

**Output Schema:**
```json
{
    "fleets": [
        {
            "arn": "string",
            "name": "string",
            "id": "string",
            "created": "timestamp",
            "lastModified": "timestamp",
            "status": {
                "statusCode": "string",
                "context": "string",
                "message": "string"
            },
            "baseCapacity": "integer",
            "environmentType": "string",
            "computeType": "string",
            "scalingConfiguration": { },
            "overflowBehavior": "QUEUE|ON_DEMAND",
            "vpcConfig": { },
            "fleetServiceRole": "string",
            "tags": [],
            "imageId": "string"
        }
    ],
    "fleetsNotFound": ["string"]
}
```

---

### 8.4 `list-fleets`

Gets a list of compute fleet names. **Paginated operation.**

**Synopsis:**
```bash
aws codebuild list-fleets \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sort-by` | No | string | `NAME` | Sort criterion: `NAME`, `CREATED_TIME`, `LAST_MODIFIED_TIME` |
| `--sort-order` | No | string | `ASCENDING` | Sort order: `ASCENDING`, `DESCENDING` |
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

### 8.5 `update-fleet`

Updates a compute fleet.

**Synopsis:**
```bash
aws codebuild update-fleet \
    --arn <value> \
    [--base-capacity <value>] \
    [--environment-type <value>] \
    [--compute-type <value>] \
    [--scaling-configuration <value>] \
    [--overflow-behavior <value>] \
    [--vpc-config <value>] \
    [--fleet-service-role <value>] \
    [--tags <value>] \
    [--image-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | Fleet ARN |
| `--base-capacity` | No | integer | None | Updated base capacity |
| `--environment-type` | No | string | None | Updated environment type |
| `--compute-type` | No | string | None | Updated compute type |
| `--scaling-configuration` | No | structure | None | Updated scaling configuration |
| `--overflow-behavior` | No | string | None | Updated overflow behavior |
| `--vpc-config` | No | structure | None | Updated VPC configuration |
| `--fleet-service-role` | No | string | None | Updated service role |
| `--tags` | No | list | None | Updated tags |
| `--image-id` | No | string | None | Updated image ID |

**Output Schema:**
Same as `create-fleet`.
