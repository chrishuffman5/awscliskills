# Coverage

### 5.1 `list-coverage`

Lists the coverage details for resources in your environment. **Paginated.**

**Synopsis:**
```bash
aws inspector2 list-coverage \
    [--filter-criteria <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter-criteria` | No | structure | None | Coverage filter criteria (JSON) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Criteria Fields:**

String filters (comparison: `EQUALS`, `NOT_EQUALS`):
- `accountId`, `resourceId`, `resourceType`, `scanStatusCode`, `scanStatusReason`, `scanType`
- `ecrRepositoryName`, `ecrImageTags`, `lambdaFunctionName`, `lambdaFunctionRuntime`
- `scanMode`, `codeRepositoryProjectName`, `codeRepositoryProviderType`

Map filters:
- `ec2InstanceTags`, `lambdaFunctionTags`

Date range filters:
- `lastScannedAt`, `imagePulledAt`, `ecrImageLastInUseAt`

Number filters:
- `ecrImageInUseCount`

**Output Schema:**
```json
{
    "coveredResources": [
        {
            "resourceType": "AWS_EC2_INSTANCE|AWS_ECR_CONTAINER_IMAGE|AWS_ECR_REPOSITORY|AWS_LAMBDA_FUNCTION|CODE_REPOSITORY",
            "resourceId": "string",
            "accountId": "string",
            "scanType": "NETWORK|PACKAGE|CODE",
            "scanStatus": {
                "statusCode": "ACTIVE|INACTIVE",
                "reason": "PENDING_INITIAL_SCAN|ACCESS_DENIED|SUCCESSFUL|..."
            },
            "resourceMetadata": {
                "ecrRepository": {
                    "name": "string",
                    "scanFrequency": "MANUAL|SCAN_ON_PUSH|CONTINUOUS_SCAN"
                },
                "ecrImage": {
                    "tags": ["string"],
                    "imagePulledAt": "timestamp",
                    "lastInUseAt": "timestamp",
                    "inUseCount": "long"
                },
                "ec2": {
                    "tags": {"key": "value"},
                    "amiId": "string",
                    "platform": "WINDOWS|LINUX|UNKNOWN|MACOS"
                },
                "lambdaFunction": {
                    "functionTags": {"key": "value"},
                    "layers": ["string"],
                    "functionName": "string",
                    "runtime": "string"
                },
                "codeRepository": {
                    "projectName": "string",
                    "integrationArn": "string",
                    "providerType": "string"
                }
            },
            "lastScannedAt": "timestamp",
            "scanMode": "EC2_SSM_AGENT_BASED|EC2_AGENTLESS"
        }
    ],
    "nextToken": "string"
}
```

---

### 5.2 `list-coverage-statistics`

Lists coverage statistics grouped by a specified category. **Paginated.**

**Synopsis:**
```bash
aws inspector2 list-coverage-statistics \
    [--filter-criteria <value>] \
    [--group-by <value>] \
    [--starting-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter-criteria` | No | structure | None | Same filter criteria as `list-coverage` |
| `--group-by` | No | string | None | Group by: `SCAN_STATUS_CODE`, `SCAN_STATUS_REASON`, `ACCOUNT_ID`, `RESOURCE_TYPE`, `ECR_REPOSITORY_NAME` |
| `--starting-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "totalCounts": "long",
    "countsByGroup": [
        {
            "count": "long",
            "groupKey": "SCAN_STATUS_CODE|SCAN_STATUS_REASON|ACCOUNT_ID|RESOURCE_TYPE|ECR_REPOSITORY_NAME"
        }
    ],
    "nextToken": "string"
}
```

---

### 5.3 `get-clusters-for-image`

Gets the ECS clusters that are running a specified container image.

**Synopsis:**
```bash
aws inspector2 get-clusters-for-image \
    --image-hash <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--image-hash` | **Yes** | string | -- | The SHA256 hash of the container image |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "clusterDetails": [
        {
            "clusterArn": "string",
            "taskArn": "string",
            "serviceArn": "string"
        }
    ],
    "nextToken": "string"
}
```
