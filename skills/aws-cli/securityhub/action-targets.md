# Action Targets

### 11.1 `create-action-target`

Creates a custom action target for use with CloudWatch Events rules.

**Synopsis:**
```bash
aws securityhub create-action-target \
    --name <value> \
    --description <value> \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the custom action target |
| `--description` | **Yes** | string | -- | Description of the custom action |
| `--id` | **Yes** | string | -- | Custom action ID (used as the suffix of the action ARN) |

**Output Schema:**
```json
{
    "ActionTargetArn": "string"
}
```

---

### 11.2 `delete-action-target`

Deletes a custom action target.

**Synopsis:**
```bash
aws securityhub delete-action-target \
    --action-target-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--action-target-arn` | **Yes** | string | -- | ARN of the action target to delete |

**Output Schema:**
```json
{
    "ActionTargetArn": "string"
}
```

---

### 11.3 `describe-action-targets`

Returns a list of custom action targets. **Paginated operation.**

**Synopsis:**
```bash
aws securityhub describe-action-targets \
    [--action-target-arns <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--action-target-arns` | No | list(string) | None | Specific action target ARNs (omit for all) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ActionTargets": [
        {
            "ActionTargetArn": "string",
            "Name": "string",
            "Description": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 11.4 `update-action-target`

Updates a custom action target.

**Synopsis:**
```bash
aws securityhub update-action-target \
    --action-target-arn <value> \
    [--name <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--action-target-arn` | **Yes** | string | -- | ARN of the action target to update |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |

**Output:** None (HTTP 200 on success)
