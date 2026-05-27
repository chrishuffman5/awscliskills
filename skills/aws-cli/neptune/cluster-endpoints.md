# Cluster Endpoints

### 3.1 `create-db-cluster-endpoint`

Creates a custom endpoint for a Neptune DB cluster.

**Synopsis:**
```bash
aws neptune create-db-cluster-endpoint \
    --db-cluster-identifier <value> \
    --db-cluster-endpoint-identifier <value> \
    --endpoint-type <value> \
    [--static-members <value>] \
    [--excluded-members <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-identifier` | **Yes** | string | -- | Cluster identifier |
| `--db-cluster-endpoint-identifier` | **Yes** | string | -- | Custom endpoint identifier |
| `--endpoint-type` | **Yes** | string | -- | Endpoint type: `READER`, `ANY` |
| `--static-members` | No | list(string) | None | List of DB instance identifiers to include |
| `--excluded-members` | No | list(string) | None | List of DB instance identifiers to exclude |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "DBClusterEndpointIdentifier": "string",
    "DBClusterIdentifier": "string",
    "DBClusterEndpointResourceIdentifier": "string",
    "Endpoint": "string",
    "Status": "creating",
    "EndpointType": "string",
    "CustomEndpointType": "string",
    "StaticMembers": ["string"],
    "ExcludedMembers": ["string"],
    "DBClusterEndpointArn": "string"
}
```

---

### 3.2 `modify-db-cluster-endpoint`

Modifies a custom endpoint for a Neptune DB cluster.

**Synopsis:**
```bash
aws neptune modify-db-cluster-endpoint \
    --db-cluster-endpoint-identifier <value> \
    [--endpoint-type <value>] \
    [--static-members <value>] \
    [--excluded-members <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-endpoint-identifier` | **Yes** | string | -- | Custom endpoint identifier |
| `--endpoint-type` | No | string | -- | Updated endpoint type: `READER`, `ANY` |
| `--static-members` | No | list(string) | -- | Updated static members |
| `--excluded-members` | No | list(string) | -- | Updated excluded members |

**Output Schema:**
```json
{
    "DBClusterEndpointIdentifier": "string",
    "DBClusterIdentifier": "string",
    "Endpoint": "string",
    "Status": "modifying",
    "EndpointType": "string",
    "CustomEndpointType": "string",
    "StaticMembers": ["string"],
    "ExcludedMembers": ["string"],
    "DBClusterEndpointArn": "string"
}
```

---

### 3.3 `delete-db-cluster-endpoint`

Deletes a custom endpoint from a Neptune DB cluster.

**Synopsis:**
```bash
aws neptune delete-db-cluster-endpoint \
    --db-cluster-endpoint-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-endpoint-identifier` | **Yes** | string | -- | Custom endpoint identifier |

**Output Schema:**
```json
{
    "DBClusterEndpointIdentifier": "string",
    "DBClusterIdentifier": "string",
    "Endpoint": "string",
    "Status": "deleting",
    "EndpointType": "string",
    "DBClusterEndpointArn": "string"
}
```

---

### 3.4 `describe-db-cluster-endpoints`

Describes custom endpoints for a Neptune DB cluster. **Paginated operation.**

**Synopsis:**
```bash
aws neptune describe-db-cluster-endpoints \
    [--db-cluster-identifier <value>] \
    [--db-cluster-endpoint-identifier <value>] \
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
| `--db-cluster-identifier` | No | string | -- | Filter by cluster identifier |
| `--db-cluster-endpoint-identifier` | No | string | -- | Specific endpoint to describe |
| `--filters` | No | list | None | Filters |

**Output Schema:**
```json
{
    "DBClusterEndpoints": [
        {
            "DBClusterEndpointIdentifier": "string",
            "DBClusterIdentifier": "string",
            "DBClusterEndpointResourceIdentifier": "string",
            "Endpoint": "string",
            "Status": "string",
            "EndpointType": "string",
            "CustomEndpointType": "string",
            "StaticMembers": ["string"],
            "ExcludedMembers": ["string"],
            "DBClusterEndpointArn": "string"
        }
    ]
}
```
