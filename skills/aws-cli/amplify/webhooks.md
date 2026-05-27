# Webhooks

### 6.1 `create-webhook`

Creates a new webhook on an Amplify app.

**Synopsis:**
```bash
aws amplify create-webhook \
    --app-id <value> \
    --branch-name <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-id` | **Yes** | string | -- | Unique ID of the Amplify app |
| `--branch-name` | **Yes** | string | -- | Branch name for the webhook |
| `--description` | No | string | None | Description of the webhook |

**Output Schema:**
```json
{
    "webhook": {
        "webhookArn": "string",
        "webhookId": "string",
        "webhookUrl": "string",
        "branchName": "string",
        "description": "string",
        "createTime": "timestamp",
        "updateTime": "timestamp"
    }
}
```

---

### 6.2 `delete-webhook`

Deletes a webhook.

**Synopsis:**
```bash
aws amplify delete-webhook \
    --webhook-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--webhook-id` | **Yes** | string | -- | Unique ID of the webhook to delete |

**Output Schema:**
```json
{
    "webhook": {
        "webhookArn": "string",
        "webhookId": "string",
        "webhookUrl": "string",
        "branchName": "string",
        "description": "string",
        "createTime": "timestamp",
        "updateTime": "timestamp"
    }
}
```

---

### 6.3 `get-webhook`

Returns a webhook for an Amplify app.

**Synopsis:**
```bash
aws amplify get-webhook \
    --webhook-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--webhook-id` | **Yes** | string | -- | Unique ID of the webhook |

**Output Schema:**
```json
{
    "webhook": {
        "webhookArn": "string",
        "webhookId": "string",
        "webhookUrl": "string",
        "branchName": "string",
        "description": "string",
        "createTime": "timestamp",
        "updateTime": "timestamp"
    }
}
```

---

### 6.4 `list-webhooks`

Returns a list of webhooks for an Amplify app. **Paginated operation.**

**Synopsis:**
```bash
aws amplify list-webhooks \
    --app-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-id` | **Yes** | string | -- | Unique ID of the Amplify app |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "webhooks": [
        {
            "webhookArn": "string",
            "webhookId": "string",
            "webhookUrl": "string",
            "branchName": "string",
            "description": "string",
            "createTime": "timestamp",
            "updateTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 6.5 `update-webhook`

Updates a webhook.

**Synopsis:**
```bash
aws amplify update-webhook \
    --webhook-id <value> \
    [--branch-name <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--webhook-id` | **Yes** | string | -- | Unique ID of the webhook |
| `--branch-name` | No | string | None | Updated branch name |
| `--description` | No | string | None | Updated description |

**Output Schema:**
```json
{
    "webhook": {
        "webhookArn": "string",
        "webhookId": "string",
        "webhookUrl": "string",
        "branchName": "string",
        "description": "string",
        "createTime": "timestamp",
        "updateTime": "timestamp"
    }
}
```
