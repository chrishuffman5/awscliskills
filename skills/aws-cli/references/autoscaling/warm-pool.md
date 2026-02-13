# Warm Pool

### 7.1 `put-warm-pool`

Creates or updates a warm pool for the specified Auto Scaling group. A warm pool is a pool of pre-initialized instances that are ready to be placed into the group when needed.

**Synopsis:**
```bash
aws autoscaling put-warm-pool \
    --auto-scaling-group-name <value> \
    [--max-group-prepared-capacity <value>] \
    [--min-size <value>] \
    [--pool-state <value>] \
    [--instance-reuse-policy <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |
| `--max-group-prepared-capacity` | No | integer | -1 | Max number of instances in warm pool + in group. `-1` means max-size of group |
| `--min-size` | No | integer | 0 | Minimum number of instances in the warm pool |
| `--pool-state` | No | string | `Stopped` | State for warm pool instances: `Stopped`, `Running`, `Hibernated` |
| `--instance-reuse-policy` | No | structure | None | Instance reuse policy. Shorthand: `ReuseOnScaleIn=boolean` |

**Output:** No output on success (empty JSON `{}`).

---

### 7.2 `delete-warm-pool`

Deletes the warm pool for the specified Auto Scaling group.

**Synopsis:**
```bash
aws autoscaling delete-warm-pool \
    --auto-scaling-group-name <value> \
    [--force-delete | --no-force-delete] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |
| `--force-delete` | No | boolean | false | Force delete warm pool and terminate instances |

**Output:** No output on success (empty JSON `{}`).

---

### 7.3 `describe-warm-pool`

Describes the warm pool for the specified Auto Scaling group. **Paginated operation.**

**Synopsis:**
```bash
aws autoscaling describe-warm-pool \
    --auto-scaling-group-name <value> \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "WarmPoolConfiguration": {
        "MaxGroupPreparedCapacity": "integer",
        "MinSize": "integer",
        "PoolState": "Stopped|Running|Hibernated",
        "Status": "PendingDelete",
        "InstanceReusePolicy": {
            "ReuseOnScaleIn": true|false
        }
    },
    "Instances": [
        {
            "InstanceId": "string",
            "InstanceType": "string",
            "AvailabilityZone": "string",
            "LifecycleState": "Warmed:Pending|Warmed:Pending:Wait|Warmed:Pending:Proceed|Warmed:Running|Warmed:Stopped|Warmed:Terminated|Warmed:Hibernated",
            "HealthStatus": "string",
            "LaunchTemplate": {
                "LaunchTemplateId": "string",
                "LaunchTemplateName": "string",
                "Version": "string"
            },
            "WeightedCapacity": "string"
        }
    ],
    "NextToken": "string"
}
```
