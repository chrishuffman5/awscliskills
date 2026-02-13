# Data Sources

### 8.1 `create-data-source`

Creates a data source connection to an external data store (RDS, Redshift, S3, Athena, etc.).

**Synopsis:**
```bash
aws quicksight create-data-source \
    --aws-account-id <value> \
    --data-source-id <value> \
    --name <value> \
    --type <value> \
    [--data-source-parameters <value>] \
    [--credentials <value>] \
    [--permissions <value>] \
    [--vpc-connection-properties <value>] \
    [--ssl-properties <value>] \
    [--tags <value>] \
    [--folder-arns <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--data-source-id` | **Yes** | string | -- | Data source ID |
| `--name` | **Yes** | string | -- | Display name (1-128 chars) |
| `--type` | **Yes** | string | -- | Data source type (see Common Data Source Types in index.md) |
| `--data-source-parameters` | No | structure | None | Connection parameters (varies by type) |
| `--credentials` | No | structure | None | Credentials for the data source |
| `--permissions` | No | list | None | Resource permissions |
| `--vpc-connection-properties` | No | structure | None | VPC connection ARN |
| `--ssl-properties` | No | structure | None | SSL settings. `{"DisableSsl":true|false}` |
| `--tags` | No | list | None | Resource tags |
| `--folder-arns` | No | list(string) | None | Folder ARNs |

**Credentials Structure:**
```json
{
    "CredentialPair": {
        "Username": "string",
        "Password": "string",
        "AlternateDataSourceParameters": []
    },
    "CopySourceArn": "string",
    "SecretArn": "string"
}
```

**Data Source Parameters Examples:**

*RDS/Aurora:*
```json
{
    "RdsParameters": {
        "InstanceId": "string",
        "Database": "string"
    }
}
```

*Redshift:*
```json
{
    "RedshiftParameters": {
        "Host": "string",
        "Port": "integer",
        "Database": "string",
        "ClusterId": "string"
    }
}
```

*Athena:*
```json
{
    "AthenaParameters": {
        "WorkGroup": "string",
        "RoleArn": "string"
    }
}
```

*S3:*
```json
{
    "S3Parameters": {
        "ManifestFileLocation": {
            "Bucket": "string",
            "Key": "string"
        },
        "RoleArn": "string"
    }
}
```

**Output Schema:**
```json
{
    "Arn": "string",
    "DataSourceId": "string",
    "CreationStatus": "CREATION_IN_PROGRESS|CREATION_SUCCESSFUL|CREATION_FAILED|UPDATE_IN_PROGRESS|UPDATE_SUCCESSFUL|UPDATE_FAILED|DELETED",
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 8.2 `describe-data-source`

Describes a data source.

**Synopsis:**
```bash
aws quicksight describe-data-source \
    --aws-account-id <value> \
    --data-source-id <value>
```

**Output Schema:**
```json
{
    "DataSource": {
        "Arn": "string",
        "DataSourceId": "string",
        "Name": "string",
        "Type": "string",
        "Status": "CREATION_IN_PROGRESS|CREATION_SUCCESSFUL|CREATION_FAILED|UPDATE_IN_PROGRESS|UPDATE_SUCCESSFUL|UPDATE_FAILED|DELETED",
        "CreatedTime": "timestamp",
        "LastUpdatedTime": "timestamp",
        "DataSourceParameters": {},
        "AlternateDataSourceParameters": [],
        "VpcConnectionProperties": {
            "VpcConnectionArn": "string"
        },
        "SslProperties": {
            "DisableSsl": "boolean"
        },
        "ErrorInfo": {
            "Type": "string",
            "Message": "string"
        },
        "SecretArn": "string"
    },
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 8.3 `update-data-source`

Updates a data source.

**Synopsis:**
```bash
aws quicksight update-data-source \
    --aws-account-id <value> \
    --data-source-id <value> \
    --name <value> \
    [--data-source-parameters <value>] \
    [--credentials <value>] \
    [--vpc-connection-properties <value>] \
    [--ssl-properties <value>]
```

---

### 8.4 `delete-data-source`

Deletes a data source.

**Synopsis:**
```bash
aws quicksight delete-data-source \
    --aws-account-id <value> \
    --data-source-id <value>
```

---

### 8.5 `list-data-sources`

Lists data sources. **Paginated operation.**

**Synopsis:**
```bash
aws quicksight list-data-sources \
    --aws-account-id <value> \
    [--starting-token <value>] [--page-size <value>] [--max-items <value>]
```

---

### 8.6 `search-data-sources`

Searches data sources using filters. **Paginated operation.**

**Synopsis:**
```bash
aws quicksight search-data-sources \
    --aws-account-id <value> \
    --filters <value>
```

---

### 8.7 `describe-data-source-permissions` / `update-data-source-permissions`

Manage data source permissions.

**Synopsis:**
```bash
aws quicksight describe-data-source-permissions \
    --aws-account-id <value> --data-source-id <value>

aws quicksight update-data-source-permissions \
    --aws-account-id <value> --data-source-id <value> \
    [--grant-permissions <value>] [--revoke-permissions <value>]
```
