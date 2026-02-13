# Data Sources

### 8.1 `add-data-source`

Adds a data source to an OpenSearch Service domain.

**Synopsis:**
```bash
aws opensearch add-data-source \
    --domain-name <value> \
    --name <value> \
    --data-source-type <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name |
| `--name` | **Yes** | string | -- | Data source name (3-80 chars) |
| `--data-source-type` | **Yes** | structure | -- | Data source type configuration |
| `--description` | No | string | None | Description (max 1000 chars) |

**Output Schema:**
```json
{
    "Message": "string"
}
```

---

### 8.2 `delete-data-source`

Deletes a data source from an OpenSearch Service domain.

**Synopsis:**
```bash
aws opensearch delete-data-source \
    --domain-name <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name |
| `--name` | **Yes** | string | -- | Data source name |

**Output Schema:**
```json
{
    "Message": "string"
}
```

---

### 8.3 `get-data-source`

Returns details about a data source.

**Synopsis:**
```bash
aws opensearch get-data-source \
    --domain-name <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name |
| `--name` | **Yes** | string | -- | Data source name |

**Output Schema:**
```json
{
    "DataSourceType": {},
    "Name": "string",
    "Description": "string",
    "Status": "string"
}
```

---

### 8.4 `list-data-sources`

Lists data sources for a domain.

**Synopsis:**
```bash
aws opensearch list-data-sources \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name |

**Output Schema:**
```json
{
    "DataSources": [
        {
            "DataSourceType": {},
            "Name": "string",
            "Description": "string",
            "Status": "string"
        }
    ]
}
```

---

### 8.5 `update-data-source`

Updates a data source.

**Synopsis:**
```bash
aws opensearch update-data-source \
    --domain-name <value> \
    --name <value> \
    --data-source-type <value> \
    [--description <value>] \
    [--status <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name |
| `--name` | **Yes** | string | -- | Data source name |
| `--data-source-type` | **Yes** | structure | -- | Updated type configuration |
| `--description` | No | string | None | Updated description |
| `--status` | No | string | None | Updated status |

**Output Schema:**
```json
{
    "Message": "string"
}
```

---

### 8.6 `add-direct-query-data-source`

Adds a direct query data source to an OpenSearch Service domain.

**Synopsis:**
```bash
aws opensearch add-direct-query-data-source \
    --domain-name <value> \
    --data-source-name <value> \
    --data-source-type <value> \
    --open-search-arns <value> \
    [--description <value>] \
    [--tag-list <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name |
| `--data-source-name` | **Yes** | string | -- | Data source name |
| `--data-source-type` | **Yes** | structure | -- | Type config (CloudWatchLog, SecurityLake, S3Glue) |
| `--open-search-arns` | **Yes** | list(string) | -- | OpenSearch collection ARNs |
| `--description` | No | string | None | Description |
| `--tag-list` | No | list | None | Tags |

**Output Schema:**
```json
{
    "DataSourceArn": "string"
}
```

---

### 8.7 `delete-direct-query-data-source`

Deletes a direct query data source.

**Synopsis:**
```bash
aws opensearch delete-direct-query-data-source \
    --domain-name <value> \
    --data-source-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name |
| `--data-source-name` | **Yes** | string | -- | Data source name |

**Output:** None

---

### 8.8 `get-direct-query-data-source`

Returns details about a direct query data source.

**Synopsis:**
```bash
aws opensearch get-direct-query-data-source \
    --domain-name <value> \
    --data-source-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name |
| `--data-source-name` | **Yes** | string | -- | Data source name |

**Output Schema:**
```json
{
    "DataSourceName": "string",
    "DataSourceType": {},
    "Description": "string",
    "OpenSearchArns": ["string"],
    "DataSourceArn": "string"
}
```

---

### 8.9 `list-direct-query-data-sources`

Lists direct query data sources for a domain.

**Synopsis:**
```bash
aws opensearch list-direct-query-data-sources \
    --domain-name <value> \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "DirectQueryDataSources": [
        {
            "DataSourceName": "string",
            "DataSourceType": {},
            "Description": "string",
            "OpenSearchArns": ["string"],
            "DataSourceArn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.10 `update-direct-query-data-source`

Updates a direct query data source.

**Synopsis:**
```bash
aws opensearch update-direct-query-data-source \
    --domain-name <value> \
    --data-source-name <value> \
    --data-source-type <value> \
    --open-search-arns <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name |
| `--data-source-name` | **Yes** | string | -- | Data source name |
| `--data-source-type` | **Yes** | structure | -- | Updated type config |
| `--open-search-arns` | **Yes** | list(string) | -- | Updated OpenSearch ARNs |
| `--description` | No | string | None | Updated description |

**Output Schema:**
```json
{
    "DataSourceArn": "string"
}
```
