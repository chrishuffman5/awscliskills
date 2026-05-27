# Subscribers

### 3.1 `create-subscriber`

Creates a subscriber for the specified Security Lake data sources. A subscriber can consume data through S3 access or Lake Formation.

**Synopsis:**
```bash
aws securitylake create-subscriber \
    --sources <value> \
    --subscriber-identity <value> \
    --subscriber-name <value> \
    [--access-types <value>] \
    [--subscriber-description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sources` | **Yes** | list(tagged union) | -- | Data sources the subscriber will access |
| `--subscriber-identity` | **Yes** | structure | -- | AWS identity used to access the data |
| `--subscriber-name` | **Yes** | string | -- | Name of the subscriber (max 64 chars) |
| `--access-types` | No | list(string) | None | Access type: `S3`, `LAKEFORMATION` |
| `--subscriber-description` | No | string | None | Description of the subscriber |
| `--tags` | No | list(structure) | None | Tags (max 50). Structure: `key=string,value=string` |

**Subscriber Identity Structure:**
```json
{
    "externalId": "string",
    "principal": "string"
}
```

**Sources Structure (tagged union — set one per entry):**
```json
{
    "awsLogSource": {
        "sourceName": "ROUTE53|VPC_FLOW|SH_FINDINGS|CLOUD_TRAIL_MGMT|LAMBDA_EXECUTION|S3_DATA|EKS_AUDIT|WAF",
        "sourceVersion": "string"
    }
}
```
or
```json
{
    "customLogSource": {
        "sourceName": "string",
        "sourceVersion": "string"
    }
}
```

**Output Schema:**
```json
{
    "subscriber": {
        "accessTypes": ["LAKEFORMATION|S3"],
        "createdAt": "timestamp",
        "resourceShareArn": "string",
        "resourceShareName": "string",
        "roleArn": "string",
        "s3BucketArn": "string",
        "sources": [
            {
                "awsLogSource": {
                    "sourceName": "string",
                    "sourceVersion": "string"
                },
                "customLogSource": {
                    "sourceName": "string",
                    "sourceVersion": "string",
                    "attributes": {
                        "crawlerArn": "string",
                        "databaseArn": "string",
                        "tableArn": "string"
                    },
                    "provider": {
                        "location": "string",
                        "roleArn": "string"
                    }
                }
            }
        ],
        "subscriberArn": "string",
        "subscriberId": "string",
        "subscriberIdentity": {
            "externalId": "string",
            "principal": "string"
        },
        "subscriberName": "string",
        "subscriberDescription": "string",
        "subscriberEndpoint": "string",
        "subscriberStatus": "ACTIVE|DEACTIVATED|PENDING|READY",
        "updatedAt": "timestamp"
    }
}
```

---

### 3.2 `delete-subscriber`

Deletes the specified subscriber from Security Lake.

**Synopsis:**
```bash
aws securitylake delete-subscriber \
    --subscriber-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscriber-id` | **Yes** | string | -- | UUID of the subscriber to delete |

**Output Schema:**

No output on success (HTTP 200).

---

### 3.3 `get-subscriber`

Retrieves the details of a subscriber from Security Lake.

**Synopsis:**
```bash
aws securitylake get-subscriber \
    --subscriber-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscriber-id` | **Yes** | string | -- | UUID of the subscriber |

**Output Schema:**
```json
{
    "subscriber": {
        "accessTypes": ["LAKEFORMATION|S3"],
        "createdAt": "timestamp",
        "resourceShareArn": "string",
        "resourceShareName": "string",
        "roleArn": "string",
        "s3BucketArn": "string",
        "sources": [
            {
                "awsLogSource": {
                    "sourceName": "string",
                    "sourceVersion": "string"
                },
                "customLogSource": {
                    "sourceName": "string",
                    "sourceVersion": "string",
                    "attributes": {
                        "crawlerArn": "string",
                        "databaseArn": "string",
                        "tableArn": "string"
                    },
                    "provider": {
                        "location": "string",
                        "roleArn": "string"
                    }
                }
            }
        ],
        "subscriberArn": "string",
        "subscriberId": "string",
        "subscriberIdentity": {
            "externalId": "string",
            "principal": "string"
        },
        "subscriberName": "string",
        "subscriberDescription": "string",
        "subscriberEndpoint": "string",
        "subscriberStatus": "ACTIVE|DEACTIVATED|PENDING|READY",
        "updatedAt": "timestamp"
    }
}
```

---

### 3.4 `update-subscriber`

Updates an existing subscriber in Security Lake.

**Synopsis:**
```bash
aws securitylake update-subscriber \
    --subscriber-id <value> \
    [--sources <value>] \
    [--subscriber-identity <value>] \
    [--subscriber-name <value>] \
    [--subscriber-description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscriber-id` | **Yes** | string | -- | UUID of the subscriber to update |
| `--sources` | No | list(tagged union) | None | Updated data sources |
| `--subscriber-identity` | No | structure | None | Updated subscriber identity |
| `--subscriber-name` | No | string | None | Updated subscriber name |
| `--subscriber-description` | No | string | None | Updated description |

**Output Schema:**
```json
{
    "subscriber": {
        "accessTypes": ["LAKEFORMATION|S3"],
        "createdAt": "timestamp",
        "resourceShareArn": "string",
        "resourceShareName": "string",
        "roleArn": "string",
        "s3BucketArn": "string",
        "sources": [],
        "subscriberArn": "string",
        "subscriberId": "string",
        "subscriberIdentity": {
            "externalId": "string",
            "principal": "string"
        },
        "subscriberName": "string",
        "subscriberDescription": "string",
        "subscriberEndpoint": "string",
        "subscriberStatus": "ACTIVE|DEACTIVATED|PENDING|READY",
        "updatedAt": "timestamp"
    }
}
```

---

### 3.5 `list-subscribers`

Lists all subscribers configured in Security Lake. **Paginated operation.**

**Synopsis:**
```bash
aws securitylake list-subscribers \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "subscribers": [
        {
            "accessTypes": ["LAKEFORMATION|S3"],
            "createdAt": "timestamp",
            "resourceShareArn": "string",
            "resourceShareName": "string",
            "roleArn": "string",
            "s3BucketArn": "string",
            "sources": [],
            "subscriberArn": "string",
            "subscriberId": "string",
            "subscriberIdentity": {
                "externalId": "string",
                "principal": "string"
            },
            "subscriberName": "string",
            "subscriberDescription": "string",
            "subscriberEndpoint": "string",
            "subscriberStatus": "ACTIVE|DEACTIVATED|PENDING|READY",
            "updatedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 3.6 `create-subscriber-notification`

Creates a notification for a subscriber when new data is written to the data lake.

**Synopsis:**
```bash
aws securitylake create-subscriber-notification \
    --subscriber-id <value> \
    --configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscriber-id` | **Yes** | string | -- | UUID of the subscriber |
| `--configuration` | **Yes** | tagged union | -- | Notification configuration (HTTPS or SQS) |

**Configuration Structure (tagged union — set one):**
```json
{
    "httpsNotificationConfiguration": {
        "endpoint": "string",
        "targetRoleArn": "string",
        "authorizationApiKeyName": "string",
        "authorizationApiKeyValue": "string",
        "httpMethod": "POST|PUT"
    }
}
```
or
```json
{
    "sqsNotificationConfiguration": {}
}
```

**Output Schema:**
```json
{
    "subscriberEndpoint": "string"
}
```

---

### 3.7 `delete-subscriber-notification`

Deletes the notification configuration for a subscriber.

**Synopsis:**
```bash
aws securitylake delete-subscriber-notification \
    --subscriber-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscriber-id` | **Yes** | string | -- | UUID of the subscriber |

**Output Schema:**

No output on success (HTTP 200).

---

### 3.8 `update-subscriber-notification`

Updates the notification configuration for a subscriber.

**Synopsis:**
```bash
aws securitylake update-subscriber-notification \
    --subscriber-id <value> \
    --configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscriber-id` | **Yes** | string | -- | UUID of the subscriber |
| `--configuration` | **Yes** | tagged union | -- | Updated notification configuration |

**Output Schema:**
```json
{
    "subscriberEndpoint": "string"
}
```
