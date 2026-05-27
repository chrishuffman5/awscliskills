# Serverless Domains & Tags (`aws redshift-serverless`)

### 18.1 `create-custom-domain-association`

Creates a custom domain association for a serverless workgroup.

**Synopsis:**
```bash
aws redshift-serverless create-custom-domain-association \
    --workgroup-name <value> \
    --custom-domain-name <value> \
    --custom-domain-certificate-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workgroup-name` | **Yes** | string | -- | Workgroup to associate domain with |
| `--custom-domain-name` | **Yes** | string | -- | Custom domain name |
| `--custom-domain-certificate-arn` | **Yes** | string | -- | ACM certificate ARN |

**Output Schema:**
```json
{
    "customDomainName": "string",
    "workgroupName": "string",
    "customDomainCertificateArn": "string",
    "customDomainCertificateExpiryTime": "timestamp"
}
```

---

### 18.2 `delete-custom-domain-association`

Deletes a custom domain association.

**Synopsis:**
```bash
aws redshift-serverless delete-custom-domain-association \
    --workgroup-name <value> \
    --custom-domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workgroup-name` | **Yes** | string | -- | Workgroup to disassociate |
| `--custom-domain-name` | **Yes** | string | -- | Domain name to remove |

No output on success.

---

### 18.3 `get-custom-domain-association`

Returns information about a custom domain association.

**Synopsis:**
```bash
aws redshift-serverless get-custom-domain-association \
    --workgroup-name <value> \
    --custom-domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workgroup-name` | **Yes** | string | -- | Workgroup name |
| `--custom-domain-name` | **Yes** | string | -- | Domain name |

**Output Schema:**
```json
{
    "customDomainName": "string",
    "workgroupName": "string",
    "customDomainCertificateArn": "string",
    "customDomainCertificateExpiryTime": "timestamp"
}
```

---

### 18.4 `list-custom-domain-associations`

Lists custom domain associations. **Paginated operation.**

**Synopsis:**
```bash
aws redshift-serverless list-custom-domain-associations \
    [--custom-domain-name <value>] \
    [--custom-domain-certificate-arn <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--custom-domain-name` | No | string | -- | Filter by domain name |
| `--custom-domain-certificate-arn` | No | string | -- | Filter by certificate ARN |
| `--next-token` | No | string | -- | Pagination token |
| `--max-results` | No | integer | -- | Maximum results |

**Output Schema:**
```json
{
    "associations": [
        {
            "customDomainName": "string",
            "workgroupName": "string",
            "customDomainCertificateArn": "string",
            "customDomainCertificateExpiryTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 18.5 `update-custom-domain-association`

Updates a custom domain association (e.g., to rotate the ACM certificate).

**Synopsis:**
```bash
aws redshift-serverless update-custom-domain-association \
    --workgroup-name <value> \
    --custom-domain-name <value> \
    --custom-domain-certificate-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workgroup-name` | **Yes** | string | -- | Workgroup name |
| `--custom-domain-name` | **Yes** | string | -- | Domain name |
| `--custom-domain-certificate-arn` | **Yes** | string | -- | New ACM certificate ARN |

**Output Schema:**
```json
{
    "customDomainName": "string",
    "workgroupName": "string",
    "customDomainCertificateArn": "string",
    "customDomainCertificateExpiryTime": "timestamp"
}
```

---

### 18.6 `tag-resource`

Adds tags to a serverless resource.

**Synopsis:**
```bash
aws redshift-serverless tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN to tag |
| `--tags` | **Yes** | list | -- | Tags. Shorthand: `key=string,value=string ...` |

No output on success.

---

### 18.7 `untag-resource`

Removes tags from a serverless resource.

**Synopsis:**
```bash
aws redshift-serverless untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN to untag |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

No output on success.

---

### 18.8 `list-tags-for-resource`

Lists tags for a serverless resource.

**Synopsis:**
```bash
aws redshift-serverless list-tags-for-resource \
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
    "tags": [
        {
            "key": "string",
            "value": "string"
        }
    ]
}
```

---

### 18.9 `get-credentials`

Returns temporary credentials to access a serverless workgroup.

**Synopsis:**
```bash
aws redshift-serverless get-credentials \
    [--workgroup-name <value>] \
    [--db-name <value>] \
    [--duration-seconds <value>] \
    [--custom-domain-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workgroup-name` | No | string | -- | Workgroup to get credentials for |
| `--db-name` | No | string | -- | Database name |
| `--duration-seconds` | No | integer | 900 | Credential duration (900-3600 seconds) |
| `--custom-domain-name` | No | string | -- | Custom domain name |

**Output Schema:**
```json
{
    "dbUser": "string",
    "dbPassword": "string",
    "expiration": "timestamp",
    "nextRefreshTime": "timestamp"
}
```

---

### 18.10 `get-table-restore-status`

Returns the status of a table restore operation.

**Synopsis:**
```bash
aws redshift-serverless get-table-restore-status \
    --table-restore-request-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-restore-request-id` | **Yes** | string | -- | Table restore request ID |

**Output Schema:**
```json
{
    "tableRestoreStatus": {
        "tableRestoreRequestId": "string",
        "status": "PENDING|IN_PROGRESS|SUCCEEDED|FAILED|CANCELED",
        "message": "string",
        "requestTime": "timestamp",
        "namespaceName": "string",
        "workgroupName": "string",
        "snapshotName": "string",
        "progressInMegaBytes": "long",
        "totalDataInMegaBytes": "long",
        "sourceDatabaseName": "string",
        "sourceSchemaName": "string",
        "sourceTableName": "string",
        "targetDatabaseName": "string",
        "targetSchemaName": "string",
        "newTableName": "string"
    }
}
```

---

### 18.11 `list-table-restore-status`

Lists table restore operations. **Paginated operation.**

**Synopsis:**
```bash
aws redshift-serverless list-table-restore-status \
    [--namespace-name <value>] \
    [--workgroup-name <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--namespace-name` | No | string | -- | Filter by namespace |
| `--workgroup-name` | No | string | -- | Filter by workgroup |
| `--next-token` | No | string | -- | Pagination token |
| `--max-results` | No | integer | -- | Maximum results |

**Output Schema:**
```json
{
    "tableRestoreStatuses": [
        {
            "tableRestoreRequestId": "string",
            "status": "string",
            "message": "string",
            "requestTime": "timestamp",
            "namespaceName": "string",
            "workgroupName": "string",
            "snapshotName": "string"
        }
    ],
    "nextToken": "string"
}
```
