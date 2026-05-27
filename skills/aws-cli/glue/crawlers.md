# Crawlers

### 2.1 `create-crawler`

Creates a new crawler.

**Synopsis:**
```bash
aws glue create-crawler \
    --name <value> \
    --role <value> \
    --database-name <value> \
    --targets <value> \
    [--description <value>] \
    [--schedule <value>] \
    [--classifiers <value>] \
    [--table-prefix <value>] \
    [--schema-change-policy <value>] \
    [--recrawl-policy <value>] \
    [--lineage-configuration <value>] \
    [--lake-formation-configuration <value>] \
    [--configuration <value>] \
    [--crawler-security-configuration <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Crawler name |
| `--role` | **Yes** | string | -- | IAM role ARN or name |
| `--database-name` | **Yes** | string | -- | Target database for discovered tables |
| `--targets` | **Yes** | structure | -- | Crawler targets (S3, JDBC, DynamoDB, etc.) as JSON |
| `--description` | No | string | -- | Description |
| `--schedule` | No | string | -- | Cron expression for scheduling |
| `--classifiers` | No | list(string) | -- | Custom classifiers to use |
| `--table-prefix` | No | string | -- | Prefix added to table names |
| `--schema-change-policy` | No | structure | -- | Schema change policy. Shorthand: `UpdateBehavior=string,DeleteBehavior=string` |
| `--recrawl-policy` | No | structure | -- | Recrawl policy. Shorthand: `RecrawlBehavior=CRAWL_EVERYTHING|CRAWL_NEW_FOLDERS_ONLY|CRAWL_EVENT_MODE` |
| `--lineage-configuration` | No | structure | -- | Lineage config. Shorthand: `CrawlerLineageSettings=ENABLE|DISABLE` |
| `--lake-formation-configuration` | No | structure | -- | Lake Formation config |
| `--configuration` | No | string | -- | JSON configuration string |
| `--crawler-security-configuration` | No | string | -- | Security configuration name |
| `--tags` | No | map | -- | Tags as JSON |

No output on success.

---

### 2.2 `delete-crawler`

Deletes a crawler.

**Synopsis:**
```bash
aws glue delete-crawler \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Crawler name to delete |

No output on success.

---

### 2.3 `get-crawler`

Retrieves metadata for a crawler.

**Synopsis:**
```bash
aws glue get-crawler \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Crawler name |

**Output Schema:**
```json
{
    "Crawler": {
        "Name": "string",
        "Role": "string",
        "Targets": {
            "S3Targets": [
                {
                    "Path": "string",
                    "Exclusions": ["string"],
                    "ConnectionName": "string",
                    "SampleSize": "integer",
                    "EventQueueArn": "string",
                    "DlqEventQueueArn": "string"
                }
            ],
            "JdbcTargets": [
                {
                    "ConnectionName": "string",
                    "Path": "string",
                    "Exclusions": ["string"],
                    "EnableAdditionalMetadata": ["COMMENTS|RAWTYPES"]
                }
            ],
            "DynamoDBTargets": [
                {
                    "Path": "string",
                    "ScanAll": "boolean",
                    "ScanRate": "double"
                }
            ],
            "CatalogTargets": [
                {
                    "DatabaseName": "string",
                    "Tables": ["string"],
                    "ConnectionName": "string",
                    "EventQueueArn": "string",
                    "DlqEventQueueArn": "string"
                }
            ],
            "DeltaTargets": [],
            "IcebergTargets": [],
            "HudiTargets": []
        },
        "DatabaseName": "string",
        "Description": "string",
        "Classifiers": ["string"],
        "RecrawlPolicy": {
            "RecrawlBehavior": "CRAWL_EVERYTHING|CRAWL_NEW_FOLDERS_ONLY|CRAWL_EVENT_MODE"
        },
        "SchemaChangePolicy": {
            "UpdateBehavior": "LOG|UPDATE_IN_DATABASE",
            "DeleteBehavior": "LOG|DELETE_FROM_DATABASE|DEPRECATE_IN_DATABASE"
        },
        "LineageConfiguration": {
            "CrawlerLineageSettings": "ENABLE|DISABLE"
        },
        "State": "READY|RUNNING|STOPPING",
        "TablePrefix": "string",
        "Schedule": {
            "ScheduleExpression": "string",
            "State": "SCHEDULED|NOT_SCHEDULED|TRANSITIONING"
        },
        "CrawlElapsedTime": "long",
        "CreationTime": "timestamp",
        "LastUpdated": "timestamp",
        "LastCrawl": {
            "Status": "SUCCEEDED|CANCELLED|FAILED",
            "ErrorMessage": "string",
            "LogGroup": "string",
            "LogStream": "string",
            "MessagePrefix": "string",
            "StartTime": "timestamp"
        },
        "Version": "long",
        "Configuration": "string",
        "CrawlerSecurityConfiguration": "string",
        "LakeFormationConfiguration": {}
    }
}
```

---

### 2.4 `get-crawlers`

Retrieves all crawlers. **Paginated operation.**

**Synopsis:**
```bash
aws glue get-crawlers \
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
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "Crawlers": ["<Crawler structure>"],
    "NextToken": "string"
}
```

---

### 2.5 `update-crawler`

Updates a crawler definition.

**Synopsis:**
```bash
aws glue update-crawler \
    --name <value> \
    [--role <value>] \
    [--database-name <value>] \
    [--description <value>] \
    [--targets <value>] \
    [--schedule <value>] \
    [--classifiers <value>] \
    [--table-prefix <value>] \
    [--schema-change-policy <value>] \
    [--recrawl-policy <value>] \
    [--lineage-configuration <value>] \
    [--lake-formation-configuration <value>] \
    [--configuration <value>] \
    [--crawler-security-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Crawler name |
| `--role` | No | string | -- | Updated IAM role |
| `--database-name` | No | string | -- | Updated target database |
| `--description` | No | string | -- | Updated description |
| `--targets` | No | structure | -- | Updated targets |
| `--schedule` | No | string | -- | Updated schedule |
| `--classifiers` | No | list(string) | -- | Updated classifiers |
| `--table-prefix` | No | string | -- | Updated table prefix |
| `--schema-change-policy` | No | structure | -- | Updated schema change policy |
| `--recrawl-policy` | No | structure | -- | Updated recrawl policy |
| `--configuration` | No | string | -- | Updated configuration |
| `--crawler-security-configuration` | No | string | -- | Updated security configuration |

No output on success.

---

### 2.6 `start-crawler`

Starts a crawler. The crawler must be in READY state.

**Synopsis:**
```bash
aws glue start-crawler \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Crawler name |

No output on success.

---

### 2.7 `stop-crawler`

Stops a running crawler.

**Synopsis:**
```bash
aws glue stop-crawler \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Crawler name |

No output on success.

---

### 2.8 `batch-get-crawlers`

Returns detailed information for a list of crawlers.

**Synopsis:**
```bash
aws glue batch-get-crawlers \
    --crawler-names <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--crawler-names` | **Yes** | list(string) | -- | Crawler names |

**Output Schema:**
```json
{
    "Crawlers": ["<Crawler structure>"],
    "CrawlersNotFound": ["string"]
}
```

---

### 2.9 `get-crawler-metrics`

Retrieves metrics for crawlers. **Paginated operation.**

**Synopsis:**
```bash
aws glue get-crawler-metrics \
    [--crawler-name-list <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--crawler-name-list` | No | list(string) | -- | Filter by crawler names |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "CrawlerMetricsList": [
        {
            "CrawlerName": "string",
            "TimeLeftSeconds": "double",
            "StillEstimating": "boolean",
            "LastRuntimeSeconds": "double",
            "MedianRuntimeSeconds": "double",
            "TablesCreated": "integer",
            "TablesUpdated": "integer",
            "TablesDeleted": "integer"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.10 `start-crawler-schedule`

Changes the schedule state of a crawler to SCHEDULED.

**Synopsis:**
```bash
aws glue start-crawler-schedule \
    --crawler-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--crawler-name` | **Yes** | string | -- | Crawler name |

No output on success.

---

### 2.11 `stop-crawler-schedule`

Sets the schedule state of a crawler to NOT_SCHEDULED.

**Synopsis:**
```bash
aws glue stop-crawler-schedule \
    --crawler-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--crawler-name` | **Yes** | string | -- | Crawler name |

No output on success.

---

### 2.12 `list-crawlers`

Lists crawler names. **Paginated operation.**

**Synopsis:**
```bash
aws glue list-crawlers \
    [--tags <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tags` | No | map | -- | Filter by tags |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "CrawlerNames": ["string"],
    "NextToken": "string"
}
```
