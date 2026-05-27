# Dev Endpoints

> **Note:** Development endpoints are a legacy feature. AWS recommends using interactive sessions or notebooks instead.

### 11.1 `create-dev-endpoint`

Creates a development endpoint.

**Synopsis:**
```bash
aws glue create-dev-endpoint \
    --endpoint-name <value> \
    --role-arn <value> \
    [--security-group-ids <value>] \
    [--subnet-id <value>] \
    [--public-key <value>] \
    [--public-keys <value>] \
    [--number-of-nodes <value>] \
    [--worker-type <value>] \
    [--glue-version <value>] \
    [--number-of-workers <value>] \
    [--extra-python-libs-s3-path <value>] \
    [--extra-jars-s3-path <value>] \
    [--security-configuration <value>] \
    [--tags <value>] \
    [--arguments <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-name` | **Yes** | string | -- | Endpoint name |
| `--role-arn` | **Yes** | string | -- | IAM role ARN |
| `--security-group-ids` | No | list(string) | -- | Security group IDs |
| `--subnet-id` | No | string | -- | Subnet ID |
| `--public-key` | No | string | -- | SSH public key |
| `--public-keys` | No | list(string) | -- | Multiple SSH public keys |
| `--number-of-nodes` | No | integer | -- | Number of nodes (mutually exclusive with WorkerType) |
| `--worker-type` | No | string | -- | `Standard`, `G.1X`, `G.2X` |
| `--glue-version` | No | string | -- | Glue version |
| `--number-of-workers` | No | integer | -- | Number of workers |
| `--extra-python-libs-s3-path` | No | string | -- | S3 path to extra Python libraries |
| `--extra-jars-s3-path` | No | string | -- | S3 path to extra JAR files |
| `--security-configuration` | No | string | -- | Security configuration name |
| `--tags` | No | map | -- | Tags as JSON |
| `--arguments` | No | map | -- | Arguments as JSON |

**Output Schema:**
```json
{
    "EndpointName": "string",
    "Status": "string",
    "SecurityGroupIds": ["string"],
    "SubnetId": "string",
    "RoleArn": "string",
    "YarnEndpointAddress": "string",
    "ZeppelinRemoteSparkInterpreterPort": "integer",
    "NumberOfNodes": "integer",
    "WorkerType": "string",
    "GlueVersion": "string",
    "NumberOfWorkers": "integer",
    "AvailabilityZone": "string",
    "VpcId": "string",
    "ExtraPythonLibsS3Path": "string",
    "ExtraJarsS3Path": "string",
    "FailureReason": "string",
    "SecurityConfiguration": "string",
    "CreatedTimestamp": "timestamp",
    "Arguments": {}
}
```

---

### 11.2 `delete-dev-endpoint`

Deletes a development endpoint.

**Synopsis:**
```bash
aws glue delete-dev-endpoint \
    --endpoint-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-name` | **Yes** | string | -- | Endpoint name |

No output on success.

---

### 11.3 `get-dev-endpoint`

Retrieves a development endpoint.

**Synopsis:**
```bash
aws glue get-dev-endpoint \
    --endpoint-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-name` | **Yes** | string | -- | Endpoint name |

**Output Schema:**
```json
{
    "DevEndpoint": {
        "EndpointName": "string",
        "RoleArn": "string",
        "SecurityGroupIds": ["string"],
        "SubnetId": "string",
        "YarnEndpointAddress": "string",
        "PrivateAddress": "string",
        "ZeppelinRemoteSparkInterpreterPort": "integer",
        "PublicAddress": "string",
        "Status": "string",
        "WorkerType": "string",
        "GlueVersion": "string",
        "NumberOfWorkers": "integer",
        "NumberOfNodes": "integer",
        "AvailabilityZone": "string",
        "VpcId": "string",
        "ExtraPythonLibsS3Path": "string",
        "ExtraJarsS3Path": "string",
        "FailureReason": "string",
        "LastUpdateStatus": "string",
        "CreatedTimestamp": "timestamp",
        "LastModifiedTimestamp": "timestamp",
        "PublicKey": "string",
        "PublicKeys": ["string"],
        "SecurityConfiguration": "string",
        "Arguments": {}
    }
}
```

---

### 11.4 `get-dev-endpoints`

Retrieves all development endpoints. **Paginated operation.**

**Synopsis:**
```bash
aws glue get-dev-endpoints \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "DevEndpoints": ["<DevEndpoint structure>"],
    "NextToken": "string"
}
```

---

### 11.5 `update-dev-endpoint`

Updates a development endpoint.

**Synopsis:**
```bash
aws glue update-dev-endpoint \
    --endpoint-name <value> \
    [--public-key <value>] \
    [--add-public-keys <value>] \
    [--delete-public-keys <value>] \
    [--custom-libraries <value>] \
    [--update-etl-libraries | --no-update-etl-libraries] \
    [--delete-arguments <value>] \
    [--add-arguments <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-name` | **Yes** | string | -- | Endpoint name |
| `--public-key` | No | string | -- | New public key |
| `--add-public-keys` | No | list(string) | -- | Public keys to add |
| `--delete-public-keys` | No | list(string) | -- | Public keys to remove |
| `--custom-libraries` | No | structure | -- | Custom libraries. Shorthand: `ExtraPythonLibsS3Path=string,ExtraJarsS3Path=string` |
| `--update-etl-libraries` | No | boolean | -- | Update ETL libraries |
| `--delete-arguments` | No | list(string) | -- | Argument keys to delete |
| `--add-arguments` | No | map | -- | Arguments to add |

No output on success.

---

### 11.6 `batch-get-dev-endpoints`

Returns detailed information for a list of development endpoints.

**Synopsis:**
```bash
aws glue batch-get-dev-endpoints \
    --dev-endpoint-names <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dev-endpoint-names` | **Yes** | list(string) | -- | Endpoint names |

**Output Schema:**
```json
{
    "DevEndpoints": ["<DevEndpoint structure>"],
    "DevEndpointsNotFound": ["string"]
}
```

---

### 11.7 `list-dev-endpoints`

Lists development endpoint names. **Paginated operation.**

**Synopsis:**
```bash
aws glue list-dev-endpoints \
    [--tags <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tags` | No | map | -- | Filter by tags |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "DevEndpointNames": ["string"],
    "NextToken": "string"
}
```
