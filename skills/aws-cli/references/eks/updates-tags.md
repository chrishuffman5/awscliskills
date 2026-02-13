# Updates & Tags

### 11.1 `describe-update`

Describes an update to an EKS resource (cluster, node group, or add-on).

**Synopsis:**
```bash
aws eks describe-update \
    --name <value> \
    --update-id <value> \
    [--nodegroup-name <value>] \
    [--addon-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Cluster name |
| `--update-id` | **Yes** | string | -- | Update ID |
| `--nodegroup-name` | No | string | None | Node group name (for node group updates) |
| `--addon-name` | No | string | None | Add-on name (for add-on updates) |

**Output Schema:**
```json
{
    "update": {
        "id": "string",
        "status": "InProgress|Failed|Cancelled|Successful",
        "type": "VersionUpdate|EndpointAccessUpdate|LoggingUpdate|ConfigUpdate|AssociateIdentityProviderConfig|DisassociateIdentityProviderConfig|AssociateEncryptionConfig|AddonUpdate|VpcConfigUpdate|AccessConfigUpdate",
        "params": [
            {
                "type": "string",
                "value": "string"
            }
        ],
        "createdAt": "timestamp",
        "errors": [
            {
                "errorCode": "SubnetNotFound|SecurityGroupNotFound|EniLimitReached|IpNotAvailable|AccessDenied|OperationNotPermitted|VpcIdNotFound|Unknown|NodeCreationFailure|PodEvictionFailure|InsufficientFreeAddresses|ClusterUnreachable|InsufficientNumberOfReplicas|ConfigurationConflict|AdmissionRequestDenied|UnsupportedAddonModification|K8sResourceNotFound",
                "errorMessage": "string",
                "resourceIds": ["string"]
            }
        ]
    }
}
```

---

### 11.2 `list-updates`

Lists updates associated with an EKS resource. **Paginated operation.**

**Synopsis:**
```bash
aws eks list-updates \
    --name <value> \
    [--nodegroup-name <value>] \
    [--addon-name <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Cluster name |
| `--nodegroup-name` | No | string | None | Node group name |
| `--addon-name` | No | string | None | Add-on name |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "updateIds": ["string"],
    "nextToken": "string"
}
```

---

### 11.3 `tag-resource`

Adds tags to an EKS resource.

**Synopsis:**
```bash
aws eks tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the EKS resource |
| `--tags` | **Yes** | map | -- | Tags as key-value pairs. Shorthand: `Key1=Value1,Key2=Value2` |

**Output:** No output on success (empty JSON `{}`).

---

### 11.4 `untag-resource`

Removes tags from an EKS resource.

**Synopsis:**
```bash
aws eks untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the EKS resource |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output:** No output on success (empty JSON `{}`).

---

### 11.5 `list-tags-for-resource`

Lists tags for an EKS resource.

**Synopsis:**
```bash
aws eks list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the EKS resource |

**Output Schema:**
```json
{
    "tags": {
        "key": "value"
    }
}
```
