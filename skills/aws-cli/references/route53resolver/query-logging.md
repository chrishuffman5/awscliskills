# Query Logging

### 4.1 `create-resolver-query-log-config`

Creates a Resolver query logging configuration. Logs DNS queries made in VPCs to S3, CloudWatch Logs, or Kinesis Data Firehose.

**Synopsis:**
```bash
aws route53resolver create-resolver-query-log-config \
    --name <value> \
    --destination-arn <value> \
    [--creator-request-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Configuration name (max 64 chars) |
| `--destination-arn` | **Yes** | string | -- | ARN of destination: S3 bucket, CloudWatch Logs log group, or Kinesis Data Firehose (max 600 chars) |
| `--creator-request-id` | No | string | None | Idempotency token (max 255 chars) |
| `--tags` | No | list | None | Tags (max 200). Shorthand: `Key=string,Value=string ...` |

**Destination ARN Examples:**
- S3: `arn:aws:s3:::my-dns-logs-bucket`
- CloudWatch Logs: `arn:aws:logs:us-east-1:123456789012:log-group:/dns-logs:*`
- Kinesis: `arn:aws:kinesis:us-east-1:123456789012:stream/dns-log-stream`

**Output Schema:**
```json
{
    "ResolverQueryLogConfig": {
        "Id": "string",
        "OwnerId": "string",
        "Status": "CREATING|CREATED|DELETING|FAILED",
        "ShareStatus": "NOT_SHARED|SHARED_WITH_ME|SHARED_BY_ME",
        "AssociationCount": "integer",
        "Arn": "string",
        "Name": "string",
        "DestinationArn": "string",
        "CreatorRequestId": "string",
        "CreationTime": "string"
    }
}
```

---

### 4.2 `delete-resolver-query-log-config`

Deletes a query logging configuration. Associated VPCs must be disassociated first.

**Synopsis:**
```bash
aws route53resolver delete-resolver-query-log-config \
    --resolver-query-log-config-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resolver-query-log-config-id` | **Yes** | string | -- | The config ID (max 64 chars) |

**Output Schema:**
Same as `create-resolver-query-log-config` output.

---

### 4.3 `get-resolver-query-log-config`

Gets details of a query logging configuration.

**Synopsis:**
```bash
aws route53resolver get-resolver-query-log-config \
    --resolver-query-log-config-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resolver-query-log-config-id` | **Yes** | string | -- | The config ID (max 64 chars) |

**Output Schema:**
Same as `create-resolver-query-log-config` output.

---

### 4.4 `list-resolver-query-log-configs`

Lists all query logging configurations. **Paginated.**

**Synopsis:**
```bash
aws route53resolver list-resolver-query-log-configs \
    [--filters <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | None | Filters. Shorthand: `Name=string,Values=string,string ...` |
| `--sort-by` | No | string | None | Field to sort by |
| `--sort-order` | No | string | None | `ASCENDING` or `DESCENDING` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Names:** `Name`, `CreatorRequestId`, `Status`, `OwnerId`, `ShareStatus`, `CreationTime`, `DestinationArn`, `AssociationCount`

**Output Schema:**
```json
{
    "ResolverQueryLogConfigs": [{"...same as ResolverQueryLogConfig above..."}],
    "TotalCount": "integer",
    "TotalFilteredCount": "integer",
    "NextToken": "string"
}
```

---

### 4.5 `associate-resolver-query-log-config`

Associates a query logging configuration with a VPC. DNS queries in the VPC will be logged.

**Synopsis:**
```bash
aws route53resolver associate-resolver-query-log-config \
    --resolver-query-log-config-id <value> \
    --resource-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resolver-query-log-config-id` | **Yes** | string | -- | The config ID (max 64 chars) |
| `--resource-id` | **Yes** | string | -- | The VPC ID (max 64 chars) |

**Output Schema:**
```json
{
    "ResolverQueryLogConfigAssociation": {
        "Id": "string",
        "ResolverQueryLogConfigId": "string",
        "ResourceId": "string",
        "Status": "CREATING|ACTIVE|ACTION_NEEDED|DELETING|FAILED",
        "Error": "NONE|DESTINATION_NOT_FOUND|ACCESS_DENIED|INTERNAL_SERVICE_ERROR",
        "ErrorMessage": "string",
        "CreationTime": "string"
    }
}
```

---

### 4.6 `disassociate-resolver-query-log-config`

Removes a query logging association from a VPC.

**Synopsis:**
```bash
aws route53resolver disassociate-resolver-query-log-config \
    --resolver-query-log-config-id <value> \
    --resource-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resolver-query-log-config-id` | **Yes** | string | -- | The config ID (max 64 chars) |
| `--resource-id` | **Yes** | string | -- | The VPC ID (max 64 chars) |

**Output Schema:**
Same as `associate-resolver-query-log-config` output.

---

### 4.7 `get-resolver-query-log-config-association`

Gets details of a query logging association.

**Synopsis:**
```bash
aws route53resolver get-resolver-query-log-config-association \
    --resolver-query-log-config-association-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resolver-query-log-config-association-id` | **Yes** | string | -- | The association ID (max 64 chars) |

**Output Schema:**
Same as `associate-resolver-query-log-config` output.

---

### 4.8 `list-resolver-query-log-config-associations`

Lists all query logging associations. **Paginated.**

**Synopsis:**
```bash
aws route53resolver list-resolver-query-log-config-associations \
    [--filters <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | None | Filters. Shorthand: `Name=string,Values=string,string ...` |
| `--sort-by` | No | string | None | Field to sort by |
| `--sort-order` | No | string | None | `ASCENDING` or `DESCENDING` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Names:** `ResolverQueryLogConfigId`, `ResourceId`, `Status`, `Error`, `CreationTime`

**Output Schema:**
```json
{
    "ResolverQueryLogConfigAssociations": [{"...same as association above..."}],
    "TotalCount": "integer",
    "TotalFilteredCount": "integer",
    "NextToken": "string"
}
```

---

### 4.9 `get-resolver-query-log-config-policy`

Gets the RAM resource-based policy for sharing a query logging configuration.

**Synopsis:**
```bash
aws route53resolver get-resolver-query-log-config-policy \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | The config ARN (max 255 chars) |

**Output Schema:**
```json
{
    "ResolverQueryLogConfigPolicy": "string"
}
```

---

### 4.10 `put-resolver-query-log-config-policy`

Sets the RAM resource-based policy for sharing a query logging configuration.

**Synopsis:**
```bash
aws route53resolver put-resolver-query-log-config-policy \
    --arn <value> \
    --resolver-query-log-config-policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | The config ARN (max 255 chars) |
| `--resolver-query-log-config-policy` | **Yes** | string | -- | IAM policy document as JSON string (max 30000 chars) |

**Output Schema:**
```json
{
    "ReturnValue": "boolean"
}
```
