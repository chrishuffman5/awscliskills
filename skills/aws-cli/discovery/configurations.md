# Configurations

### 2.1 `describe-configurations`

Retrieves attributes for specified configuration IDs.

**Synopsis:**
```bash
aws discovery describe-configurations \
    --configuration-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-ids` | **Yes** | list(string) | -- | Configuration IDs to describe (max 200) |

**Output Schema:**
```json
{
    "configurations": [
        {
            "key": "string",
            "value": "string"
        }
    ]
}
```

> **Note:** Output fields vary by asset type (server, application, process, connection). For servers: hostname, OS, CPU, RAM, network interfaces. For applications: name, description, server count.

---

### 2.2 `list-configurations`

Lists configurations by type with optional filtering and sorting. **Paginated operation.**

**Synopsis:**
```bash
aws discovery list-configurations \
    --configuration-type <value> \
    [--filters <value>] \
    [--order-by <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-type` | **Yes** | string | -- | `SERVER`, `PROCESS`, `CONNECTION`, or `APPLICATION` |
| `--filters` | No | list | None | Filter results (name, values, condition) |
| `--order-by` | No | list | None | Sort results (fieldName, sortOrder) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Structure (shorthand):**
```
name=string,values=string,string,condition=EQUALS|NOT_EQUALS|CONTAINS|NOT_CONTAINS
```

**Order By Structure (shorthand):**
```
fieldName=string,sortOrder=ASC|DESC
```

**Output Schema:**
```json
{
    "configurations": [
        {
            "key": "string",
            "value": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.3 `list-server-neighbors`

Lists server network dependencies (one-hop connections).

**Synopsis:**
```bash
aws discovery list-server-neighbors \
    --configuration-id <value> \
    [--port-information-needed | --no-port-information-needed] \
    [--neighbor-configuration-ids <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-id` | **Yes** | string | -- | Server configuration ID |
| `--port-information-needed` | No | boolean | false | Include port and protocol info |
| `--neighbor-configuration-ids` | No | list(string) | None | Filter to specific neighbor IDs |
| `--max-results` | No | integer | None | Maximum results per page |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "neighbors": [
        {
            "sourceServerId": "string",
            "destinationServerId": "string",
            "destinationPort": "integer",
            "transportProtocol": "string",
            "connectionsCount": "long"
        }
    ],
    "nextToken": "string",
    "knownDependencyCount": "long"
}
```

---

### 2.4 `get-discovery-summary`

Retrieves summary of discovered servers, applications, agents, and collectors.

**Synopsis:**
```bash
aws discovery get-discovery-summary \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No required parameters.

**Output Schema:**
```json
{
    "servers": "long",
    "applications": "long",
    "serversMappedToApplications": "long",
    "serversMappedtoTags": "long",
    "agentSummary": {
        "activeAgents": "integer",
        "healthyAgents": "integer",
        "blackListedAgents": "integer",
        "shutdownAgents": "integer",
        "unhealthyAgents": "integer",
        "totalAgents": "integer",
        "unknownAgents": "integer"
    },
    "connectorSummary": {
        "activeConnectors": "integer",
        "healthyConnectors": "integer",
        "blackListedConnectors": "integer",
        "shutdownConnectors": "integer",
        "unhealthyConnectors": "integer",
        "totalConnectors": "integer",
        "unknownConnectors": "integer"
    },
    "meCollectorSummary": {
        "activeMeCollectors": "integer",
        "healthyMeCollectors": "integer",
        "denyListedMeCollectors": "integer",
        "shutdownMeCollectors": "integer",
        "unhealthyMeCollectors": "integer",
        "totalMeCollectors": "integer",
        "unknownMeCollectors": "integer"
    },
    "agentlessCollectorSummary": {
        "activeAgentlessCollectors": "integer",
        "healthyAgentlessCollectors": "integer",
        "denyListedAgentlessCollectors": "integer",
        "shutdownAgentlessCollectors": "integer",
        "unhealthyAgentlessCollectors": "integer",
        "totalAgentlessCollectors": "integer",
        "unknownAgentlessCollectors": "integer"
    }
}
```

---

### 2.5 `start-batch-delete-configuration-task`

Starts a batch deletion of configuration items (currently supports SERVER type only).

**Synopsis:**
```bash
aws discovery start-batch-delete-configuration-task \
    --configuration-type <value> \
    --configuration-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-type` | **Yes** | string | -- | `SERVER` (currently only supported type) |
| `--configuration-ids` | **Yes** | list(string) | -- | Configuration IDs to delete (max 200) |

**Output Schema:**
```json
{
    "taskId": "string"
}
```

---

### 2.6 `describe-batch-delete-configuration-task`

Describes a batch deletion task.

**Synopsis:**
```bash
aws discovery describe-batch-delete-configuration-task \
    --task-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-id` | **Yes** | string | -- | Task ID from start-batch-delete-configuration-task |

**Output Schema:**
```json
{
    "task": {
        "taskId": "string",
        "status": "INITIALIZING|VALIDATING|DELETING|COMPLETED|FAILED",
        "startTime": "timestamp",
        "endTime": "timestamp",
        "configurationType": "SERVER",
        "requestedConfigurations": ["string"],
        "deletedConfigurations": ["string"],
        "failedConfigurations": [
            {
                "configurationId": "string",
                "errorStatusCode": "integer",
                "errorMessage": "string"
            }
        ]
    }
}
```
