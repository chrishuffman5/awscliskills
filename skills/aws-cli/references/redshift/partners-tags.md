# Partners & Tags

### 12.1 `add-partner`

Adds a partner integration to a cluster.

**Synopsis:**
```bash
aws redshift add-partner \
    --account-id <value> \
    --cluster-identifier <value> \
    --database-name <value> \
    --partner-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID of the cluster owner |
| `--cluster-identifier` | **Yes** | string | -- | Cluster identifier |
| `--database-name` | **Yes** | string | -- | Database name |
| `--partner-name` | **Yes** | string | -- | Partner name |

**Output Schema:**
```json
{
    "DatabaseName": "string",
    "PartnerName": "string"
}
```

---

### 12.2 `delete-partner`

Deletes a partner integration from a cluster.

**Synopsis:**
```bash
aws redshift delete-partner \
    --account-id <value> \
    --cluster-identifier <value> \
    --database-name <value> \
    --partner-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID |
| `--cluster-identifier` | **Yes** | string | -- | Cluster identifier |
| `--database-name` | **Yes** | string | -- | Database name |
| `--partner-name` | **Yes** | string | -- | Partner name to delete |

**Output Schema:**
```json
{
    "DatabaseName": "string",
    "PartnerName": "string"
}
```

---

### 12.3 `describe-partners`

Returns information about partner integrations.

**Synopsis:**
```bash
aws redshift describe-partners \
    --account-id <value> \
    --cluster-identifier <value> \
    [--database-name <value>] \
    [--partner-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID |
| `--cluster-identifier` | **Yes** | string | -- | Cluster identifier |
| `--database-name` | No | string | -- | Filter by database |
| `--partner-name` | No | string | -- | Filter by partner |

**Output Schema:**
```json
{
    "PartnerIntegrationInfoList": [
        {
            "DatabaseName": "string",
            "PartnerName": "string",
            "Status": "Active|Inactive|RuntimeFailure|ConnectionFailure",
            "StatusMessage": "string",
            "CreatedAt": "timestamp",
            "UpdatedAt": "timestamp"
        }
    ]
}
```

---

### 12.4 `create-tags`

Adds tags to a Redshift resource.

**Synopsis:**
```bash
aws redshift create-tags \
    --resource-name <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-name` | **Yes** | string | -- | Resource ARN to tag |
| `--tags` | **Yes** | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |

No output on success.

---

### 12.5 `delete-tags`

Deletes tags from a Redshift resource.

**Synopsis:**
```bash
aws redshift delete-tags \
    --resource-name <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-name` | **Yes** | string | -- | Resource ARN to untag |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

No output on success.

---

### 12.6 `describe-tags`

Returns tag information associated with Redshift resources. **Paginated operation.**

**Synopsis:**
```bash
aws redshift describe-tags \
    [--resource-name <value>] \
    [--resource-type <value>] \
    [--tag-keys <value>] \
    [--tag-values <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-name` | No | string | -- | Specific resource ARN |
| `--resource-type` | No | string | -- | Resource type filter: `cluster`, `cluster-snapshot`, `cluster-parameter-group`, `cluster-security-group`, `cluster-subnet-group`, `hsm-client-certificate`, `hsm-configuration`, `snapshot-schedule`, `snapshot-copy-grant` |
| `--tag-keys` | No | list(string) | -- | Filter by tag keys |
| `--tag-values` | No | list(string) | -- | Filter by tag values |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "TaggedResources": [
        {
            "Tag": {
                "Key": "string",
                "Value": "string"
            },
            "ResourceName": "string",
            "ResourceType": "string"
        }
    ],
    "Marker": "string"
}
```
