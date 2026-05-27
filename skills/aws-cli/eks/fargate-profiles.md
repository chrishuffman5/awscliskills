# Fargate Profiles

### 3.1 `create-fargate-profile`

Creates an AWS Fargate profile for your Amazon EKS cluster. Pods that match the selectors run on Fargate.

**Synopsis:**
```bash
aws eks create-fargate-profile \
    --fargate-profile-name <value> \
    --cluster-name <value> \
    --pod-execution-role-arn <value> \
    [--subnets <value>] \
    [--selectors <value>] \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fargate-profile-name` | **Yes** | string | -- | Fargate profile name |
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--pod-execution-role-arn` | **Yes** | string | -- | IAM role ARN for pod execution |
| `--subnets` | No | list(string) | None | Subnet IDs (private subnets only) |
| `--selectors` | No | list | None | Pod selectors. Shorthand: `namespace=string,labels={key=value,key2=value2} ...` |
| `--client-request-token` | No | string | None | Idempotency token |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "fargateProfile": {
        "fargateProfileName": "string",
        "fargateProfileArn": "string",
        "clusterName": "string",
        "createdAt": "timestamp",
        "podExecutionRoleArn": "string",
        "subnets": ["string"],
        "selectors": [
            {
                "namespace": "string",
                "labels": {"string": "string"}
            }
        ],
        "status": "CREATING|ACTIVE|DELETING|CREATE_FAILED|DELETE_FAILED",
        "tags": {"string": "string"}
    }
}
```

---

### 3.2 `delete-fargate-profile`

Deletes an AWS Fargate profile.

**Synopsis:**
```bash
aws eks delete-fargate-profile \
    --cluster-name <value> \
    --fargate-profile-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--fargate-profile-name` | **Yes** | string | -- | Fargate profile name |

**Output Schema:** Same fargateProfile object with status `DELETING`.

---

### 3.3 `describe-fargate-profile`

Returns descriptive information about an AWS Fargate profile.

**Synopsis:**
```bash
aws eks describe-fargate-profile \
    --cluster-name <value> \
    --fargate-profile-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--fargate-profile-name` | **Yes** | string | -- | Fargate profile name |

**Output Schema:** Same as `create-fargate-profile` output.

---

### 3.4 `list-fargate-profiles`

Lists the AWS Fargate profiles for a cluster. **Paginated operation.**

**Synopsis:**
```bash
aws eks list-fargate-profiles \
    --cluster-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "fargateProfileNames": ["string"],
    "nextToken": "string"
}
```
