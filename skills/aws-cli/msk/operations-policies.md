# Operations & Policies

## 8.1 `describe-cluster-operation`

Returns details for a cluster operation.

**Synopsis:**
```bash
aws kafka describe-cluster-operation \
    --cluster-operation-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-operation-arn` | **Yes** | string | -- | ARN of the cluster operation |

**Output Schema:**
```json
{
    "ClusterOperationInfo": {
        "ClientRequestId": "string",
        "ClusterArn": "string",
        "CreationTime": "timestamp",
        "EndTime": "timestamp",
        "ErrorInfo": {
            "ErrorCode": "string",
            "ErrorString": "string"
        },
        "OperationArn": "string",
        "OperationState": "string",
        "OperationSteps": [
            {
                "StepInfo": {
                    "StepStatus": "string"
                },
                "StepName": "string"
            }
        ],
        "OperationType": "string",
        "SourceClusterInfo": {},
        "TargetClusterInfo": {},
        "VpcConnectionInfo": {}
    }
}
```

---

## 8.2 `describe-cluster-operation-v2`

Returns details for a cluster operation using the v2 API.

**Synopsis:**
```bash
aws kafka describe-cluster-operation-v2 \
    --cluster-operation-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-operation-arn` | **Yes** | string | -- | ARN of the cluster operation |

**Output Schema:**
```json
{
    "ClusterOperationInfo": {
        "ClusterArn": "string",
        "ClusterType": "PROVISIONED|SERVERLESS",
        "StartTime": "timestamp",
        "EndTime": "timestamp",
        "ErrorInfo": {
            "ErrorCode": "string",
            "ErrorString": "string"
        },
        "OperationArn": "string",
        "OperationState": "string",
        "OperationType": "string",
        "Provisioned": {
            "OperationSteps": [],
            "SourceClusterInfo": {},
            "TargetClusterInfo": {},
            "VpcConnectionInfo": {}
        },
        "Serverless": {
            "VpcConnectionInfo": {}
        }
    }
}
```

---

## 8.3 `list-cluster-operations`

Lists cluster operations for a specified cluster. **Paginated operation.**

**Synopsis:**
```bash
aws kafka list-cluster-operations \
    --cluster-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ClusterOperationInfoList": [
        {
            "ClientRequestId": "string",
            "ClusterArn": "string",
            "CreationTime": "timestamp",
            "EndTime": "timestamp",
            "OperationArn": "string",
            "OperationState": "string",
            "OperationType": "string"
        }
    ],
    "NextToken": "string"
}
```

---

## 8.4 `list-cluster-operations-v2`

Lists cluster operations using the v2 API. **Paginated operation.**

**Synopsis:**
```bash
aws kafka list-cluster-operations-v2 \
    --cluster-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ClusterOperationInfoList": [
        {
            "ClusterArn": "string",
            "ClusterType": "PROVISIONED|SERVERLESS",
            "StartTime": "timestamp",
            "EndTime": "timestamp",
            "OperationArn": "string",
            "OperationState": "string",
            "OperationType": "string"
        }
    ],
    "NextToken": "string"
}
```

---

## 8.5 `get-cluster-policy`

Returns the cluster resource policy.

**Synopsis:**
```bash
aws kafka get-cluster-policy \
    --cluster-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |

**Output Schema:**
```json
{
    "CurrentVersion": "string",
    "Policy": "string"
}
```

---

## 8.6 `put-cluster-policy`

Sets a cluster resource policy (for cross-account access).

**Synopsis:**
```bash
aws kafka put-cluster-policy \
    --cluster-arn <value> \
    --policy <value> \
    [--current-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |
| `--policy` | **Yes** | string | -- | Resource policy JSON string |
| `--current-version` | No | string | None | Current policy version (for updates) |

**Output Schema:**
```json
{
    "CurrentVersion": "string"
}
```

---

## 8.7 `delete-cluster-policy`

Deletes the cluster resource policy.

**Synopsis:**
```bash
aws kafka delete-cluster-policy \
    --cluster-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |

**Output Schema:**

None (HTTP 200 on success).

---

## 8.8 `tag-resource`

Adds tags to an MSK resource.

**Synopsis:**
```bash
aws kafka tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tags` | **Yes** | map | -- | Key-value tags to add |

**Output Schema:**

None (HTTP 204 on success).

---

## 8.9 `untag-resource`

Removes tags from an MSK resource.

**Synopsis:**
```bash
aws kafka untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:**

None (HTTP 204 on success).

---

## 8.10 `list-tags-for-resource`

Lists tags for an MSK resource.

**Synopsis:**
```bash
aws kafka list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |

**Output Schema:**
```json
{
    "Tags": {
        "string": "string"
    }
}
```
