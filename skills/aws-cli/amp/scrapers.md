# Scrapers

### 4.1 `create-scraper`

Creates a scraper to collect Prometheus metrics from an EKS cluster and send them to an AMP workspace.

**Synopsis:**
```bash
aws amp create-scraper \
    --source <value> \
    --destination <value> \
    --scrape-configuration <value> \
    [--alias <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source` | **Yes** | structure | -- | Scraper source configuration. JSON: `{"eksConfiguration":{"clusterArn":"string","subnetIds":["string"],"securityGroupIds":["string"]}}` |
| `--destination` | **Yes** | structure | -- | Scraper destination. JSON: `{"ampConfiguration":{"workspaceArn":"string"}}` |
| `--scrape-configuration` | **Yes** | structure | -- | Scrape configuration. JSON: `{"configurationBlob":"blob"}` |
| `--alias` | No | string | -- | Alias for the scraper |
| `--client-token` | No | string | auto-generated | Idempotency token |
| `--tags` | No | map | -- | Tags as key-value pairs |

**Output Schema:**
```json
{
    "arn": "string",
    "scraperId": "string",
    "status": {
        "statusCode": "CREATING|ACTIVE|DELETING|CREATION_FAILED|DELETION_FAILED"
    },
    "tags": {
        "string": "string"
    }
}
```

---

### 4.2 `delete-scraper`

Deletes a scraper.

**Synopsis:**
```bash
aws amp delete-scraper \
    --scraper-id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scraper-id` | **Yes** | string | -- | ID of the scraper to delete |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Output Schema:**
```json
{
    "arn": "string",
    "scraperId": "string",
    "status": {
        "statusCode": "CREATING|ACTIVE|DELETING|CREATION_FAILED|DELETION_FAILED"
    }
}
```

---

### 4.3 `describe-scraper`

Describes an existing scraper.

**Synopsis:**
```bash
aws amp describe-scraper \
    --scraper-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scraper-id` | **Yes** | string | -- | ID of the scraper |

**Output Schema:**
```json
{
    "scraper": {
        "alias": "string",
        "arn": "string",
        "createdAt": "timestamp",
        "destination": {
            "ampConfiguration": {
                "workspaceArn": "string"
            }
        },
        "lastModifiedAt": "timestamp",
        "roleArn": "string",
        "scrapeConfiguration": {
            "configurationBlob": "blob"
        },
        "scraperId": "string",
        "source": {
            "eksConfiguration": {
                "clusterArn": "string",
                "securityGroupIds": ["string"],
                "subnetIds": ["string"]
            }
        },
        "status": {
            "statusCode": "CREATING|ACTIVE|DELETING|CREATION_FAILED|DELETION_FAILED"
        },
        "statusReason": "string",
        "tags": {
            "string": "string"
        }
    }
}
```

---

### 4.4 `list-scrapers`

Lists all scrapers in the account. **Paginated operation.**

**Synopsis:**
```bash
aws amp list-scrapers \
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
| `--filters` | No | map | -- | Filters as key-value pairs. Keys: `clusterArn`, `workspaceArn`, `alias` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "scrapers": [
        {
            "alias": "string",
            "arn": "string",
            "createdAt": "timestamp",
            "destination": {
                "ampConfiguration": {
                    "workspaceArn": "string"
                }
            },
            "lastModifiedAt": "timestamp",
            "roleArn": "string",
            "scraperId": "string",
            "source": {
                "eksConfiguration": {
                    "clusterArn": "string",
                    "securityGroupIds": ["string"],
                    "subnetIds": ["string"]
                }
            },
            "status": {
                "statusCode": "CREATING|ACTIVE|DELETING|CREATION_FAILED|DELETION_FAILED"
            },
            "statusReason": "string",
            "tags": {
                "string": "string"
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 4.5 `update-scraper`

Updates an existing scraper.

**Synopsis:**
```bash
aws amp update-scraper \
    --scraper-id <value> \
    [--alias <value>] \
    [--scrape-configuration <value>] \
    [--destination <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scraper-id` | **Yes** | string | -- | ID of the scraper to update |
| `--alias` | No | string | -- | New alias |
| `--scrape-configuration` | No | structure | -- | New scrape configuration |
| `--destination` | No | structure | -- | New destination configuration |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Output Schema:**
```json
{
    "arn": "string",
    "scraperId": "string",
    "status": {
        "statusCode": "CREATING|ACTIVE|DELETING|CREATION_FAILED|DELETION_FAILED"
    },
    "tags": {
        "string": "string"
    }
}
```

---

### 4.6 `get-default-scraper-configuration`

Returns the default scraper configuration used when Amazon EKS creates a scraper.

**Synopsis:**
```bash
aws amp get-default-scraper-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| (none) | -- | -- | -- | No parameters required |

**Output Schema:**
```json
{
    "configuration": "blob"
}
```
