# Data Sharing

### 5.1 `create-data-share`

Creates a datashare.

**Synopsis:**
```bash
aws redshift create-data-share \
    --data-share-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-share-arn` | **Yes** | string | -- | ARN of the datashare (namespace ARN format) |

**Output Schema:**
```json
{
    "DataShareArn": "string",
    "ProducerArn": "string",
    "AllowPubliclyAccessibleConsumers": "boolean",
    "DataShareAssociations": [
        {
            "ConsumerIdentifier": "string",
            "Status": "ACTIVE|PENDING_AUTHORIZATION|AUTHORIZED|DEAUTHORIZED|REJECTED|AVAILABLE",
            "ConsumerRegion": "string",
            "CreatedDate": "timestamp",
            "StatusChangeDate": "timestamp",
            "ConsumerAcceptedWrites": "boolean",
            "ProducerAllowedWrites": "boolean"
        }
    ],
    "ManagedBy": "string"
}
```

---

### 5.2 `delete-data-share`

Deletes a datashare.

**Synopsis:**
```bash
aws redshift delete-data-share \
    --data-share-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-share-arn` | **Yes** | string | -- | ARN of the datashare to delete |

No output on success.

---

### 5.3 `describe-data-shares`

Describes datashares. **Paginated operation.**

**Synopsis:**
```bash
aws redshift describe-data-shares \
    [--data-share-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-share-arn` | No | string | -- | Specific datashare ARN |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "DataShares": [
        {
            "DataShareArn": "string",
            "ProducerArn": "string",
            "AllowPubliclyAccessibleConsumers": "boolean",
            "DataShareAssociations": [],
            "ManagedBy": "string"
        }
    ],
    "Marker": "string"
}
```

---

### 5.4 `describe-data-shares-for-consumer`

Returns datashares available to be consumed by the specified consumer. **Paginated operation.**

**Synopsis:**
```bash
aws redshift describe-data-shares-for-consumer \
    [--consumer-arn <value>] \
    [--status <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--consumer-arn` | No | string | -- | Consumer namespace ARN |
| `--status` | No | string | -- | Filter: `ACTIVE`, `AVAILABLE` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "DataShares": [
        {
            "DataShareArn": "string",
            "ProducerArn": "string",
            "AllowPubliclyAccessibleConsumers": "boolean",
            "DataShareAssociations": []
        }
    ],
    "Marker": "string"
}
```

---

### 5.5 `describe-data-shares-for-producer`

Returns datashares owned by the specified producer. **Paginated operation.**

**Synopsis:**
```bash
aws redshift describe-data-shares-for-producer \
    [--producer-arn <value>] \
    [--status <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--producer-arn` | No | string | -- | Producer namespace ARN |
| `--status` | No | string | -- | Filter: `ACTIVE`, `AUTHORIZED`, `PENDING_AUTHORIZATION`, `DEAUTHORIZED`, `REJECTED` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "DataShares": [
        {
            "DataShareArn": "string",
            "ProducerArn": "string",
            "AllowPubliclyAccessibleConsumers": "boolean",
            "DataShareAssociations": []
        }
    ],
    "Marker": "string"
}
```

---

### 5.6 `associate-data-share-consumer`

Associates a consumer with a datashare.

**Synopsis:**
```bash
aws redshift associate-data-share-consumer \
    --data-share-arn <value> \
    [--associate-entire-account | --no-associate-entire-account] \
    [--consumer-arn <value>] \
    [--consumer-region <value>] \
    [--allow-writes | --no-allow-writes] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-share-arn` | **Yes** | string | -- | Datashare ARN |
| `--associate-entire-account` | No | boolean | -- | Associate all namespaces in the account |
| `--consumer-arn` | No | string | -- | Consumer namespace ARN |
| `--consumer-region` | No | string | -- | Consumer region |
| `--allow-writes` | No | boolean | -- | Allow write operations from consumer |

**Output Schema:**
```json
{
    "DataShareArn": "string",
    "ProducerArn": "string",
    "AllowPubliclyAccessibleConsumers": "boolean",
    "DataShareAssociations": [
        {
            "ConsumerIdentifier": "string",
            "Status": "string",
            "ConsumerRegion": "string",
            "CreatedDate": "timestamp",
            "StatusChangeDate": "timestamp"
        }
    ]
}
```

---

### 5.7 `disassociate-data-share-consumer`

Removes a consumer from a datashare.

**Synopsis:**
```bash
aws redshift disassociate-data-share-consumer \
    --data-share-arn <value> \
    [--disassociate-entire-account | --no-disassociate-entire-account] \
    [--consumer-arn <value>] \
    [--consumer-region <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-share-arn` | **Yes** | string | -- | Datashare ARN |
| `--disassociate-entire-account` | No | boolean | -- | Disassociate all namespaces in the account |
| `--consumer-arn` | No | string | -- | Consumer namespace ARN |
| `--consumer-region` | No | string | -- | Consumer region |

**Output Schema:**
```json
{
    "DataShareArn": "string",
    "ProducerArn": "string",
    "DataShareAssociations": []
}
```

---

### 5.8 `authorize-data-share`

Authorizes a datashare consumer.

**Synopsis:**
```bash
aws redshift authorize-data-share \
    --data-share-arn <value> \
    --consumer-identifier <value> \
    [--allow-writes | --no-allow-writes] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-share-arn` | **Yes** | string | -- | Datashare ARN to authorize |
| `--consumer-identifier` | **Yes** | string | -- | Consumer identifier (account ID or namespace ARN) |
| `--allow-writes` | No | boolean | -- | Allow writes from the consumer |

**Output Schema:**
```json
{
    "DataShareArn": "string",
    "ProducerArn": "string",
    "AllowPubliclyAccessibleConsumers": "boolean",
    "DataShareAssociations": [
        {
            "ConsumerIdentifier": "string",
            "Status": "AUTHORIZED"
        }
    ]
}
```

---

### 5.9 `deauthorize-data-share`

Removes authorization from a datashare consumer.

**Synopsis:**
```bash
aws redshift deauthorize-data-share \
    --data-share-arn <value> \
    --consumer-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-share-arn` | **Yes** | string | -- | Datashare ARN |
| `--consumer-identifier` | **Yes** | string | -- | Consumer to deauthorize |

**Output Schema:**
```json
{
    "DataShareArn": "string",
    "ProducerArn": "string",
    "DataShareAssociations": [
        {
            "ConsumerIdentifier": "string",
            "Status": "DEAUTHORIZED"
        }
    ]
}
```
