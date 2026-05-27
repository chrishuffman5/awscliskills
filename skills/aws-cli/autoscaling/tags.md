# Tags

### 10.1 `create-or-update-tags`

Creates or updates tags for the specified Auto Scaling group.

**Synopsis:**
```bash
aws autoscaling create-or-update-tags \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tags` | **Yes** | list | -- | Tags to create or update. Shorthand: `ResourceId=string,ResourceType=auto-scaling-group,Key=string,Value=string,PropagateAtLaunch=boolean ...` |

**Tag Structure:**
```json
[
    {
        "ResourceId": "my-asg",
        "ResourceType": "auto-scaling-group",
        "Key": "Environment",
        "Value": "prod",
        "PropagateAtLaunch": true
    }
]
```

**Output:** No output on success.

---

### 10.2 `delete-tags`

Deletes the specified tags.

**Synopsis:**
```bash
aws autoscaling delete-tags \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tags` | **Yes** | list | -- | Tags to delete. Must specify `ResourceId`, `ResourceType`, and `Key` |

**Output:** No output on success.

---

### 10.3 `describe-tags`

Describes the tags for the specified Auto Scaling group. **Paginated operation.**

**Synopsis:**
```bash
aws autoscaling describe-tags \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | None | Filters. Shorthand: `Name=auto-scaling-group,Values=string,string ...` or `Name=key,Values=string` or `Name=value,Values=string` or `Name=propagate-at-launch,Values=true\|false` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "Tags": [
        {
            "ResourceId": "string",
            "ResourceType": "auto-scaling-group",
            "Key": "string",
            "Value": "string",
            "PropagateAtLaunch": true|false
        }
    ],
    "NextToken": "string"
}
```
