# Data Grants

## 4.1 `create-data-grant`

Creates a data grant for sharing a data set with another AWS account.

**Synopsis:**
```bash
aws dataexchange create-data-grant \
    --name <value> \
    --grant-distribution-scope <value> \
    --receiver-principal <value> \
    --source-data-set-id <value> \
    [--ends-at <value>] \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Data grant name (1-256 chars) |
| `--grant-distribution-scope` | **Yes** | string | -- | Distribution scope: `AWS_ORGANIZATION` or `NONE` |
| `--receiver-principal` | **Yes** | string | -- | AWS account ID of the receiver (12 digits) |
| `--source-data-set-id` | **Yes** | string | -- | Source data set ID |
| `--ends-at` | No | timestamp | None | Expiration time for the grant |
| `--description` | No | string | None | Description of the grant |
| `--tags` | No | map | None | Key-value tags |

**Output Schema:**
```json
{
    "Name": "string",
    "SenderPrincipal": "string",
    "ReceiverPrincipal": "string",
    "Description": "string",
    "AcceptanceState": "PENDING_RECEIVER_ACCEPTANCE|ACCEPTED",
    "AcceptedAt": "timestamp",
    "EndsAt": "timestamp",
    "GrantDistributionScope": "AWS_ORGANIZATION|NONE",
    "DataSetId": "string",
    "SourceDataSetId": "string",
    "Id": "string",
    "Arn": "string",
    "CreatedAt": "timestamp",
    "UpdatedAt": "timestamp",
    "Tags": { "string": "string" }
}
```

---

## 4.2 `get-data-grant`

Returns details for a data grant that you created.

**Synopsis:**
```bash
aws dataexchange get-data-grant \
    --data-grant-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-grant-id` | **Yes** | string | -- | Data grant ID |

**Output Schema:**
```json
{
    "Name": "string",
    "SenderPrincipal": "string",
    "ReceiverPrincipal": "string",
    "Description": "string",
    "AcceptanceState": "PENDING_RECEIVER_ACCEPTANCE|ACCEPTED",
    "AcceptedAt": "timestamp",
    "EndsAt": "timestamp",
    "GrantDistributionScope": "string",
    "DataSetId": "string",
    "SourceDataSetId": "string",
    "Id": "string",
    "Arn": "string",
    "CreatedAt": "timestamp",
    "UpdatedAt": "timestamp",
    "Tags": { "string": "string" }
}
```

---

## 4.3 `list-data-grants`

Lists data grants that you have sent. **Paginated operation.**

**Synopsis:**
```bash
aws dataexchange list-data-grants \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "DataGrantSummaries": [
        {
            "Name": "string",
            "SenderPrincipal": "string",
            "ReceiverPrincipal": "string",
            "AcceptanceState": "string",
            "AcceptedAt": "timestamp",
            "EndsAt": "timestamp",
            "DataSetId": "string",
            "SourceDataSetId": "string",
            "Id": "string",
            "Arn": "string",
            "CreatedAt": "timestamp",
            "UpdatedAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

## 4.4 `delete-data-grant`

Deletes a data grant.

**Synopsis:**
```bash
aws dataexchange delete-data-grant \
    --data-grant-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-grant-id` | **Yes** | string | -- | Data grant ID to delete |

**Output Schema:**

None (HTTP 204 on success).

---

## 4.5 `accept-data-grant`

Accepts a received data grant.

**Synopsis:**
```bash
aws dataexchange accept-data-grant \
    --data-grant-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-grant-arn` | **Yes** | string | -- | ARN of the data grant to accept |

**Output Schema:**
```json
{
    "Name": "string",
    "SenderPrincipal": "string",
    "ReceiverPrincipal": "string",
    "Description": "string",
    "AcceptanceState": "ACCEPTED",
    "AcceptedAt": "timestamp",
    "EndsAt": "timestamp",
    "GrantDistributionScope": "string",
    "DataSetId": "string",
    "Id": "string",
    "Arn": "string",
    "CreatedAt": "timestamp",
    "UpdatedAt": "timestamp"
}
```

---

## 4.6 `get-received-data-grant`

Returns details for a data grant that you received.

**Synopsis:**
```bash
aws dataexchange get-received-data-grant \
    --data-grant-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-grant-arn` | **Yes** | string | -- | ARN of the received data grant |

**Output Schema:**
```json
{
    "Name": "string",
    "SenderPrincipal": "string",
    "ReceiverPrincipal": "string",
    "Description": "string",
    "AcceptanceState": "PENDING_RECEIVER_ACCEPTANCE|ACCEPTED",
    "AcceptedAt": "timestamp",
    "EndsAt": "timestamp",
    "GrantDistributionScope": "string",
    "DataSetId": "string",
    "Id": "string",
    "Arn": "string",
    "CreatedAt": "timestamp",
    "UpdatedAt": "timestamp"
}
```

---

## 4.7 `list-received-data-grants`

Lists data grants that you have received. **Paginated operation.**

**Synopsis:**
```bash
aws dataexchange list-received-data-grants \
    [--accepted-at <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--accepted-at` | No | string | None | Filter by acceptance time |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "DataGrantSummaries": [
        {
            "Name": "string",
            "SenderPrincipal": "string",
            "ReceiverPrincipal": "string",
            "AcceptanceState": "string",
            "AcceptedAt": "timestamp",
            "EndsAt": "timestamp",
            "DataSetId": "string",
            "Id": "string",
            "Arn": "string",
            "CreatedAt": "timestamp",
            "UpdatedAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
