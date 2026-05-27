# Access Management

### 5.1 `create-access-entry`

Creates an access entry, granting an IAM principal access to the EKS cluster.

**Synopsis:**
```bash
aws eks create-access-entry \
    --cluster-name <value> \
    --principal-arn <value> \
    [--kubernetes-groups <value>] \
    [--tags <value>] \
    [--client-request-token <value>] \
    [--username <value>] \
    [--type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--principal-arn` | **Yes** | string | -- | IAM principal ARN (user or role) |
| `--kubernetes-groups` | No | list(string) | None | Kubernetes groups |
| `--tags` | No | map | None | Tags |
| `--client-request-token` | No | string | None | Idempotency token |
| `--username` | No | string | None | Kubernetes username |
| `--type` | No | string | `STANDARD` | `STANDARD`, `FARGATE_LINUX`, `EC2_LINUX`, `EC2_WINDOWS`, `HYBRID_LINUX` |

**Output Schema:**
```json
{
    "accessEntry": {
        "clusterName": "string",
        "principalArn": "string",
        "kubernetesGroups": ["string"],
        "accessEntryArn": "string",
        "createdAt": "timestamp",
        "modifiedAt": "timestamp",
        "tags": {"string": "string"},
        "username": "string",
        "type": "string"
    }
}
```

---

### 5.2 `delete-access-entry`

Deletes an access entry.

**Synopsis:**
```bash
aws eks delete-access-entry \
    --cluster-name <value> \
    --principal-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--principal-arn` | **Yes** | string | -- | IAM principal ARN |

**Output:** No output on success (empty JSON `{}`).

---

### 5.3 `describe-access-entry`

Describes an access entry.

**Synopsis:**
```bash
aws eks describe-access-entry \
    --cluster-name <value> \
    --principal-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--principal-arn` | **Yes** | string | -- | IAM principal ARN |

**Output Schema:** Same as `create-access-entry` output.

---

### 5.4 `list-access-entries`

Lists access entries for a cluster. **Paginated operation.**

**Synopsis:**
```bash
aws eks list-access-entries \
    --cluster-name <value> \
    [--associated-policy-arn <value>] \
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
| `--associated-policy-arn` | No | string | None | Filter by associated policy ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "accessEntries": ["string"],
    "nextToken": "string"
}
```

---

### 5.5 `update-access-entry`

Updates an access entry.

**Synopsis:**
```bash
aws eks update-access-entry \
    --cluster-name <value> \
    --principal-arn <value> \
    [--kubernetes-groups <value>] \
    [--client-request-token <value>] \
    [--username <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--principal-arn` | **Yes** | string | -- | IAM principal ARN |
| `--kubernetes-groups` | No | list(string) | None | Updated Kubernetes groups |
| `--client-request-token` | No | string | None | Idempotency token |
| `--username` | No | string | None | Updated username |

**Output Schema:** Same as `create-access-entry` output.

---

### 5.6 `associate-access-policy`

Associates an access policy with an access entry.

**Synopsis:**
```bash
aws eks associate-access-policy \
    --cluster-name <value> \
    --principal-arn <value> \
    --policy-arn <value> \
    --access-scope <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--principal-arn` | **Yes** | string | -- | IAM principal ARN |
| `--policy-arn` | **Yes** | string | -- | Access policy ARN |
| `--access-scope` | **Yes** | structure | -- | Access scope. Shorthand: `type=cluster\|namespace,namespaces=string,string` |

**Output Schema:**
```json
{
    "clusterName": "string",
    "principalArn": "string",
    "associatedAccessPolicy": {
        "policyArn": "string",
        "accessScope": {
            "type": "cluster|namespace",
            "namespaces": ["string"]
        },
        "associatedAt": "timestamp",
        "modifiedAt": "timestamp"
    }
}
```

---

### 5.7 `disassociate-access-policy`

Disassociates an access policy from an access entry.

**Synopsis:**
```bash
aws eks disassociate-access-policy \
    --cluster-name <value> \
    --principal-arn <value> \
    --policy-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--principal-arn` | **Yes** | string | -- | IAM principal ARN |
| `--policy-arn` | **Yes** | string | -- | Access policy ARN |

**Output:** No output on success (empty JSON `{}`).

---

### 5.8 `list-associated-access-policies`

Lists the access policies associated with an access entry. **Paginated operation.**

**Synopsis:**
```bash
aws eks list-associated-access-policies \
    --cluster-name <value> \
    --principal-arn <value> \
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
| `--principal-arn` | **Yes** | string | -- | IAM principal ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "clusterName": "string",
    "principalArn": "string",
    "associatedAccessPolicies": [
        {
            "policyArn": "string",
            "accessScope": {
                "type": "cluster|namespace",
                "namespaces": ["string"]
            },
            "associatedAt": "timestamp",
            "modifiedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 5.9 `list-access-policies`

Lists available access policies. **Paginated operation.**

**Synopsis:**
```bash
aws eks list-access-policies \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "accessPolicies": [
        {
            "name": "string",
            "arn": "string"
        }
    ],
    "nextToken": "string"
}
```
