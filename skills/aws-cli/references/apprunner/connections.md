# Connections

### 2.1 `create-connection`

Creates a connection to a source code provider (GitHub).

**Synopsis:**
```bash
aws apprunner create-connection \
    --connection-name <value> \
    --provider-type <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-name` | **Yes** | string | -- | Name for the connection |
| `--provider-type` | **Yes** | string | -- | Provider type: `GITHUB`, `BITBUCKET` |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "Connection": {
        "ConnectionName": "string",
        "ConnectionArn": "string",
        "ProviderType": "GITHUB|BITBUCKET",
        "Status": "PENDING_HANDSHAKE|AVAILABLE|ERROR|DELETED",
        "CreatedAt": "timestamp"
    }
}
```

---

### 2.2 `delete-connection`

Deletes a connection.

**Synopsis:**
```bash
aws apprunner delete-connection \
    --connection-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-arn` | **Yes** | string | -- | ARN of the connection to delete |

**Output Schema:**
```json
{
    "Connection": {
        "ConnectionName": "string",
        "ConnectionArn": "string",
        "ProviderType": "GITHUB|BITBUCKET",
        "Status": "DELETED",
        "CreatedAt": "timestamp"
    }
}
```

---

### 2.3 `list-connections`

Lists connections. **Paginated operation.**

**Synopsis:**
```bash
aws apprunner list-connections \
    [--connection-name <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-name` | No | string | None | Filter by connection name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ConnectionSummaryList": [
        {
            "ConnectionName": "string",
            "ConnectionArn": "string",
            "ProviderType": "GITHUB|BITBUCKET",
            "Status": "PENDING_HANDSHAKE|AVAILABLE|ERROR|DELETED",
            "CreatedAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
