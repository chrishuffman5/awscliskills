# Scheduling Policies

### 5.1 `create-scheduling-policy`

Creates a fair share scheduling policy.

**Synopsis:**
```bash
aws batch create-scheduling-policy \
    --name <value> \
    [--fairshare-policy <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name for the scheduling policy |
| `--fairshare-policy` | No | structure | None | Fair share policy configuration |
| `--tags` | No | map | None | Tags |

**Fair Share Policy Structure:**
```json
{
    "shareDecaySeconds": "integer",
    "computeReservation": "integer",
    "shareDistribution": [
        {
            "shareIdentifier": "string",
            "weightFactor": "float"
        }
    ]
}
```

**Output Schema:**
```json
{
    "name": "string",
    "arn": "string"
}
```

---

### 5.2 `update-scheduling-policy`

Updates a scheduling policy.

**Synopsis:**
```bash
aws batch update-scheduling-policy \
    --arn <value> \
    [--fairshare-policy <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the scheduling policy |
| `--fairshare-policy` | No | structure | None | Updated fair share policy |

**Output Schema:**
```json
{}
```

---

### 5.3 `delete-scheduling-policy`

Deletes a scheduling policy. Must not be associated with any job queues.

**Synopsis:**
```bash
aws batch delete-scheduling-policy \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the scheduling policy to delete |

**Output Schema:**
```json
{}
```

---

### 5.4 `describe-scheduling-policies`

Describes one or more scheduling policies.

**Synopsis:**
```bash
aws batch describe-scheduling-policies \
    --arns <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arns` | **Yes** | list(string) | -- | ARNs of the scheduling policies |

**Output Schema:**
```json
{
    "schedulingPolicies": [
        {
            "name": "string",
            "arn": "string",
            "fairsharePolicy": {
                "shareDecaySeconds": "integer",
                "computeReservation": "integer",
                "shareDistribution": [
                    {
                        "shareIdentifier": "string",
                        "weightFactor": "float"
                    }
                ]
            },
            "tags": {}
        }
    ]
}
```

---

### 5.5 `list-scheduling-policies`

Lists scheduling policies. **Paginated operation.**

**Synopsis:**
```bash
aws batch list-scheduling-policies \
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
    "schedulingPolicies": [
        {
            "arn": "string",
            "name": "string"
        }
    ],
    "nextToken": "string"
}
```
