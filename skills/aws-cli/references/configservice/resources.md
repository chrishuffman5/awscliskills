# Resources

### 7.1 `list-discovered-resources`

Lists resources discovered by AWS Config. **Paginated operation.**

**Synopsis:**
```bash
aws configservice list-discovered-resources \
    --resource-type <value> \
    [--resource-ids <value>] \
    [--resource-name <value>] \
    [--include-deleted-resources | --no-include-deleted-resources] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-type` | **Yes** | string | -- | AWS resource type (e.g., `AWS::EC2::Instance`) |
| `--resource-ids` | No | list(string) | None | Specific resource IDs to include |
| `--resource-name` | No | string | None | Filter by resource name |
| `--include-deleted-resources` | No | boolean | false | Include deleted resources |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "resourceIdentifiers": [
        {
            "resourceType": "string",
            "resourceId": "string",
            "resourceName": "string",
            "resourceDeletionTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 7.2 `get-discovered-resource-counts`

Returns the count of resources discovered by Config, grouped by resource type. **Paginated operation.**

**Synopsis:**
```bash
aws configservice get-discovered-resource-counts \
    [--resource-types <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-types` | No | list(string) | None | Filter to specific resource types |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 100) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "totalDiscoveredResources": "integer",
    "resourceCounts": [
        {
            "resourceType": "string",
            "count": "integer"
        }
    ],
    "nextToken": "string"
}
```

---

### 7.3 `get-resource-config-history`

Returns a list of configuration items for a specified resource over time. **Paginated operation.**

**Synopsis:**
```bash
aws configservice get-resource-config-history \
    --resource-type <value> \
    --resource-id <value> \
    [--later-time <value>] \
    [--earlier-time <value>] \
    [--chronological-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-type` | **Yes** | string | -- | AWS resource type |
| `--resource-id` | **Yes** | string | -- | Resource ID |
| `--later-time` | No | timestamp | None | End time for the range |
| `--earlier-time` | No | timestamp | None | Start time for the range |
| `--chronological-order` | No | string | `Reverse` | Order: `Forward` or `Reverse` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "configurationItems": [
        {
            "version": "string",
            "accountId": "string",
            "configurationItemCaptureTime": "timestamp",
            "configurationItemStatus": "OK|ResourceDiscovered|ResourceNotRecorded|ResourceDeleted|ResourceDeletedNotRecorded",
            "configurationStateId": "string",
            "configurationItemMD5Hash": "string",
            "arn": "string",
            "resourceType": "string",
            "resourceId": "string",
            "resourceName": "string",
            "awsRegion": "string",
            "availabilityZone": "string",
            "resourceCreationTime": "timestamp",
            "tags": {},
            "relatedEvents": ["string"],
            "relationships": [
                {
                    "resourceType": "string",
                    "resourceId": "string",
                    "resourceName": "string",
                    "relationshipName": "string"
                }
            ],
            "configuration": "string",
            "supplementaryConfiguration": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 7.4 `batch-get-resource-config`

Returns the current configuration for one or more resources.

**Synopsis:**
```bash
aws configservice batch-get-resource-config \
    --resource-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-keys` | **Yes** | list | -- | Resource keys (up to 100). Shorthand: `resourceType=string,resourceId=string ...` |

**Output Schema:**
```json
{
    "baseConfigurationItems": [
        {
            "version": "string",
            "accountId": "string",
            "configurationItemCaptureTime": "timestamp",
            "configurationItemStatus": "string",
            "arn": "string",
            "resourceType": "string",
            "resourceId": "string",
            "resourceName": "string",
            "awsRegion": "string",
            "configuration": "string",
            "supplementaryConfiguration": {}
        }
    ],
    "unprocessedResourceKeys": [
        {
            "resourceType": "string",
            "resourceId": "string"
        }
    ]
}
```

---

### 7.5 `select-resource-config`

Runs a SQL-like query against the configuration data of discovered resources. **Paginated operation.**

**Synopsis:**
```bash
aws configservice select-resource-config \
    --expression <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--expression` | **Yes** | string | -- | SQL SELECT expression |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 100) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Results": ["string"],
    "QueryInfo": {
        "SelectFields": [
            {
                "Name": "string"
            }
        ]
    },
    "NextToken": "string"
}
```
