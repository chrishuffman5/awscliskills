# Graph Endpoints (Neptune Analytics)

### 12.1 `create-private-graph-endpoint`

Creates a private endpoint for a Neptune Analytics graph in a VPC.

**Synopsis:**
```bash
aws neptune-graph create-private-graph-endpoint \
    --graph-identifier <value> \
    [--vpc-id <value>] \
    [--subnet-ids <value>] \
    [--vpc-security-group-ids <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-identifier` | **Yes** | string | -- | Graph ID |
| `--vpc-id` | No | string | -- | VPC ID (required if not using existing endpoint) |
| `--subnet-ids` | No | list(string) | -- | Subnet IDs for the endpoint |
| `--vpc-security-group-ids` | No | list(string) | -- | Security group IDs |

**Output Schema:**
```json
{
    "vpcId": "string",
    "subnetIds": ["string"],
    "status": "CREATING",
    "vpcEndpointId": "string"
}
```

---

### 12.2 `delete-private-graph-endpoint`

Deletes a private endpoint from a Neptune Analytics graph.

**Synopsis:**
```bash
aws neptune-graph delete-private-graph-endpoint \
    --graph-identifier <value> \
    --vpc-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-identifier` | **Yes** | string | -- | Graph ID |
| `--vpc-id` | **Yes** | string | -- | VPC ID of the endpoint to delete |

**Output Schema:**
```json
{
    "vpcId": "string",
    "subnetIds": ["string"],
    "status": "DELETING",
    "vpcEndpointId": "string"
}
```

---

### 12.3 `get-private-graph-endpoint`

Gets details about a private endpoint for a Neptune Analytics graph.

**Synopsis:**
```bash
aws neptune-graph get-private-graph-endpoint \
    --graph-identifier <value> \
    --vpc-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-identifier` | **Yes** | string | -- | Graph ID |
| `--vpc-id` | **Yes** | string | -- | VPC ID |

**Output Schema:**
```json
{
    "vpcId": "string",
    "subnetIds": ["string"],
    "status": "string",
    "vpcEndpointId": "string"
}
```

---

### 12.4 `list-private-graph-endpoints`

Lists private endpoints for a Neptune Analytics graph. **Paginated operation.**

**Synopsis:**
```bash
aws neptune-graph list-private-graph-endpoints \
    --graph-identifier <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-identifier` | **Yes** | string | -- | Graph ID |

**Output Schema:**
```json
{
    "privateGraphEndpoints": [
        {
            "vpcId": "string",
            "subnetIds": ["string"],
            "status": "string",
            "vpcEndpointId": "string"
        }
    ]
}
```
