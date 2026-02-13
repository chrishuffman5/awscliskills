# Permissions

### 4.1 `add-permission`

Adds a statement to a topic's access control policy, granting access for the specified AWS accounts to the specified actions.

**Synopsis:**
```bash
aws sns add-permission \
    --topic-arn <value> \
    --label <value> \
    --aws-account-id <value> \
    --action-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--topic-arn` | **Yes** | string | -- | ARN of the topic |
| `--label` | **Yes** | string | -- | Unique identifier for the new policy statement |
| `--aws-account-id` | **Yes** | list(string) | -- | AWS account IDs to grant access. Space-separated |
| `--action-name` | **Yes** | list(string) | -- | SNS actions to allow (e.g., `Publish`). Space-separated |

**Output Schema:** None

---

### 4.2 `remove-permission`

Removes a statement from a topic's access control policy.

**Synopsis:**
```bash
aws sns remove-permission \
    --topic-arn <value> \
    --label <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--topic-arn` | **Yes** | string | -- | ARN of the topic |
| `--label` | **Yes** | string | -- | Unique label of the statement to remove |

**Output Schema:** None
