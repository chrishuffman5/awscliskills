# Fleet Advisor

DMS Fleet Advisor inventories and assesses your on-premises database and analytics server fleet to plan migrations to AWS.

### 9.1 `create-fleet-advisor-collector`

Creates a Fleet Advisor collector using the specified parameters.

**Synopsis:**
```bash
aws dms create-fleet-advisor-collector \
    --collector-name <value> \
    --service-access-role-arn <value> \
    --s3-bucket-name <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collector-name` | **Yes** | string | -- | Name for the collector |
| `--service-access-role-arn` | **Yes** | string | -- | Service access IAM role ARN |
| `--s3-bucket-name` | **Yes** | string | -- | S3 bucket for collector data |
| `--description` | No | string | -- | Description |

**Output Schema:**
```json
{
    "CollectorReferencedId": "string",
    "CollectorName": "string",
    "Description": "string",
    "ServiceAccessRoleArn": "string",
    "S3BucketName": "string"
}
```

---

### 9.2 `delete-fleet-advisor-collector`

Deletes the specified Fleet Advisor collector.

**Synopsis:**
```bash
aws dms delete-fleet-advisor-collector \
    --collector-referenced-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collector-referenced-id` | **Yes** | string | -- | Collector reference ID |

**Output Schema:** None (HTTP 200 on success).

---

### 9.3 `describe-fleet-advisor-collectors`

Returns a list of the Fleet Advisor collectors. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-fleet-advisor-collectors \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | -- | Filters: `collector-referenced-id`, `collector-name` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Collectors": [
        {
            "CollectorReferencedId": "string",
            "CollectorName": "string",
            "CollectorVersion": "string",
            "VersionStatus": "string",
            "Description": "string",
            "S3BucketName": "string",
            "ServiceAccessRoleArn": "string",
            "CollectorHealthCheck": {
                "CollectorStatus": "string",
                "LocalCollectorS3Access": "boolean",
                "WebCollectorS3Access": "boolean",
                "WebCollectorGrantedRoleBasedAccess": "boolean"
            },
            "LastDataReceived": "string",
            "RegisteredDate": "string",
            "CreatedDate": "string",
            "ModifiedDate": "string",
            "InventoryData": {
                "NumberOfDatabases": "integer",
                "NumberOfSchemas": "integer"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 9.4 `delete-fleet-advisor-databases`

Deletes the specified Fleet Advisor databases.

**Synopsis:**
```bash
aws dms delete-fleet-advisor-databases \
    --database-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-ids` | **Yes** | list(string) | -- | List of database IDs to delete |

**Output Schema:**
```json
{
    "DatabaseIds": ["string"]
}
```

---

### 9.5 `describe-fleet-advisor-databases`

Returns a list of Fleet Advisor databases. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-fleet-advisor-databases \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | -- | Filters: `database-id`, `database-name`, `database-engine`, `server-ip-address` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Databases": [
        {
            "DatabaseId": "string",
            "DatabaseName": "string",
            "DatabaseIpAddress": "string",
            "NumberOfSchemas": "long",
            "Server": {
                "ServerId": "string",
                "IpAddress": "string",
                "ServerName": "string"
            },
            "DatabaseEngine": {
                "EngineName": "string",
                "EngineVersion": "string"
            },
            "Collectors": [
                {
                    "CollectorReferencedId": "string",
                    "CollectorName": "string"
                }
            ]
        }
    ],
    "NextToken": "string"
}
```

---

### 9.6 `describe-fleet-advisor-schemas`

Returns a list of schemas detected by Fleet Advisor Collectors. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-fleet-advisor-schemas \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | -- | Filters: `schema-id`, `schema-name`, `server-ip-address`, `database-id`, `database-name`, `database-engine` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "FleetAdvisorSchemas": [
        {
            "CodeLineCount": "long",
            "CodeSize": "long",
            "Complexity": "string",
            "Server": {},
            "DatabaseInstance": {},
            "SchemaId": "string",
            "SchemaName": "string",
            "OriginalSchema": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 9.7 `describe-fleet-advisor-schema-object-summary`

Provides descriptions of the schemas discovered by your Fleet Advisor collectors. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-fleet-advisor-schema-object-summary \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | -- | Filters: `schema-id` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "FleetAdvisorSchemaObjects": [
        {
            "SchemaId": "string",
            "ObjectType": "string",
            "NumberOfObjects": "long",
            "CodeLineCount": "long",
            "CodeSize": "long"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.8 `run-fleet-advisor-lsa-analysis`

Runs large-scale assessment (LSA) analysis on the Fleet Advisor collector data.

**Synopsis:**
```bash
aws dms run-fleet-advisor-lsa-analysis \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No required parameters.

**Output Schema:**
```json
{
    "LsaAnalysisId": "string",
    "Status": "string"
}
```

---

### 9.9 `describe-fleet-advisor-lsa-analysis`

Provides descriptions of large-scale assessment analysis results.

**Synopsis:**
```bash
aws dms describe-fleet-advisor-lsa-analysis \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Analysis": [
        {
            "LsaAnalysisId": "string",
            "Status": "string"
        }
    ],
    "NextToken": "string"
}
```
