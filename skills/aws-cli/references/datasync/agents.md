# Agents

### 1.1 `create-agent`

Activates a DataSync agent that you deploy in your storage environment. The agent connects your on-premises storage to DataSync.

**Synopsis:**
```bash
aws datasync create-agent \
    --activation-key <value> \
    [--agent-name <value>] \
    [--tags <value>] \
    [--vpc-endpoint-id <value>] \
    [--subnet-arns <value>] \
    [--security-group-arns <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--activation-key` | **Yes** | string | -- | Agent activation key (format: `AAAAA-BBBBB-CCCCC-DDDDD-EEEEE`) |
| `--agent-name` | No | string | None | Agent name (max 256 chars) |
| `--tags` | No | list | None | Tags (max 50) |
| `--vpc-endpoint-id` | No | string | None | VPC endpoint ID for private connectivity |
| `--subnet-arns` | No | list(string) | None | Subnet ARN (max 1) for VPC endpoint |
| `--security-group-arns` | No | list(string) | None | Security group ARN (max 1) for VPC endpoint |

**Output Schema:**
```json
{
    "AgentArn": "string"
}
```

---

### 1.2 `delete-agent`

Deletes a DataSync agent.

**Synopsis:**
```bash
aws datasync delete-agent \
    --agent-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-arn` | **Yes** | string | -- | ARN of the agent to delete |

**Output:** None on success.

---

### 1.3 `describe-agent`

Gets details about a DataSync agent.

**Synopsis:**
```bash
aws datasync describe-agent \
    --agent-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-arn` | **Yes** | string | -- | ARN of the agent |

**Output Schema:**
```json
{
    "AgentArn": "string",
    "Name": "string",
    "Status": "ONLINE|OFFLINE",
    "LastConnectionTime": "timestamp",
    "CreationTime": "timestamp",
    "EndpointType": "PUBLIC|PRIVATE_LINK|FIPS",
    "PrivateLinkConfig": {
        "VpcEndpointId": "string",
        "PrivateLinkEndpoint": "string",
        "SubnetArns": ["string"],
        "SecurityGroupArns": ["string"]
    },
    "Platform": {
        "Version": "string"
    }
}
```

---

### 1.4 `list-agents`

Lists DataSync agents. **Paginated operation.**

**Synopsis:**
```bash
aws datasync list-agents \
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
    "Agents": [
        {
            "AgentArn": "string",
            "Name": "string",
            "Status": "ONLINE|OFFLINE",
            "Platform": {"Version": "string"}
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `update-agent`

Updates an agent's name.

**Synopsis:**
```bash
aws datasync update-agent \
    --agent-arn <value> \
    [--name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-arn` | **Yes** | string | -- | ARN of the agent |
| `--name` | No | string | None | New agent name (max 256 chars) |

**Output:** None on success.
