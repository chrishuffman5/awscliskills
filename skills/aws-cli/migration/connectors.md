# Connectors

### 6.1 `create-connector`

Creates a connector for agentless replication.

**Synopsis:**
```bash
aws mgn create-connector \
    --name <value> \
    --ssm-instance-id <value> \
    [--ssm-command-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Connector name (1-256 chars) |
| `--ssm-instance-id` | **Yes** | string | -- | SSM instance ID for the connector |
| `--ssm-command-config` | No | structure | None | SSM command config. Shorthand: `s3OutputEnabled=boolean,outputS3BucketName=string,cloudWatchOutputEnabled=boolean,cloudWatchLogGroupName=string` |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "connectorID": "string",
    "name": "string",
    "arn": "string",
    "ssmInstanceID": "string",
    "ssmCommandConfig": {
        "s3OutputEnabled": true|false,
        "outputS3BucketName": "string",
        "cloudWatchOutputEnabled": true|false,
        "cloudWatchLogGroupName": "string"
    },
    "tags": {"key": "value"}
}
```

---

### 6.2 `delete-connector`

Deletes a connector.

**Synopsis:**
```bash
aws mgn delete-connector \
    --connector-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connector-id` | **Yes** | string | -- | Connector ID |

**Output:** None

---

### 6.3 `list-connectors`

Lists connectors. **Paginated.**

**Synopsis:**
```bash
aws mgn list-connectors \
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
| `--filters` | No | structure | None | Filters: `connectorIDs=["string"]` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "items": [{"connectorID": "string", "...": "..."}],
    "nextToken": "string"
}
```

---

### 6.4 `update-connector`

Updates a connector.

**Synopsis:**
```bash
aws mgn update-connector \
    --connector-id <value> \
    [--name <value>] \
    [--ssm-command-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connector-id` | **Yes** | string | -- | Connector ID |
| `--name` | No | string | None | Updated name |
| `--ssm-command-config` | No | structure | None | Updated SSM command config |

**Output Schema:** Same as create-connector.
