# Log Sources

### 2.1 `create-aws-log-source`

Adds a natively-supported AWS service as a log source in Amazon Security Lake.

**Synopsis:**
```bash
aws securitylake create-aws-log-source \
    --sources <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sources` | **Yes** | list(structure) | -- | AWS services to enable as sources (min 1, max 50) |

**Sources Structure:**
```json
{
    "accounts": ["string"],
    "regions": ["string"],
    "sourceName": "ROUTE53|VPC_FLOW|SH_FINDINGS|CLOUD_TRAIL_MGMT|LAMBDA_EXECUTION|S3_DATA|EKS_AUDIT|WAF",
    "sourceVersion": "string"
}
```

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `accounts` | No | list(string) | AWS account IDs (12 digits) to enable. Omit for all accounts |
| `regions` | **Yes** | list(string) | AWS regions to enable the source in |
| `sourceName` | **Yes** | string | Name of the AWS source to enable |
| `sourceVersion` | No | string | Source version (e.g., `2.0` or `latest`) |

**Output Schema:**
```json
{
    "failed": ["string"]
}
```

The `failed` array contains account IDs where enabling the source failed (e.g., accounts not part of the organization).

---

### 2.2 `delete-aws-log-source`

Removes a natively-supported AWS service as a log source from Security Lake.

**Synopsis:**
```bash
aws securitylake delete-aws-log-source \
    --sources <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sources` | **Yes** | list(structure) | -- | AWS services to disable as sources (same structure as create) |

**Output Schema:**
```json
{
    "failed": ["string"]
}
```

---

### 2.3 `create-custom-log-source`

Adds a custom source to Security Lake, enabling you to ingest data from third-party sources.

**Synopsis:**
```bash
aws securitylake create-custom-log-source \
    --source-name <value> \
    [--source-version <value>] \
    [--configuration <value>] \
    [--event-classes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-name` | **Yes** | string | -- | Name for the custom source (1-64 chars) |
| `--source-version` | No | string | None | Version for the custom source (1-32 chars) |
| `--configuration` | No | structure | None | Configuration for the custom source |
| `--event-classes` | No | list(string) | None | OCSF event classes to collect |

**Configuration Structure:**
```json
{
    "crawlerConfiguration": {
        "roleArn": "string"
    },
    "providerIdentity": {
        "externalId": "string",
        "principal": "string"
    }
}
```

**Output Schema:**
```json
{
    "source": {
        "attributes": {
            "crawlerArn": "string",
            "databaseArn": "string",
            "tableArn": "string"
        },
        "provider": {
            "location": "string",
            "roleArn": "string"
        },
        "sourceName": "string",
        "sourceVersion": "string"
    }
}
```

---

### 2.4 `delete-custom-log-source`

Removes a custom log source from Security Lake.

**Synopsis:**
```bash
aws securitylake delete-custom-log-source \
    --source-name <value> \
    [--source-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-name` | **Yes** | string | -- | Name of the custom source to remove |
| `--source-version` | No | string | None | Version of the custom source to remove |

**Output Schema:**

No output on success (HTTP 200).

---

### 2.5 `list-log-sources`

Lists the log sources enabled in Security Lake. **Paginated operation.**

**Synopsis:**
```bash
aws securitylake list-log-sources \
    [--accounts <value>] \
    [--regions <value>] \
    [--sources <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--accounts` | No | list(string) | All accounts | AWS account IDs to list sources for |
| `--regions` | No | list(string) | All regions | AWS regions to list sources for |
| `--sources` | No | list(structure) | All sources | Filter by specific sources |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "account": "string",
    "region": "string",
    "sources": [
        {
            "awsLogSource": {
                "sourceName": "string",
                "sourceVersion": "string"
            },
            "customLogSource": {
                "attributes": {
                    "crawlerArn": "string",
                    "databaseArn": "string",
                    "tableArn": "string"
                },
                "provider": {
                    "location": "string",
                    "roleArn": "string"
                },
                "sourceName": "string",
                "sourceVersion": "string"
            }
        }
    ],
    "nextToken": "string"
}
```
