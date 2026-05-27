# Graphs

### 1.1 `create-graph`

Creates a new behavior graph. The calling account becomes the administrator account.

**Synopsis:**
```bash
aws detective create-graph \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tags` | No | map | None | Tags to add to the behavior graph (max 50) |

**Output Schema:**
```json
{
    "GraphArn": "string"
}
```

---

### 1.2 `delete-graph`

Deletes a behavior graph and all data associated with it. Only the administrator account can delete.

**Synopsis:**
```bash
aws detective delete-graph \
    --graph-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-arn` | **Yes** | string | -- | ARN of the behavior graph to delete |

**Output:** None (HTTP 200 on success)

---

### 1.3 `list-graphs`

Lists the behavior graphs managed by the calling account. **Paginated operation.**

**Synopsis:**
```bash
aws detective list-graphs \
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
    "GraphList": [
        {
            "Arn": "string",
            "CreatedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
