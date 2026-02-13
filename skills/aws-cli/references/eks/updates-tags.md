# Updates & Tags

### 11.1 `describe-update`

Returns descriptive information about an update to an EKS resource.

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
| `--nodegroup-name` | No | string | None | Node group name (if update is for a node group) |
| `--addon-name` | No | string | None | Add-on name (if update is for an add-on) |

**Output Schema:**
```json
{
    "update": {
        "id": "string",
        "status": "InProgress|Failed|Cancelled|Successful",
        "type": "VersionUpdate|EndpointAccessUpdate|LoggingUpdate|ConfigUpdate|AssociateIdentityProviderConfig|DisassociateIdentityProviderConfig|AssociateEncryptionConfig|AddonUpdate|VpcConfigUpdate|AccessConfigUpdate|UpgradePolicyUpdate|ZonalShiftConfigUpdate",
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

Lists the updates associated with an EKS resource. **Paginated operation.**

**Synopsis:**
```bash
aws eks list-updates \
    --name <value> \
    [--nodegroup-name <value>] \
    [--addon-name <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Cluster name |
| `--nodegroup-name` | No | string | None | Filter by node group |
| `--addon-name` | No | string | None | Filter by add-on |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
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

Adds tags to an Amazon EKS resource.

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
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tags` | **Yes** | map | -- | Tags as key=value pairs |

**Output:** No output on success (empty JSON `{}`).

---

### 11.4 `untag-resource`

Removes tags from an Amazon EKS resource.

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
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output:** No output on success (empty JSON `{}`).

---

### 11.5 `list-tags-for-resource`

Lists the tags for an Amazon EKS resource.

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
| `--resource-arn` | **Yes** | string | -- | Resource ARN |

**Output Schema:**
```json
{
    "tags": {"string": "string"}
}
```
