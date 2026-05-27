# Permissions

### 4.1 `add-permission`

Adds a permission to a queue for a specific principal and action. Generates a policy statement added to the queue's access policy. Max 7 actions per statement.

**Synopsis:**
```bash
aws sqs add-permission \
    --queue-url <value> \
    --label <value> \
    --aws-account-ids <value> \
    --actions <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--queue-url` | **Yes** | string | -- | URL of the queue. Case-sensitive. |
| `--label` | **Yes** | string | -- | Unique permission label (max 80 chars, alphanumeric/hyphens/underscores) |
| `--aws-account-ids` | **Yes** | list | -- | AWS account IDs to grant permission to |
| `--actions` | **Yes** | list | -- | Actions to allow: `SendMessage`, `ReceiveMessage`, `DeleteMessage`, `ChangeMessageVisibility`, `GetQueueAttributes`, `GetQueueUrl`, or `*` |

**Notes:**
- Granting `SendMessage` also grants `SendMessageBatch`
- Granting `DeleteMessage` also grants `DeleteMessageBatch`
- Granting `ChangeMessageVisibility` also grants `ChangeMessageVisibilityBatch`

**Output:** None

---

### 4.2 `remove-permission`

Revokes a permission from a queue by its label. Only the queue owner can remove permissions.

**Synopsis:**
```bash
aws sqs remove-permission \
    --queue-url <value> \
    --label <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--queue-url` | **Yes** | string | -- | URL of the queue. Case-sensitive. |
| `--label` | **Yes** | string | -- | Permission label to remove (created by `add-permission`) |

**Output:** None
