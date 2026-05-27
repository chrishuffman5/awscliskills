# Add-ons

### 4.1 `create-addon`

Creates an Amazon EKS add-on.

**Synopsis:**
```bash
aws eks create-addon \
    --cluster-name <value> \
    --addon-name <value> \
    [--addon-version <value>] \
    [--service-account-role-arn <value>] \
    [--resolve-conflicts <value>] \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--configuration-values <value>] \
    [--pod-identity-associations <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--addon-name` | **Yes** | string | -- | Add-on name (e.g., `vpc-cni`, `coredns`, `kube-proxy`) |
| `--addon-version` | No | string | latest compatible | Add-on version |
| `--service-account-role-arn` | No | string | None | IAM role ARN for the add-on service account (IRSA) |
| `--resolve-conflicts` | No | string | `NONE` | `OVERWRITE`, `PRESERVE`, `NONE` |
| `--client-request-token` | No | string | None | Idempotency token |
| `--tags` | No | map | None | Tags |
| `--configuration-values` | No | string | None | JSON string of add-on configuration values |
| `--pod-identity-associations` | No | list | None | Pod Identity associations. Shorthand: `serviceAccount=string,roleArn=string ...` |

**Output Schema:**
```json
{
    "addon": {
        "addonName": "string",
        "clusterName": "string",
        "status": "CREATING|ACTIVE|CREATE_FAILED|UPDATING|DELETING|DELETE_FAILED|DEGRADED|UPDATE_FAILED",
        "addonVersion": "string",
        "health": {
            "issues": [
                {
                    "code": "string",
                    "message": "string",
                    "resourceIds": ["string"]
                }
            ]
        },
        "addonArn": "string",
        "createdAt": "timestamp",
        "modifiedAt": "timestamp",
        "serviceAccountRoleArn": "string",
        "tags": {"string": "string"},
        "publisher": "string",
        "owner": "string",
        "marketplaceInformation": {
            "productId": "string",
            "productUrl": "string"
        },
        "configurationSchema": "string",
        "configurationValues": "string",
        "podIdentityAssociations": ["string"]
    }
}
```

---

### 4.2 `delete-addon`

Deletes an Amazon EKS add-on.

**Synopsis:**
```bash
aws eks delete-addon \
    --cluster-name <value> \
    --addon-name <value> \
    [--preserve | --no-preserve] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--addon-name` | **Yes** | string | -- | Add-on name |
| `--preserve` | No | boolean | false | Preserve add-on Kubernetes resources on deletion |

**Output Schema:** Same addon object with status `DELETING`.

---

### 4.3 `describe-addon`

Describes an Amazon EKS add-on.

**Synopsis:**
```bash
aws eks describe-addon \
    --cluster-name <value> \
    --addon-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--addon-name` | **Yes** | string | -- | Add-on name |

**Output Schema:** Same as `create-addon` output.

---

### 4.4 `describe-addon-versions`

Describes the versions available for Amazon EKS add-ons. **Paginated operation.**

**Synopsis:**
```bash
aws eks describe-addon-versions \
    [--kubernetes-version <value>] \
    [--addon-name <value>] \
    [--types <value>] \
    [--publishers <value>] \
    [--owners <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--kubernetes-version` | No | string | None | Filter by Kubernetes version |
| `--addon-name` | No | string | None | Filter by add-on name |
| `--types` | No | list(string) | None | Filter by type |
| `--publishers` | No | list(string) | None | Filter by publisher |
| `--owners` | No | list(string) | None | Filter by owner (`aws`, `aws-marketplace`, `self`) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "addons": [
        {
            "addonName": "string",
            "type": "string",
            "addonVersions": [
                {
                    "addonVersion": "string",
                    "architecture": ["string"],
                    "compatibilities": [
                        {
                            "clusterVersion": "string",
                            "platformVersions": ["string"],
                            "defaultVersion": true|false
                        }
                    ],
                    "requiresConfiguration": true|false,
                    "requiresIamPermissions": true|false
                }
            ],
            "publisher": "string",
            "owner": "string",
            "marketplaceInformation": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 4.5 `describe-addon-configuration`

Returns configuration schemas for an add-on.

**Synopsis:**
```bash
aws eks describe-addon-configuration \
    --addon-name <value> \
    --addon-version <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--addon-name` | **Yes** | string | -- | Add-on name |
| `--addon-version` | **Yes** | string | -- | Add-on version |

**Output Schema:**
```json
{
    "addonName": "string",
    "addonVersion": "string",
    "configurationSchema": "string"
}
```

---

### 4.6 `list-addons`

Lists the installed add-ons for a cluster. **Paginated operation.**

**Synopsis:**
```bash
aws eks list-addons \
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
    "addons": ["string"],
    "nextToken": "string"
}
```

---

### 4.7 `update-addon`

Updates an Amazon EKS add-on.

**Synopsis:**
```bash
aws eks update-addon \
    --cluster-name <value> \
    --addon-name <value> \
    [--addon-version <value>] \
    [--service-account-role-arn <value>] \
    [--resolve-conflicts <value>] \
    [--client-request-token <value>] \
    [--configuration-values <value>] \
    [--pod-identity-associations <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-name` | **Yes** | string | -- | Cluster name |
| `--addon-name` | **Yes** | string | -- | Add-on name |
| `--addon-version` | No | string | None | Target version |
| `--service-account-role-arn` | No | string | None | Updated IAM role ARN |
| `--resolve-conflicts` | No | string | `NONE` | `OVERWRITE`, `PRESERVE`, `NONE` |
| `--client-request-token` | No | string | None | Idempotency token |
| `--configuration-values` | No | string | None | Updated configuration |
| `--pod-identity-associations` | No | list | None | Updated Pod Identity associations |

**Output Schema:** Update object (same as cluster update).
