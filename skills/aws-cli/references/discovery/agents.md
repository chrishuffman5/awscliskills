# Agents

### 1.1 `describe-agents`

Lists agents or collectors associated with your account. **Paginated operation.**

**Synopsis:**
```bash
aws discovery describe-agents \
    [--agent-ids <value>] \
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
| `--agent-ids` | No | list(string) | None | Agent/collector IDs to query |
| `--filters` | No | list | None | Filter results (name, values, condition) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Structure (shorthand):**
```
name=string,values=string,string,condition=EQUALS|NOT_EQUALS|CONTAINS|NOT_CONTAINS
```

**Output Schema:**
```json
{
    "agentsInfo": [
        {
            "agentId": "string",
            "hostName": "string",
            "agentNetworkInfoList": [
                {
                    "ipAddress": "string",
                    "macAddress": "string"
                }
            ],
            "connectorId": "string",
            "version": "string",
            "health": "HEALTHY|UNHEALTHY|RUNNING|UNKNOWN|BLACKLISTED|SHUTDOWN",
            "lastHealthPingTime": "string",
            "collectionStatus": "string",
            "agentType": "string",
            "registeredTime": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.2 `start-data-collection-by-agent-ids`

Instructs specified agents to start collecting data.

**Synopsis:**
```bash
aws discovery start-data-collection-by-agent-ids \
    --agent-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-ids` | **Yes** | list(string) | -- | IDs of agents to start collecting data |

**Output Schema:**
```json
{
    "agentsConfigurationStatus": [
        {
            "agentId": "string",
            "operationSucceeded": "boolean",
            "description": "string"
        }
    ]
}
```

---

### 1.3 `stop-data-collection-by-agent-ids`

Instructs specified agents to stop collecting data.

**Synopsis:**
```bash
aws discovery stop-data-collection-by-agent-ids \
    --agent-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-ids` | **Yes** | list(string) | -- | IDs of agents to stop collecting data |

**Output Schema:**
```json
{
    "agentsConfigurationStatus": [
        {
            "agentId": "string",
            "operationSucceeded": "boolean",
            "description": "string"
        }
    ]
}
```

---

### 1.4 `batch-delete-agents`

Deletes one or more agents in batch (max 50).

**Synopsis:**
```bash
aws discovery batch-delete-agents \
    --delete-agents <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--delete-agents` | **Yes** | list | -- | Agents to delete (max 50) |

**Delete Agents Structure (shorthand):**
```
agentId=string,force=boolean ...
```

> **Note:** Use `force=true` to delete agents in HEALTHY, UNHEALTHY, or RUNNING status.

**Output Schema:**
```json
{
    "errors": [
        {
            "agentId": "string",
            "errorMessage": "string",
            "errorCode": "NOT_FOUND|INTERNAL_SERVER_ERROR|AGENT_IN_USE"
        }
    ]
}
```
