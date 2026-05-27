# Endpoints

### 8.1 `create-endpoint`

Creates a model endpoint for real-time inference using a custom document classifier or entity recognizer.

**Synopsis:**
```bash
aws comprehend create-endpoint \
    --endpoint-name <value> \
    --desired-inference-units <value> \
    [--model-arn <value>] \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--data-access-role-arn <value>] \
    [--flywheel-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-name` | **Yes** | string | -- | Name for the endpoint (max 40 chars, alphanumeric with hyphens) |
| `--desired-inference-units` | **Yes** | integer | -- | Number of inference units (each = 100 chars/second throughput). Min: 1 |
| `--model-arn` | No | string | -- | ARN of the model (document-classifier or entity-recognizer) to attach |
| `--client-request-token` | No | string | auto | Idempotency token (1-64 chars) |
| `--tags` | No | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |
| `--data-access-role-arn` | No | string | -- | IAM role ARN for accessing encrypted custom models |
| `--flywheel-arn` | No | string | -- | ARN of flywheel to attach |

**Output Schema:**
```json
{
    "EndpointArn": "string",
    "ModelArn": "string"
}
```

---

### 8.2 `delete-endpoint`

Deletes a model endpoint. All endpoints must be deleted before the associated model can be deleted.

**Synopsis:**
```bash
aws comprehend delete-endpoint \
    --endpoint-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-arn` | **Yes** | string | -- | ARN of the endpoint to delete |

**Output:** None (HTTP 200 on success)

---

### 8.3 `describe-endpoint`

Gets the properties associated with a specific endpoint.

**Synopsis:**
```bash
aws comprehend describe-endpoint \
    --endpoint-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-arn` | **Yes** | string | -- | ARN of the endpoint |

**Output Schema:**
```json
{
    "EndpointProperties": {
        "EndpointArn": "string",
        "Status": "CREATING|DELETING|FAILED|IN_SERVICE|UPDATING",
        "Message": "string",
        "ModelArn": "string",
        "DesiredModelArn": "string",
        "DesiredInferenceUnits": "integer",
        "CurrentInferenceUnits": "integer",
        "CreationTime": "timestamp",
        "LastModifiedTime": "timestamp",
        "DataAccessRoleArn": "string",
        "DesiredDataAccessRoleArn": "string",
        "FlywheelArn": "string"
    }
}
```

---

### 8.4 `list-endpoints`

Gets a list of all existing endpoints. **Paginated operation.**

**Synopsis:**
```bash
aws comprehend list-endpoints \
    [--filter <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter` | No | structure | -- | Filter by Status, ModelArn, CreationTimeBefore, CreationTimeAfter |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "EndpointPropertiesList": [
        {
            "EndpointArn": "string",
            "Status": "CREATING|DELETING|FAILED|IN_SERVICE|UPDATING",
            "ModelArn": "string",
            "DesiredInferenceUnits": "integer",
            "CurrentInferenceUnits": "integer",
            "CreationTime": "timestamp",
            "LastModifiedTime": "timestamp",
            "FlywheelArn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.5 `update-endpoint`

Updates the configuration of an existing endpoint, including model version and inference units.

**Synopsis:**
```bash
aws comprehend update-endpoint \
    --endpoint-arn <value> \
    [--desired-model-arn <value>] \
    [--desired-inference-units <value>] \
    [--desired-data-access-role-arn <value>] \
    [--flywheel-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-arn` | **Yes** | string | -- | ARN of the endpoint to update |
| `--desired-model-arn` | No | string | -- | ARN of the new model to use |
| `--desired-inference-units` | No | integer | -- | New number of inference units. Min: 1 |
| `--desired-data-access-role-arn` | No | string | -- | Data access role for encrypted models |
| `--flywheel-arn` | No | string | -- | ARN of the flywheel |

**Output Schema:**
```json
{
    "DesiredModelArn": "string"
}
```
