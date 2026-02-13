# Runtime

Commands in the `aws sagemaker-runtime` service for real-time and async inference.

---

## 1. `invoke-endpoint`

Invokes an endpoint for real-time inference. The response body is written to the specified output file.

**Synopsis:**
```bash
aws sagemaker-runtime invoke-endpoint \
    --endpoint-name <value> \
    --body <value> \
    <outfile> \
    [--content-type <value>] \
    [--accept <value>] \
    [--custom-attributes <value>] \
    [--target-model <value>] \
    [--target-variant <value>] \
    [--target-container-hostname <value>] \
    [--inference-id <value>] \
    [--enable-explanations <value>] \
    [--inference-component-name <value>] \
    [--session-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-name` | **Yes** | string | -- | Endpoint name (max 63 chars) |
| `--body` | **Yes** | blob | -- | Input data (max 6 MB) |
| `outfile` | **Yes** | string | -- | Output filename for response body |
| `--content-type` | No | string | -- | Input MIME type (max 1024 chars) |
| `--accept` | No | string | -- | Desired output MIME type |
| `--custom-attributes` | No | string | -- | Custom metadata (max 1024 chars) |
| `--target-model` | No | string | -- | Target model for multi-model endpoint |
| `--target-variant` | No | string | -- | Target production variant |
| `--target-container-hostname` | No | string | -- | Target container for direct invocation |
| `--inference-id` | No | string | -- | Identifier for data capture (max 64 chars) |
| `--enable-explanations` | No | string | -- | JMESPath expression for Clarify explainer |
| `--inference-component-name` | No | string | -- | Inference component name |
| `--session-id` | No | string | -- | Session ID or `NEW_SESSION` for stateful inference |

**Output Schema:**
```json
{
    "Body": "blob",
    "ContentType": "string",
    "InvokedProductionVariant": "string",
    "CustomAttributes": "string",
    "NewSessionId": "string",
    "ClosedSessionId": "string"
}
```

**Example:**
```bash
aws sagemaker-runtime invoke-endpoint \
    --endpoint-name my-endpoint \
    --content-type text/csv \
    --body '1.0,2.0,3.0,4.0' \
    output.json
```

**Constraints:**
- Request body: max 6 MB
- Model processing time: 60 seconds max
- Recommended SDK socket timeout: 70 seconds

---

## 2. `invoke-endpoint-async`

Invokes an endpoint asynchronously. Input and output are stored in S3.

**Synopsis:**
```bash
aws sagemaker-runtime invoke-endpoint-async \
    --endpoint-name <value> \
    --input-location <value> \
    [--content-type <value>] \
    [--accept <value>] \
    [--custom-attributes <value>] \
    [--inference-id <value>] \
    [--request-ttl-seconds <value>] \
    [--invocation-timeout-seconds <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-name` | **Yes** | string | -- | Endpoint name |
| `--input-location` | **Yes** | string | -- | S3 URI for input data |
| `--content-type` | No | string | -- | Input MIME type |
| `--accept` | No | string | -- | Desired output MIME type |
| `--custom-attributes` | No | string | -- | Custom metadata |
| `--inference-id` | No | string | -- | Identifier for tracking |
| `--request-ttl-seconds` | No | integer | -- | Request time-to-live (60-21600 seconds) |
| `--invocation-timeout-seconds` | No | integer | -- | Invocation timeout (1-3600 seconds) |

**Output Schema:**
```json
{
    "InferenceId": "string",
    "OutputLocation": "string",
    "FailureLocation": "string"
}
```

**Example:**
```bash
aws sagemaker-runtime invoke-endpoint-async \
    --endpoint-name my-async-endpoint \
    --input-location s3://bucket/input/data.csv \
    --content-type text/csv
```
