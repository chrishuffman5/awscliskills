# Resources

### 4.1 `register-resource`

Registers an S3 location with Lake Formation so the service can manage access to the data.

**Synopsis:**
```bash
aws lakeformation register-resource \
    --resource-arn <value> \
    [--use-service-linked-role | --no-use-service-linked-role] \
    [--role-arn <value>] \
    [--with-federation | --no-with-federation] \
    [--hybrid-access-enabled | --no-hybrid-access-enabled] \
    [--with-privileged-access | --no-with-privileged-access] \
    [--expected-resource-owner-account <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | S3 ARN of the resource to register |
| `--use-service-linked-role` | No | boolean | false | Use the Lake Formation service-linked role |
| `--role-arn` | No | string | None | IAM role ARN for data access |
| `--with-federation` | No | boolean | false | Whether the resource is federated |
| `--hybrid-access-enabled` | No | boolean | false | Allow both LF permissions and S3 bucket policies |
| `--with-privileged-access` | No | boolean | false | Grant calling principal all operations on the location |
| `--expected-resource-owner-account` | No | string | None | AWS account that owns the Glue tables |

**Output:** None

---

### 4.2 `deregister-resource`

Deregisters a resource from Lake Formation. After deregistering, access reverts to IAM permissions.

**Synopsis:**
```bash
aws lakeformation deregister-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to deregister |

**Output:** None

---

### 4.3 `describe-resource`

Describes a registered resource.

**Synopsis:**
```bash
aws lakeformation describe-resource \
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
    "ResourceInfo": {
        "ResourceArn": "string",
        "RoleArn": "string",
        "LastModified": "timestamp",
        "WithFederation": "boolean",
        "HybridAccessEnabled": "boolean"
    }
}
```

---

### 4.4 `update-resource`

Updates the IAM role used for a registered resource.

**Synopsis:**
```bash
aws lakeformation update-resource \
    --role-arn <value> \
    --resource-arn <value> \
    [--with-federation | --no-with-federation] \
    [--hybrid-access-enabled | --no-hybrid-access-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--role-arn` | **Yes** | string | -- | New IAM role ARN |
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to update |
| `--with-federation` | No | boolean | unchanged | Whether the resource is federated |
| `--hybrid-access-enabled` | No | boolean | unchanged | Allow both LF and S3 bucket policies |

**Output:** None

---

### 4.5 `list-resources`

Lists registered resources. **Paginated operation.**

**Synopsis:**
```bash
aws lakeformation list-resources \
    [--filter-condition-list <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter-condition-list` | No | list | None | Filters: `Field` (`RESOURCE_ARN`, `ROLE_ARN`, `LAST_MODIFIED`), `StringValueList`, `ComparisonOperator` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items |

**Output Schema:**
```json
{
    "ResourceInfoList": [
        {
            "ResourceArn": "string",
            "RoleArn": "string",
            "LastModified": "timestamp",
            "WithFederation": "boolean",
            "HybridAccessEnabled": "boolean"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.6 `list-table-storage-optimizers`

Lists table storage optimizers for a given table. **Paginated operation.**

**Synopsis:**
```bash
aws lakeformation list-table-storage-optimizers \
    --database-name <value> \
    --table-name <value> \
    [--catalog-id <value>] \
    [--storage-optimizer-type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--catalog-id` | No | string | account ID | Data Catalog identifier |
| `--storage-optimizer-type` | No | string | None | `COMPACTION`, `GARBAGE_COLLECTION`, `ALL` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items |

**Output Schema:**
```json
{
    "StorageOptimizerList": [
        {
            "StorageOptimizerType": "COMPACTION|GARBAGE_COLLECTION|ALL",
            "Config": {
                "key": "string"
            },
            "ErrorMessage": "string",
            "Warnings": "string",
            "LastRunDetails": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.7 `update-table-storage-optimizer`

Updates the configuration of a table storage optimizer.

**Synopsis:**
```bash
aws lakeformation update-table-storage-optimizer \
    --database-name <value> \
    --table-name <value> \
    --storage-optimizer-config <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--storage-optimizer-config` | **Yes** | map | -- | Optimizer type to config map |
| `--catalog-id` | No | string | account ID | Data Catalog identifier |

**Output Schema:**
```json
{
    "Result": "string"
}
```
