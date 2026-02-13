# EMR Containers — Security & Managed Endpoints (`aws emr-containers`)

### 13.1 `create-managed-endpoint`

Creates a managed endpoint (interactive endpoint) for a virtual cluster.

**Synopsis:**
```bash
aws emr-containers create-managed-endpoint \
    --virtual-cluster-id <value> \
    --name <value> \
    --type <value> \
    --release-label <value> \
    --execution-role-arn <value> \
    [--certificate-arn <value>] \
    [--configuration-overrides <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--virtual-cluster-id` | **Yes** | string | -- | Virtual cluster ID |
| `--name` | **Yes** | string | -- | Endpoint name |
| `--type` | **Yes** | string | -- | Endpoint type: `JUPYTER_ENTERPRISE_GATEWAY` |
| `--release-label` | **Yes** | string | -- | EMR release label |
| `--execution-role-arn` | **Yes** | string | -- | IAM execution role ARN |
| `--certificate-arn` | No | string | -- | ACM certificate ARN |
| `--configuration-overrides` | No | structure | -- | Configuration overrides (JSON) |
| `--client-token` | No | string | -- | Idempotency token |
| `--tags` | No | map | -- | Tags |

**Output Schema:**
```json
{
    "id": "string",
    "name": "string",
    "arn": "string",
    "virtualClusterId": "string"
}
```

---

### 13.2 `delete-managed-endpoint`

Deletes a managed endpoint.

**Synopsis:**
```bash
aws emr-containers delete-managed-endpoint \
    --id <value> \
    --virtual-cluster-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Endpoint ID |
| `--virtual-cluster-id` | **Yes** | string | -- | Virtual cluster ID |

**Output Schema:**
```json
{
    "id": "string",
    "virtualClusterId": "string"
}
```

---

### 13.3 `describe-managed-endpoint`

Describes a managed endpoint.

**Synopsis:**
```bash
aws emr-containers describe-managed-endpoint \
    --id <value> \
    --virtual-cluster-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Endpoint ID |
| `--virtual-cluster-id` | **Yes** | string | -- | Virtual cluster ID |

**Output Schema:**
```json
{
    "endpoint": {
        "id": "string",
        "name": "string",
        "arn": "string",
        "virtualClusterId": "string",
        "type": "JUPYTER_ENTERPRISE_GATEWAY",
        "state": "CREATING|ACTIVE|TERMINATING|TERMINATED|TERMINATED_WITH_ERRORS",
        "releaseLabel": "string",
        "executionRoleArn": "string",
        "certificateArn": "string",
        "certificateAuthority": {
            "certificateArn": "string",
            "certificateData": "string"
        },
        "configurationOverrides": {},
        "serverUrl": "string",
        "createdAt": "timestamp",
        "securityGroup": "string",
        "subnetIds": ["string"],
        "stateDetails": "string",
        "failureReason": "string",
        "tags": {}
    }
}
```

---

### 13.4 `list-managed-endpoints`

Lists managed endpoints. **Paginated operation.**

**Synopsis:**
```bash
aws emr-containers list-managed-endpoints \
    --virtual-cluster-id <value> \
    [--created-before <value>] \
    [--created-after <value>] \
    [--types <value>] \
    [--states <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--virtual-cluster-id` | **Yes** | string | -- | Virtual cluster ID |
| `--created-before` | No | timestamp | -- | Filter before this time |
| `--created-after` | No | timestamp | -- | Filter after this time |
| `--types` | No | list(string) | -- | Filter by type |
| `--states` | No | list(string) | -- | Filter by state |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "endpoints": [
        {
            "id": "string",
            "name": "string",
            "arn": "string",
            "virtualClusterId": "string",
            "type": "string",
            "state": "string",
            "releaseLabel": "string",
            "createdAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 13.5 `create-security-configuration`

Creates a security configuration for EMR on EKS.

**Synopsis:**
```bash
aws emr-containers create-security-configuration \
    --name <value> \
    --security-configuration-data <value> \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Configuration name |
| `--security-configuration-data` | **Yes** | structure | -- | Security configuration data (JSON) |
| `--client-token` | No | string | -- | Idempotency token |
| `--tags` | No | map | -- | Tags |

**Output Schema:**
```json
{
    "id": "string",
    "name": "string",
    "arn": "string"
}
```

---

### 13.6 `delete-security-configuration`

Deletes a security configuration for EMR on EKS.

**Synopsis:**
```bash
aws emr-containers delete-security-configuration \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Security configuration ID |

No output on success.

---

### 13.7 `describe-security-configuration`

Describes a security configuration.

**Synopsis:**
```bash
aws emr-containers describe-security-configuration \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Security configuration ID |

**Output Schema:**
```json
{
    "securityConfiguration": {
        "id": "string",
        "name": "string",
        "arn": "string",
        "securityConfigurationData": {},
        "tags": {},
        "createdAt": "timestamp",
        "createdBy": "string"
    }
}
```

---

### 13.8 `list-security-configurations`

Lists security configurations. **Paginated operation.**

**Synopsis:**
```bash
aws emr-containers list-security-configurations \
    [--created-after <value>] \
    [--created-before <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--created-after` | No | timestamp | -- | Filter after this time |
| `--created-before` | No | timestamp | -- | Filter before this time |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "securityConfigurations": [
        {
            "id": "string",
            "name": "string",
            "arn": "string",
            "createdAt": "timestamp",
            "createdBy": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 13.9 `tag-resource`

Adds tags to an EMR on EKS resource.

**Synopsis:**
```bash
aws emr-containers tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tags` | **Yes** | map | -- | Tags as key-value pairs |

No output on success.

---

### 13.10 `untag-resource`

Removes tags from an EMR on EKS resource.

**Synopsis:**
```bash
aws emr-containers untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

No output on success.

---

### 13.11 `list-tags-for-resource`

Lists tags for an EMR on EKS resource.

**Synopsis:**
```bash
aws emr-containers list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |

**Output Schema:**
```json
{
    "tags": {"string": "string"}
}
```
