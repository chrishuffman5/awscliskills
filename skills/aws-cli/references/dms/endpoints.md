# Endpoints

### 2.1 `create-endpoint`

Creates an endpoint using the provided settings.

**Synopsis:**
```bash
aws dms create-endpoint \
    --endpoint-identifier <value> \
    --endpoint-type <value> \
    --engine-name <value> \
    [--username <value>] \
    [--password <value>] \
    [--server-name <value>] \
    [--port <value>] \
    [--database-name <value>] \
    [--extra-connection-attributes <value>] \
    [--kms-key-id <value>] \
    [--tags <value>] \
    [--certificate-arn <value>] \
    [--ssl-mode <value>] \
    [--service-access-role-arn <value>] \
    [--external-table-definition <value>] \
    [--resource-identifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-identifier` | **Yes** | string | -- | Endpoint identifier (ASCII letters, digits, hyphens) |
| `--endpoint-type` | **Yes** | string | -- | Endpoint type: `source` or `target` |
| `--engine-name` | **Yes** | string | -- | Engine type (see Engine Names below) |
| `--username` | No | string | -- | Database username |
| `--password` | No | string | -- | Database password |
| `--server-name` | No | string | -- | Server hostname |
| `--port` | No | integer | -- | Database port |
| `--database-name` | No | string | -- | Database name |
| `--extra-connection-attributes` | No | string | -- | Additional attributes (semicolon-separated `name=value`) |
| `--kms-key-id` | No | string | Account default | KMS key for encrypting connection parameters |
| `--tags` | No | list | -- | Tags: `key=string,value=string ...` |
| `--certificate-arn` | No | string | -- | ARN of the certificate for SSL |
| `--ssl-mode` | No | string | `none` | SSL mode: `none`, `require`, `verify-ca`, `verify-full` |
| `--service-access-role-arn` | No | string | -- | Service access IAM role ARN |
| `--external-table-definition` | No | string | -- | External table definition |
| `--resource-identifier` | No | string | Auto-generated | Friendly ARN identifier |

**Engine Names:** `mysql`, `oracle`, `postgres`, `mariadb`, `aurora`, `aurora-postgresql`, `opensearch`, `redshift`, `redshift-serverless`, `s3`, `db2`, `db2-zos`, `azuredb`, `sybase`, `dynamodb`, `mongodb`, `kinesis`, `kafka`, `elasticsearch`, `docdb`, `sqlserver`, `neptune`, `babelfish`, `redis`, `dms-transfer`

**Engine-Specific Settings:** Each engine has a dedicated `--<engine>-settings` parameter (e.g., `--my-sql-settings`, `--oracle-settings`, `--s3-settings`, `--kinesis-settings`, `--kafka-settings`, `--redshift-settings`, `--postgre-sql-settings`, `--dynamo-db-settings`, `--mongo-db-settings`, `--elasticsearch-settings`, `--neptune-settings`, `--redis-settings`, `--doc-db-settings`, `--microsoft-sql-server-settings`, `--ibm-db2-settings`, `--sybase-settings`).

**Output Schema:**
```json
{
    "Endpoint": {
        "EndpointIdentifier": "string",
        "EndpointType": "source|target",
        "EngineName": "string",
        "EngineDisplayName": "string",
        "Username": "string",
        "ServerName": "string",
        "Port": "integer",
        "DatabaseName": "string",
        "ExtraConnectionAttributes": "string",
        "Status": "string",
        "KmsKeyId": "string",
        "EndpointArn": "string",
        "CertificateArn": "string",
        "SslMode": "none|require|verify-ca|verify-full",
        "ServiceAccessRoleArn": "string",
        "ExternalTableDefinition": "string",
        "ExternalId": "string"
    }
}
```

---

### 2.2 `delete-endpoint`

Deletes the specified endpoint.

**Synopsis:**
```bash
aws dms delete-endpoint \
    --endpoint-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-arn` | **Yes** | string | -- | ARN of the endpoint to delete |

**Output Schema:** Same as `create-endpoint`.

---

### 2.3 `describe-endpoints`

Returns information about the endpoints. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-endpoints \
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
| `--filters` | No | list | -- | Filters: `endpoint-arn`, `endpoint-type`, `endpoint-id`, `engine-name` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Marker": "string",
    "Endpoints": [
        {
            "EndpointIdentifier": "string",
            "EndpointType": "source|target",
            "EngineName": "string",
            "EngineDisplayName": "string",
            "Username": "string",
            "ServerName": "string",
            "Port": "integer",
            "DatabaseName": "string",
            "ExtraConnectionAttributes": "string",
            "Status": "string",
            "KmsKeyId": "string",
            "EndpointArn": "string",
            "CertificateArn": "string",
            "SslMode": "string",
            "ServiceAccessRoleArn": "string",
            "ExternalTableDefinition": "string",
            "ExternalId": "string",
            "IsReadOnly": "boolean"
        }
    ]
}
```

---

### 2.4 `modify-endpoint`

Modifies the specified endpoint.

**Synopsis:**
```bash
aws dms modify-endpoint \
    --endpoint-arn <value> \
    [--endpoint-identifier <value>] \
    [--endpoint-type <value>] \
    [--engine-name <value>] \
    [--username <value>] \
    [--password <value>] \
    [--server-name <value>] \
    [--port <value>] \
    [--database-name <value>] \
    [--extra-connection-attributes <value>] \
    [--certificate-arn <value>] \
    [--ssl-mode <value>] \
    [--service-access-role-arn <value>] \
    [--external-table-definition <value>] \
    [--exact-settings | --no-exact-settings] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-arn` | **Yes** | string | -- | ARN of the endpoint to modify |
| `--endpoint-identifier` | No | string | -- | New endpoint identifier |
| `--endpoint-type` | No | string | -- | New endpoint type |
| `--engine-name` | No | string | -- | New engine name |
| `--username` | No | string | -- | New username |
| `--password` | No | string | -- | New password |
| `--server-name` | No | string | -- | New server hostname |
| `--port` | No | integer | -- | New port number |
| `--database-name` | No | string | -- | New database name |
| `--extra-connection-attributes` | No | string | -- | New extra connection attributes |
| `--certificate-arn` | No | string | -- | New certificate ARN |
| `--ssl-mode` | No | string | -- | New SSL mode |
| `--exact-settings` | No | boolean | -- | Use exact settings (removes undeclared engine-specific settings) |

**Output Schema:** Same as `create-endpoint`.

---

### 2.5 `describe-endpoint-settings`

Returns information about possible endpoint settings for a specified database engine. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-endpoint-settings \
    --engine-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--engine-name` | **Yes** | string | -- | Database engine name |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Marker": "string",
    "EndpointSettings": [
        {
            "Name": "string",
            "Type": "string",
            "EnumValues": ["string"],
            "Sensitive": "boolean",
            "Units": "string",
            "Applicability": "string",
            "IntValueMin": "integer",
            "IntValueMax": "integer",
            "DefaultValue": "string"
        }
    ]
}
```

---

### 2.6 `describe-endpoint-types`

Returns information about the type of endpoints available. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-endpoint-types \
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
| `--filters` | No | list | -- | Filters: `engine-name`, `endpoint-type` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Marker": "string",
    "SupportedEndpointTypes": [
        {
            "EngineName": "string",
            "SupportsCDC": "boolean",
            "EndpointType": "source|target",
            "ReplicationInstanceEngineMinimumVersion": "string",
            "EngineDisplayName": "string"
        }
    ]
}
```

---

### 2.7 `test-connection`

Tests the connection between the replication instance and the endpoint.

**Synopsis:**
```bash
aws dms test-connection \
    --replication-instance-arn <value> \
    --endpoint-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-instance-arn` | **Yes** | string | -- | ARN of the replication instance |
| `--endpoint-arn` | **Yes** | string | -- | ARN of the endpoint |

**Output Schema:**
```json
{
    "Connection": {
        "ReplicationInstanceArn": "string",
        "EndpointArn": "string",
        "Status": "string",
        "LastFailureMessage": "string",
        "EndpointIdentifier": "string",
        "ReplicationInstanceIdentifier": "string"
    }
}
```

---

### 2.8 `describe-connections`

Describes the status of the connections tested between the replication instance and an endpoint. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-connections \
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
| `--filters` | No | list | -- | Filters: `endpoint-arn`, `replication-instance-arn` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Marker": "string",
    "Connections": [
        {
            "ReplicationInstanceArn": "string",
            "EndpointArn": "string",
            "Status": "string",
            "LastFailureMessage": "string",
            "EndpointIdentifier": "string",
            "ReplicationInstanceIdentifier": "string"
        }
    ]
}
```

---

### 2.9 `delete-connection`

Deletes the connection between a replication instance and an endpoint.

**Synopsis:**
```bash
aws dms delete-connection \
    --endpoint-arn <value> \
    --replication-instance-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-arn` | **Yes** | string | -- | ARN of the endpoint |
| `--replication-instance-arn` | **Yes** | string | -- | ARN of the replication instance |

**Output Schema:**
```json
{
    "Connection": {
        "ReplicationInstanceArn": "string",
        "EndpointArn": "string",
        "Status": "string",
        "LastFailureMessage": "string",
        "EndpointIdentifier": "string",
        "ReplicationInstanceIdentifier": "string"
    }
}
```
