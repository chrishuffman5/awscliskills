# Security Scans

> **Note:** CodeGuru Security reached end of support in November 2025. These commands use `aws codeguru-security`.

### 4.1 `create-scan`

Creates a security scan for a resource. Uses `aws codeguru-security`.

**Synopsis:**
```bash
aws codeguru-security create-scan \
    --scan-name <value> \
    --resource-id <value> \
    [--scan-type <value>] \
    [--analysis-type <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scan-name` | **Yes** | string | -- | Name of the scan (unique per account and region) |
| `--resource-id` | **Yes** | structure | -- | Resource identifier. JSON: `{"ScanName":"string"}` or `{"CodeArtifactId":"string"}` |
| `--scan-type` | No | string | `Standard` | Type of scan: `Standard` or `Express` |
| `--analysis-type` | No | string | `Security` | Type of analysis: `Security` or `All` |
| `--client-token` | No | string | None | Unique idempotency token (auto-generated if not specified) |
| `--tags` | No | map | None | Tags to associate. Shorthand: `KeyName1=string,KeyName2=string` |

**Output Schema:**
```json
{
    "scanName": "string",
    "runId": "string",
    "resourceId": {
        "ScanName": "string",
        "CodeArtifactId": "string"
    },
    "scanState": "InProgress|Successful|Failed",
    "scanNameArn": "string"
}
```

---

### 4.2 `get-scan`

Returns details about a scan. Uses `aws codeguru-security`.

**Synopsis:**
```bash
aws codeguru-security get-scan \
    --scan-name <value> \
    [--run-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scan-name` | **Yes** | string | -- | Name of the scan to retrieve |
| `--run-id` | No | string | None | UUID of a specific scan run to retrieve |

**Output Schema:**
```json
{
    "scanName": "string",
    "runId": "string",
    "scanState": "InProgress|Successful|Failed",
    "createdAt": "timestamp",
    "updatedAt": "timestamp",
    "analysisType": "Security|All",
    "scanNameArn": "string",
    "numberOfRevisions": "long",
    "errorMessage": "string"
}
```

---

### 4.3 `list-scans`

Returns a list of all scans in an account. Uses `aws codeguru-security`. **Paginated operation.**

**Synopsis:**
```bash
aws codeguru-security list-scans \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "summaries": [
        {
            "scanName": "string",
            "runId": "string",
            "scanState": "InProgress|Successful|Failed",
            "createdAt": "timestamp",
            "updatedAt": "timestamp",
            "scanNameArn": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 4.4 `create-upload-url`

Generates a pre-signed URL and request headers for uploading code to be scanned. Uses `aws codeguru-security`.

**Synopsis:**
```bash
aws codeguru-security create-upload-url \
    --scan-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scan-name` | **Yes** | string | -- | Name of the scan to upload code for |

**Output Schema:**
```json
{
    "s3Url": "string",
    "requestHeaders": {
        "string": "string"
    },
    "codeArtifactId": "string"
}
```
