# Outpost Resolvers

### 6.1 `create-outpost-resolver`

Creates a Route 53 Resolver on an AWS Outpost. Provides local DNS resolution for resources on the Outpost.

**Synopsis:**
```bash
aws route53resolver create-outpost-resolver \
    --creator-request-id <value> \
    --name <value> \
    --preferred-instance-type <value> \
    --outpost-arn <value> \
    [--instance-count <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--creator-request-id` | **Yes** | string | -- | Idempotency token (max 255 chars) |
| `--name` | **Yes** | string | -- | Friendly name (max 255 chars) |
| `--preferred-instance-type` | **Yes** | string | -- | EC2 instance type for Resolver (max 255 chars) |
| `--outpost-arn` | **Yes** | string | -- | ARN of the Outpost (max 255 chars) |
| `--instance-count` | No | integer | 4 | Number of EC2 instances (minimum 4) |
| `--tags` | No | list | None | Tags (max 200). Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "OutpostResolver": {
        "Arn": "string",
        "CreationTime": "string",
        "ModificationTime": "string",
        "CreatorRequestId": "string",
        "Id": "string",
        "InstanceCount": "integer",
        "PreferredInstanceType": "string",
        "Name": "string",
        "Status": "CREATING|OPERATIONAL|UPDATING|DELETING|ACTION_NEEDED|FAILED_CREATION|FAILED_DELETION",
        "StatusMessage": "string",
        "OutpostArn": "string"
    }
}
```

---

### 6.2 `delete-outpost-resolver`

Deletes a Resolver on Outpost.

**Synopsis:**
```bash
aws route53resolver delete-outpost-resolver \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | The Outpost Resolver ID (max 64 chars) |

**Output Schema:**
Same as `create-outpost-resolver` output.

---

### 6.3 `get-outpost-resolver`

Gets details of a Resolver on Outpost.

**Synopsis:**
```bash
aws route53resolver get-outpost-resolver \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | The Outpost Resolver ID (max 64 chars) |

**Output Schema:**
Same as `create-outpost-resolver` output.

---

### 6.4 `list-outpost-resolvers`

Lists all Resolvers on Outposts. **Paginated.**

**Synopsis:**
```bash
aws route53resolver list-outpost-resolvers \
    [--outpost-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--outpost-arn` | No | string | None | Filter by Outpost ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "OutpostResolvers": [{"...same as OutpostResolver above..."}],
    "NextToken": "string"
}
```

---

### 6.5 `update-outpost-resolver`

Updates a Resolver on Outpost (name or instance count).

**Synopsis:**
```bash
aws route53resolver update-outpost-resolver \
    --id <value> \
    [--name <value>] \
    [--instance-count <value>] \
    [--preferred-instance-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | The Outpost Resolver ID (max 64 chars) |
| `--name` | No | string | None | New friendly name (max 255 chars) |
| `--instance-count` | No | integer | None | New instance count (minimum 4) |
| `--preferred-instance-type` | No | string | None | New EC2 instance type (max 255 chars) |

**Output Schema:**
Same as `create-outpost-resolver` output.
