# Pod Identity

### 7.1 `create-pod-identity-association`

Creates an EKS Pod Identity association between a Kubernetes service account and an IAM role.

**Synopsis:**
```bash
aws eks create-pod-identity-association \
    --cluster-name <value> \
    --namespace <value> \
    --service-account <value> \
    --role-arn <value> \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--namespace` | **Yes** | string | -- | Kubernetes namespace |
| `--service-account` | **Yes** | string | -- | Kubernetes service account name |
| `--role-arn` | **Yes** | string | -- | IAM role ARN |
| `--client-request-token` | No | string | None | Idempotency token |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "association": {
        "clusterName": "string",
        "namespace": "string",
        "serviceAccount": "string",
        "roleArn": "string",
        "associationArn": "string",
        "associationId": "string",
        "tags": {"string": "string"},
        "createdAt": "timestamp",
        "modifiedAt": "timestamp",
        "ownerArn": "string"
    }
}
```

---

### 7.2 `delete-pod-identity-association`

Deletes a Pod Identity association.

**Synopsis:**
```bash
aws eks delete-pod-identity-association \
    --cluster-name <value> \
    --association-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--association-id` | **Yes** | string | -- | Association ID |

**Output Schema:** Same association object.

---

### 7.3 `describe-pod-identity-association`

Describes a Pod Identity association.

**Synopsis:**
```bash
aws eks describe-pod-identity-association \
    --cluster-name <value> \
    --association-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--association-id` | **Yes** | string | -- | Association ID |

**Output Schema:** Same as `create-pod-identity-association` output.

---

### 7.4 `list-pod-identity-associations`

Lists Pod Identity associations for a cluster. **Paginated operation.**

**Synopsis:**
```bash
aws eks list-pod-identity-associations \
    --cluster-name <value> \
    [--namespace <value>] \
    [--service-account <value>] \
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
| `--namespace` | No | string | None | Filter by namespace |
| `--service-account` | No | string | None | Filter by service account |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "associations": [
        {
            "clusterName": "string",
            "namespace": "string",
            "serviceAccount": "string",
            "associationArn": "string",
            "associationId": "string",
            "ownerArn": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 7.5 `update-pod-identity-association`

Updates a Pod Identity association.

**Synopsis:**
```bash
aws eks update-pod-identity-association \
    --cluster-name <value> \
    --association-id <value> \
    [--role-arn <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--association-id` | **Yes** | string | -- | Association ID |
| `--role-arn` | No | string | None | Updated IAM role ARN |
| `--client-request-token` | No | string | None | Idempotency token |

**Output Schema:** Same as `create-pod-identity-association` output.
