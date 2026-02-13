# Connections

### 6.1 `create-connection`

Creates a connection definition in the Data Catalog.

**Synopsis:**
```bash
aws glue create-connection \
    --connection-input <value> \
    [--catalog-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-input` | **Yes** | structure | -- | Connection definition (JSON). Must include Name, ConnectionType, ConnectionProperties |
| `--catalog-id` | No | string | -- | Catalog ID |
| `--tags` | No | map | -- | Tags as JSON |

**Connection Types:** `JDBC`, `SFTP`, `MONGODB`, `KAFKA`, `NETWORK`, `MARKETPLACE`, `CUSTOM`, `SALESFORCE`, `VIEW_VALIDATION_REDSHIFT`, `VIEW_VALIDATION_ATHENA`

No output on success (returns `CreateConnectionResponse`).

---

### 6.2 `delete-connection`

Deletes a connection from the Data Catalog.

**Synopsis:**
```bash
aws glue delete-connection \
    --connection-name <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-name` | **Yes** | string | -- | Connection name |
| `--catalog-id` | No | string | -- | Catalog ID |

No output on success.

---

### 6.3 `get-connection`

Retrieves a connection definition.

**Synopsis:**
```bash
aws glue get-connection \
    --name <value> \
    [--catalog-id <value>] \
    [--hide-password | --no-hide-password] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Connection name |
| `--catalog-id` | No | string | -- | Catalog ID |
| `--hide-password` | No | boolean | true | Hide password in connection properties |

**Output Schema:**
```json
{
    "Connection": {
        "Name": "string",
        "Description": "string",
        "ConnectionType": "JDBC|SFTP|MONGODB|KAFKA|NETWORK|MARKETPLACE|CUSTOM|SALESFORCE",
        "MatchCriteria": ["string"],
        "ConnectionProperties": {
            "HOST": "string",
            "PORT": "string",
            "USERNAME": "string",
            "PASSWORD": "string",
            "JDBC_CONNECTION_URL": "string"
        },
        "PhysicalConnectionRequirements": {
            "SubnetId": "string",
            "SecurityGroupIdList": ["string"],
            "AvailabilityZone": "string"
        },
        "CreationTime": "timestamp",
        "LastUpdatedTime": "timestamp",
        "LastUpdatedBy": "string",
        "Status": "READY|IN_PROGRESS|FAILED",
        "StatusReason": "string",
        "LastConnectionValidationTime": "timestamp",
        "AuthenticationConfiguration": {}
    }
}
```

---

### 6.4 `get-connections`

Retrieves all connections. **Paginated operation.**

**Synopsis:**
```bash
aws glue get-connections \
    [--catalog-id <value>] \
    [--filter <value>] \
    [--hide-password | --no-hide-password] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--catalog-id` | No | string | -- | Catalog ID |
| `--filter` | No | structure | -- | Filter criteria. Shorthand: `MatchCriteria=string,string,ConnectionType=string` |
| `--hide-password` | No | boolean | true | Hide passwords |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "ConnectionList": ["<Connection structure>"],
    "NextToken": "string"
}
```

---

### 6.5 `update-connection`

Updates a connection definition.

**Synopsis:**
```bash
aws glue update-connection \
    --name <value> \
    --connection-input <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Connection name |
| `--connection-input` | **Yes** | structure | -- | Updated connection definition (JSON) |
| `--catalog-id` | No | string | -- | Catalog ID |

No output on success.

---

### 6.6 `batch-delete-connection`

Deletes multiple connections in a batch.

**Synopsis:**
```bash
aws glue batch-delete-connection \
    --connection-name-list <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-name-list` | **Yes** | list(string) | -- | Connection names to delete |
| `--catalog-id` | No | string | -- | Catalog ID |

**Output Schema:**
```json
{
    "Succeeded": ["string"],
    "Errors": {
        "ConnectionName": {
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    }
}
```
