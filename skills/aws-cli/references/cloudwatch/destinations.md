# Destinations

### 13.1 `put-destination`

Creates or updates a destination for cross-account log data delivery.

**Synopsis:**
```bash
aws logs put-destination \
    --destination-name <value> \
    --target-arn <value> \
    --role-arn <value> \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--destination-name` | **Yes** | string | -- | Destination name (1-512 chars). Pattern: `[^:*]*` |
| `--target-arn` | **Yes** | string | -- | ARN of Kinesis stream or Firehose delivery stream |
| `--role-arn` | **Yes** | string | -- | IAM role ARN granting CloudWatch Logs permissions |
| `--tags` | No | map | -- | Key-value tags (1-50) |

**Output Schema:**
```json
{
    "destination": {
        "destinationName": "string",
        "targetArn": "string",
        "roleArn": "string",
        "accessPolicy": "string",
        "arn": "string",
        "creationTime": long
    }
}
```

---

### 13.2 `put-destination-policy`

Sets the access policy for a destination, controlling which accounts can send logs to it.

**Synopsis:**
```bash
aws logs put-destination-policy \
    --destination-name <value> \
    --access-policy <value> \
    [--force-update | --no-force-update]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--destination-name` | **Yes** | string | -- | Destination name (1-512 chars) |
| `--access-policy` | **Yes** | string | -- | IAM policy document in JSON |
| `--force-update` | No | boolean | false | Force update even if policy hasn't changed |

**Output:** None on success.

---

### 13.3 `describe-destinations`

Lists log destinations. **Paginated.**

**Synopsis:**
```bash
aws logs describe-destinations \
    [--destination-name-prefix <value>] \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--destination-name-prefix` | No | string | -- | Destination name prefix (1-512 chars) |
| `--max-items` | No | integer | -- | Total items to return |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |

**Output Schema:**
```json
{
    "destinations": [
        {
            "destinationName": "string",
            "targetArn": "string",
            "roleArn": "string",
            "accessPolicy": "string",
            "arn": "string",
            "creationTime": long
        }
    ],
    "nextToken": "string"
}
```

---

### 13.4 `delete-destination`

Deletes a destination.

**Synopsis:**
```bash
aws logs delete-destination \
    --destination-name <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--destination-name` | **Yes** | string | -- | Destination name (1-512 chars) |

**Output:** None on success.

---
